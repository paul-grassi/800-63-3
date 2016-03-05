### 5.2 Registration and Issuance Threats
There are two general categories of threats to the registration process:
impersonation and either compromise or malfeasance of the infrastructure
(RAs and CSPs). This recommendation concentrates on addressing
impersonation threats. Infrastructure threats are addressed by normal
computer security controls (e.g., separation of duties, record keeping,
independent audits) and are outside the scope of this document<sup>[9](#note9)</sup>.

The threats to the issuance process include impersonation attacks and
threats to the transport mechanism for the token and credential
issuance. Table 1 lists the threats related to registration and
issuance.

**Table 1 - Registration and Issuance Threats**

|**Activity**   |     **Threat/Attack**  | **Example** |
|---------------|------------------------|------------------|
|Registration<sup>[10](#note10)</sup> | Impersonation of claimed identity | An Applicant claims an incorrect identity by using a forged driver's license.|
| | Repudiation of registration | A Subscriber denies registration, claiming that he or she did not register that token.|
|Issuance|Disclosure | A key created by the CSP for a Subscriber is copied by an Attacker as it is transported from the CSP to the Subscriber during token issuance.|
| |Tampering | A new password created by the Subscriber is modified by an Attacker as it is being submitted to the CSP during the credential issuance phase.
| |Unauthorized issuance | A person claiming to be the Subscriber (but in reality is not the Subscriber) is issued credentials for that Subscriber.

#### 5.2.1 Threat Mitigation Strategies
Registration threats can be deterred by making impersonation more
difficult to accomplish or increasing the likelihood of detection. This
recommendation deals primarily with methods for making impersonation
more difficult; however, it does prescribe certain methods and
procedures that may help to prove who carried out an impersonation. At
each level, methods are employed to determine that a person with the
claimed identity exists, that the Applicant is the person who is
entitled to the claimed identity, and that the Applicant cannot later
repudiate the registration. As the level of assurance increases, the
methods employed provide increasing resistance to casual, systematic and
insider impersonation. Table 2 lists strategies for mitigating threats
to the registration and issuance processes.

**Table 2 - Registration and Issuance Threat Mitigation Strategies**

| **Activity** | **Threat/Attack** | **Mitigation Strategy** |
|--------------|-------------------|-------------------------|
| Registration | Impersonation of claimed identity | RAs request documentation that provides a specified level of confidence (or assurance) in the identity of the Applicant and makes it more difficult for imposters to successfully pass the identity proofing step. Government issued documents such as driver’s licenses, and passports presented by the Applicant are often used to assert the identity of the Applicant. |
| | | Have the Applicant provide non-government issued documentation (e.g. electricity bills in the name of the Applicant with the current address of the Applicant printed on the bill, or a credit card bill) to help in achieving a higher level of confidence in the identity of the Applicant. |
| | Repudiation of registration | Have the Applicant sign a form acknowledging participation in the registration activity. |
| |
| Issuance | Disclosure | Issue the token in person, physically mail it in a sealed envelope to a secure location, or use a protected session to send the token electronically.
| | Tampering | Issue credentials in person, physically mailing storage media in a sealed envelope, or through the use of a communication protocol that protects the integrity of the session data.
| | | Establish a procedure that allows the Subscriber to authenticate the CSP as the source of any token and credential data that he or she may receive.
| | Unauthorized issuance | Establish procedures to ensure that the individual who receives the token is the same individual who participated in the registration procedure.
| | | Implement a dual-control issuance process that ensures two independent individuals shall cooperate in order to issue a token and/or credential.
