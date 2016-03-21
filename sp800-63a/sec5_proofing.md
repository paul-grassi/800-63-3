
#<a name="ipv-section"></a> 5. Identity Proofing and Verification

**Credential or Authenticator?  
User, applicant, claimant, subject?
fix the damn headers**

The following sections list the requirements CSPs must follow to identity proof an individual at each identity assurance level. The requirements for each identity assurance level are derived to ensure the claimed identity is the actual identity of the person attempting to gain access to a system **and** at-scale attacks are difficult to execute without significant time and cost. 

## 5.1 General Requirements per Identity Assurance Level

The following requirements apply to any CSP performing identity proofing at IAL 2 or 3. 

**@privacy:** 

1. The CSP SHALL collect full legal name, an address of record, and date of birth from the applicant.
2. Records of registration SHALL be maintained.  
4. The CSP SHALL maintain a record of each individual whose identity has been verified and the steps taken to verify his   or her identity, including any information collected from the Applicant in compliance with the sections below.  
3. The CSP SHALL have the capability to provide records of identity proofing to RPs if required<sup>[11](#note11)</sup>.
4. The identity proofing and registration processes SHALL be performed according to applicable written policy or *practice statement* that specifies the particular steps taken to verify identities.
5.  The CSP SHALL record the identification/reference number of the presented identity evidence.
9. **The CSP SHALL NOT record an image/scan/copy of the presented identity evidence.**  
10. Personally identifiable information (PII) collected as part of the registration process SHALL be protected, and all privacy requirements shall be satisfied.  
11. PII collect SHALL be limited to the minimum data necessary to validate the existance of the claimed identity and associate it the claimed identity to the person providing identity evidence. 
12. **Jim:  Put in assertions/authenticator docs? CSP SHALL support pseudonymous pairwise identifiers**
12. Exact matches of personal information may be difficult to achieve due to multiple factors. The CSP MAY employ appropriate matching alogrithms to account for differences in personal information and other relevant proofing data across multiple pieces of evidence, authoritative records, and 3rd party records. Matching algorithms/rules used SHALL be publicly avialable. 
13. The entire proofing transaction, including transactions that involve a 3rd party, SHALL occur over a mutually authenticated protected session. Equivalently, the transaction SHOULD consist of time-stamped or sequenced messages and SHOULD signed by their source and be encrypted for their recipient.  
14. Current encryption algorithms in accordance with NIST standards and guidelines SHALL be used.  
12. The results of the identity proofing step (which may include background investigations of the Applicant) SHALL be protected to ensure source authentication, confidentiality, and integrity.  
13. Agencies MAY obtain additional confidence using risk mitigation measures such as geolocation, device characterists, or behavioral characterists so long as additional mitigation approaches do not substitute for requirements contained herein. 
15. Knowledge based proofing (KBP) (sometimes referred to as knowledge-based authentication (KBA)) verifies the identity by testing the personal knowledge of the individual against information obtained from public databases. KBP SHALL NOT be used to verify the identity of a claimant. KBP MAY be used to resolve to a unique, claimed identity.  See section [Knowledge Based Verification Requirements](#kbv) for more details.

##5.2 Identity Validation Requirements
The goal of identity validation is to determine the authenticity, validity, and accuracy of the identity evidence that a claimant provides.  Validation establishes the physical, live existence of the claimed identity.  Identity Validation is made up of two process steps: collecting the appropriate identity evidence and confirming the data is valid and related to an actual, live individual.

###5.2.1 Identity Evidence Characteristic Requirements

This section provides requirements on the acceptable properties and qualities of identity evidence that a claimant asserts (online) or presents (in-person) at each IAL.

The following table lists qualities of the various form and types of identity evidence that are acceptable to begin identity proofing an individual. The evidence MUST, at a minimum, meet all the properties defined to achieve that score.

> **Open items for Jim to help decide:**  
Identity evidence, regardless of properties, MUST be issued by a legitimate 3rd party and MUST have authoritative records to validate evidence.  
Might want to just make the table additive:  All of 3 + these things...  
What about name change since we have content about issuance and name  
Score of 3 had 'if it includes security features' and 4 'must'.  Is that ok?  


|Score|Properties of Identity Evidence|
|:---:|:------------------------------| 
|1|-The issuing source did not perform identity proofing<br>  -The issuing process for the evidence means that it can reasonably be assumed to have been delivered into the possession of an individual<br>  -The issued evidence contains at least one identification/reference number that uniquely identifies itself or the person to whom it relates; **or**<br>   the issued evidence contains a photograph/image/Biometric of the person to whom it relates|
|2|-The issuing source of the evidence confirmed the applicant’s identity through an identity checking process<br>  -The issuing process for the evidence means that it can reasonably be assumed to have been delivered into the possession of the person to whom it relates<br>-The issued evidence contains at least one identification/reference number that uniquely identifies itself or the person to whom it relates; **or**<br>  The issued evidence contains a photograph/image/Biometric of the person to whom it relates<br>  -Where the issued evidence is, or includes, electronic information, that information is protected using cryptographic methods and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed<br> -Where the issued evidence contains physical security features, it requires proprietary knowledge to be able to reproduce it<br> -The issued evidence is unexpired|
3|-The issuing source of the evidence confirmed the applicant’s identity in a manner that complies with, or is aligned to, the Know Your Customer guidelines, of the US Patriot Act of 2001<br>  -The issuing process for the evidence ensured that it was delivered into the possession of the person to whom it relates<br>  -The issued evidence contains at least one identification/reference number that uniquely identifies itself or the person to whom it relates<br>  -The name value on the issued evidence must be the name that the identity was officially known at the time of issuance. Pseudonyms, aliases and initials for given and surnames are not permitted<br>  -The issued evidence contains a photograph/image/Biometric of the person to whom it relates; -Where the issued evidence is, or includes, electronic information that information is protected using cryptographic methods and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed<br>  -Where the issued evidence contains physical security features, it requires proprietary knowledge and proprietary equipment to be able to reproduce it<br> -The issued evidence is unexpired|
|4|-The issuing source of the evidence confirmed the applicant’s identity in a manner that complies with, or is aligned to, the Know Your Customer guidelines, of the US Patriot Act of 2001<br>  -The issuing source visually identified the applicant and performed further checks to confirm the existence of that identity<br>  -The issuing process for the evidence ensured that it was delivered into the possession of the person to whom it relates<br>  -The issued evidence contains at least one identification/reference number that uniquely identifies itself or the person to whom it relates<br>  -The name value on the issued evidence must be the name that the identity was officially known at the time of issuance. Pseudonyms, aliases and initials for forenames and surnames are not permitted<br>  -The issued evidence contains a photograph/image of the person to whom it relates<br>  -The issued evidence contains a fingerprint, facial, or iris biometric of the person to whom it relates<br>  -Where the issued evidence is, or includes, electronic information that information is protected using cryptographic methods and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed<br>  -The issued evidence contains physical security features that require proprietary knowledge and proprietary equipment to be able to reproduce it<br> -The issued evidence is unexpired|

#### Identity Evidence Requirements per Identity Assurance Level
The following table lists the minimum requirements of identity evidence and its corresponding characteristics a CSP SHALL meet per IAL.  


|IAL|Requirements|
|:-:|:-----------|
|1|Identity evidence is not required|
|2|-2 pieces of evidence with a score of 3; **or**<br>  -1 piece of evidence with a score of 3<br>  -2 pieces of evidence with a score of 2|
|3|- Presentation SHALL be done in person<br>**and**<br>-1 piece of evidence with a score of 4<br>  -1 piece of evidence with a score of 3; **or**<br>  -2 pieces of evidence with a score of 3<br>  -1 piece of evidence with a score of 2|



###5.2.2 Validating Identity Evidence
Once identity evidence is obtained by the CSP, the accuracy, authenticity, and integrity of the evidence and related information is checked against authoritative sources in order to determine that the presented evidence is:  

* Genuine, authentic, and not a counterfit, fake, or forgery.
* The information is correct  
* The information relates to a real individual  
* The information relates to the correct individual  

#### Methods to Perform Identity Evidence Validation
For each IAL, the CSP is expected to obtain a minimum validation score.  The following table provides details the properties of validations required to achieve a given score.

|Score|Method(s)|
|:---:|:------------------------------| 
|0|- Validation of the evidence failed|
|1|- All personal details from the evidence have been confirmed as valid by comparison with information held/published by the issuing/authoritative source **or a third party data service**|
|2|-All personal details *and evidence details* from the evidence have been confirmed as valid by comparison with information held/published by the Issuing/Authoritative Source. <br> **or** <br>- The issued evidence has been confirmed as genuine by trained personnel using their skill and appropriate equipment, and confirmed the integrity of the physical security features <br> **or** <br>- The issued evidence has been confirmed as genuine by confirmation of the integrity of the cryptographic security features|
|3|- The issued evidence has been confirmed as genuine by trained personnel using their skill **and** appropriate equipment, and confirmed the integrity of the physical security features **or** The issued evidence has been confirmed as genuine by confirmation of the integrity of the cryptographic security features <br>**and**<br> - All personal details and evidence details have been confirmed as valid by comparison with information held/published by the Issuing/Authoritative Source **or** evidence details from the evidence have been confirmed as not known to be invalid by comparison with information held/published by the Issuing Source/Authoritative Source|
|4|- The issued evidence has been confirmed as genuine by trained personnel using their skill **and** appropriate equipment including the integrity of any cryptographic security features<br>**and**<br>- All personal details and evidence details from the evidence have been confirmed as valid by comparison with information held/published by the Issuing Source/Authoritative Source|

#### Validation Requirements per Identity Assurance Level
The following table lists the minimum requirements of identity evidence validation a CSP SHALL meet per IAL.  

|IAL|Requirements|
|:-:|:-----------|
|1|No validation of evidence is required|
|2|- Each piece of evidence must be validated with a process that is able to achieve a score that matches the summation of identity evidence scores based on the evidence presented; For example, if two forms of identity evidence of score 3 were presented, each evidence must be validated at a score of 3.<br>**- Validation against a 3rd party data service SHALL only be used for 1 piece of presented identity evidence**|
|3|- Each piece of evidence must be validated with a process that is able to achieve a score that matches the summation of identity evidence scores based on the evidence presented; For example, if two forms of identity evidence of score 3 were presented, each evidence must be validated at a score of 3.<br>- Validation SHALL be performed in person|

##5.3 Verification Requirements
The purpose of identity verification is to confirm that the presented identity evidence and attributes relates to the person making the claim.  

####Identity Verification Methods
The following table details the verification methods necessary to achieve appropriate identity verification.

**Jim:  
Need to determine what the heck to do with KBV and micro-payment verification.  Current language needs help.**


|Score|Identity Verification Methods|
|:---:|:------------------------------| 
|0|- Unable to confirm that the applicant is the owner of the claimed identity|
|1|- The Applicant has been confirmed as having access to the evidence provided to support the claimed identity|
|2|- The Applicant’s ownership of the Claimed Identity has been confirmed by a Dynamic Knowledge Based Verification <br>**or**<br>- The Applicant’s ownership of the Claimed Identity has been confirmed by proving control of an account<br>**or**<br>- The Applicant’s ownership of the Claimed Identity has been confirmed by a physical comparison of the Applicant to the strongest piece of Identity Evidence provided to support the Claimed Identity<br>**or**<br>**- The Applicant’s ownership of the Claimed Identity has been confirmed by a Biometric comparison of the Applicant to the strongest piece of Identity Evidence provided to support the Claimed Identity**|
|3|- The Applicant’s ownership of the Claimed Identity has been confirmed by physical comparison using a photograph/image **or** Biometric comparison of the Applicant to the strongest piece of Identity Evidence provided to support the Claimed Identity<br>**AND**<br>- The Applicant’s ownership of the Claimed Identity has been confirmed by Dynamic Knowledge Based Verification **or** proving control of an account **or** a trusted referee confirms the identity of the claimant|
|4|- The Applicant’s ownership of the Claimed Identity has been confirmed by a physical comparison of the Applicant using a photograph/image to the strongest pieces of Identity Evidence **OR** By a Biometric comparison of the Applicant to the strongest piece of Identity Evidence provided to support the Claimed Identity<br>**AND**<br>- The Applicant’s ownership of the Claimed Identity has been confirmed by both a Dynamic Knowledge Based Verification **and** proving control of an account<br>**AND**<br>- The Applicant’s ownership of the Claimed Identity has been confirmed by an interaction with the Applicant via the declared address|

#### Identity Verification Requirements per Identity Assurance Level
The following table lists the minimum requirements of identity verification properties a CSP SHALL meet per IAL.  

|IAL|Requirements|
|:-:|:-----------|
|1|No verification of identity is required|
|2|- MAY be performed remote or in-person<br>- At a minimum the Applicant must be Verified as being the owner of the Claimed Identity by a process that is able to achieve a score of 3 for Verification.- Remote sessions SHALL timeout after 5 minutes of inactivity|
|3|- MAY be performed remote or in-person<br>- At a minimum the Applicant must be Verified as being the owner of the Claimed Identity by a process that is able to achieve a score of 4 for Verification.<br>- **Jim: If remote, the CSP SHALL have a live operator participate remotely with and the claimant for the entirety of the identity proofing and registration session<br>**AND**<br>The video feed must ensure that all actions taken by the applicant are within the field of view of the operator throughout the entire identity proofing and registration session**|

Identity Verification Requirements per Identity Assurance Level

###5.3.1 Address Confirmation Requirements
Address confirmation is a critical step in identity proofing.  It allows the CSP validate and verify claimed identity information as well as defend against at scale attacks as address verification occurs in out of band channels from the actual proofing process.  The following is a set of requirements for address confirmation.


|IAL|CSP Address Confirmation Requirements|
|:-:|:--------------------------------|
|1|- No requirements for address confirmation|
|2|- Self-asserted address data SHALL NOT be used for confirmation.<br>- An enrollment code SHALL be included in address confirmation<br>- May be mobile SMS, email, or physical mailing address<br>- SHALL be sent to an address that is maintained in records<br>- SHALL NOT be sent any form of software-based phone number. If SMS is used, the CSP SHALL send the enrollment code to a phone number maintained and managed by a mobile carrier<br>- If the enrollment code is also intended to be an authentication factor, it SHALL be reset upon first use.<br>- Enrollment codes sent to email or phone of record SHALL be valid for a maximum lifetime of 10 minutes<br>- Enrollment codes sent to postal address of record SHALL be valid for a maximum lifetime of 7 days<br> - A notification of proofing SHALL be sent via a different address of record than the destination of the enrollment code|
|3|- All IAL 2 requirements apply.  However, only postal address SHALL be used for address confirmation|


###<a name="kbv"></a>5.3.2 Knowledge Based Verification Requirements
KBV MAY be used if the CSP is, or maintains a relationship with, an authoritative source, the authoritative source is the only entity that maintains control over specific data, the data has never been aggregated or accessed by a 3rd party.  In instances with the CSP leverages and 3rd party for KBV, the 3rd party provide SHALL NOT provide the authoritative data to the CSP.  Rather, only boolean values or error codes SHALL be returned.  

- Enrollment codes sent to a mobile phone (cell SMS or voice) verification must not be via soft phones such as Google Voice or Skype.
- Shared devices? Is this solved by in-records check?
- KBA allowed if temporal **and** spacial

- Trusted referee (canadian language), vouchee (already proofed-kind of happens in places like HSIN) or notary

- Capture biometric at IAL3

- Once a CSP has met the minimum requirements for an IAL:
	- The CSP MAY use additional risk-based/indicators/context/adaptive  authentication methods to increase confidence in identity verification.
	- If the CSP is an authoritative source, the only entity that maintains control over specific data, and the data has never been aggregated or accessed by a 3rd party, the CSP MAY use knowledge based authentication verification to increase confidence in identity verification.

###5.3.3 Trusted Referee Requirements
The CSP MAY determine to utilize trusted referees, such as notaries, legal guardian, or some other form of certified individual that can legally vouch for and/or act on behalf of the individual.  CSP MAY use a trusted referee for both remote and in-person processes.  

In some instances, the CSP MAY allow an individual that has successfully completed identity proofing with the same CSP to act as a trusted referee for another individual.  The CSP SHALL not accept this type of trusted referee verification at IAL3.

###5.3.4 Binding Requirements
Registration, identity proofing, token creation/issuance, and credential issuance are separate processes that can be broken up into a number of separate physical encounters or electronic transactions. (Two electronic transactions are considered to be separate if they are not part of the same protected session.) These transactions may span distict organizational entities, and in some instance, especially with the separation of credential from proofing, a subject may already possess authenticators at a suitable AAL without having been proofed at the equivalent IAL. For example, a user may have a two-factor credential from a social network provider, considered AAL2 and IAL1, and would like to use those credentials at a relying party that requires IAL2.

The following sections provide requirements for ensuring the integrity of identity proofing when proofing and/or credential issuance do not occur within the same session and/or organizational entity.

####5.1.4.1 Identity Proofing Transaction Binding
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
* issue a temporary secret OOB (includes text, email, phone, address, paper, qrcode or proof of posession of authenticator within the proofing session 
* Come back at AAL2 and bind with temporary secret
* time the secret out
* SMS will be allowed - need some language about a should with bring your own 2nd factor.  Let's not confuse enrollment code/receipt with 2nd factor.  Enrolment code should be different than the text.  Separates the 2 elements, even if they ultimately are the same mechanism.  Email or SMS may be part of proofing and account recovery, but we allow other authenticators beyond what was sent to confirm identity.

##5.4 Requirements for Derived Credentials
CSP looks at a credential from a different CSP that it trusts, records the information, and issues its own credential and binds it to an authenticator. I'd call that identity proofing and include that in 63A.
Where the Applicant already possesses recognized authentication credentials a trusted CSP, the additional CSP may choose to identity proof the Claimant by verifying possession and control of the token associated with the credentials and issue a new derived credential.  The following details the proofing requirements for the CSP issuing a derived credential.
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



##5.5 Considerations for Minors and Other Vulnerable People

**Jim: Do we need this?**


