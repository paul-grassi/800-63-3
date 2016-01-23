## NIST Special Publication 800-63-2

# Electronic Authentication Guideline

William E. Burr  
Donna F. Dodson  
Elaine M. Newton  
Ray A. Perlner  
W. Timothy Polk  
Sarbari Gupta  
Emad A. Nabbus

![](media/nist_logo.png)

## NIST Special Publication 800-63-2

# Electronic Authentication Guideline

William E. Burr  
Donna F. Dodson  
Elaine M. Newton  
Ray A. Perlner  
W. Timothy Polk  
*Computer Security Division  
Information Technology Laboratory*

Sarbari Gupta  
Emad A. Nabbus  
*Electrosoft Services, Inc.  
Reston, VA*

August 2013

![](media/commerce_logo.png)

U.S. Department of Commerce  
*Penny Pritzker, Secretary*

National Institute of Standards and Technology  
*Patrick D. Gallagher, Under Secretary of Commerce for Standards and
Technology and Director*

### Authority

This publication has been developed by NIST to further its statutory
responsibilities under the Federal Information Security Management Act
(FISMA), Public Law (P.L.) 107-347. NIST is responsible for developing
information security standards and guidelines, including minimum
requirements for Federal information systems, but such standards and
guidelines shall not apply to national security systems without the
express approval of appropriate Federal officials exercising policy
authority over such systems. This guideline is consistent with the
requirements of the Office of Management and Budget (OMB) Circular
A-130, Section 8b(3), *Securing Agency Information Systems*, as analyzed
in Circular A-130, Appendix IV: *Analysis of Key Sections*. Supplemental
information is provided in Circular A-130, Appendix III, *Security of
Federal Automated Information Resources*.

Nothing in this publication should be taken to contradict the standards
and guidelines made mandatory and binding on Federal agencies by the
Secretary of Commerce under statutory authority. Nor should these
guidelines be interpreted as altering or superseding the existing
authorities of the Secretary of Commerce, Director of the OMB, or any
other Federal official. This publication may be used by nongovernmental
organizations on a voluntary basis and is not subject to copyright in
the United States. Attribution would, however, be appreciated by NIST.

National Institute of Standards and Technology Special Publication
800-63-2  
Natl. Inst. Stand. Technol. Spec. Publ. 800-63-2, 112 pages (August
2013)  
CODEN: NSPUE2

**Comments on this publication may be submitted to:**

National Institute of Standards and Technology  
Attn: Computer Security Division, Information Technology Laboratory  
100 Bureau Drive (Mail Stop 8930) Gaithersburg, MD 20899-8930  
Email: <eauth-comments@nist.gov>


### Reports on Computer Systems Technology

The Information Technology Laboratory (ITL) at the National Institute of
Standards and Technology (NIST) promotes the U.S. economy and public
welfare by providing technical leadership for the Nation’s measurement
and standards infrastructure. ITL develops tests, test methods,
reference data, proof of concept implementations, and technical analyses
to advance the development and productive use of information technology.
ITL’s responsibilities include the development of management,
administrative, technical, and physical standards and guidelines for the
cost-effective security and privacy of other than national
security-related information in Federal information systems. The Special
Publication 800-series reports on ITL’s research, guidelines, and
outreach efforts in information system security, and its collaborative
activities with industry, government, and academic organizations.

### Abstract

This recommendation provides technical guidelines for Federal agencies
implementing electronic authentication and is not intended to constrain
the development or use of standards outside of this purpose. The
recommendation covers remote authentication of users (such as employees,
contractors, or private individuals) interacting with government IT
systems over open networks. It defines technical requirements for each
of four levels of assurance in the areas of identity proofing,
registration, tokens, management processes, authentication protocols and
related assertions. This publication supersedes NIST SP 800-63-1.

### Keywords

authentication; authentication assurance; credential service provider;
electronic authentication; electronic credentials; identity proofing;
passwords; PKI; tokens.

### Acknowledgements

The authors, William Burr, Donna Dodson, Elaine Newton, Ray Perlner, Tim
Polk of the National Institute of Standards and Technology (NIST), and
Sarbari Gupta, and Emad Nabbus of Electrosoft, would like to acknowledge
the contributions of our many reviewers, including Jim Fenton from
OneID, Hildegard Ferraiolo from NIST, and Erika McCallister from NIST,
as well as those from Enspier, Orion Security, and MITRE.

### Executive Summary

Electronic authentication (e-authentication) is the process of
establishing confidence in user identities electronically presented to
an information system. E-authentication presents a technical challenge
when this process involves the remote authentication of individual
people over an open network, for the purpose of electronic government
and commerce. The guidelines in this document assume the authentication
and transaction take place across an open network such as the Internet.
In cases where the authentication and transaction take place over a
controlled network, agencies may take these security controls into
account as part of their risk assessment.

This recommendation provides technical guidelines to agencies to allow
an individual to remotely authenticate his or her identity to a Federal
IT system. This document may inform but does not restrict or constrain
the development or use of standards for application outside of the
Federal government, such as e-commerce transactions. These guidelines
address only traditional, widely implemented methods for remote
authentication based on secrets. With these methods, the individual to
be authenticated proves that he or she knows or possesses some secret
information.

Current government systems do not separate functions related to identity
proofing in registration from credential issuance. In some applications,
credentials (used in authentication) and attribute information
(established through identity proofing) could be provided by different
parties. While a simpler model is used in this document, it does not
preclude agencies from separating these functions.

These technical guidelines supplement OMB guidance, *E-Authentication
Guidance for Federal Agencies* \[[OMB M-04-04](#OMB_0404)\] and
supersede NIST SP 800-63-1. OMB M-04-04 defines four levels of
assurance, Levels 1 to 4, in terms of the consequences of authentication
errors and misuse of credentials. Level 1 is the lowest assurance level,
and Level 4 is the highest. The OMB guidance defines the required level
of authentication assurance in terms of the likely consequences of an
authentication error. As the consequences of an authentication error
become more serious, the required level of assurance increases. The OMB
guidance provides agencies with the criteria for determining the level
of e-authentication assurance required for specific applications and
transactions, based on the risks and their likelihood of occurrence of
each application or transaction.

OMB guidance outlines a 5-step process by which agencies should meet
their e-authentication assurance requirements:

1.  Conduct a risk assessment of the government system.

2.  Map identified risks to the appropriate assurance level.

3.  Select technology based on e-authentication technical guidance.

4.  Validate that the implemented system has met the required
    assurance level.

5.  Periodically reassess the information system to determine technology
    refresh requirements.

This document provides guidelines for implementing the third step of the
above process. After completing a risk assessment and mapping the
identified risks to the required assurance level, agencies can select
appropriate technology that, at a minimum, meets the technical
requirements for the required level of assurance. In particular, the
document states specific technical requirements for each of the four
levels of assurance in the following areas:

-   Identity proofing and registration of Applicants (covered in Section
    5),

-   Tokens (typically a cryptographic key or password) for
    authentication (covered in Section 6),

-   Token and credential management mechanisms used to establish and
    maintain token and credential information (covered in Section 7),

-   Protocols used to support the authentication mechanism between the
    Claimant and the Verifier (covered in Section 8),

-   Assertion mechanisms used to communicate the results of a remote
    authentication if these results are sent to other parties (covered
    in Section 9).

A summary of the technical requirements for each of the four levels is
provided below.

**Level 1** - Although there is no identity proofing requirement at this
level, the authentication mechanism provides some assurance that the
same Claimant who participated in previous transactions is accessing the
protected transaction or data. It allows a wide range of available
authentication technologies to be employed and permits the use of any of
the token methods of Levels 2, 3, or 4. Successful authentication
requires that the Claimant prove through a secure authentication
protocol that he or she possesses and controls the token.

Plaintext passwords or secrets are not transmitted across a network at
Level 1. However this level does not require cryptographic methods that
block offline attacks by eavesdroppers. For example, simple password
challenge-response protocols are allowed. In many cases an eavesdropper,
having intercepted such a protocol exchange, will be able to find the
password with a straightforward dictionary attack.

At Level 1, long-term shared authentication secrets may be revealed to
Verifiers. At Level 1, assertions and assertion references require
protection from manufacture/modification and reuse attacks.

**Level 2** – Level 2 provides single factor remote network
authentication. At Level 2, identity proofing requirements are
introduced, requiring presentation of identifying materials or
information. A wide range of available authentication technologies can
be employed at Level 2. For single factor authentication, Memorized
Secret Tokens, Pre-Registered Knowledge Tokens, Look-up Secret Tokens,
Out of Band Tokens, and Single Factor One-Time Password Devices are
allowed at Level 2. Level 2 also permits any of the token methods of
Levels 3 or 4. Successful authentication requires that the Claimant
prove through a secure authentication protocol that he or she controls
the token. Online guessing, replay, session hijacking, and eavesdropping
attacks are resisted. Protocols are also required to be at least weakly
resistant to man-in-the middle attacks as defined in Section 8.2.2.

Long-term shared authentication secrets, if used, are never revealed to
any other party except Verifiers operated by the Credential Service
Provider (CSP); however, session (temporary) shared secrets may be
provided to independent Verifiers by the CSP. In addition to Level 1
requirements, assertions are resistant to disclosure, redirection,
capture and substitution attacks. Approved cryptographic techniques are
required for all assertion protocols used at Level 2 and above.

**Level 3** – Level 3 provides multi-factor remote network
authentication. At least two authentication factors are required. At
this level, identity proofing procedures require verification of
identifying materials and information. Level 3 authentication is based
on proof of possession of the allowed types of tokens through a
cryptographic protocol. Multi-factor Software Cryptographic Tokens are
allowed at Level 3. Level 3 also permits any of the token methods of
Level 4. Level 3 authentication requires cryptographic strength
mechanisms that protect the primary authentication token against
compromise by the protocol threats for all threats at Level 2 as well as
verifier impersonation attacks. Various types of tokens may be used as
described in Section 6.

Authentication requires that the Claimant prove, through a secure
authentication protocol, that he or she controls the token. The Claimant
unlocks the token with a password or biometric, or uses a secure
multi-token authentication protocol to establish two-factor
authentication (through proof of possession of a physical or software
token in combination with some memorized secret knowledge). Long-term
shared authentication secrets, if used, are never revealed to any party
except the Claimant and Verifiers operated directly by the CSP; however,
session (temporary) shared secrets may be provided to independent
Verifiers by the CSP. In addition to Level 2 requirements, assertions
are protected against repudiation by the Verifier.

**Level 4** – Level 4 is intended to provide the highest practical
remote network authentication assurance. Level 4 authentication is based
on proof of possession of a key through a cryptographic protocol. At
this level, in-person identity proofing is required. Level 4 is similar
to Level 3 except that only “hard” cryptographic tokens are allowed. The
token is required to be a hardware cryptographic module validated at
Federal Information Processing Standard (FIPS) 140-2 Level 2 or higher
overall with at least FIPS 140-2 Level 3 physical security. Level 4
token requirements can be met by using the PIV authentication key of a
FIPS 201 compliant Personal Identity Verification (PIV) Card.

Level 4 requires strong cryptographic authentication of all
communicating parties and all sensitive data transfers between the
parties. Either public key or symmetric key technology may be used.
Authentication requires that the Claimant prove through a secure
authentication protocol that he or she controls the token. All protocol
threats at Level 3 are required to be prevented at Level 4. Protocols
shall also be strongly resistant to man-in-the-middle attacks. Long-term
shared authentication secrets, if used, are never revealed to any party
except the Claimant and Verifiers operated directly by the CSP; however,
session (temporary) shared secrets may be provided to independent
Verifiers by the CSP. Approved cryptographic techniques are used for all
operations. All sensitive data transfers are cryptographically
authenticated using keys bound to the authentication process.

At Level 4, “bearer” assertions (as defined in Section 9) are not used
to establish the identity of the Claimant to the Relying Party (RP).
“Holder-of-key” assertions (as defined in Section 9) may be used,
provided that the assertion contains a reference to a key that is
possessed by the Subscriber and is cryptographically linked to the Level
4 token used to authenticate to the Verifier. The RP should maintain
records of the assertions it receives, to support detection of a
compromised verifier impersonating the subscriber.