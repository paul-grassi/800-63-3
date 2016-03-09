##<a name="ipv-section"></a> 5. Identity Proofing and Verification

**Credential or Authenticator?  
User, applicant, claimant, subject?**

The following sections list the requirements CSPs must follow to identity proof an individual at each identity assurance level. The requirements for each identity assurance level are derived to ensure the claimed identity is the actual identity of the person attempting to gain access to a system **and** at-scale attacks are difficult to execute without significant time and cost. 

### Random Thoughts That May Become Requirements Later  


- Human-in-the-loop for remote video proofing.  Perhaps if we allow at IAL3?
- user can't pause session and return later. Or maybe allow a small window
- Visual match to photo id vs. combo of visual and automated match
- Subjects may remain pseudonymous at RP's at both IAL2 or 3.  pseudonymous pseudonymity
- Allow KYC in as IAL2?
- Allow mobile in as IAL2?  
- Deprecate KYC single factor in the future?
- SMS Laundering  
- KYC Reg Sucks.  Red flags rule (identity theft)? Grandfather banks and mno, with TFA, to allow the as valid identities.
- Reasonable matching (see canada)
- Should we do tiers within each IAL just to give agencies a chance to select psuedonymous vs identified.  And then enforce this on the CSP side.  Log in with IAL 2/3, but don't give away jack about me.
- Digital license?  Already covered by the new requirements?
- Training requirements for proofers.  More than just training, it could be security clearance as well.

## 5.1 Process Overview
* The CSP SHALL collect full legal name, an address of record, and date of birth from the applicant.

Include process overview mapped to sections.  This is especially important with the new binding chapter.

## 5.2 General Requirements per Identity Assurance Level

For levels 2 and above:  

1. Records of registration SHALL be maintained.  
2. The CSP SHALL maintain a record of each individual whose identity has been verified and the steps taken to verify his   or her identity, including any information collected from the Applicant in compliance with the sections below.  
3. The CSP SHALL have the capability to provide records of identity proofing to RPs if required<sup>[11](#note11)</sup>.
4. The identity proofing and registration processes SHALL be performed according to applicable written policy or *practice statement* that specifies the particular steps taken to verify identities.
5. The entire proofing transaction, including transactions that involve a 3rd party to the CSP, SHALL occur over a mutually authenticated protected session. Equivalently, the transaction SHOULD consist of time-stamped or sequenced messages and SHOULD signed by their source and SHOULD be encrypted for their recipient.  
6. Approved cryptography SHALL be used.  
7. The CSP SHALL be able to uniquely identify each Subscriber and any associated authenticators that may have been issued to that Subscriber.  
8. The CSP SHALL record the identification/reference number of the presented identity evidence.
9. **The CSP SHALL NOT record an image/scan/copy of the presented identity evidence.**  
10. Personally identifiable information (PII) collected as part of the registration process SHALL be protected, and all privacy requirements shall be satisfied.  
11. PII collect SHALL be limited to the minimum data necessary to validate the existance of the claimed identity and associate it the claimed identity to the person providing identity evidence.  
12. The results of the identity proofing step (which may include background investigations of the Applicant) SHALL be protected to ensure source authentication, confidentiality, and integrity.  
13. Agencies MAY obtain additional confidence using additional risk mitigation measures so long as additional mitigation approaches do not substitute for the guidelines herein.
14. Agencies MAY consider partitioning the functionality of an e-authentication enabled application to allow functions requiring less stringent identification of the subscriber to be available at a lower identity assurance level, while other functions are available only at a higher identity assurance level.  
15. Knowledge based proofing (KBP) (sometimes referred to as knowledge-based authentication (KBA)) verifies the identity by testing the personal knowledge of the individual against information obtained from public databases. KBP SHALL NOT be used to verify the identity of a claimant. KBP MAY be used to resolve to a unique, claimed identity.
16. Exact matches of personal information may be difficult to achieve to due multiple factors. The CSP MAY employ appropriate matching alogrithms to account for differences in personal information and other relevant proofing data across multiple pieces of evidence, authoritative records, and 3rd party records. Matching algorithms used SHALL be publicly avialable.

 

##5.3 Validation Requirements
The goal of identity validation is to determine the authenticity and validity of the identity evidence that a claimant provides.  Validation establishes the physical, live existence of the claimed idenity. 

###5.3.1 Identity Evidence Properties and Requirements
>UK Language The purpose of this element is to record the strength of the Identity Evidence provided by the Applicant in support of the Claimed Identity. The following Table demonstrates the properties of the Identity Evidence and the corresponding score for this element. The Identity Evidence must, as a minimum, meet all the properties defined for a particular strength to achieve that score.

This section provides guidelines and requirements on the acceptable properties and qualities of identity evidence that a claimant asserts to claim identity, and the requirements for evidence collected at each identity assurance level.

#### Properties of Identity Evidence
The following table lists qualities of various form and types of identity evidence that are acceptable to identity proof an individual. However, in instances when this is not possible or desirable, the CSP MAY collect identity evidence (and its corresponding data) via other means such as online forms or data files.

~~~
Identity evidence, regardless of properties, MUST be issued by a legitimate 3rd party and MUST have authoritative records to validate evidence.

Might want to just make the table additive:  All of 3 + these things...

What about name change since we have content about issuance and name

Score of 3 had 'if it includes security features' and 4 'must'.  Is that ok?
~~~

|Score|Properties of Identity Evidence|
|:---:|:------------------------------| 
|1|-The issuing source did not perform identity proofing<br>  -The issuing process for the evidence means that it can reasonably be assumed to have been delivered into the possession of an individual<br>  -The issued evidence contains at least one identification/reference number that uniquely identifies itself or the person to whom it relates; **or**<br>   the issued evidence contains a photograph/image/Biometric of the person to whom it relates|
|2|-The issuing source of the evidence confirmed the applicant’s identity through an identity checking process<br>  -The issuing process for the evidence means that it can reasonably be assumed to have been delivered into the possession of the person to whom it relates<br>-The issued evidence contains at least one identification/reference number that uniquely identifies itself or the person to whom it relates; **or**<br>  The issued evidence contains a photograph/image/Biometric of the person to whom it relates<br>  -Where the issued evidence is, or includes, electronic information, that information is protected using cryptographic methods and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed<br> -Where the issued evidence contains physical security features, it requires proprietary knowledge to be able to reproduce it|
3|-The issuing source of the evidence confirmed the applicant’s identity in a manner that complies with, or is aligned to, the Know Your Customer guidelines, of the US Patriot Act of 2001<br>  -The issuing process for the evidence ensured that it was delivered into the possession of the person to whom it relates<br>  -The issued evidence contains at least one identification/reference number that uniquely identifies itself or the person to whom it relates<br>  -The name value on the issued evidence must be the name that the identity was officially known at the time of issuance. Pseudonyms, aliases and initials for given and surnames are not permitted<br>  -The issued evidence contains a photograph/image/Biometric of the person to whom it relates; **or** The ownership or control of the issued evidence can be confirmed through **activity verification**<br>  -Where the issued evidence is, or includes, electronic information that information is protected using cryptographic methods and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed<br>  -Where the issued evidence contains physical security features, it requires proprietary knowledge and proprietary equipment to be able to reproduce it|
|4|-The issuing source of the evidence confirmed the applicant’s identity in a manner that complies with, or is aligned to, the Know Your Customer guidelines, of the US Patriot Act of 2001<br>  -The issuing source visually identified the applicant and performed further checks to confirm the existence of that identity<br>  -The issuing process for the evidence ensured that it was delivered into the possession of the person to whom it relates<br>  -The issued evidence contains at least one identification/reference number that uniquely identifies itself or the person to whom it relates<br>  -The name value on the issued evidence must be the name that the identity was officially known at the time of issuance. Pseudonyms, aliases and initials for forenames and surnames are not permitted<br>  -The issued evidence contains a photograph/image of the person to whom it relates<br>  -The issued evidence contains a fingerprint, facial, or iris biometric of the person to whom it relates<br>  -Where the issued evidence is, or includes, electronic information that information is protected using cryptographic methods and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed<br>  -The issued evidence contains physical security features that require proprietary knowledge and proprietary equipment to be able to reproduce it|

#### Identity Evidence Requirements per Identity Assurance Level
The following table lists the minimum requirement of identity evidence properties a CSP SHALL meet per IAL.  


|IAL|Requirements|
|:-:|:-----------|
|1|Identity evidence is not required|
|2|-2 pieces of evidence with a score of 3; **or**<br>  -1 piece of evidence with a score of 3<br>  -2 pieces of evidence with a score of 2|
|3|-1 piece of evidence with a score of 4<br>  -1 piece of evidence with a score of 3; **or**<br>  -2 pieces of evidence with a score of 3<br>  -1 piece of evidence with a score of 2|


####5.1.2.2 Identity Evidence Validation


###5.1.3 Verification Requirements
- Phone (cell SMS or voice) verification must not be via soft phones such as Google Voice or Skype.
- KBA allowed if temporal **and** spacial
- Prove control over email, however email MUST be protected at the same AAL as the IAL.  For example, if proofing is done according to IAL 2, the email must be protected with an authenticator at AAL2. KYC banks get a pass.
- Only allow credit records at higher IAL for 1 of the presented identity evidence materials.
- Trusted referee (canadian language), vouchee (already proofed-kind of happens in places like HSIN) or notary
- Once a CSP has met the minimum requirements for an IAL:
	- The CSP MAY use additional risk-based/indicators/context/adaptive  authentication methods to increase confidence in identity verification.
	- If the CSP is an authoritative source, the only entity that maintains control over specific data, and the data has never been aggregated by a 3rd party, the CSP MAY use knowledge based authentication verification to increase confidence in identity verification.

###5.1.4 Binding Requirements (continuation)
Registration, identity proofing, token creation/issuance, and credential issuance are separate processes that can be broken up into a number of separate physical encounters or electronic transactions. (Two electronic transactions are considered to be separate if they are not part of the same protected session.) These transactions may span distict organizational entities, and in some instance, especially with the separation of credential from proofing, a subject may already possess authenticators at a suitable AAL without having been proofed at the equivalent IAL. For example, a user may have a two-factor credential from a social network provider, considered AAL2 and IAL1, and would like to use those credentials at a relying party that requires IAL2.

The following sections provide requirements for ensuring the integrity of identity proofing when proofing and/or credential issuance do not occur within the same session and/or organizational entity.

####5.1.4.1 Identity Proofing Transaction Binding
The following requirements apply when the applicant does not already have an existing credential with the CSP or any other CSP that supports federation. **this language sucks**


#####IAL1 Requirements
No specific requirements, however effort should be made by the CSP to uniquely identify the claimant and provide a suitable user experience such that risk of establishing multiple authenticators is limited.

#####IAL2 Requirements
1. For remote transactions:
	2. The applicant SHALL identify himself/herself in each new transaction by presenting a temporary secret which was established during a prior transaction or encounter, or sent to the Applicant’s phone number, email address, or physical address of record.
	3. Permanent secrets shall only be issued to the Applicant within a protected session.
2. For physical transactions:
	3. The applicant SHALL identify himself/herself in person by either using a secret as described above, or through the use of a biometric that was recorded during a prior encounter.
	4. Temporary secrets SHALL not be reused.
	5. If the CSP issues permanent secrets during a physical transaction, then they SHALL be loaded locally onto a physical device that is issued in person to the applicant or delivered in a manner that confirms the address of record.

#####IAL3 Requirements
1. Only physical encounters SHALL apply. 
2. The applicant SHALL identify himself/herself in person in each new physical transaction through the use of a biometric that was recorded during a prior encounter.
3. If the CSP issues permanent secrets, then they SHALL be loaded locally onto a physical device that is issued in person or delivered in a manner that confirms the address of record.

####5.1.4.2 Binding Identity to an Authenticator
In some instances, a user may already have an existing token, from the CSP with whom the user wishes perform identity proofing, or from another CSP.  The following requirements apply when a user choses to increase IAL.

1. The CSP MAY accept an existing authenticator at or above the desired IAL
2. The CSP SHALL require the user to authenticate using their existing authenticate
3. The CSP SHALL execute all required identity proofing processes for the desired IAL
4. If the user successfully completes identity proofing, the CSP SHALL issue a temporary secret that confirms address of record or require the user to register their own authenticator only after proving proof of possession (for example, activating a private key by physically touching the token)
5. The temporary secret SHALL expire within **XXXXX**
6. What to do with AAL2?
7. What to do with AAL1?

* Come with AAL2 or
* Proofing at IAL2 with AAL1 BUT
* issue a temporary secret OOB (includes text, email, phone, address, paper, qrcode or proof of posession of authenticator within the proofing session 
* Come back at AAL2 and bind with temporary secret
* time the secret out


###5.1.5. Requirements for Derived Credentials
```**Jim credential lifecycle requirements for expiration?**```
  
Where the Applicant already possesses recognized authentication credentials from a trusted CSP, the additional CSP may choose to identity proof the Claimant by verifying possession and control of the token associated with the credentials and issue a new derived credential.  The following details the proofing requirements for the CSP.

####5.1.5.1 General Requirements
1.  Before issuing any derived credential the CSP SHALL verify the original credential status and SHALL verify that the corresponding credential is possessed and controlled by the claimant.  
2. The CSP SHALL record the details of the original credential used as the basis for derived credential issuance. 
3. The CSP SHALL set the expiration of the new credential to the expiration of the original credential.
4. The CSP that issued the derived credential SHOULD notify the issuer of the original credential if the derived credential is revoked.

####5.1.5.1 IAL3 Requirements
1. The CSP MAY perform remote or in-person proofing, but SHALL support at least one proofing process. 
2. The CSP SHALL check the expiration/revocation/termination status of the original credential weekly


####5.1.5.1 IAL4 Requirements
1. The CSP SHALL perform in-person proofing only
2. The CSP SHALL check the expiration/revocation/termination status of the original credential daily
3. The CSP SHALL obtain and verify a copy of a biometric recorded when the original credential was issued. An example of such a biometric is the signed biometric data object, however if the biometric reference is not available from the original AAL 3 authenticator, it may be obtained elsewhere, as long as its authenticity is assured
4. Compare a fresh biometric sample obtained in person from the Applicant to the reference biometric retained from the original Level 4 credentials and determine that they match
5. Determine that the authenticator of the original credential meets all requirements of an IAL3 authenticator