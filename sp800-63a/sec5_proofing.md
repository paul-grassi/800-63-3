
#<a name="ipv-section"></a> 5. Identity Proofing and Verification
**digital/non-cryptographic**

The following sections list the steps CSPs SHALL follow to identity proof an individual at each identity assurance level. The requirements for each identity assurance level are intended to ensure the claimed identity is the actual identity of the person attempting to enroll with the CSP and that scalable attacks are difficult to execute without significant time and cost. 


##5.2. Evidence Validation

The goal of identity validation is to determine the authenticity, validity, and accuracy of the identity evidence that a claimant provides.  Validation establishes the physical, live existence of the claimed identity.  Identity Validation is made up of two process steps: collecting the appropriate identity evidence and confirming the data is valid and related to an actual, live individual.

###5.2.1. Identity Evidence Characteristic Requirements

This section provides requirements on the acceptable properties and qualities of identity evidence that an applicant asserts remotely or in-person.

The following table lists qualities of identity evidence that are acceptable to begin identity proofing an individual. Unless otherwise noted, the evidence SHALL, at a minimum, meet all the properties to achieve a given strength.


####5.2.1.1. Scoring of Identity Evidence


|Strength|Properties of Identity Evidence|
|:---:|:------------------------------| 
|Unacceptable|The issuing source did not perform identity proofing |
|Weak|- The issuing source of the evidence performed no identity checking.<br><br>- The issuing process for the evidence means that it can reasonably be assumed to have been delivered into the possession of an individual.<br><br>- The evidence contains at least one reference number that uniquely identifies the person to whom it relates.|
|Adequate|- The issuing source of the evidence confirmed the claimed identity through an identity checking process.<br><br>- The issuing process for the evidence means that it can reasonably be assumed to have been delivered into the possession of the person to whom it relates.<br><br>- The evidence contains at least one reference number that uniquely identifies the person to whom it relates. <br>**OR**<br> the evidence contains a photograph, image, or biometric of the person to whom it relates.<br><br>- Where the evidence includes electronic information, that information is protected using cryptographic methods and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed. <br><br>- Where the evidence contains physical security features, it requires proprietary knowledge to be able to reproduce it.<br><br> -The issued evidence is unexpired.<br><br>-**Should we include anything about bar codes/checksums on id numbers, etc?**|
Strong|- The issuing source of the  evidence confirmed the applicants identity in a manner that complies with, or is aligned to, the Customer Identification Program guidelines established in response to the USA PATRIOT Act of 2001. **So only financial evidence meets this level?**<br><br>- The issuing process for the evidence ensured that it was delivered into the possession of the person to whom it relates.<br><br>  -The issued evidence contains at least one reference number that uniquely identifies the person to whom it relates.<br><br>- The applicants name on the issued evidence must be the name that the identity was officially known at the time of issuance. Pseudonyms, aliases and initials for last name and at least one first name are not permitted.<br><br>- The issued evidence contains a photograph/image/biometric of the person to whom it relates.<br>**OR**<br>ownership of the evidence can be confirmed through KBV.<br><br>- Where the issued evidence includes electronic information, that information is protected using cryptographic methods and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed.<br><br>  -Where the issued evidence contains physical security features, it requires proprietary knowledge and proprietary equipment to be able to reproduce it.<br><br>- The evidence is unexpired.|
|Superior|- The issuing source of the  evidence confirmed the applicants identity in a manner that complies with, or is aligned to, the Customer Identification Program guidelines established in response to the USA PATRIOT Act of 2001.<br><br>- The issuing source visually identified the applicant and performed further checks to confirm the existence of that identity.<br><br>The issuing process for the evidence ensured that it was delivered into the possession of the person to whom it relates.<br><br>The evidence contains at least one reference number that uniquely identifies person to whom it relates.<br><br>The applicants name on the evidence must be the name that the identity was officially known at the time of issuance. Pseudonyms, aliases and initials for firs and last names are not permitted.<br><br>The issued Identity Evidence contains a photograph/image of the person to whom it relates.<br><br>The evidence contains a biometric of the person to whom it relates.<br><br>Where the evidence includes electronic information, that information is protected using cryptographic methods and those methods ensure the integrity of the information and enable the authenticity of the issuing source to be confirmed.<br><br>Where the issued Identity Evidence is, or includes, a physical object it contains developed security features that requires proprietary knowledge and proprietary equipment to be able to reproduce it.<br><br>- The evidence is unexpired.|


###5.2.2. Validating Identity Evidence
Once identity evidence is obtained by the CSP, the accuracy, authenticity, and integrity of the evidence and related information is checked against authoritative sources in order to determine that the presented evidence is:  

* Genuine, authentic, and not a counterfeit, fake, or forgery.
* The information is correct  
* The information relates to a real individual  

#### 5.2.2.1. Methods to Perform Identity Evidence Validation
For each pice of evidence, the CSP determines a validation score.  The following table provides details the evidence validation properties required to achieve a given score.

|Strength|Method(s)|
|:---:|:------------------------------| 
|Unacceptable|Validation of the evidence failed.|
|Weak|All personal details from the evidence have been confirmed as valid by comparison with information held or published by an authoritative source.|
|Adequate|- All personal and evidence details have been confirmed as valid by comparison with information held/published by the issuing source <br> **OR** <br>- The evidence has been confirmed as genuine by trained personnel and appropriate equipment, confirming the integrity of physical security features <br> **OR** <br>- The issued evidence has been confirmed as genuine by confirmation of the integrity of cryptographic security features|
|Strong|- The evidence has been confirmed as genuine by trained personnel and appropriate equipment, confirming the integrity of the physical security features **OR** The evidence has been confirmed as genuine by confirmation of the integrity of cryptographic security features.<br>**AND**<br> - All personal details and evidence details have been confirmed as valid by comparison with information held/published by the issuing source **OR** evidence details have been confirmed as valid by comparison with information held/published by the issuing source|
|Superior|- The evidence has been confirmed as genuine by trained personnel and appropriate equipment including the integrity of any physical and cryptographic security features<br>**AND**<br>- All personal details and evidence details from the evidence have been confirmed as valid by comparison with information held/published by the issuing source|

##5.3. Identity Verification

The purpose of identity verification is to confirm that the presented identity evidence and information is associated to the individual making the claim.  

###5.3.1. Identity Verification Methods
The following table details the verification methods necessary to achieve appropriate identity verification.  

|Strength|Identity Verification Methods|
|:---:|:------------------------------| 
|Unacceptable|Unable to confirm that the applicant is the owner of the claimed identity.|
|Weak|The applicant has been confirmed as having access to the evidence provided to support the claimed identity.|
|Adequate|- The applicant’s ownership of the claimed identity has been confirmed by Knowledge Based Verification.  See [Section 5.3.2](#kbv)  for more details.<br>**OR**<br>- The applicant’s ownership of the claimed identity has been confirmed by a physical **or** biometric comparison of the applicant to the strongest piece of evidence provided.|
|Strong|- The applicant’s ownership of the claimed identity has been confirmed by physical comparison using a photograph/image **or** Biometric comparison of the Applicant to the strongest piece of evidence provided to support the claimed identity.<br>**AND**<br>- The applicant’s ownership of the claimed identity has been confirmed by Knowledge Based Verification See [Section 5.3.2](#kbv) for more details **or** a trusted referee confirms the identity of the claimant.|
|Superior|- The applicant’s ownership of the claimed identity has been confirmed by a physical comparison of the applicant using a photograph/image to the strongest pieces of evidence **or** by a biometric comparison of the applicant to the strongest piece of evidence provided to support the claimed identity.<br>**AND**<br>- The applicant’s ownership of the claimed identity has been confirmed by Knowledge Based VerificationSee [Section 5.3.2](#kbv) for more details.<br>**AND**<br>- The applicant’s ownership of the claimed identity has been confirmed by an interaction with the applicant via the postal address of record.|



###<a name="kbv"></a>5.3.2. Knowledge Based Verification Requirements

The following requirements apply to the identity verification steps for IAL 2 and 3. There are no restrictions for the use of KBV to complete identity resolution.

- A CSP SHALL allow a resolved, validated, or verified identity to opt-out of KBV in current and/or future attempts to identity proof.
- A CSP SHALL time out KBV sessions after 5 minutes of inactivity.  In cases of session timeout, the CSP SHALL restart the entire KBV process.
- A CSP SHOULD allow two (2) attempts for an applicant to complete the KBV.  CSPs MAY allow no more than three (3) attempts to complete the KBV.

- A CSP SHOULD verify knowledge of recent transactional history that the CSP is a participant to.  For example, verification of amount and confirmation number of a micro-deposit to a claimed and valid bank account.
- A CSP MAY perform KBV by asking questions of the claimed identity to demonstrate they are the owner of the claimed information. 
	- A CSP MAY use KBV to verify an identity if the CSP is, or maintains a relationship with, an authoritative source. In instances when the CSP leverages a third party authoritative source, the third party provider SHALL NOT assert the authoritative data to the CSP.  Rather, only boolean values, risk indicators, or error codes SHALL be returned.
	- A CSP MAY use KBV to verify an applicants identity against one (1) piece of validated identity evidence.  The CSP SHALL NOT use KBV to verify the application relationship to validated identity evidence.
	- KBV questions SHALL NOT be diversionary.  The CSP SHALL not allow answers to KBV questions be 'None of the Above', 'Not Applicable (N/A)', or similar be regarded as a correct answer.
	- A CSP SHALL NOT ask the same KBV questions in subsequent attempts.
	- A CSP SHALL ensure that one KBV question does not allude, hint, or provide an answer to a subsequent KBV question in any session or attempt by the applicant.
	- A CSP SHALL require a minimum of four (4) KBV questions each requiring a correct answer to successfully complete the KBV step.


###5.3.3. Trusted Referee Requirements
The CSP MAY determine to utilize trusted referees, such as notaries, legal guardian, or some other form of certified individual that can legally vouch for and/or act on behalf of the individual.  CSP MAY use a trusted referee for both remote and in-person processes.  

In some instances, the CSP MAY allow an individual that has successfully completed identity proofing with the same CSP to act as a trusted referee for another individual.  The CSP SHALL not accept this type of trusted referee verification at IAL3.

###5.3.4. Considerations for Minors and Other People with Unique Needs
Enrollment of minors under age 18, unable to meet the evidence requirements of identity proofing SHOULD involve a parent or legal adult guardian as a trusted referee as described in Section 5.3.4. Minors under age 13 require special consideration to ensure compliance with the Children's Online Privacy Protection Act of 1998, 15 USC 6501-6505 and 16 CFR Part 312.

Other individuals may have difficulty completing the identity proofing process based on various circumstances, such as not possessing the complete set of evidence requirements at a given IAL.  In these circumstances, the CSP SHOULD allow the applicant to be enrolled by a conservator or other person with power of attorney.


###5.3.5. Binding Requirements
See [800-63B, Section 6.1, Authenticator Binding](../sp800-63b/sec6_lifecycle.md/#binding) for instructions on binding authenticators to subscribers.  


##5.4 Requirements for Derived Credentials

CSP looks at a credential from a different CSP that it trusts, records the information, and issues its own credential and binds it to an authenticator. I'd call that identity proofing and include that in 63A.
Where the Applicant already possesses recognized authentication credentials a trusted CSP, the additional CSP may choose to identity proof the Claimant by verifying possession and control of the token associated with the credentials and issue a new derived credential.  The following details the proofing requirements for the CSP issuing a derived credential.
####5.4.1. General Requirements

1.  Before issuing any derived credential the CSP SHALL verify the original credential status and SHALL verify that the corresponding credential is possessed and controlled by the claimant.  
2. The CSP SHALL record the details of the original credential used as the basis for derived credential issuance. 
3. The CSP SHALL set the expiration of the new credential to the expiration of the original credential.
4. The CSP that issued the derived credential SHOULD notify the issuer of the original credential if the derived credential is revoked.

####5.4.2. IAL 2 Requirements

1. The CSP MAY perform remote or in-person proofing, but SHALL support at least one proofing process. 
2. The CSP SHALL check the expiration/revocation/termination status of the original credential weekly


####5.4.3. IAL 3 Requirements
1. The CSP SHALL perform in-person proofing only
2. The CSP SHALL check the expiration/revocation/termination status of the original credential daily
3. The CSP SHALL obtain and verify a copy of a biometric recorded when the original credential was issued. An example of such a biometric is the signed biometric data object, however if the biometric reference is not available from the original AAL 3 authenticator, it may be obtained elsewhere, as long as its authenticity is assured
4. Compare a fresh biometric sample obtained in person from the Applicant to the reference biometric retained from the original Level 3 credentials and determine that they match
5. Determine that the authenticator of the original credential meets all requirements of an IAL 3 authenticator



