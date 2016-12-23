<a name="sec6"></a>

<div class="breaker"></div>

# 6. Leveraging Antecedent Proofing Events

_This section is normative._

Possession of an authenticator, bound to an identity that is proofed at a given IAL, should allow a claimant to obtain additional authenticators, per CSP policy.  This section details requirements for two specific use cases:

1. A _claimant_ obtains a secondary, or derived authenticator, for use only within the limits and authorizations of the primary authenticator.  For example, this could be a derived PIV credential in federal use cases, or a temporary authenticator. See [Section 6.1](#dc) for more details.
2. An _applicant_ seeks to obtain another primary authenticator from a CSP that did not issue the original authenticator. For example, if an applicant wants to switch CSPs or have another authenticator at a new CSP for other uses (e.g. basic browsing vs. financial). See [Section 6.2](#prior) for more details.

## <a name="dc"></a> 6.1. Issuance Requirements for Derived Authenticators

This section applies when the secondary authenticator is directly tied to the authorizations of having, and proving possession of, a primary authenticator, typically issued by the same CSP.

### 6.1.1. General Requirements

1. Before issuance, the CSP SHALL verify the original authenticator status. The CSP SHALL NOT issue a derived authenticator if status indicates any type of termination, disablement, revocation, or expiration.
2. Before issuance, the CSP SHALL verify that the corresponding authenticator is possessed and controlled by the claimant.  
3. The derived authenticator SHALL be valid only as long as the subscriber is authorized to hold the original authenticator.
4. The CSP SHALL record the details of the original authenticator used as the basis for derived authenticator issuance. **MG: what are the details?**
5. The CSP SHOULD set the expiration of the derived authenticator to no later than the expiration of the primary authenticator. There are instances where the derived authenticator need not be directly tied to the expiration of the primary authenticator as the derived authenticator can provide authentication services in its place, for example, while the expiring primary credential is being replaced.
6. The CSP SHOULD issue the derived authenticator at an AAL that will supports the maximum IAL and AAL necessary for application(s) in which the dervied authenticator will be used. That is, the CSP need not issue a derived authenticator at the same AAL as the primary authenticator, but instead to SHOULD issue the derived authenticator at an AAL most appropriate for the risk of its intended use. The derived authenticator MAY be issued at an AAL higher than the IAL to which the primary authenticator is bound. For example, if the primary authenticator is bound to an IAL 2 credential, the authenticator that is issued could be AAL 2 or AAL 3 and would retain the binding to the IAL 2 credential. If, however, the derived authenticator is issued at AAL 1, the derived authenticator would retain a binding to the primary authenticator, but would only suppport IAL 1 in its use. The IAL the derived authenticator is bound to SHALL remain at the IAL of the primary authenticator.

>**MG: Tried to rewrite (6) to cover the notion that the CSP can't step up IAL in a derived, but could step down if so desired. Per our discussion, what I wrote at least as awful, probably more so, and likely incorrect, so we should probably revert or cut it back substantially.**


### 6.1.2. IAL 2 Requirements

- The CSP SHOULD check the status of the original authenticator weekly. 


### <a name="dc-ial3"></a>6.1.3. IAL 3 Requirements

1.  The CSP SHOULD perform in-person issuance. This is important if the CSP needs to explicitly provision the authenticator to a trusted device and in-person is the only mechanism to ensure delivery and assurance.
2. The CSP SHOULD check the status of the original authenticator daily.
3. The CSP SHALL obtain and verify a copy of a biometric recorded when the primary authenticator was issued. An example of such a biometric is the signed biometric data object, however if the biometric reference is not available from the original authenticator, it may be obtained elsewhere, as long as its authenticity is assured. **MG: How do we know it's an AAL 3 authenticator?**
4. The CSP SHALL compare a fresh biometric sample to the reference biometric obtained from the original, primary authenticator and determine that they match.
5. The CSP SHALL determine that the derived authenticator meets all the requirements of the primary authenticator's AAL.

>**MG: Leaving this but I think we can simplify.**

## <a name="prior"></a>6.2 Issuance Requirements for Accepting Results of Prior Proofing

Where the applicant already possesses an authenticator from a trusted CSP, the new CSP could choose to inherit the identity proofing performed in a prior encounter at the original CSP, by verifying possession and control of the authenticator associated with the original CSP.  The following details the requirements for the new CSP:

### 6.2.1. General Requirements

Unless otherwise specified, the term CSP in this section pertains to the new CSP that depends on the identity proofing performed by the original CSP.

1. Before issuance, the CSP SHALL verify that the corresponding authenticator is possessed and controlled by the claimant.
2. Before issuance, the CSP SHOULD verify the original authenticator status. The CSP SHALL NOT issue a derived authenticator if status indicates any type of termination, disablement, revocation, or expiration.
3. The CSP SHOULD maintain a written policy to query the authenticator status of the original CSP on a periodic basis.
4. The CSP SHALL determine the IAL associated with the original authenticator.
5. The CSP SHOULD determine the proofing process used by the originating CSP.  If the processes are materially different such that the CSP is unsure of the veracity of the proofing, the CSP SHOULD re-proof the identity.
6. The CSP SHOULD document and be able to assert the number of credential issuances removed from the original proofing event.  For example, if the applicant obtains a 3rd authenticator from a 3rd CSP, the 3rd CSP would document and assert "3" or "twice removed".  The assertion type, attribute name, and corresponding value is not in scope of this document.
7. The CSP MAY check the status of the original authenticator on a periodic basis. **MG: It's a bit odd to allow them to check something. Maybe this is better as a SHOULD?** 
8. The new authenticator SHOULD be issued at an AAL equivalent to the IAL the primary authenticator is bound to.  The new authenticator MAY be issued at an AAL higher than the IAL the primary authenticator is bound to. For example, if the primary IAL is 2, the new authenticator that is issued could be AAL2 or 3. The IAL the new authenticator is bound to SHALL remain at the IAL of the primary authenticator.

### 6.2.2. IAL 2 Requirements

- No additional requirements for IAL 2.

### 6.2.3. IAL 3 Requirements

1. All of the requirements of [Section 6.1.3.](#dc-ial3), in addition;
2. The CSP SHALL collect and record a biometric sample at the time of proofing (e.g., facial image or fingerprints) to ensure that the applicant cannot repudiate application.  See [Section 5.2.3](#biometric_use) of SP 800-63B for more detail on biometric collection.