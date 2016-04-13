
#<a name="ipv-section"></a> 5. Identity Proofing and Verification

The following sections list the steps CSPs SHALL follow to identity proof an individual at each identity assurance level. The requirements for each identity assurance level are intended to ensure the claimed identity is the actual identity of the person attempting to enroll with the CSP and that scalable attacks are difficult to execute without significant time and cost. 


##5.2. Evidence Validation

The goal of identity validation is to determine the authenticity, validity, and accuracy of the identity evidence that a claimant provides.  Validation establishes the physical, live existence of the claimed identity.  Identity Validation is made up of two process steps: collecting the appropriate identity evidence and confirming the data is valid and related to an actual, live individual.

###5.2.1. Identity Evidence Characteristic Requirements

This section provides requirements on the acceptable properties and qualities of identity evidence that a claimant asserts remotely at IAL 2 or presents in-person at IAL 2 or 3.

The following table lists qualities of the various form and types of identity evidence that are acceptable to begin identity proofing an individual. The evidence MUST, at a minimum, meet all the properties defined to achieve that score.

> **Open items for Jim to help decide:**  
Identity evidence, regardless of properties, MUST be issued by a legitimate third party and MUST have authoritative records to validate evidence.  
Might want to just make the table additive:  All of 3 + these things...  
What about name change since we have content about issuance and name  
Score of 3 had 'if it includes security features' and 4 'must'.  Is that ok?

####5.2.1.1. Scoring of Identity Evidence


|Score|Properties of Identity Evidence|
|:---:|:------------------------------| 
|0|The issuing source did not perform identity proofing |
|2|- The issuing source of the evidence has confirmed the claimed identity through an identity checking process.<br>- The issuing process for the evidence means that it can reasonably be assumed to have been delivered into the possession of the person to whom it relates.<br>- The issued evidence contains at least one identification/reference number that uniquely identifies itself or the person to whom it relates, or contains a photograph, image, or biometric of the person to whom it relates.<br>- Where the issued evidence is, or includes, electronic information, that information is protected using cryptographic methods and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed. ***This means you can't use information on a magnetic stripe unless it's signed***<br>- Where the issued evidence contains physical security features, it requires proprietary knowledge to be able to reproduce it.<br> -The issued evidence is unexpired.|
3|- The issuing source of the  evidence confirmed the claimed identity in a manner that complies with, or is aligned to, the Customer Identification Program guidelines established in response to the USA PATRIOT Act of 2001 ***So only financial evidence meets this level?***<br>- The issuing process for the evidence ensured that it was delivered into the possession of the person to whom it relates<br>  -The issued evidence contains at least one identification/reference number that uniquely identifies itself or the person to whom it relates<br>- The name value on the issued evidence must be the name that the identity was officially known at the time of issuance. Pseudonyms, aliases and initials for surname and at least one given name are not permitted<br>- The issued evidence contains a photograph/image/biometric of the person to whom it relates<br>- Where the issued evidence is, or includes, electronic information that information is protected using cryptographic methods and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed<br>  -Where the issued evidence contains physical security features, it requires proprietary knowledge and proprietary equipment to be able to reproduce it<br>- The issued evidence is unexpired|
|4|- Meets all of the requirements to achieve a score of 3, above.<br>- The issuing source visually identified the applicant and performed further checks to confirm the existence of that identity<br>- The issuing process for the evidence ensured that it was delivered into the possession of the person to whom it relates<br>- The issued evidence contains a fingerprint, facial, or iris biometric of the person to whom it relates. ***How is facial biometric different from photo/image?***<br>- The issued evidence contains physical security features that require proprietary knowledge and proprietary equipment to be able to reproduce it.|


###5.2.2. Validating Identity Evidence
Once identity evidence is obtained by the CSP, the accuracy, authenticity, and integrity of the evidence and related information is checked against authoritative sources in order to determine that the presented evidence is:  

* Genuine, authentic, and not a counterfeit, fake, or forgery.
* The information is correct  
* The information relates to a real individual  
* The information relates to the correct individual  ***But isn't this verification?***

#### 5.2.2.1. Methods to Perform Identity Evidence Validation
For each pice of evidence, the CSP determines a validation score.  The following table provides details the evidence validation properties required to achieve a given score.

|Score|Method(s)|
|:---:|:------------------------------| 
|0|Validation of the evidence failed.|
|1|All personal details from the evidence have been confirmed as valid by comparison with information held or published by a trusted third party data service.|
|2|- All personal details from the evidence have been confirmed as valid by comparison with information held/published by the Issuing/Authoritative Source <br> **or** <br>- The issued evidence has been confirmed as genuine by trained personnel using their skill and appropriate equipment, confirming the integrity of physical security features <br> **or** <br>- The issued evidence has been confirmed as genuine by confirmation of the integrity of cryptographic security features|
|3|- The issued evidence has been confirmed as genuine by trained personnel using their skill and appropriate equipment, and confirmed the integrity of the physical security features **or** The issued evidence has been confirmed as genuine by confirmation of the integrity of cryptographic security features.<br>**and**<br> - All personal details and evidence details have been confirmed as valid by comparison with information held/published by the Issuing/Authoritative Source **or** evidence details from the evidence have been confirmed as not known to be invalid by comparison with information held/published by the Issuing Source/Authoritative Source|
|4|- The issued evidence has been confirmed as genuine by trained personnel using their skill and appropriate equipment including the integrity of any cryptographic security features<br>**and**<br>- All personal details and evidence details from the evidence have been confirmed as valid by comparison with information held/published by the Issuing Source/Authoritative Source|

***Above: This is hard to follow. Are "skill and appropriate equipment" needed for physical features, cryptographic features, or both?***


##5.3. Identity Verification

The purpose of identity verification is to confirm that the presented identity evidence and attributes relates to the person making the claim.  

###5.3.1. Identity Verification Methods
The following table details the verification methods necessary to achieve appropriate identity verification.


|Score|Identity Verification Methods|
|:---:|:------------------------------| 
|0|Unable to confirm that the applicant is the owner of the claimed identity.|
|1|The Applicant has been confirmed as having access to the evidence provided to support the claimed identity.|
|2|- The Applicant’s ownership of the Claimed Identity has been confirmed by Dynamic Knowledge Based Verification <br>**or**<br>- The Applicant’s ownership of the Claimed Identity has been confirmed by proving control of an account. Account control MAY be verified by depositing a small but random amount of funds to the applicant's account and verifying the applicant's ability to identify that transaction and its amount.<br>**or**<br>- The Applicant’s ownership of the Claimed Identity has been confirmed by a physical or biometric comparison of the Applicant to the strongest piece of Identity Evidence provided to support the Claimed Identity<br>|
|3|- The Applicant’s ownership of the Claimed Identity has been confirmed by physical comparison using a photograph/image **or** Biometric comparison of the Applicant to the strongest piece of Identity Evidence provided to support the Claimed Identity<br>**AND**<br>- The Applicant’s ownership of the Claimed Identity has been confirmed by Dynamic Knowledge Based Verification **or** proving control of an account **or** a trusted referee confirms the identity of the claimant|
|4|- The Applicant’s ownership of the Claimed Identity has been confirmed by a physical comparison of the Applicant using a photograph/image to the strongest pieces of Identity Evidence **OR** By a Biometric comparison of the Applicant to the strongest piece of Identity Evidence provided to support the Claimed Identity<br>**AND**<br>- The Applicant’s ownership of the Claimed Identity has been confirmed by both a Dynamic Knowledge Based Verification **and** proving control of an account<br>**AND**<br>- The Applicant’s ownership of the Claimed Identity has been confirmed by an interaction with the Applicant via the declared address|



###<a name="kbv"></a>5.3.3. Knowledge Based Verification Requirements

- Remote sessions SHALL time out after 5 minutes of inactivity
**For Paul to update**

KBV MAY be used if the CSP is, or maintains a relationship with, an authoritative source, the authoritative source is the only entity that maintains control over specific data, the data has never been aggregated or accessed by a third party.  In instances with the CSP leverages and third party for KBV, the third party provide SHALL NOT provide the authoritative data to the CSP.  Rather, only boolean values or error codes SHALL be returned.  

- Enrollment codes sent to a mobile phone (cell SMS or voice) verification must not be via soft phones such as Google Voice or Skype.
- Shared devices? Is this solved by in-records check?
- KBA allowed if temporal **and** spacial

- Trusted referee (canadian language), vouchee (already proofed-kind of happens in places like HSIN) or notary

- Capture biometric at IAL3

- Once a CSP has met the minimum requirements for an IAL:
	- The CSP MAY use additional risk-based/indicators/context/adaptive  authentication methods to increase confidence in identity verification.
	- If the CSP is an authoritative source, the only entity that maintains control over specific data, and the data has never been aggregated or accessed by a third party, the CSP MAY use knowledge based authentication verification to increase confidence in identity verification.

###5.3.4. Trusted Referee Requirements
The CSP MAY determine to utilize trusted referees, such as notaries, legal guardian, or some other form of certified individual that can legally vouch for and/or act on behalf of the individual.  CSP MAY use a trusted referee for both remote and in-person processes.  

In some instances, the CSP MAY allow an individual that has successfully completed identity proofing with the same CSP to act as a trusted referee for another individual.  The CSP SHALL not accept this type of trusted referee verification at IAL3.

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



##5.5 Considerations for Minors and Other Vulnerable People

Enrollment of minors under age 18 normally requires the involvement of a parent or legal adult guardian as trusted referee as described in Section 5.3.4. Minors under age 13 require special consideration to ensure compliance with the Children's Online Privacy Protection Act of 1998, 15 USC 6501-6505 and 16 CFR Part 312.

Other vulnerable persons may be enrolled by a conservator or other person with power of attorney.
