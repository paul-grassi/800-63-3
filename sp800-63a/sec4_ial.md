
#<a name="ial-section"></a> 4. Identity Assurance Levels

## 4.1. Process Flow
The paradigm of this document is that individuals (referred to as *applicants* at this stage) are enrolled and undergo a registration process, consisting principally of identity proofing, in which their identity attributes are collected and verified. These attributes are then bound to an authenticator (described in SP 800-63B). The attributes MAY also be placed on a physical authenticator, usually in a signed form; such an authenticator is referred to as a credential. Higher Identity Assurance Levels require stronger enrollment and identity proofing procedures.

![](media/Proofing_process.png)



## 4.1. General Requirements

The following requirements apply to any CSP performing identity proofing at IAL 2 or 3. 

**@privacy:** 

1. The CSP SHALL collect and maintain a record of the full legal name, date of birth, and the mailing/residential address of record of the applicant.  
2. The CSP SHALL record the types of identity evidence presented in the proofing process, including any identification and reference number. The CSP SHALL NOT record an image, scan, or other copy of the evidence.
3. The CSP SHALL maintain a record of any other steps taken to verify the identity of the applicant.
4. The identity proofing and enrollment processes SHALL be performed according to an applicable written policy or *practice statement* that specifies the particular steps taken to verify identities.
5. Collection of personally identifiable information (PII) shall be limited to the minimum necessary to validate the existence of the claimed identity and associate the claimed identity to the person providing identity evidence. All PII collected in the proofing process, other than that listed above, other information the applicant consents to have asserted by the CSP, and the biometric collected for non-repudiation at IAL 3, SHALL NOT be retained by the CSP beyond the end of the proofing/enrollment process.
6. All personally identifiable information (PII) collected (which may include the results of a background investigation of the applicant) as part of the enrollment process SHALL be protected to ensure confidentiality, integrity, and attribution of the information source. All privacy requirements shall be satisfied.  ***Can we be more specific about the privacy part?***
12. Exact matches of personal information may be difficult to achieve due to multiple factors. The CSP MAY employ appropriate matching algorithms to account for differences in personal information and other relevant proofing data across multiple pieces of evidence, authoritative records, and third party records. Matching algorithms/rules used SHALL be publicly available. 
13. The entire proofing transaction, including transactions that involve a third party, SHALL occur over mutually authenticated protected sessions. Equivalently, the transaction SHALL consist of time-stamped or sequenced messages which are signed by their source and be encrypted for their recipient.  ***Uncomfortable with the last sentence***  
13. Agencies MAY obtain additional confidence in remote identity proofing using risk mitigation measures such as geolocation, device characteristics, and behavioral characteristics, so long as additional mitigation approaches do not substitute for requirements contained herein. 
15. Knowledge-based verification (KBV) (sometimes referred to as knowledge-based authentication (KBA)) verifies the identity by testing the personal knowledge of the individual against information obtained from public databases. KBV SHALL NOT be used to verify the identity of a claimant. KBP MAV be used to resolve to a unique, claimed identity.  See section [Knowledge Based Verification Requirements](./sec5_proofing.md/#kbv) for more details.

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

###4.5 Summary of Requirements


***Jim validation questions - Is it intentional that the only difference between IAL 2 and IAL 3 above is the in-person requirement at IAL 3? If so, let's say that.***



The following table summarizes the requirements for each of the authenticator assurance levels:

Requirement | IAL 1 | IAL 2 | IAL 3
------------|-------|-------|-------
Resolution||
Evidence|Identity evidence is not required|2 pieces of evidence with a score of 3; **or**<br>  1 piece of evidence with a score of 3 plus 2 pieces of evidence with a score of 2|1 piece of evidence with a score of 4 plus 1 piece of evidence with a score of 3; **or**<br>  2 pieces of evidence with a score of 3 plus 1 piece of evidence with a score of 2
Validation|No validation of evidence is required|- Each piece of evidence must be validated with a process that is able to achieve a score that matches the summation of identity evidence scores ***???*** based on the evidence presented; For example, if two forms of identity evidence of score 3 were presented, each evidence must be validated at a score of 3.<br>**- Validation against a third party data service SHALL only be used for one piece of presented identity evidence.**|- Requirements are the same as IAL 2, with additional requirement that validation SHALL be performed in person or using an approved virtual in-person technology.
Verification| No verification of identity is required |- MAY be performed remote or in-person<br>- At a minimum the applicant must be verified as being the owner of the Claimed Identity by a process that is able to achieve a score of 3 for Verification.<br>|- SHALL be performed in person (see also section 5.1.1)<br>- At a minimum the Applicant must be Verified as being the owner of the Claimed Identity by a process that is able to achieve a score of 4 for Verification.<br>
Address Confirmation|No requirements for address confirmation|- Self-asserted address data SHALL NOT be used for confirmation.<br>- An enrollment code consisting of at least 6 random digits SHALL be included in address confirmation.<br>- May be sent to a mobile telephone (SMS or voice), landline telephone, email, or physical mailing address obtained from records- SHALL NOT be sent any form of software-based (i.e., VoIP) telephone number.<br>- If the enrollment code is also intended to be an authentication factor, it SHALL be reset upon first use.<br>- Enrollment codes sent by means other than physical mail SHALL be valid for a maximum of 10 minutes; those sent to a postal address of record SHALL be valid for a maximum of 7 days.<br> - A notification of proofing SHALL be sent via a different address of record than the destination of the enrollment code|All IAL 2 requirements apply.  However, only postal address SHALL be used for address confirmation


