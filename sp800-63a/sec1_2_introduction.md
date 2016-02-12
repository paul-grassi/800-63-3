
## 1. Purpose

This recommendation and its companion documents, SP 800-63-3, SP 800-63B, and SP 800-63C, provide technical guidelines to agencies for the implementation of electronic authentication (e-authentication).

##2. Introduction

Electronic authentication (e-authentication) is the process of establishing confidence in user identities electronically presented to an information system. E-authentication presents a technical challenge when this process involves the remote authentication of individual people over a network. This recommendation provides technical guidelines for the first step of that process, the enrollment and credentialing of subscribers (users).

One of the challenges associated with authenticating people is the association of their online activities with a specific physical person. While there are situations where this is not required or is even undesirable (i.e., use cases where anonymity or pseudonymity are required), there are others where it is important to reliably establish the association with a physical person. Examples include health care and many financial transactions. There are also situations where the association is required for regulatory reasons (e.g., banking Know Your Customer requirements) or to establish accountability for high-risk actions (e.g., the release of water from a hydroelectric dam).

This document provides guidance on the issuance of credentials, including the identity proofing process, at specified identity assurance levels. It also provides guidance on the life cycle of credentials, including maintenance (such as name changes) and revocation.

Agencies may obtain additional confidence using additional risk mitigation measures, such as by imposing more stringent identity proofing requirements than those required herein. While easing identity proofing requirements may increase the size of the enabled customer pool, agencies must ensure that this does not corrupt the system’s choice of the appropriate identity assurance level. Agencies may consider partitioning the functionality of an e-authentication enabled application to allow functions requiring less stringent identification of the subscriber to be available at a lower identity assurance level, while other functions are available only at a higher identity assurance level.

These technical guidelines apply to remote electronic authentication of human users to digital systems over a network. They do not address the authentication of a person who is physically present, for example, for access to buildings. These technical guidelines establish requirements that Federal IT systems and service providers participating in authentication protocols be authenticated to subscribers. However, these guidelines do not specifically address machine-to-machine (such as router-to-router) authentication, or establish specific requirements for issuing authentication credentials to machines and servers when they are used in e-authentication protocols with people.

The paradigm of this document is that individuals (referred to as *applicants* at this stage) are enrolled and undergo a registration process, consisting principally of identity proofing, in which their identity attributes are collected and verified. These attributes are then bound to an authenticator (described in SP 800-63B), creating a credential. Higher confidence levels require stronger registration and identity proofing procedures.

Knowledge based proofing (sometimes referred to as knowledge-based authentication) verifies the identity by testing the personal knowledge of the individual against information obtained from public databases. As this information is considered private but not actually secret, confidence in the identity of an applicant is limited. Accordingly, knowledge-based proofing is not accepted as primary evidence of identity, and is acceptable only at moderate levels of confidence.

Assurance in a subscriber's identity is described using one of three levels as follows:

**Identity Assurance Level 1** – At this level, attributes provided in conjunction with the authentication process, if any, are self-asserted. They may be used by the relying party but must not be depended upon in making authorization decisions. **Identity Assurance Level 2** – Identity Assurance Level 2 introduces the need for either remote or in-person identity proofing. Credentials at Confidence Level 2 provide identifying attributes which have been verified in person or remotely.**Identity Assurance Level 3** – At Identity Assurance Level 3, in-person identity proofing is required. Identifying attributes must be verified by an authorized representative of the CSP through examination of physical documentation.

Detailed requirements for each of the identity assurance levels is given in Section 5.
