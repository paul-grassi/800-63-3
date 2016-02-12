## 5. Identity Proofing and Verification

### Random Thoughts That May Become Requirements Later  

- Phone verification must not be via soft phones such as Google Voice or Skype.
- Human-in-the-loop for remote video proofing.  Perhaps if we allow at IAL3?
- CSP must determine the minimum attributes required to uniquely resolve an identity in their target population of potential users
- user can't pause session and return later. Or maybe allow a small window
- Visual match to photo id vs. combo of visual and automated match



### 5.1 Registration and Issuance Assurance Levels
The following sections list the NIST recommendations for registration
and issuance for the four levels corresponding to the OMB guidance. As
noted in the OMB guidance, Levels 1 and 2 recognize the use of
pseudonymous credentials. When pseudonymous credentials are used to
imply membership in a group, the level of proofing shall be consistent
with the requirements for the credential of that level. Explicit
requirements for registration processes for pseudonymous credentials are
not specified, as they are unique to the membership criteria for each
specific group.

#### 5.1.1 General Requirements per Assurance Level
For levels 2 and above records of registration shall be maintained
either by the RA or by the CSP, depending on the context. Either the RA
or the CSP shall maintain a record of each individual whose identity has
been verified and the steps taken to verify his or her identity,
including any information collected from the Applicant in compliance
with the sections below. The CSP shall have the capability to provide
records of identity proofing to RPs if required<sup>[11](#note11)</sup>. The identity
proofing and registration processes shall be performed according to
applicable written policy or *practice statement* that specifies the
particular steps taken to verify identities.

For Levels 2 and above, if the RA and CSP are remotely located and
communicate over a network, the entire registration transaction between
the RA and CSP shall occur over a mutually authenticated protected
session. Equivalently, the transaction may consist of time-stamped or
sequenced messages signed by their source and encrypted for their
recipient. In either case, Approved cryptography is required.

The CSP shall be able to uniquely identify each Subscriber and the
associated tokens and the credentials issued to that Subscriber. The CSP
shall be capable of conveying this information to Verifiers. At Level 1,
the name associated with the Subscriber is provided by the Applicant and
accepted without verification. At Level 2, the identifier associated
with the Subscriber may be pseudonymous but the RA or CSP shall retain
the actual identity of the Subscriber. In addition, pseudonymous Level 2
credentials shall be distinguishable from Level 2 credentials that
contain verified names.

At Level 3 and above, the name associated with the Subscriber shall be
verified. At all levels, personally identifiable information (PII)
collected as part of the registration process shall be protected, and
all privacy requirements shall be satisfied.

The following text establishes registration requirements specific to
each level, except as noted in the following subsections. There are no
level-specific requirements at Level 1. Both in-person and remote
registration are permitted for Levels 2 and 3. Remote registration
requirements are designed to permit fully automated solutions. However,
implementations may also leverage call centers or online assistance as a
substitute or complement for fully automated solutions. Explicit
requirements are specified for each scenario in Levels 2 and 3. At Level
4, only in-person registration is permitted.

At Level 2 and higher, the Applicant supplies his or her full legal
name, an address of record, and date of birth, and may, subject to the
policy of the RA or CSP, also supply other PII. Detailed level-by-level
identity proofing requirements are stated in Table 3.

In some contexts, once an agency has met the minimum registration
requirements for an assurance level, the agency may choose to use
additional knowledge based authentication methods to increase confidence
in the registration process. For example, an Applicant could be asked to
supply non-public information on his or her past dealing with the agency
that could help confirm the Applicant’s identity.

The sensitive data collected during the registration and identity
proofing stage shall be protected at all times (i.e., transmission,
storage) to ensure their security and confidentiality. Additionally, the
results of the identity proofing step (which may include background
investigations of the Applicant) have to be protected to ensure source
authentication, confidentiality, and integrity.

###5.1.2 Validation Requirements
###5.1.3 Verification Requirements
###5.1.5. Requirements for Derived Credentials

>**Old Footnote: This document does not require or prevent CSPs from linking the expiration of the original and derived credentials. However, where the revocation status is tightly coupled, this may simplify revocation procedures.  
I think we should require this.**

Where the Applicant already possesses recognized authentication credentials, the CSP may choose to identity proof the Claimant by verifying possession and control of the token associated with the credentials and issue a new derived credential.Before issuing any derived credential the CSP shall verify the original credential status and shall verify that the corresponding token is possessed and controlled by the Claimant. The status of the original credential should be re-checked at a later date (e.g. after a week) to confirm that it was not compromised at the time of issuance of the derived credential. (This guards against the case where an Attacker requests the desired credential before revocation information can be updated.) Further, the CSP shall record the details of the original credential used as the basis for derived credential issuance. If the derived credential is revoked, the CSP that issued the derived credential may notify the issuer of the original credential, if the reason for revocation might motivate action by the issuer of the original credential and applicable law, regulation, and agreements permit such notification.The CSP may issue a derived level 4 credential for a suitable Level 4 capable token, based on an original level 4 credential. Before issuing the derived Level 4 credential, the CSP shall:  
- Obtain and verify a copy of a biometric recorded when the original credential was issued. An example of such a biometric is the signed biometric data object on a PIV card, however if the biometric reference is not available from the Level 4 token, it may be obtained elsewhere, as long as its authenticity is assured;- Compare a fresh biometric sample obtained in person from the Applicant to the reference biometric retained from the original Level 4 credentials and determine that they match, and;- Determine that the token that contains the token secret associated with the derived credential meets the requirements of Table 6 for a Level 4 token.  

The CSP may issue a Level 3 derived credential based on proof of possession of a Level 4 token. Issuance may be in person or remote. If Level 3 credentials are electronically transmitted, or physically shipped with a token to a claimant, then token activation shall require proof of possession of both the derived token and the original Level 4 token.
The CSP may issue a Level 2 derived credential based on proof of possession of a Level 3 or 4 token. Issuance may be in person or remote. If Level 2 credentials are electronically transmitted, or physically shipped with a token to a claimant, then token activation shall require proof of possession of both the derived token and the original Level 3 or Level 4 token.
In some cases, there may be a desire to tightly couple the revocation status of the derived credential to the original. In this case, it is the responsibility of the CSP that issued the derived credential to ensure that a tight coupling is maintained. For example, the issuer of the derived credential could regularly monitor the status of the primary credential.