
#<a name="ipv-section"></a> 5. Identity Proofing and Verification

The following sections list the steps CSPs SHALL follow to identity proof an individual at each identity assurance level. The requirements for each identity assurance level are intended to ensure the claimed identity is the actual identity of the person attempting to enroll with the CSP and that at-scale attacks are difficult to execute without significant time and cost. ***What sort of at-scale attacks?***

## 5.1. General Requirements

The following requirements apply to any CSP performing identity proofing at IAL 2 or 3. 

**@privacy:** 

1. The CSP SHALL collect and maintain a record of the full legal name, date of birth, gender, and an address of record of the applicant.  
2. The CSP SHALL record the types of identity evidence presented in the proofing process, including any identification and reference number. The CSP SHALL NOT record an image, scan, or other copy of the evidence.
3. The CSP SHALL maintain a record of any other steps taken to verify the identity of the applicant.
4. The identity proofing and enrollment processes SHALL be performed according to an applicable written policy or *practice statement* that specifies the particular steps taken to verify identities.
5. Collection of personally identifiable information (PII) shall be limited to the minimum necessary to validate the existence of the claimed identity and associate the claimed identity to the person providing identity evidence. All PII collected in the proofing process, other than that listed above, other information the applicant consents to have asserted by the CSP, and the biometric collected for non-repudiation at IAL 3, SHALL NOT be retained by the CSP beyond the end of the proofing/enrollment process.
6. All personally identifiable information (PII) collected (which may include the results of a background investigation of the applicant) as part of the enrollment process SHALL be protected to ensure confidentiality, integrity, and attribution of the information source. All privacy requirements shall be satisfied.  ***Can we be more specific about the privacy part?***
12. Exact matches of personal information may be difficult to achieve due to multiple factors. The CSP MAY employ appropriate matching algorithms to account for differences in personal information and other relevant proofing data across multiple pieces of evidence, authoritative records, and third party records. Matching algorithms/rules used SHALL be publicly available. 
13. The entire proofing transaction, including transactions that involve a third party, SHALL occur over mutually authenticated protected sessions. Equivalently, the transaction SHALL consist of time-stamped or sequenced messages which are signed by their source and be encrypted for their recipient.  ***Uncomfortable with the last sentence***  
13. Agencies MAY obtain additional confidence in remote identity proofing using risk mitigation measures such as geolocation, device characteristics, and behavioral characteristics, so long as additional mitigation approaches do not substitute for requirements contained herein. 
15. Knowledge based proofing (KBP) (sometimes referred to as knowledge-based authentication (KBA)) verifies the identity by testing the personal knowledge of the individual against information obtained from public databases. KBP SHALL NOT be used to verify the identity of a claimant. KBP MAY be used to resolve to a unique, claimed identity.  See section [Knowledge Based Verification Requirements](#kbv) for more details.

###5.1.1. In-person Proofing Requirements

At IAL 3, identity proofing SHALL be performed in person. For the purposes of this document, "virtual in-person" identity proofing methodologies MAY be employed by a CSP. Any such enrollment and identity proofing done via a kiosk and Remote Proofing Center (RPC) with the following characteristics MAY be considered to meet the in-person requirement:

1. The entire identity proofing transaction is monitored by a continuous high-resolution video transmission of the applicant, from which the applicant does not depart during the identity proofing session.
2. All actions taken by the applicant during the enrollment and identity proofing process are visible through the camera.
3. Evidence documentation SHALL be scanned by an associated document scanner that is part of the kiosk.
4. Electronic verification of evidence (e.g., via chip or wireless technologies) SHALL be performed by sensors that are part of the kiosk.
5. Collection of biometrics SHALL be done in such a way that ensures that the biometric is collected from the applicant, and not another individual. Presentation attack detection (PAD, also called liveness detection) SHALL be employed.
6. The operator at the RPC communicating with the applicant during the session SHALL have undergone a training program to detect potential fraud.
7. The kiosk SHALL have tamper detection and resistance features appropriate for the environment in which it is located. For example, a kiosk located in a restricted area or one where it is monitored by a trusted individual requires less tamper detection than one that is located in a semi-public area such as a retail store.
8. All communications between the kiosk and the RPC shall take place over a mutually-authenticated encrypted session that securely authenticates the kiosk.

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

#### 5.2.1.2. Identity Evidence Requirements per Identity Assurance Level
The following table lists the minimum requirements of identity evidence and its corresponding characteristics a CSP SHALL meet for each IAL.  

|IAL|Requirements|
|:-:|:-----------|
|1|Identity evidence is not required|
|2|2 pieces of evidence with a score of 3; **or**<br>  1 piece of evidence with a score of 3 plus 2 pieces of evidence with a score of 2|
|3|1 piece of evidence with a score of 4 plus 1 piece of evidence with a score of 3; **or**<br>  2 pieces of evidence with a score of 3 plus 1 piece of evidence with a score of 2|

At IAL 3, evidence presentation SHALL be done in person.

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

#### 5.2.2.2. Validation Requirements per Identity Assurance Level
The following table lists the minimum requirements of identity evidence validation a CSP SHALL meet for each IAL.  

|IAL|Requirements|
|:-:|:-----------|
|1|No validation of evidence is required|
|2|- Each piece of evidence must be validated with a process that is able to achieve a score that matches the summation of identity evidence scores ***???*** based on the evidence presented; For example, if two forms of identity evidence of score 3 were presented, each evidence must be validated at a score of 3.<br>**- Validation against a third party data service SHALL only be used for one piece of presented identity evidence.**|
|3|- Requirements are the same as IAL 2, with additional requirement that validation SHALL be performed in person or using an approved virtual in-person technology.|

***Is it intentional that the only difference between IAL 2 and IAL 3 above is the in-person requirement at IAL 3? If so, let's say that.***

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

####5.3.1.2 Identity Verification Requirements per Identity Assurance Level
The following table lists the minimum requirements of identity verification properties a CSP SHALL meet per IAL.  

|IAL|Requirements|
|:-:|:-----------|
|1|No verification of identity is required|
|2|- MAY be performed remote or in-person<br>- At a minimum the applicant must be verified as being the owner of the Claimed Identity by a process that is able to achieve a score of 3 for Verification.<br>- Remote sessions SHALL time out after 5 minutes of inactivity|
|3|- SHALL be performed in person (see also section 5.1.1)<br>- At a minimum the Applicant must be Verified as being the owner of the Claimed Identity by a process that is able to achieve a score of 4 for Verification.<br>|

###5.3.2. Address Confirmation Requirements
Address confirmation is a critical step in identity proofing.  It allows the CSP validate and verify claimed identity information as well as defend against at scale attacks as address verification occurs in out of band channels from the actual proofing process.  The following is a set of requirements for address confirmation.


|IAL|CSP Address Confirmation Requirements|
|:-:|:--------------------------------|
|1|No requirements for address confirmation|
|2|- Self-asserted address data SHALL NOT be used for confirmation.<br>- An enrollment code consisting of at least 6 random digits SHALL be included in address confirmation.<br>- May be sent to a mobile telephone (SMS or voice), landline telephone, email, or physical mailing address obtained from records- SHALL NOT be sent any form of software-based (i.e., VoIP) telephone number.<br>- If the enrollment code is also intended to be an authentication factor, it SHALL be reset upon first use.<br>- Enrollment codes sent by means other than physical mail SHALL be valid for a maximum of 10 minutes; those sent to a postal address of record SHALL be valid for a maximum of 7 days.<br> - A notification of proofing SHALL be sent via a different address of record than the destination of the enrollment code|
|3|All IAL 2 requirements apply.  However, only postal address SHALL be used for address confirmation|


###<a name="kbv"></a>5.3.3. Knowledge Based Verification Requirements

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
Enrollment, identity proofing, token creation/issuance, and credential issuance are separate processes that can be broken up into a number of separate physical encounters or electronic transactions. (Two electronic transactions are considered to be separate if they are not part of the same protected session.) These transactions may span distinct organizational entities, and in some instance, especially with the separation of credential from proofing, a subject may already possess authenticators at a suitable AAL without having been proofed at the equivalent IAL. For example, a user may have a two-factor credential from a social network provider, considered AAL2 and IAL1, and would like to use those credentials at a relying party that requires IAL2.

The following sections provide requirements for ensuring the integrity of identity proofing when proofing and/or credential issuance do not occur within the same session and/or organizational entity.

####5.3.5.1 Identity Proofing Transaction Binding
The following requirements apply when the applicant does not already have an existing credential with the CSP or any other CSP that supports federation. **this language sucks**


#####IAL1 Requirements
No specific requirements, however effort should be made by the CSP to uniquely identify the claimant and provide a suitable user experience such that risk of establishing multiple authenticators is limited.

#####IAL2 Requirements
1. For remote transactions:
	2. The applicant SHALL identify himself/herself in each new transaction by presenting a temporary secret which was established during a prior transaction or encounter, or sent to the Applicant’s phone number, email address, or postal address of record.
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
In some instances, a user may already have an existing authenticator that has an AAL at or above the IAL needed to perform an online transaction.  The following requirements apply when a user choses to increase IAL.

1. The CSP MAY accept an existing authenticator at or above the desired IAL
2. The CSP SHALL require the user to authenticate using their existing authenticate
3. The CSP SHALL execute all required identity proofing processes for the desired IAL
4. If the user successfully completes identity proofing, the CSP SHALL issue a temporary secret that confirms address of record or require the user to register their own authenticator only after proving proof of possession (for example, activating a private key by physically touching the token)
5. The temporary secret SHALL expire within **XXXXX**
6. What to do with AAL2?
7. What to do with AAL1?

* Come with AAL2 or
* Proofing at IAL2 with AAL1 BUT
* issue a temporary secret OOB (includes text, email, phone, address, paper, qrcode or proof of possession of authenticator within the proofing session 
* Come back at AAL2 and bind with temporary secret
* time the secret out
* SMS will be allowed - need some language about a should with bring your own 2nd factor.  Let's not confuse enrollment code/receipt with 2nd factor.  Enrollment code should be different than the text.  Separates the 2 elements, even if they ultimately are the same mechanism.  Email or SMS may be part of proofing and account recovery, but we allow other authenticators beyond what was sent to confirm identity.

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
