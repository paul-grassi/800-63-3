
## 1. Purpose

This recommendation and its companion documents, SP 800-63A, SP 800-63B, and SP 800-63C, provide technical guidelines to agencies for the implementation of digital authentication.

##2. Introduction

Digital authentication is the process of
establishing confidence in user identities presented to
an information system. Digital authentication presents a technical challenge
when this process involves the remote authentication of individual
people over a network. This recommendation provides technical guidelines
to agencies to allow an individual person to remotely authenticate
his/her identity to a Federal Information Technology (IT) system. This
recommendation also provides guidelines for Registration Authorities
(RAs), Verifiers, Relying Parties (RPs) and Credential Service Providers
(CSPs).

Current government systems do not separate the functions of
authentication and attribute providers. However, in some applications, these
functions are provided by different parties. This document describes authenticator assurance and identity assurance as separate metrics, and provides a mapping between these metrics and overall level of assurance.

These technical guidelines supplement OMB guidance, *E-Authentication
Guidance for Federal Agencies* \[[OMB M-04-04](#OMB_0404)\] and
supersede NIST SP 800-63-1 and SP 800-63-2. OMB M-04-04 defines four levels of
assurance, Levels 1 to 4, in terms of the consequences of authentication
errors and misuse of credentials. Level 1 is the lowest assurance level
and Level 4 is the highest. The guidance defines the required level of
authentication assurance in terms of the likely consequences of an
authentication error. As the consequences of an authentication error
become more serious, the required level of assurance increases. The OMB
guidance provides agencies with criteria for determining the level of
assurance required for specific digital transactions
and systems, based on the risks and their likelihood of occurrence.

SP 800-63 is organized as a family of documents as follows:

- SP 800-63A *Enrollment and Identity Proofing* - Deals with the processes by which a credential, and authenticator(s) associated with that credential can be bound to a specific individual. This typically happens when that individual is enrolled in an identity system, through the identity proofing process.

- SP 800-63B *Subscriber Authentication* - provides guidance on the selection, use, and management of authenticators (formerly called *tokens*) to authenticate a remote subscriber to an identity system at specified authenticator assurance levels.

- SP 800-63C *Authentication-based Assertions* - Provides guidance on the use of assertions to convey the results of authentication processes to a relying party.

It is anticipated that SP 800-63A, SP 800-63B, and SP 800-63C will be revised asynchronously with each other and with this document. The latest revision of each should be used for guidance.

OMB guidance outlines a five-step process by which agencies should meet
their authentication assurance requirements:

1.  *Conduct a risk assessment of the government system* – No specific
    risk assessment methodology is prescribed for this purpose;
    however, the e-RA tool<sup>[1](#note1)</sup> at &lt;<http://www.idmanagement.gov/>&gt;
    is an example of a suitable tool and methodology, while NIST Special
    Publication (SP) 800-30 \[[SP 800-30](#SP800_30)\] offers a general
    process for Risk Assessment and Risk Mitigation.

2.  *Map identified risks to the appropriate assurance level* – Section
    2.2 of OMB M-04-04 provides the guidance necessary for agencies to
    perform this mapping.

3.  *Select technology based on digital authentication technical guidance* –
    After the appropriate assurance level has been determined, OMB
    guidance states that agencies should select technologies that meet
    the corresponding technical requirements, as specified by
    this document. Some agencies may possess existing
    digital authentication technology. Agencies should verify that any
    existing technology meets the requirements specified in
    this document.

4.  *Validate that the implemented system has met the required assurance
    level* – As some implementations may create or compound particular
    risks, agencies should conduct a final validation to confirm that
    the system achieves the required assurance level for the
    user-to-agency process. NIST SP 800-53A \[[SP 800-53A](#SP800_53A)\]
    provides guidelines for the assessment of the implemented system
    during the validation process. Validation should be performed as
    part of a security authorization process as described in NIST SP
    800-37, Revision 1 \[[SP 800-37](#SP800_37)\].

5.  *Periodically reassess the information system to determine
    technology refresh requirements* – The agency shall periodically
    reassess the information system to ensure that the identity
    authentication requirements continue to be satisfied. NIST SP
    800-37, Revision 1 \[[SP 800-37](#SP800_37)\] provides guidelines on
    the frequency, depth and breadth of periodic reassessments. As with
    the initial validation process, agencies should follow the
    assessment guidelines specified in SP 800-53A \[[SP
    800-53A](#SP800_53A)\] for conducting the security assessment.

This family of documents provides guidelines for implementing the third step of the
above process. In particular, this document maps the four Levels of Assurance defined in OMB M-04-04 into corresponding authenticator assurance and identity assurance levels. Other documents in the family state specific technical
requirements for identity assurance and authenticator assurance in the following
areas:

-   Identity proofing and registration of Applicants (covered in SP 800-63A)

-   Credential lifecycle and management mechanisms (covered in SP 800-63A)

-   Authenticators (typically a cryptographic key or password) for
    authentication (covered in SP 800-63B)
    
-	Authenticator lifecycle and management mechanisms (covered in SP 800-63B)

-   Protocols used to support the authentication mechanism between the
    Claimant and the Verifier (covered in SP 800-63B)

-   Assertion mechanisms used to communicate the results of a remote
    authentication if these results are sent to other parties (covered
    in SP 800-63C).

The overall authentication assurance level is determined by the lowest identity assurance and authenticator assurance level achieved in any of the areas listed above, and then by mapping the result to the corresponding Level of Assurance.

Agencies may adjust the level of assurance using additional risk
mitigation measures. Easing credential assurance level requirements may
increase the size of the enabled customer pool, but agencies shall
ensure that this does not corrupt the system’s choice of the appropriate
assurance level. Alternatively, agencies may consider partitioning the
functionality of an digital authentication enabled application to allow less
sensitive functions to be available at a lower level of authentication
and attribute assurance, while more sensitive functions are available
only at a higher level of assurance.

These technical guidelines cover remote digital authentication of
human users to IT systems over a network. They do not address the
authentication of a person who is physically present, for example, for
access to buildings, although some credentials and authenticators that are used
remotely may also be used for local authentication. These technical
guidelines establish requirements that Federal IT systems and service
providers participating in authentication protocols be authenticated to
Subscribers. However, these guidelines do not specifically address
machine-to-machine (such as router-to-router) authentication, or
establish specific requirements for issuing authentication credentials
and authenticators to machines and servers when they are used in
authentication protocols with people.

The paradigm of this document is that individuals are enrolled, issued an authenticator, and
undergo a registration process in which their identity is bound to that authenticator. Thereafter, the individuals are remotely authenticated to systems
and applications over a network, using the authenticator in an authentication
protocol. The authentication protocol allows an individual to
demonstrate to a Verifier that he or she has possession and control of
the authenticator<sup>[2](#note2)</sup>, in a manner that protects the authenticator secret from
compromise by different kinds of attacks. Higher authenticator assurance levels require use of stronger authenticators, better protection of
the authenticator(s) and related secrets from attacks. Higher identity assurance levels require stronger registration procedures.

This document family focuses on authenticators that are difficult to forge because they
contain some type of secret information that is not available to
unauthorized parties and that is preferably not used in unrelated
contexts. Certain authentication technologies, particularly biometrics
and knowledge based authentication, use information that is private
rather than secret. While they are discussed to a limited degree, they
are largely avoided because their security is often weak or difficult to
quantify<sup>[3](#note3)</sup>, especially in the remote situations that are the primary
scope of this document.

Knowledge based authentication achieves authentication by testing the
personal knowledge of the individual against information obtained from
public databases. As this information is considered private but not
actually secret, confidence in the identity of an individual can be hard
to achieve. In addition, the complexity and interdependencies of
knowledge based authentication systems are difficult to quantify.
However, knowledge based authentication techniques are included as part
of registration in this document.

Biometric characteristics do not constitute secrets suitable for use in
the conventional remote authentication protocols addressed in this
document either. In the local authentication case (which is outside the scope of this document family), where the Claimant is
observed by an attendant and uses a capture device controlled by the
Verifier, authentication does not require that biometrics be kept
secret. This document supports the use of biometrics to “unlock”
multifactor authentication authenticators, to prevent repudiation of
registration, and to verify that the same individual participates in all
phases of the registration process.

This document identifies minimum technical requirements for remotely
authenticating users. Agencies may determine based on their risk
analysis that additional measures are appropriate in certain contexts.
In particular, privacy requirements and legal risks may lead agencies to
determine that additional authentication measures or other process
safeguards are appropriate. When developing digital authentication processes
and systems, agencies should consult *OMB Guidance for Implementing the
Privacy Provisions of the E-Government Act of 2002* \[[OMB
M-03-22](#_General_References)\]. See the *Guide to Federal Agencies on
Implementing Electronic Processes* \[[DOJ 2000](#DOJ2000)\] for
additional information on legal risks, especially those that are related
to the need to satisfy legal standards of proof and prevent repudiation,
as well as *Use of Electronic Signatures in Federal Organization
Transactions* \[[GSA ESIG](#GSA_ESIG)\].

Additionally, Federal agencies implementing these guidelines should
adhere to the requirements of Title III of the E-Government Act,
entitled the *Federal Information Security Management Act*
\[[FISMA](#FISMA)\], and the related NIST standards and guidelines.
FISMA directs Federal agencies to develop, document, and implement
agency-wide programs to provide information security for the information
and information systems that support the operations and assets of the
agency. This includes the security authorization of IT systems that
digital authentication. It is recommended that non-Federal entities
implementing these guidelines follow equivalent standards of security
management, certification and accreditation to ensure the secure
operations of their digital systems.

###2.1. Relationship to Other Standards and Guidelines

This document has been written with the intention of achieving alignment to National and International standards describing levels of identity assurance, including CESG Good Practice Guide No. 43 (GPG 43), Requirements for Secure Delivery of Online Public Services (RSDOPS) (reference [a]). It provides an interpretation of these levels of assurance in the context of IPV for UK public sector for both citizen and internal system users.7. This is not meant to imply that there is direct correlation between the Assured Identity Levels in this document and the levels in those standards but that it is seen that this document fulfils the criteria as demonstrated in those standards.8. This document only covers the identity proofing and verification processes, therefore, it may only fulfil part of the requirements of these standards and further measures are required in order to wholly comply (e.g. issuing of a credential). 



GPG 45 RSDOPS STORK 2.0 29115:2011 ISO 29003 NIST 800-63N/ALevel 01N/AN/AN/AN/ALevel 1Level 1QAA Level 1LoA 1LoA 1Level 1Level 2Level 2QAA Level 2LoA 2LoA 2Level 2Level 3Level 3QAA Level 3LoA 3LoA 3Level 3Level 4N/A2QAA Level 4LoA 4LoA 4Level 4

###2.2. Change History

####2.2.1. SP 800-63-1

NIST SP 800-63-1 updated NIST SP 800-63 to reflect current authenticator (then referred to as token)
technologies and restructured to provide a better understanding of the
digital authentication architectural model used here. Additional (minimum)
technical requirements were specified for the CSP, protocols utilized to
transport authentication information, and assertions if implemented
within the digital authentication model. Other changes to NIST SP 800-63
included:

-   Recognition of more types of tokens, including pre-registered
    knowledge token, look-up secret token, out-of-band token, as well
    as some terminology changes for more conventional token types;

-   Detailed requirements for assertion protocols and Kerberos;

-   A new section on token and credential management;

-   Simplification of guidelines for password entropy and throttling;

-   Emphasis that the document is aimed at Federal IT systems;

-   Recognition of different models, including a broader
    digital authentication model (in contrast to the simpler model common
    among Federal IT systems shown in Figure 1) and an additional
    assertion model, the Proxy Model, presented in Figure 6;

-   Clarification of differences between Levels 3 and 4 in Table 12; and

-   New guidelines that permit leveraging existing credentials to issue
    derived credentials.

The subsequent sections of NIST SP 800-63-1 presented a series of
recommendations for the secure implementation of RAs, CSPs, Verifiers,
and RPs. It should be noted that secure implementation of any one of
these can only provide the desired level of assurance if the others are
also implemented securely. Therefore, the following assumptions were
made in NIST SP 800-63-1:

-   RAs, CSPs, and Verifiers are trusted entities. Agencies implementing
    any of the above trusted entities have some assurance that all other
    trusted entities with which the agency interacts are also
    implemented appropriately for the desired security level.

-   The RP is not considered a trusted entity. However, in some
    authentication systems the Verifier maintains a relationship with
    the RP to facilitate secure communications and may employ security
    controls which only attain their full value when the RP
    acts responsibly. The Subscriber also trusts the RP to properly
    perform the requested service and to follow all relevant
    privacy policy.

-   It is assumed that there exists a process of certification through
    which agencies can obtain the above assurance for trusted entities
    which they do not implement themselves.

-   A trusted entity is considered to be implemented appropriately if it
    complies with the recommendations in this document and does not
    behave maliciously.

-   While it is generally assumed that trusted entities will not behave
    maliciously, this document does contain some recommendations to
    reduce and isolate any damage done by a malicious or negligent
    trusted entity.

####2.2.2 SP 800-63-2

NIST SP 800-63-2 was a limited update of Special Publication 800-63-1 and
substantive changes were made only in section 5. *Registration and
Issuance Processes*. The substantive changes in the revised draft were
intended to facilitate the use of professional credentials in the
identity proofing process, and to reduce the need to use postal mail to
an address of record to issue credentials for level 3 remote
registration. Other changes to section 5 were minor explanations and
clarifications.


####2.2.3. SP 800-63-3

NIST SP 800-63-3 is a substantial update and restructuring of Special Publication 800-63-2. It introduces the concepts of Authenticator Assurance Level and Identity Assurance Level to support the growing need for independent treatment of authentication strength and confidence in the claimant's identity (for example, in strong pseudonymous authentication). It also moves from a single document describing authentication to a family of four documents, of which SP 800-63-3 is the top-level document.Other areas of update to SP 800-63-2 include:
-	Terminology changes, primarily the use of *authenticator* in place of *token* to avoid conflicting use of the word *token* in assertion technologies-	Updates to authentication and assertion requirements to reflect advances in both security technology and threats-	Requirements on the storage of long-term secrets by verifiers-	Updated requirements regarding remote identity proofing-	Clarification on the use of independent channels and devices as “something you have”-	Removal of pre-registered knowledge tokens (authenticators), with the recognition that they are special cases of (often very weak) passwords.-	Requirements regarding account recovery in the event of loss or theft of an authenticator

---
**Footnotes**

<a name="note1">1</a>: At the time of publication, the specific URL for this tool is at <http://www.idmanagement.gov/drilldown.cfm?action=era>.  Alternatively, the tool can be found by searching for “Electronic Risk and Requirements Assessment (e-RA)” at <http://www.idmanagement.gov/>.

<a name="note2">2</a>: SP 800-63-3 uses the term *authenticator* in place of *token* in order to avoid conflicts with the common use of *token* in assertion protocols. See Section 3 for more information.

<a name="note3">3</a>: For example, see article by V. Griffith and M. Jakobsson, entitled “Messin’ with Texas – Deriving Mother’s Maiden Names Using Public Records,” in RSA CryptoBytes, Winter 2007. 

