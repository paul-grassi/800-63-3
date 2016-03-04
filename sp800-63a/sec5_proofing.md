## 5. Identity Proofing and Verification
The following sections list the requirements CSPs must follow to identity proof an individual at each identity assurance level. 

### Random Thoughts That May Become Requirements Later  

- Phone verification must not be via soft phones such as Google Voice or Skype.
- Human-in-the-loop for remote video proofing.  Perhaps if we allow at IAL3?
- CSP must determine the minimum attributes required to uniquely resolve an identity in their target population of potential users
- user can't pause session and return later. Or maybe allow a small window
- Visual match to photo id vs. combo of visual and automated match
- Subjects may remain pseudonymous at RP's at both IAL2 or 3.  pseudonymous pseudonymity
- Allow KYC in as IAL2?
- Allow mobile in as IAL2?
- Trusted referee (canadian language), vouchee (already proofed-kind of happens in places like HSIN) or notary





#### 5.1.1 General Requirements per Identity Assurance Level
For levels 2 and above:  
1. Records of registration SHALL be maintained.   
2. The CSP SHALL maintain a record of each individual whose identity has been verified and the steps taken to verify his or her identity, including any information collected from the Applicant in compliance with the sections below.  
3. The CSP SHALL have the capability to provide records of identity proofing to RPs if required<sup>[11](#note11)</sup>.  
4. The identity proofing and registration processes SHALL be performed according to applicable written policy or *practice statement* that specifies the particular steps taken to verify identities.  
5. The entire proofing transaction, including transactions that involve a 3rd party to the CSP, SHALL occur over a mutually authenticated protected session. Equivalently, the transaction SHOULD consist of time-stamped or sequenced messages and SHOULD signed by their source and SHOULD be encrypted for their recipient.  
6. Approved cryptography SHALL be used.    
7. The CSP SHALL be able to uniquely identify each Subscriber and any associated authenticators that may have been issued to that Subscriber.  
7. Personally identifiable information (PII) collected as part of the registration process SHALL be protected, and all privacy requirements shall be satisfied.  
8. PII collect SHALL be limited to the minimum data necessary to validate the existance of the claimed identity and associate it the claimed identity to the person providing identity evidence.  
8. The results of the identity proofing step (which may include background investigations of the Applicant) SHALL be protected to ensure source authentication, confidentiality, and integrity.  
9. Agencies MAY obtain additional confidence using additional risk mitigation measures so long as additional mitigation approaches do not substitute for the guidelines herein.
10. Agencies MAY consider partitioning the functionality of an e-authentication enabled application to allow functions requiring less stringent identification of the subscriber to be available at a lower identity assurance level, while other functions are available only at a higher identity assurance level.  
11. Knowledge based proofing (KBP) (sometimes referred to as knowledge-based authentication (KBA)) verifies the identity by testing the personal knowledge of the individual against information obtained from public databases. KBP SHALL NOT be used to verify the identity of a claimant.

>**For Assertion Chapter** The CSP shall be capable of conveying this information to Verifiers. At Level 1,
the name associated with the Subscriber is provided by the Applicant and
accepted without verification. At Level 2, the identifier associated
with the Subscriber may be pseudonymous but the RA or CSP shall retain
the actual identity of the Subscriber. In addition, pseudonymous Level 2
credentials shall be distinguishable from Level 2 credentials that
contain verified names.
At Level 3 and above, the name associated with the Subscriber shall be
verified. 

> **Do we want a process section ala GPG45**  At Level 2 and higher, the Applicant supplies his or her full legal name, an address of record, and date of birth, and may, subject to the policy of the RA or CSP, also supply other PII. Detailed level-by-level identity proofing requirements are stated in Table 3.

###5.1.2 Validation Requirements
The goal of identity validation is to determine the authenticity and validity of the identity evidence that a claimant provides.  Validation establishes the physical, live existence of the claimed idenity. 

####5.1.2.1 Identity Evidence Properties and Requirements
>UK Language The purpose of this element is to record the strength of the Identity Evidence provided by the Applicant in support of the Claimed Identity. The following Table demonstrates the properties of the Identity Evidence and the corresponding score for this element. The Identity Evidence must, as a minimum, meet all the properties defined for a particular strength to achieve that score.

This section provides guidelines and requirements on the acceptable properties and qualities of identity evidence that a claimant asserts to claim identity, and the requirements for evidence collected at each identity assurance level.

##### Properties of Identity Evidence
The following table lists qualities of various form and types of identity evidence that are acceptable to identity proof an individual.  IdentityFor remote identity proofing, the CSP SHOULD collect actual images of asserted identity evidence.  However, in instances when this is not possible or desirable, the CSP MAY collect identity evidence (and its corresponding data) via other means such as online forms or data files.

>Identity evidence, regardless of properties, MUST be issued by a legitimate 3rd party and MUST have authoritative records to validate evidence.

>Might want to just make the table additive:  All of 3 + these things...
>
>What about name change since we have content about issuance and name
>
>Score of 3 had 'if it includes security features' and 4 'must'.  Is that ok?

|Score|Properties of Identity Evidence|
|:---:|:------------------------------| 
|1|-The issuing source did not perform identity proofing<br>  -The issuing process for the evidence means that it can reasonably be assumed to have been delivered into the possession of an individual<br>  -The issued evidence contains at least one identification/reference number that uniquely identifies itself or the person to whom it relates; **or**<br>   the issued evidence contains a photograph/image/Biometric of the person to whom it relates|
|2|-The issuing source of the evidence confirmed the applicant’s identity through an identity checking process<br>  -The issuing process for the evidence means that it can reasonably be assumed to have been delivered into the possession of the person to whom it relates<br>-The issued evidence contains at least one identification/reference number that uniquely identifies itself or the person to whom it relates; **or**<br>  The issued evidence contains a photograph/image/Biometric of the person to whom it relates<br>  -Where the issued evidence is, or includes, electronic information, that information is protected using cryptographic methods and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed<br> -Where the issued evidence contains physical security features, it requires proprietary knowledge to be able to reproduce it|
3|-The issuing source of the evidence confirmed the applicant’s identity in a manner that complies with, or is aligned to, the Know Your Customer guidelines, of the US Patriot Act of 2001<br>  -The issuing process for the evidence ensured that it was delivered into the possession of the person to whom it relates<br>  -The issued evidence contains at least one identification/reference number that uniquely identifies itself or the person to whom it relates<br>  -The name value on the issued evidence must be the name that the identity was officially known at the time of issuance. Pseudonyms, aliases and initials for given and surnames are not permitted<br>  -The issued evidence contains a photograph/image/Biometric of the person to whom it relates; **or** The ownership or control of the issued evidence can be confirmed through **activity verification**<br>  -Where the issued evidence is, or includes, electronic information that information is protected using cryptographic methods and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed<br>  -Where the issued evidence contains physical security features, it requires proprietary knowledge and proprietary equipment to be able to reproduce it|
|4|-The issuing source of the evidence confirmed the applicant’s identity in a manner that complies with, or is aligned to, the Know Your Customer guidelines, of the US Patriot Act of 2001<br>  -The issuing source visually identified the applicant and performed further checks to confirm the existence of that identity<br>  -The issuing process for the evidence ensured that it was delivered into the possession of the person to whom it relates<br>  -The issued evidence contains at least one identification/reference number that uniquely identifies itself or the person to whom it relates<br>  -The name value on the issued evidence must be the name that the identity was officially known at the time of issuance. Pseudonyms, aliases and initials for forenames and surnames are not permitted<br>  -The issued evidence contains a photograph/image of the person to whom it relates<br>  -The issued evidence contains a fingerprint, facial, or iris biometric of the person to whom it relates<br>  -Where the issued evidence is, or includes, electronic information that information is protected using cryptographic methods and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed<br>  -The issued evidence contains physical security features that require proprietary knowledge and proprietary equipment to be able to reproduce it|

##### Identity Evidence Requirements per Identity Assurance Level
The following table lists the minimum requirement of identity evidence properties a CSP SHALL meet per IAL.  

|IAL|Requirements|
|:-:|:-----------|
|1|Identity evidence is not required|
|2|-2 pieces of evidence with a score of 3; **or**<br>  -1 piece of evidence with a score of 3<br>  -2 pieces of evidence with a score of 2|
|3|-1 piece of evidence with a score of 4<br>  -1 piece of evidence with a score of 3; **or**<br>  -2 pieces of evidence with a score of 3<br>  -1 piece of evidence with a score of 2|

####5.1.2.2 Identity Evidence Validation


###5.1.3 Verification Requirements
In some contexts, once an agency has met the minimum registration
requirements for an assurance level, the agency may choose to use
additional knowledge based authentication methods to increase confidence
in the registration process. For example, an Applicant could be asked to
supply non-public information on his or her past dealing with the agency
that could help confirm the Applicant’s identity.
###5.1.5. Requirements for Derived Credentials
CSP looks at a credential from a different CSP that it trusts, records the information, and issues its own credential and binds it to an authenticator. I'd call that identity proofing and include that in 63A.
Where the Applicant already possesses recognized authentication credentials a trusted CSP, the additional CSP may choose to identity proof the Claimant by verifying possession and control of the token associated with the credentials and issue a new derived credential.  The following details the proofing requirements for the CSP issuing a derived credential.1.  Before issuing any derived credential the CSP **shall** verify the original credential status and shall verify that the corresponding token is possessed and controlled by the Claimant.  
2. The CSP **shall** record the details of the original credential used as the basis for derived credential issuance. 
3. Issuance may be in person or remote. 

> 
**FOR JIM?**
The new CSP **shall** set the expiration of the new credential to the expiration of the original credential.
In situations where the authenticator does not support an automated expiration date, the status of the original credential **shall** be re-checked:
- At IAL1
- At IAL2
- At IAL3
at a later date (e.g. after a week) to confirm that it was not compromised at the time of issuance of the derived credential. (This guards against the case where an Attacker requests the desired credential before revocation information can be updated.) 
If the derived credential is revoked, the CSP that issued the derived credential may notify the issuer of the original credential, if the reason for revocation might motivate action by the issuer of the original credential and applicable law, regulation, and agreements permit such notification.  
**End for Jim**