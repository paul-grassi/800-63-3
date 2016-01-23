## 5. Registration and Issuance Processes
### 5.1.  Overview
In the registration process, an Applicant undergoes identity proofing by
a trusted RA. If the RA is able to verify the Applicant’s identity, the
CSP registers or gives the Applicant a token and issues a credential as
needed to bind that token to the identity or some related attribute. The
Applicant is now a Subscriber of the CSP and may use the token as a
Claimant in an authentication protocol. This section describes the
requirements for registration and for token and credential issuance.

The RA can be a part of the CSP, or the RA can be a separate and
independent entity; however, a trusted relationship always exists
between the RA and CSP. Where the RA and CSP are separate entities, the
trust relationship is often contractual, but the trust relationship may
also be based on laws and regulations, such as when a notary performs
the RA function. The RA or CSP maintain records of the registration. The
RA and CSP can provide services on behalf of an organization or may
provide services to the public. The processes and mechanisms available
to the RA for identity proofing may differ as a result. Where the RA
operates on behalf of an organization, the identity proofing process may
be able to leverage a pre-existing relationship (e.g., the Applicant is
an employee or student). Where the RA provides services to the public,
the identity proofing process is generally limited to confirming
publicly available information and previously issued credentials.

The registration and identity proofing processes are designed based on
the required assurance level, to ensure that the RA/CSP knows the true
identity of the Applicant. Specifically, the requirements include
measures to ensure that:

-   A person with the Applicant’s claimed attributes exists, and those
    attributes are sufficient to uniquely identify a single person;

-   The Applicant whose token is registered is in fact the person who is
    entitled to the identity;

-   It is difficult for the Claimant to later repudiate the registration
    and dispute an authentication using the Subscriber’s token.

An Applicant may appear in person to register, or the Applicant may
register remotely. Somewhat different processes and mechanisms apply to
identity proofing in each case. Remote registration is limited to Levels
1 through 3.

After successful identity proofing of the Applicant, the RA registers
the Applicant, and then the CSP is responsible for token and credential
issuance for the new Subscriber (additional CSP responsibilities are
discussed further in Section 7). Issuance includes creation of the
token. Depending on the type of token being used, the CSP will either
create a new token and supply the token to the Subscriber, or require
the Subscriber to register a token that the Applicant already possesses
or has newly created. In either case, the mechanism for transporting the
token from the token origination point to the Subscriber may need to be
secured to ensure that the confidentiality and integrity of the newly
established token is maintained and that token is in possession of
correct Applicant.

The CSP is also responsible for the creation of a credential that binds
the Subscriber’s identity to his or her token. Optionally, the CSP may
include other verified attributes about the Subscriber within the
credential, such as his or her organizational affiliation, policies, or
constraints for token use.

In models where the registration and identity proofing take place
separately from credential issuance, the CSP is responsible for
verifying that the credential is being issued to the same person who was
identity proofed by the RA. In this model, issuance must be strongly
bound to registration and identity proofing so that an Attacker cannot
pose as a newly registered Subscriber and attempt to collect a
token/credential meant for the actual Subscriber. This attack, and
similar attacks, can be thwarted by the methods described in Section
5.3.1 (below Table 3), which describes which techniques are considered
appropriate for establishing the necessary binding at the various
assurance levels.

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

### 5.3 Registration and Issuance Assurance Levels
The following sections list the NIST recommendations for registration
and issuance for the four levels corresponding to the OMB guidance. As
noted in the OMB guidance, Levels 1 and 2 recognize the use of
pseudonymous credentials. When pseudonymous credentials are used to
imply membership in a group, the level of proofing shall be consistent
with the requirements for the credential of that level. Explicit
requirements for registration processes for pseudonymous credentials are
not specified, as they are unique to the membership criteria for each
specific group.

#### 5.3.1 General Requirements per Assurance Level
For levels 2 and above records of registration shall be maintained
either by the RA or by the CSP, depending on the context. Either the RA
or the CSP shall maintain a record of each individual whose identity has
been verified and the steps taken to verify his or her identity,
including any information collected from the Applicant in compliance
with the sections below. The CSP shall have the capability to provide
records of identity proofing to RPs if required<sup>[11](#note11)</sup>. The identity
proofing and registration processes shall be performed according to
applicable written policy or *practice statement* that specifies the
particular steps taken to verify identities.

For Levels 2 and above, if the RA and CSP are remotely located and
communicate over a network, the entire registration transaction between
the RA and CSP shall occur over a mutually authenticated protected
session. Equivalently, the transaction may consist of time-stamped or
sequenced messages signed by their source and encrypted for their
recipient. In either case, Approved cryptography is required.

The CSP shall be able to uniquely identify each Subscriber and the
associated tokens and the credentials issued to that Subscriber. The CSP
shall be capable of conveying this information to Verifiers. At Level 1,
the name associated with the Subscriber is provided by the Applicant and
accepted without verification. At Level 2, the identifier associated
with the Subscriber may be pseudonymous but the RA or CSP shall retain
the actual identity of the Subscriber. In addition, pseudonymous Level 2
credentials shall be distinguishable from Level 2 credentials that
contain verified names.

At Level 3 and above, the name associated with the Subscriber shall be
verified. At all levels, personally identifiable information (PII)
collected as part of the registration process shall be protected, and
all privacy requirements shall be satisfied.

The following text establishes registration requirements specific to
each level, except as noted in the following subsections. There are no
level-specific requirements at Level 1. Both in-person and remote
registration are permitted for Levels 2 and 3. Remote registration
requirements are designed to permit fully automated solutions. However,
implementations may also leverage call centers or online assistance as a
substitute or complement for fully automated solutions. Explicit
requirements are specified for each scenario in Levels 2 and 3. At Level
4, only in-person registration is permitted.

At Level 2 and higher, the Applicant supplies his or her full legal
name, an address of record, and date of birth, and may, subject to the
policy of the RA or CSP, also supply other PII. Detailed level-by-level
identity proofing requirements are stated in Table 3.

In some contexts, once an agency has met the minimum registration
requirements for an assurance level, the agency may choose to use
additional knowledge based authentication methods to increase confidence
in the registration process. For example, an Applicant could be asked to
supply non-public information on his or her past dealing with the agency
that could help confirm the Applicant’s identity.

The sensitive data collected during the registration and identity
proofing stage shall be protected at all times (i.e., transmission,
storage) to ensure their security and confidentiality. Additionally, the
results of the identity proofing step (which may include background
investigations of the Applicant) have to be protected to ensure source
authentication, confidentiality, and integrity.

**Table 3 - Identity Proofing Requirements by Assurance Level**

|             | **In-Person** | **Remote** |
|-------------|---------------|------------|
| **Level 2**<sup>[12](#note12)</sup> | | |
| Basis for issuing credentials | Possession of a valid current primary government picture ID<sup>[13](#note13)</sup> that contains Applicant’s picture, and either address of record or nationality of record (e.g., driver’s license or Passport) | Possession of a valid current government ID<sup>[14](#note14)</sup> (e.g., a driver’s license or Passport) number and a financial or utility account number (e.g. checking account, savings account, utility account, loan or credit card, or tax ID) confirmed via records of either the government ID or account number. Note that confirmation of the financial or utility account may require supplemental information from the applicant.
| RA and CSP actions | ***RA*** inspects photo-ID; compares picture to Applicant; and records the ID number, address and date of birth (DoB). (***RA*** optionally reviews personal information in records to support issuance process “a” below.) If the photo-ID appears valid and the photo matches Applicant then: a)  If personal information in records includes a telephone number or e-mail address, the ***CSP*** issues credentials in a manner that confirms the ability of the Applicant to receive telephone communications or text message at phone number or e-mail address associated with the Applicant in records. Any secret sent over an unprotected session shall be reset upon first use; or | ***RA*** inspects both ID number and account number supplied by Applicant (e.g., for correct number of digits). Verifies information provided by Applicant including ID number OR account number through record checks either with the applicable agency or institution or through credit bureaus or similar databases, and confirms that: name, DoB, address and other personal information in records are on balance consistent with the application and sufficient to identify a unique individual. For utility account numbers, confirmation shall be performed by verifying knowledge of recent account activity. (This technique may also be applied to some financial accounts.)
| | b)  If ID confirms address of record, ***RA*** authorizes or ***CSP*** issues credentials. Notice is sent to address of record, or;                                                                                                                                                                                                                                                           c)  If ID does not confirm address of record, ***CSP*** issues credentials in a manner that confirms the claimed address. | Address/phone number confirmation and notification:<sup>[15](#note15)</sup> a.  ***CSP*** issues credentials in a manner that confirms the ability of the Applicant to receive mail at a physical address associated with the Applicant in records; or b.  If personal information in records includes a telephone number or e-mail address, the ***CSP*** issues credentials in a manner that confirms the ability of the Applicant to receive telephone communications or text message at phone number or e-mail address associated with the Applicant in records. Any secret sent over an unprotected session shall be reset upon first use and shall be valid for a maximum lifetime of seven days; or c.  ***CSP*** issues credentials. ***RA*** or ***CSP*** sends notice to an address of record confirmed in the records check.<sup>[16](#note16)</sup>
| **Level 3^12^** | | 
| Basis for issuing credentials| Possession of verified current primary Government Picture ID that contains Applicant’s picture and either address of record or nationality of record (e.g., driver’s license or passport) | Possession of a valid Government ID (e.g., a driver’s license or Passport) number and a financial or utility account number (e.g., checking account, savings account, utility account, loan or credit card) confirmed via records of both numbers. Note that confirmation of the financial or utility account may require supplemental information from the Applicant. |
| RA and CSP actions | ***RA*** inspects photo-ID and verifies via the issuing government agency or through credit bureaus or similar databases.  Confirms that: name, DoB, address and other personal information in record are consistent with the application. Compares picture to Applicant and records ID number. If ID is valid and photo matches Applicant, then: a)	If personal information in records includes a telephone number, the ***CSP*** issues credentials in a manner that confirms the ability of the Applicant to receive telephone communications at a number associated with the Applicant in records, while recording the Applicant’s voice or using alternative means that establish an equivalent level of non-repudiation; or b)	If ID confirms address of record, ***RA*** authorizes or ***CSP*** issues credentials. Notice is sent to address of record, or; c)	If ID does not confirm address of record, ***CSP*** issues credentials in a manner that confirms the claimed address. | •	RA verifies information provided by Applicant including ID number AND account number through record checks either with the applicable agency or institution or through credit bureaus or similar databases, and confirms that: name, DoB, address and other personal information in records are consistent with the application and sufficient to identify a unique individual. At a minimum, the records check for both the ID number AND the account number should confirm the name and address of the Applicant.   For utility account numbers, confirmation shall be performed by verifying knowledge of recent account activity.  (This technique may also be applied to some financial accounts.) •	Address confirmation: a) ***CSP*** issues credentials in a manner that confirms the ability of the applicant to receive mail at a physical address associated with the Applicant in records; or<sup>[15](#note15)</sup> b)	If personal information in records includes both an electronic address and a physical address that are linked together with the Applicant’s name, and are consistent with the information provided by the applicant, then the ***CSP*** may issue credentials in a manner that confirms ability of the Applicant to receive messages (SMS, voice or e-mail) sent to the electronic address.  Any secret sent over an unprotected session shall be reset upon first use and shall be valid for a maximum lifetime of seven days.| **Level 4^12** | | |
| Basis for issuing credentials | In-person appearance and verification of: a)	a current primary Government Picture ID that contains Applicant’s picture, and either address of record or nationality of record (e.g., driver’s license or passport), and; b)	either a second, independent Government ID document that contains current corroborating information (e.g., either address of record or nationality of record), OR verification of  a financial account number (e.g., checking account, savings account, loan or credit card) confirmed via records. | Not applicable 
| RA and CSP actions | •	*Primary Photo ID*: ***RA*** inspects photo-ID and verifies via the issuing government agency or through credit bureaus or similar databases.  Confirms that: name, DoB, address, and other personal information in record are consistent with the application. Compares picture to Applicant and records ID number. •	*Secondary Government ID or financial account* a)	***RA*** inspects secondary Government ID and if apparently valid, confirms that the identifying information is consistent with the primary Photo-ID, or; b)	***RA*** verifies financial account number supplied by Applicant through record checks or through credit bureaus or similar databases, and confirms that: name, DoB, address, and other personal information in records are on balance consistent with the application and sufficient to identify a unique individual. **\[Note:  Address of record shall be confirmed through validation of either the primary or secondary ID.\]** •	*Current Biometric* ***RA*** records a current biometric (e.g., photograph or fingerprints) to ensure that Applicant cannot repudiate application. •	*Credential Issuance* ***CSP*** issues credentials in a manner that confirms address of record. | Not applicable |

Remote registration at Levels 2 and 3 requires confirmation of a
financial or utility account number. The requirement for a financial
account or utility account number may be satisfied by a cellular or
landline telephone service account under the following conditions:

-   the phone is associated in Records with the Applicant's name and
    address of record; and

-   the applicant demonstrates that they are able to send or receive
    messages at the phone number.

Registration, identity proofing, token creation/issuance, and credential
issuance are separate processes that can be broken up into a number of
separate physical encounters or electronic transactions. (Two electronic
transactions are considered to be separate if they are not part of the
same protected session.) In these cases, the following methods shall be
used to ensure that the same party acts as Applicant throughout the
processes:

-   At Level 1, there is no specific requirement, however some effort
    should be made to uniquely identify and track applications.

-   At Level 2: For electronic transactions, the Applicant shall
    identify himself/herself in any new transaction (beyond the first
    transaction or encounter) by presenting a temporary secret which was
    established during a prior transaction or encounter, or sent to the
    Applicant’s phone number, email address, or physical address
    of record. For physical transactions, the Applicant shall identify
    himself/herself in person by either using a secret as described
    above, or by biometric verification (comparing a captured biometric
    sample to a reference biometric sample that was enrolled during a
    prior encounter).

-   At Level 3: For electronic transactions, the Applicant shall
    identify himself/herself in each new electronic transaction by
    presenting a temporary secret which was established during a prior
    transaction or encounter, or sent to the Applicant’s phone number,
    email address, or physical address of record. Permanent secrets
    shall only be issued to the Applicant within a protected session.

    For physical transactions, the Applicant shall identify
    himself/herself in person by either using a secret as described above,
    or through the use of a biometric that was recorded during a prior
    encounter. Temporary secrets shall not be reused. If the CSP issues
    permanent secrets during a physical transaction, then they shall be
    loaded locally onto a physical device that is issued in person to the
    Applicant or delivered in a manner that confirms the address of
    record.

-   At Level 4: Only physical transactions apply. The Applicant shall
    identify himself/herself in person in each new physical transaction
    through the use of a biometric that was recorded during a prior
    encounter.<sup>[17](#note17)</sup> If the CSP issues permanent secrets, then they shall
    be loaded locally onto a physical device that is issued in person or
    delivered in a manner that confirms the address of record.

A common reason for breaking up the registration process as described
above is to allow the subscriber to register or obtain tokens for use in
two or more environments. This is permissible as long as the tokens
individually meet the appropriate assurance level. However, if the exact
number of tokens to be issued is not agreed upon early in the
registration process, then the tokens should be distinguishable so that
Verifiers will be able to detect whether any suspicious activity occurs
during the first few uses of a newly issued token.

If a valid credential has already been issued, the CSP may issue another
credential of equivalent or lower assurance. In this case, proof of
possession and control of the original token may be substituted for
repeating the identity proofing steps. (This is a special case of a
derived credential. See Section 5.3.5 for procedures when the derived
credential is issued by a different CSP.) Any requirements for
credential delivery at the appropriate Level shall still be satisfied.

#### 5.3.2 Requirements for Educational and Financial Institutions and other Organizations

The relationships of many organizations (e.g., corporations, healthcare
organizations, educational institutions and financial institutions) to
the individuals who are employees, affiliates, associates, students and
customers are often regulated or supervised by government, while law and
regulation place burdens on these organizations to know the identities
of such individuals. The strength of these relationships and the
obligations of organizations to know identities vary considerably, for
example employers have legal obligations to withhold and pay taxes on
employees and are regulated by a variety of local, state and Federal
entities, but the certainty enforced in many employment situations is
not high. Retail stores are not broadly required to know their
customers, but financial institutions are. Healthcare organizations are
regulated at many levels and are expected to know the identities and
professional qualifications of their professional staff, as are legal
and accounting firms. This section identifies several areas where these
organizations may leverage their existing relationships with individuals
to act as CAs or CSPs for those individuals and issue credentials for
use with Federal entities.

At Level 2, employers and educational institutions who verify the
identity of their employees or students by means comparable to those
stated above for Level 2 may elect to become an RA or CSP and issue
credentials to employees or students, either in-person by inspection of
a corporate or school issued picture ID, or through online processes,
where notification is via the distribution channels normally used for
sensitive, personal communications.

Federal or State laws and regulations impose requirements for
institutions in certain businesses to confirm the educational and
licensing credentials for selected employees or affiliates. For example,
a health care organization that has accepted the Medicare "Conditions
for Participation" is required to examine the credentials for each
candidate for the medical staff. Where such institutions rigorously
confirm the identity, education, and licensing credentials of a licensed
professional through an in-person appearance before employment or
affiliation, this specification permits issuing e-authentication
credentials without repeating the identity proofing process.

The initial process for confirming the identity, education, and
licensing credentials of a licensed professional through an in-person
process must include the following steps:

-   Verification of a current primary Government Picture ID that
    contains Applicant’s picture, and either address of record or
    nationality of record (e.g., a driver’s license or passport);

-   Verification of post-secondary education/training of two or more
    years appropriate for the position (e.g., an appropriate medical
    degree); and

-   Verification of current state or federal licensure (e.g., as
    a physician) based on an examination process, with requirements for
    continuing education or active professional participation as a
    condition of valid licensing.

(Examples of licensed professionals that would generally be eligible for
streamlined credential issuance include medical doctors, registered
nurses, dentists, pharmacists, optometrists, veterinarians, lawyers, and
licensed professional engineers.)

Institutions that have performed a process satisfying these conditions
may issue e-authentication tokens and credentials to those employees and
affiliates with verified credentials at Levels 2, 3, or 4 provided that:

-   the issuance process is either:

    1.  in-person, or
    
    2.  for Levels 2 and 3, the remote issuance process incorporates the
        address/phone number confirmation appropriate for that level, and

-   they meet the corresponding provisions of Sections 6 through 9 for
    that Level.

Federal law, including the Bank Secrecy Act and the USA PATRIOT Act,
imposes a duty on financial institutions to “know their customers” and
report suspicious transactions to help prevent money laundering and
terrorist financing. Many financial institutions are regulated by
Federal agencies such as the Office of the Comptroller of the Currency
(OCC) or other members of the Federal Financial Institutions Examination
Council (FFIEC) and the Securities and Exchanges Commission (SEC). These
regulators normally require the institutions to implement a Customer
Identification Program.

The following provisions apply to Federally regulated financial
institutions, brokerages and dealers subject to such Federal regulation,
that implement such a Customer Identification Program:

-   At Level 2, such institutions may issue credentials to their
    customers via the mechanisms normally used for online banking or
    brokerage credentials and may use online banking or brokerage
    credentials and tokens as Level 2 e-authentication credentials and
    tokens, provided they meet the provisions of Sections 6 through 9
    for Level 2.

-   At Level 3, such institutions may issue credentials to their
    customers via the mechanisms normally used for online banking or
    brokerage credentials and may use online banking or brokerage
    credentials and tokens as Level 3 e-authentication credentials and
    tokens, provided:

1.  The customers have been in good standing with the institution for a
    period of at least 1 year prior to the issuance of e-authentication
    credentials, and

2.  The credentials and tokens meet the provisions of Sections 6 through
    9 for Level 3.

-   At Level 4, such institutions may issue credentials to their
    customers via the mechanisms normally used for online banking or
    brokerage credentials and may use online banking or brokerage
    credentials and tokens as Level 4 e-authentication credentials,
    provided:

1.  The customers have appeared in-person before a representative of the
    financial institution, and the representative has inspected a
    Government issued primary Photo-ID and compared the picture to the
    customer; and

2.  The credentials and tokens meet all additional provisions of Section
    5, as well as all provisions in Sections 6 through 9 for Level 4,
    as appropriate.

#### 5.3.3 Requirements for Certificates Issued under FPKI and Mapped Policies         

The identity proofing and certificate issuance processes specified in
the Federal PKI Certificate Policies \[FBCA1, FBCA2, FBCA3\] are
considered equivalent to the requirements specified in Section 5.3.1 in
accordance with [Appendix B].

At Level 2, agencies may rely on any CA whose policy satisfies the
identity proofing and registration requirements specified for Level 2,
in addition to any CA cross-certified with the Federal Bridge CA under
one of the certificate policies identified in Appendix B as a Level 2
certificate or a policy mapped to one of those policies through
cross-certificates. For Levels 3 and 4, agencies shall only accept PKI
certificates issued by a CA cross-certified with the Federal Bridge CA
under one of the certificate policies identified in Appendix B as a
Level 3 or Level 4 certificate or a policy mapped to one of those
policies through cross-certificates.

The identity proofing and certificate issuance processes specified in
Federal Information Processing Standard (FIPS) 201, ‘Personal Identity
Verification’ \[FIPS201\], meet and exceed the Level 4 requirements
specified in the preceding section.

#### 5.3.4 Requirements for One-Time Use

For infrequently used applications, issuance and maintenance of
credentials would be prohibitively expensive. Claimants can be
authenticated for immediate one-time access to an application for Levels
1 through 3. At Level 1, there is no requirement for identity proofing
before one-time use. At Levels 2 and 3, application owners act as the
RA/CSP in the remote registration processes described in Section 5.3.1,
using processes that do not require confirmation of the address of
record and omitting credential issuance.

For immediate one-time access at Level 2, application owners can use the
registration processes specified in Table 3 that:

-   Confirm "the ability of the Applicant to receive telephone
    communications or text message at phone number or e-mail address
    associated with the Applicant in records”; or

-   Subsequently send a “notice to an address of record confirmed in the
    records check.”

For immediate one-time access at Level 3, application owners can use the
registration process specified in Table 3 that:

-   Confirms "the ability of the Applicant to receive telephone
    communications at a phone number associated with the Applicant in
    records while recording the Applicant’s voice or using alternative
    means that establish an equivalent level of non-repudiation.”

#### 5.3.5 Requirements for Derived Credentials
Where the Applicant already possesses recognized authentication
credentials, the CSP may choose to identity proof the Claimant by
verifying possession and control of the token associated with the
credentials and issue a new derived credential.

Before issuing any derived credential the CSP shall verify the original
credential status and shall verify that the corresponding token is
possessed and controlled by the Claimant. The status of the original
credential should be re-checked at a later date (e.g. after a week) to
confirm that it was not compromised at the time of issuance of the
derived credential. (This guards against the case where an Attacker
requests the desired credential before revocation information can be
updated.) Further, the CSP shall record the details of the original
credential used as the basis for derived credential issuance. If the
derived credential is revoked, the CSP that issued the derived
credential may notify the issuer of the original credential, if the
reason for revocation might motivate action by the issuer of the
original credential and applicable law, regulation, and agreements
permit such notification.

The CSP may issue a derived level 4 credential for a suitable Level 4
capable token, based on an original level 4 credential. Before issuing
the derived Level 4 credential, the CSP shall:

-   Obtain and verify a copy of a biometric recorded when the original
    credential was issued. An example of such a biometric is the signed
    biometric data object on a PIV card, however if the biometric
    reference is not available from the Level 4 token, it may be
    obtained elsewhere, as long as its authenticity is assured;

-   Compare a fresh biometric sample obtained in person from the
    Applicant to the reference biometric retained from the original
    Level 4 credentials and determine that they match, and;

-   Determine that the token that contains the token secret associated
    with the derived credential meets the requirements of Table 6 for a
    Level 4 token.

The CSP may issue a Level 3 derived credential based on proof of
possession of a Level 4 token. Issuance may be in person or remote. If
Level 3 credentials are electronically transmitted, or physically
shipped with a token to a claimant, then token activation shall require
proof of possession of both the derived token and the original Level 4
token.

The CSP may issue a Level 2 derived credential based on proof of
possession of a Level 3 or 4 token. Issuance may be in person or remote.
If Level 2 credentials are electronically transmitted, or physically
shipped with a token to a claimant, then token activation shall require
proof of possession of both the derived token and the original Level 3
or Level 4 token.

In some cases, there may be a desire to tightly couple the revocation
status of the derived credential to the original. In this case, it is
the responsibility of the CSP that issued the derived credential to
ensure that a tight coupling is maintained. For example, the issuer of
the derived credential could regularly monitor the status of the primary
credential.<sup>[18](#note18)</sup> <sup>[19](#note19)</sup>

---
**Footnotes**

<a name="note9">9</a>: See NIST SP800-53, Recommended Security Controls For Federal Information Systems for appropriate security controls.

<a name="note10">10</a>: Some impostors may attempt to register as any Subscriber in the system and other impostors may wish to register as a specific Subscriber.

<a name="note11">11</a>: It is beyond the scope of this document to specify what circumstances make it is necessary and/or appropriate for the CSP to provide this information. Refer to applicable privacy laws, rules of evidence etc.

<a name="note12">12</a>: A token at this Level may also be obtained by authenticating to the CSP using mechanisms at the same or a higher Level (e.g. PIV). See 5.3.5 for more information.

<a name="note13">13</a>: The following resources offer examples of what some agencies consider to be primary or secondary ID:- USCIS Form I-9, "Lists of Acceptable Documents", http://www.uscis.gov/files/form/i-9.pdf- Instructions for First Time Passport Applicants http://travel.state.gov/passport/get/first/first_830.html#step4first- Secondary Evidence of Identification http://travel.state.gov/passport/get/secondary_evidence/secondary_evidence_4314.html

<a name="note14">14</a>: Agencies issuing credentials to foreign nationals residing in foreign countries determine what constitutes a valid Government issued ID as required.

<a name="note15">15</a>: Requirements that use USPS mail for address confirmation and/or notification have a legal basis:  Title 18 U.S. Code: Criminal Procedure, Section 1708: Theft or receipt of stolen mail matter generally.

<a name="note16">16</a>: Agencies are encouraged to use methods a) and b) where possible to achieve better security.  Method c) is especially weak when not used in combination with knowledge of account activity

<a name="note17">17</a>: Special arrangements can be made for Applicants who are unable to provide the required biometrics.

<a name="note18">18</a>: This document does not require or prevent CSPs from linking the expiration of the original and derived credentials. However, where the revocation status is tightly coupled, this may simplify revocation procedures.

<a name="note19">19</a>: Requirements for derived credentials issued by the same CSP are at the end of Section 5.3.1.