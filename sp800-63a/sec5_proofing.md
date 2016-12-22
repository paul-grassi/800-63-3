<a name="sec5"></a>

<div class="breaker"></div>

# <a name="ipv-section"></a> 5. Identity Resolution, Validation, and Verification

_This section is normative._

This section list the steps a CSP SHALL follow to identity proof an individual to meet the requirements for each IAL. The requirements are intended to ensure the claimed identity is the actual identity of the subject attempting to enroll with the CSP and that scalable attacks effecting a large population of enrolled individuals require a greater time and cost than the value of the resources the system is protecting.

## <a name="resolve"></a>5.1. Identity Resolution
  
1.  Exact matches of information used in the proofing process may be difficult to achieve. The CSP MAY employ appropriate matching algorithms to account for differences in personal information and other relevant proofing data across multiple forms of identity evidence, authoritative records, and third party records. Matching algorithms and rules used SHOULD be available publicly or, at minimum, to the relevant community of interest. For example, they may be included as part of the written policy or practice statement referenced above.
2.  Knowledge based verification (KBV) (sometimes referred to as knowledge based authentication (KBA)) has historically been used to verify a claimed identity by testing the knowledge of the applicant against information obtained from public databases. The CSP MAY use KBV to resolve to a unique, claimed identity. 

>**MG: I changed the MAY in (1) to lower case because as part of an example I don't believe it is a may in the normative sense. No strong feeling on it.**

>**Also, it is odd we don't have more to say about resolution? Maybe we should at least talk about the goal (lest is be thought bigger than it is) like with the other sections.**

## <a name="validate"></a>5.2. Identity Evidence Validation

The goal of identity validation is to collect from the applicant the most appropriate identity evidence (e.g., a passport or drivers license) and determine its authenticity, validity, and accuracy.  Identity validation is made up of three process steps: collecting the appropriate identity evidence, confirming the evidence is genuine and authentic, and confirming the data contained on the identity evidence is valid, current, and related to a real-life subject.

>**MG: I don't have a particularly strong allegiance to "e.g.," but we switch back and forth and sholud stick to one. e.g.,takes up less space and doesn't require conjunctions so I usually roll with it.**

### 5.2.1. Identity Evidence Characteristic Requirements

This section provides requirements on the properties and qualities of identity evidence at a given IAL.

#### 5.2.1.1. Scoring of Identity Evidence

[Table 5-1](#63aSec5-Table1) lists qualities, ranging from unacceptable to superior, of identity evidence that is collected to establish a valid identity. Unless otherwise noted, to achieve a given strength the evidence SHALL, at a minimum, meet all the properties listed.

<a name="63aSec5-Table1"></a>

<div class="text-center" markdown="1">

**Table 5-1.  Properties of Identity Evidence**

</div> 

|Strength|Properties of Identity Evidence|
|:---:|:------------------------------| 
|Unacceptable|The issuing source of the evidence did not perform identity proofing |
|Weak|- The issuing source of the evidence did not perform identity proofing.<br><br>- The issuing process for the evidence means that it can reasonably be assumed to have been delivered into the possession of the subject.<br><br>- The evidence contains at least one reference number that uniquely identifies the subject to whom it relates.|
|Fair|- The issuing source of the evidence confirmed the claimed identity through an identity proofing process.<br><br>- The issuing process for the evidence means that it can reasonably be assumed to have been delivered into the possession of the subject to whom it relates.<br><br>- The evidence:<br>&nbsp;&nbsp;&nbsp;&nbsp;- contains at least one reference number that uniquely identifies the subject to whom it relates. <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR**<br>&nbsp;&nbsp;&nbsp;&nbsp;- contains a photograph, image, or biometric of the person to whom it relates.<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR**<br>&nbsp;&nbsp;&nbsp;&nbsp;- can have ownership confirmed through KBV.<br><br>- Where the evidence includes digital information, that information is protected using cryptographic or proprietary methods, or both, and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed. <br><br>- Where the evidence includes physical security features, it requires proprietary knowledge to be able to reproduce it.<br><br> -The issued evidence is unexpired.|
|Strong|- The issuing source of the evidence confirmed the claimed identity through written procedures designed to enable it to form a reasonable belief that it knows the true identity of the subject. Such procedures shall be subject to recurring oversight by regulatory or publicly accountable institutions. For example, the Customer Identification Program guidelines established in response to the USA PATRIOT Act of 2001 or the [Red Flags Rule](#rfr), under Section 114 of the Fair and Accurate Credit Transaction Act of 2003 (FACT Act)<br><br>- The issuing process for the evidence ensured that it was delivered into the possession of the subject to whom it relates.<br><br>  -The issued evidence contains at least one reference number that uniquely identifies the subject to whom it relates.<br><br>- The applicant's name on the issued evidence must be the name that the identity was officially known at the time of issuance. Pseudonyms, aliases, and initials for last name and at least one first name are not permitted. **MG: I can't parse this. Can we split it into two requirements?Is initial not allowed for last name at all and allowed for no more than one first name? Also, should we refer to "last or family name" and "first or given name"?**<br><br>- The issued evidence contains a photograph, image, or biometric of the person to whom it relates.<br><br>- Where the issued evidence includes digital information, that information is protected using cryptographic or proprietary methods, or both, and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed.<br><br>  -Where the issued evidence contains physical security features, it requires proprietary knowledge and proprietary equipment to be able to reproduce it.<br><br>- The evidence is unexpired.|
|Superior|- The issuing source of the evidence confirmed the claimed identity by following written procedures designed to enable it to have high confidence that the source knows the true identity of the subject. Such procedures shall be subject to recurring oversight by regulatory or publicly accountable institutions.<br><br>- The issuing source visually identified the applicant and performed further checks to confirm the existence of that identity. **MG: Are these really two requirements?**<br><br>- The issuing process for the evidence ensured that it was delivered into the possession of the subject to whom it relates.<br><br>- The evidence contains at least one reference number that uniquely identifies subject to whom it relates.<br><br>- The applicant's name on the evidence must be the name that the identity was officially known at the time of issuance. No pseudonyms, aliases, or initials for first or last names are permitted.<br><br>- The evidence contains a photograph/image of the person to whom it relates.<br><br>- The evidence contains a biometric of the person to whom it relates.<br><br>- The evidence includes digital information, the information is protected using cryptographicor proprietary methods, or both, and those methods ensure the integrity of the information and enable the authenticity of the issuing source to be confirmed.<br><br>- The evidence includes physical security features that requires proprietary knowledge and proprietary equipment to be able to reproduce it.<br><br>- The evidence is unexpired.|

>**MG: Did we try to create a graphic with each property having a row on the left column and the strength in the right columns with checks and Xs? Given the amount of repetition, it might be worth a shot.**

### 5.2.2. Validating Identity Evidence

Once identity evidence is obtained by the CSP, the accuracy, authenticity, and integrity of the evidence and related information is checked against authoritative sources in order to determine that the presented evidence is:  

* Genuine, authentic, and not a counterfeit, fake, or forgery.
* The information is correct.  
* The information relates to a real-life subject.  

#### 5.2.2.1. Methods to Perform Identity Evidence Validation

[Table 5-2](#63aSec5-Table2) lists qualities, ranging from unacceptable to superior, of identity validation that is performed by the CSP to validate the evidence presented for the current proofing session and the information contained therein. 

>**MG: I want to make sure it's clear that we mean the current CSP is doing these things, not that they were done in the issuancd process. It's logically obvious, but we should make it blatant.**

<a name="63aSec5-Table2"></a>

<div class="text-center" markdown="1">

**Table 5-2.  Validating Identity Evidence**

</div> 

|Strength|Method(s) performed by the CSP|
|:---:|:------------------------------| 
|Unacceptable|Evidence validation was not performed, or validation of the evidence failed.|
|Weak|All personal details from the evidence have been confirmed as valid by comparison with information held or published by an authoritative source.|
|Fair|- The evidence:<br>&nbsp;&nbsp;&nbsp;&nbsp;- details have been confirmed as valid by comparison with information held or published by the issuing source.<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR**<br>&nbsp;&nbsp;&nbsp;&nbsp;- has been confirmed as genuine using appropriate equipment, confirming the integrity of physical security features and lack of fraudulent modification.<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR** <br>&nbsp;&nbsp;&nbsp;&nbsp;- The evidence has been confirmed as genuine by trained personnel. <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR** <br>&nbsp;&nbsp;&nbsp;&nbsp;- The issued evidence has been confirmed as genuine by confirmation of the integrity of cryptographic security features.|
|Strong|- The evidence has been confirmed as genuine:<br>&nbsp;&nbsp;&nbsp;&nbsp;- using appropriate equipment, confirming the integrity of physical security features and lack of fraudulent modification. <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR**<br>&nbsp;&nbsp;&nbsp;&nbsp;- by trained personnel and appropriate equipment, confirming the integrity of the physical security features and lack of fraudulent modification<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR**<br>&nbsp;&nbsp;&nbsp;&nbsp;- by confirmation of the integrity of cryptographic security features.<br><br> - All personal details and evidence details have been confirmed as valid by comparison with information held or published by the issuing source.|
|Superior|- The evidence has been confirmed as genuine by trained personnel and appropriate equipment including the integrity of any physical and cryptographic security features.<br><br>- All personal details and evidence details from the evidence have been confirmed as valid by comparison with information held or published by the issuing source.|

## 5.3. <a name="verify"></a> Identity Verification

The goal of identity verification is to confirm and establish a linkage between the claimed identity and the real-live existence of the subject presenting the evidence.

### 5.3.1. Identity Verification Methods

[Table 5-3](#63aSec5-Table3) details the verification methods necessary to achieve a given identity verification strength.  

<a name="63aSec5-Table3"></a>

<div class="text-center" markdown="1">

**Table 5-3.  Verifying Identity Evidence**

</div> 

|Strength|Identity Verification Methods|
|:---:|:------------------------------| 
|Unacceptable|Evidence verification was not performed or verification of the evidence failed. Unable to confirm that the applicant is the owner of the claimed identity.|
|Weak|The applicant has been confirmed as having access to the evidence provided to support the claimed identity.|
|Fair|- The applicant’s ownership of the claimed identity has been confirmed by:<br>&nbsp;&nbsp;&nbsp;&nbsp;- KBV.  See [Section 5.3.2](#kbv) for more details. <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR**<br>&nbsp;&nbsp;&nbsp;&nbsp;- a physical comparison of the applicant to the strongest piece of evidence provided. Physical comparison performed remotely SHALL include presentation attack detection as specified in [Section 5.2.3](#biometric_use) of [SP 800-63B](#800-63b). <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR**<br>&nbsp;&nbsp;&nbsp;&nbsp;- biometric comparison of the applicant to the strongest piece of evidence provided. Biometric comparison performed remotely SHALL adhere to the appropriate requirements as specified in [Section 5.2.3](#biometric_use) of [SP 800-63B](#800-63b). |
|Strong|- The applicant’s ownership of the claimed identity has been confirmed by <br>&nbsp;&nbsp;&nbsp;&nbsp;- physical comparison, using appropriate equipment, to a photograph or image. Physical comparison performed remotely SHALL include presentation attack detection as specified in [Section 5.2.3](#biometric_use) of [SP 800-63B](#800-63b). <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR**<br>&nbsp;&nbsp;&nbsp;&nbsp;- biometric comparison, using appropriate equipment, of the applicant to the strongest piece of evidence provided to support the claimed identity. Biometric comparison performed remotely SHALL adhere to the appropriate requirements as specified in [Section 5.2.3](#biometric_use) of [SP 800-63B](#800-63b).|
|Superior|- The applicant’s ownership of the claimed identity has been confirmed by biometric comparison, using appropriate equipment, of the applicant to the strongest piece of evidence provided to support the claimed identity. Biometric comparison performed remotely SHALL adhere to the appropriate requirements as specified in [Section 5.2.3](#biometric_use) of [SP 800-63B](#800-63b).|

The CSP MAY use KBV to verify the identity of an applicant provided the requirements in [Section 5.3.2](#kbv) _Knowledge Based Verification Requirements_ are met. 

### <a name="kbv"></a>5.3.2. Knowledge Based Verification Requirements

The following requirements apply to the identity verification steps for IAL 2 and 3. There are no restrictions for the use of KBV for identity resolution.

- KBV SHALL NOT be used if the CSP is not, or does not maintain a relationship with, an authoritative source. 
- KBV SHALL NOT be based on data held by the issuing source of an applicant's supplied identity evidence. **MG: I think I get the point here, but does it mean that if the dmv is the issuing source, and the dmv knows everything about my car ownership and driving history, then nothing ever involving a car or driving can be used?**
- The CSP SHALL only use information that is expected to be known only to the applicant and the source, to include any information needed to trigger the KBV process. Information accessible freely or for any fee in the public domain SHALL NOT be used. **MG: Not sure I get the "trigger" part. Isn't it just resolution that triggers (I think I'd prefer "seed") the process?**
- The CSP SHALL allow a resolved, validated, or verified identity to opt-out of KBV and leverage another process for verification.
- The CSP SHOULD perform KBV by verifying knowledge of recent transactional history that the CSP is a participant in.  The CSP SHALL ensure that transaction information has at least 20 bits of entropy. For example, to reach minimum entropy requirements, the CSP could ask the applicant for verification of the amount(s) of a micro-deposit(s) to a valid bank account, so long as the total number of digits is seven or greater. **MG: is this better?** 
- The CSP MAY perform KBV by asking the applicant questions to demonstrate they are the owner of the claimed information. However, the following requirements apply:
	- The CSP SHALL require a minimum of four KBV questions with each requiring a correct answer to successfully complete the KBV step.
	- The CSP SHOULD require a free form response to a KBV question.  The CSP MAY allow multiple choice answers, however, if multiple choice answer are provided, the CSP SHALL require a minimum of four answer options per question.
	- The CSP SHOULD allow two attempts for an applicant to complete the KBV.  A CSP SHALL NOT allow more than three attempts to complete the KBV.
	- The CSP MAY use KBV to verify an applicant's identity against only one piece of validated identity evidence.  
	- The CSP SHALL NOT present diversionary KBV questions.  The CSP SHALL NOT allow answers to KBV questions be 'None of the Above', 'Not Applicable (N/A)', or similar to be regarded as correct. **MG: Brent was telling me diversionary questions actually statistically less likely for an attacker to get right. Do we have any data either way?**
	- The CSP SHOULD NOT ask the same KBV questions in subsequent attempts.
	- The CSP SHALL NOT ask a KBV question that provides infomation that could assist in answering any future KBV question in a single session or a subsequent session after a failed attempt.
	- The CSP SHALL NOT use KBV questions for which the answers do not change regularly over a period of time (e.g., What was your first car?).
	- The CSP SHALL ensure that any KBV approach does not reveal PII that the applicant has not already provided, nor personal information that, when combined with other information in a KBV session, could result in unique identification.
	- The CSP SHALL time out KBV sessions after two minutes of inactivity per question.  In cases of session timeout, the CSP SHALL restart the entire KBV process and consider this a failed session.

>**MG: I toughened some of these. Too much?**

### <a name="vip"></a>5.3.3. In-person Proofing Requirements

#### 5.3.3.1 General Requirements

1.	The CSP SHALL have the operator view the biometric source (e.g., fingers or face) for presence of non-natural materials and perform such inspections as part of the proofing process.

2.	The CSP SHALL collect biometrics in such a way that ensures that the biometric is collected from the applicant, and not another individual. All biometric performance requirements in [SP 800-63B, Section 5.2.3 Biometric Considerations](sp800-63b.html/#biometric_use) apply.

#### 5.3.3.2. Requirements for in-person proofing performed over remote channels

It is possible for a CSP to achieve the security and confidence comparable to in-peson proofing over remote channels.  The following requirements establish comparability between in-person transactions where the enrollee in the same physical location as the CSP or when the enrollee is remote to the CSP.

Virtual in-person identity proofing and enrollment transaction SHALL meet the following requirements, in addition to the IAL 3 validation and verification requirements specified in [Section 4.6](#ial3-requirements):

1. The CSP SHALL monitor the entire identity proofing transaction, from which the applicant SHALL NOT depart during the identity proofing session.  For example, by a continuous high-resolution video transmission of the applicant.
2. The CSP SHALL require all actions taken by the applicant during the enrollment and identity proofing process to be clearly visible to the remote operator. The operator SHALL direct the applicant as required to remove any doubt in the proofing process.
3. The CSP SHALL require that all digital verification of evidence (e.g., via chip or wireless technologies) be performed by integrated scanners and sensors that are in the entire field of view of the camera and the remote, live operator.
4. The CSP SHALL have an operator participate remotely with the applicant for the entirety of the enrollment and identity proofing session.
5. The CSP SHALL require operators to have undergone a training program to detect potential fraud and to properly perform a virtual in-process proofing session.
6. A CSP MAY have an attendant participate in-person, at the same physical location as the applicant, for the entirety of the enrollment and identity proofing session.
7. The CSP SHALL employ physical tamper detection and resistance features appropriate for the environment in which it is located. For example, a kiosk located in a restricted area or one where it is monitored by a trusted individual requires less tamper detection than one that is located in a semi-public area such as a retail store.
8. The CSP SHALL ensure that all communications take place over a mutually authenticated encrypted session.

### <a name="trustref"></a> 5.3.4. Trusted Referee Requirements

The CSP MAY use trusted referees, such as notaries, legal guardians, medical professionals, conservators, persons with power of attorney, or some other form of certified/trained/approved individuals that can vouch for or act on behalf of the individual in accordance with applicable laws, regulations, or agency policy.  The CSP MAY allow an individual that has successfully completed identity proofing to act as a trusted referee for another individual.  The CSP MAY use a trusted referee for both remote and in-person processes.  

The CSP SHALL establish written policy and procedures as to how a trusted referee is determined and the lifecycle by which the trusted referee retains his/her status as a valid referee, to include any restrictions, as well as any revocation and suspension requirements. 

The CSP SHALL determine the minimum evidence required to bind the relationship between the trusted referee and the applicant. 

The CSP MAY perform re-proofing of the subscriber on a regular basis, as defined by CSP policy, with the goal of satisfying the requirements of [Section 4.5.1](#normal). 

##### Considerations for Minors

The CSP SHALL give special consideration to the legal restrictions of interacting with minors unable to meet the evidence requirements of identity proofing.

The CSP SHOULD involve a parent or legal adult guardian as a trusted referee as described in [Section 5.4.4](#trustref). 

Minors under age 13 require special consideration to ensure compliance with the Children's Online Privacy Protection Act of 1998, 15 USC 6501-6505 and 16 CFR Part 312.

## 5.4. Binding Requirements

See [800-63B, Section 6.1, Authenticator Binding](#binding) for instructions on binding authenticators to subscribers.  
