
#<a name="ial-section"></a> 4. Identity Assurance Levels
The paradigm of this document is that individuals (referred to as *applicants* at this stage) are undergo an identity proofing and enrollement process, in which their identity evidence and attributes are collected, validated, and verified. These attributes are then bound to an authenticator (described in SP 800-63B).

The only outcome of identity proofing is to ensure that the applicant is who he/she claims to be.  This includes validation and verification of the following core attributes:  

1. Full name
2. Date of Birth
3. Home Address

A CSP MAY also collect additional information, provided validation and verification follow the requirements contained herein, and the individual explicitly consents to the CSP collecting and storing the attributes.  

## 4.1. Process Flow
The following diagram outlines the basic flow for Identity Proofing and Enrollement, to include the corresponding sections with normative requirements.

<center>
![](media/ProofingProcess.bmp)
<a name="figure1"></a>Figure 1.  The Identity Proofing Process
</center>

## 4.2. General Requirements

The following requirements apply to any CSP performing identity proofing at IAL 2 or 3. 

1. Identity proofing SHALL NOT be performed to determine suitability and/or entitlement to any protected service or benefit. The RP, not the CSP, is responsible for collecting and validation information for access control purposes.
2. The CSP SHALL collect and maintain a record of the full legal name, date of birth, and the mailing/residential address of record of the applicant.  
2. The CSP SHALL record the types of identity evidence presented in the proofing process, including any identification and reference number. The CSP SHALL NOT record an image, scan, or other copy of the evidence.
3. The CSP SHALL maintain a record of all steps taken to verify the identity of the applicant, to include steps that are additive to mandatory requirements specified herein.
4. The identity proofing and enrollment processes SHALL be performed according to an applicable written policy or *practice statement* that specifies the particular steps taken to verify identities.
5. Collection of personally identifiable information (PII) shall be limited to the minimum necessary to validate the existence of the claimed identity and associate the claimed identity to the person providing identity evidence. 
6. The CSP SHALL NOT retain any PII collected, other than that listed above, without explicit consent from the applicant. 
7. The CSP SHALL require explicit consent from the applicant to store any biometric collected for non-repudiation at IAL 3. **Jim, what happened here?  The sentence you checked in was:  'All PII collected in the proofing process, other than that listed above, other information the applicant consents to have asserted by the CSP, and the biometric collected for non-repudiation at IAL 3, SHALL NOT be retained by the CSP beyond the end of the proofing/enrollment process.' Do you agree with how I changed it?**
6. All personally identifiable information (PII) collected as part of the enrollment process SHALL be protected to ensure confidentiality, integrity, and attribution of the information source. 
12. Exact matches of personal information may be difficult to achieve due to multiple factors. The CSP MAY employ appropriate matching algorithms to account for differences in personal information and other relevant proofing data across multiple pieces of evidence, authoritative records, and third party records. Matching algorithms/rules used SHALL be publicly or community of interest available. For example, included as part of the written policy or practice statement referenced above. 
13. The entire proofing transaction, including transactions that involve a third party, SHALL occur over mutually authenticated protected sessions. Equivalently, the transaction SHALL consist of time-stamped or sequenced messages which are signed by their source and be encrypted for their recipient.  ***Jim: Why? Uncomfortable with the last sentence***  
13. Agencies MAY obtain additional confidence in remote identity proofing using risk mitigation measures such as geolocation, device characteristics, and behavioral characteristics, so long as additional mitigation approaches do not substitute for requirements contained herein. The CSP SHALL NOT apply additional risk-based approaches without explicit user consent. **Naomi - Cool?  If user bails, they will fail proofing**
15. Knowledge-based verification (KBV) (sometimes referred to as knowledge-based authentication (KBA)) is typically used to verify a claimed identity by testing the personal knowledge of the applicant against information obtained from public databases. KBP MAV be used to resolve to a unique, claimed identity. KBV MAY to verify the identity of a applicant provided the requirements in section [Knowledge Based Requirements](./sec5_proofing.md/#kbv) are met. **Jim-may or shall? The details get into the shalls, and shall read strangely here. It almost made it look like we were requiring KBV, hence the MAY.**

##<a name="in-person"></a>4.3. In-person Proofing Requirements

At IAL 3, identity proofing SHOULD be performed in person. In addition, "virtual in-person" identity proofing MAY be employed by a CSP. Any such identity proofing and enrollment transaction SHALL meet the following requirements:

1. The CSP monitors the entire identity proofing transaction by a continuous high-resolution video transmission of the applicant, from which the applicant SHALL NOT depart during the identity proofing session.
2. All actions taken by the applicant during the enrollment and identity proofing process are visible through the camera.
3. Evidence documentation SHALL be scanned by an associated document scanner that is part of the kiosk. **Jim - This should be covered in the actual validation and verification requirements, so doesn't need to be said**
4. All electronic verification of evidence (e.g., via chip or wireless technologies) SHALL be performed by sensors that are integrated into the solution. **Jim, need stronger language - integrated into hardware...**
5. Collection of biometrics SHALL be done in such a way that ensures that the biometric is collected from the applicant, and not another individual. All biometric requirements in [Section 5.2.3](../sp800-63b/sec5_authenticators.md/#biometric_use) apply.
6. The CSP SHALL have a live operator participate remotely with the applicant for the entirety of the identity proofing and registration session
6. The CSP SHALL require operators to have undergone a training program to detect potential fraud.
7. The CSP SHALL employ tamper detection and resistance features appropriate for the environment in which it is located. For example, a kiosk located in a restricted area or one where it is monitored by a trusted individual requires less tamper detection than one that is located in a semi-public area such as a retail store.
8. All communications between the kiosk and the CSP shall take place over a mutually-authenticated encrypted session that securely authenticates the kiosk.

##4.4. Identity Assurance Level 1
The CSP SHALL NOT proof any applications.  Applicates MAY self-assert 0 or more attributes to the CSP.

##4.5. Identity Assurance Level 2
IAL 2 allows for remote or in-person identity proofing.  IAL supports a wide range of acceptable identity evidence and validation techniques in order to increase user adoption, decrease false negatives (legitimate applicants that cannot successfully complete identity proofing), and detect to the best extent possible the presentation of fraudulent identities by a malicious applicant.

###4.5.1. Evidence Requirements
Two (2) pieces of STRONG evidence; **OR**
One (1) piece of STRONG evidence plus two (2) pieces of ADEQUATE evidence.

###4.5.2. Validation Requirements
- Each piece of evidence must be validated with a process that is able to achieve the same strength as the evidence presented; For example, if two forms pieceof STRONG identity evidence are presented, each evidence will be validated at a strength of STRONG.
- Validation against a third party data service SHALL only be used for one piece of presented identity evidence.

###4.5.3. Verification Requirements
At a minimum, the applicant must be verified by a process that is able to achieve a strength of STRONG.

##4.6. Identity Assurance Level 3
IAL 3 adds additional rigor to the steps required at IAL 3, to include providing further evidence of superior strength, and is subjected to additional and specific processes, including the use of biometrics, to further protect the identity and RP from impersonation, fraud, or other significantly harmful damages.  In addition, IAL 3 SHALL be performed in-person. SHALL be performed in person.  See [Section 4.3](#in-person) for more details.

###4.6.1. Evidence Requirements


###4.6.2. Validation Requirements

###4.6.3. Verification Requirements

##4.7. Address Confirmation
Some language about enrollment code.  See section 5 for data.

###4.7.1. Identity Assurance Level 1
No requirements for address confirmation.
###4.7.2. Identity Assurance Level 2
- Self-asserted address data SHALL NOT be used for confirmation.
- An enrollment code consisting of at least 6 random digits SHALL be included in address confirmation.
- May be sent to a mobile telephone (SMS or voice), landline telephone, email, or physical mailing address verified records
- SHALL NOT be sent any form of software-based (i.e., VoIP) telephone number.
- If the enrollment code is also intended to be an authentication factor, it SHALL be reset upon first use.
- Enrollment codes sent by means other than physical mail SHALL be valid for a maximum of 10 minutes; those sent to a postal address of record SHALL be valid for a maximum of 7 days.
- A notification of proofing SHALL be sent via a different address of record than the destination of the enrollment code.

###4.7.3. Identity Assurance Level 3
- Self-asserted address data SHALL NOT be used for confirmation.
- An enrollment code consisting of at least 6 random digits SHALL be included in address confirmation.
- SHALL be sent the physical mailing address verified in records
- If the enrollment code is also intended to be an authentication factor, it SHALL be reset upon first use.
- Enrollment code SHALL be valid for a maximum of 5 days.
- A notification of proofing SHALL be sent via a different address of record than the destination of the enrollment code.


##4.8. Summary of Requirements
*(Non-normative; refer to preceding sections for normative requirements)*

The following table summarizes the requirements for each of the authenticator assurance levels:

Requirement | IAL 1 | IAL 2 | IAL 3
------------|-------|-------|-------
Resolution||
Evidence|Identity evidence is not required|2 pieces of evidence with a score of 3;<br>**OR**<br>  1 piece of STRONG evidence plus 2 pieces of ADEQUATE evidence|1 piece of SUPERIOR evidence plus 1 piece of STRONG evidence; <br>**OR**<br>  Two (2) pieces of STRONG evidence and 1 piece of ADEQUATE evidence
Validation|No validation of evidence is required|- Each piece of evidence must be validated with a process that is able to achieve the same strength as the evidence presented; For example, if two forms pieceof STRONG identity evidence are presented, each evidence will be validated at a strength of STRONG.<br><br>- Validation against a third party data service SHALL only be used for one piece of presented identity evidence.|- SHALL be performed in person.  See [Section 4.3](#in-person) for more details. **THIS IS NOT RIGHT**- Requirements are the same as IAL 2, with additional requirement that validation SHALL be performed in person or using an approved virtual in-person technology.
Verification| No verification of identity is required |- MAY be performed remote or in-person<br><br>- At a minimum, the applicant must be verified by a process that is able to achieve a strength of STRONG.|- SHALL be performed in person.  See [Section 4.3](#in-person) for more details.)<br><br>- At a minimum, the applicant must be verified by a process that is able to achieve a strength of SUPERIOR.<br>
Address Confirmation|No requirements for address confirmation|- Self-asserted address data SHALL NOT be used for confirmation.<br>- An enrollment code consisting of at least 6 random digits SHALL be included in address confirmation.<br>- May be sent to a mobile telephone (SMS or voice), landline telephone, email, or physical mailing address obtained from records- SHALL NOT be sent any form of software-based (i.e., VoIP) telephone number.<br>- If the enrollment code is also intended to be an authentication factor, it SHALL be reset upon first use.<br>- Enrollment codes sent by means other than physical mail SHALL be valid for a maximum of 10 minutes; those sent to a postal address of record SHALL be valid for a maximum of 7 days.<br> - A notification of proofing SHALL be sent via a different address of record than the destination of the enrollment code|All IAL 2 requirements apply.  However, only postal address SHALL be used for address confirmation.



