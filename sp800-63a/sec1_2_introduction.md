<a name="sec1"></a>

<div class="breaker"></div>

# 1. <a name="purpose"></a> Purpose

_This section is informative._

This document provides requirements for enrollment and identity proofing of subscribers that wish to gain access to resources at each Identity Assurance Level (IAL).  The requirements detail the acceptability, validation, and verification of identity evidence that will be presented by an individual to support their claim of identity. This document also details the responsibilities of Credential Service Providers (CSPs) with respect to establishing and maintaining enrollment records and binding authenticators (either CSP issued or subscriber-provided) to the enrollment record. 

<a name="sec2"></a>

# 2. <a name="intro"></a> Introduction

_This section is informative._

One of the challenges associated with digital identity is the association of set of online activities with a single, specific entity. While there are situations where this is not required or is even undesirable (e.g., use cases where anonymity or pseudonymity are required), there are others where it is important to reliably establish an association with a real-life subject. Examples include obtaining health care and executing financial transactions. There are also situations where the association is required for regulatory reasons (e.g., Know Your Customer requirements in the financial community) or to establish accountability for high-risk actions (e.g., changing the release rate of water from a dam).

There are also instances where it is desirable for a relying party (RP) to know something about a user executing a transaction, but not know the real life identity of user.  For example, in order to maintain integrity of the service, it may be desirable to know the home ZIP Code of a user for purposes of census taking or petitioning an elected official but where it is not necessary or desirable to know the underlying identity of the person. Identity assurance levels provide a method for expressing the level of assurance associated with attributes established by the credential service provider during the proofing process.

## 2.1. Expected Outcomes of Identity Proofing

The objective of identity proofing is to:  

* Resolve a claimed identity to a single, unique identity within the context of the population of users the CSP serves.
* Validate that all supplied evidence is correct and genuine (e.g., not counterfeit or misappropriated).
* Validate that the claimed identity exists in the real world.
* Verify that the claimed identity is associated with the real person supplying the identity evidence.

## 2.2. Identity Assurance Levels

Assurance in a subscriber's identity is described using one of three IALs: 

>**MG: make sure it matches with edits in -3.**

**Identity Assurance Level 1**:
There is no requirement for an applicant's identity to be proven.  Any attributes provided in conjunction with the authentication process are self-asserted.

**Identity Assurance Level 2**:
The claimed identity is proven with evidence that supports the real world existence of the claimed identity and identifies and verifies the person to whom the claimed identity belongs.  IAL 2 introduces the need for either remote or in-person identity proofing.  Attributes MAY be asserted by CSPs to RPs in support of pseudonymous identity with verified attributes.

**Identity Assurance Level 3**:
At Identity Assurance Level 3, in-person identity proofing is required. Identifying attributes must be verified by an authorized and trained representative of the CSP. As with IAL 2, attributes MAY be asserted by CSPs to RPs in support of pseudonymous identity with verified attributes. 

At IAL 2 and IAL 3, pseudonymity is enabled by CSP limiting the number of attributes sent, or the way they are presented, to the RP. For example, if an RP needs a valid birthdate but no other personal details, the RP should leverage a CSP to request just the birthdate of the subscriber. It is preferred for the RP to ask the CSP for an attribute claim. For example, if an RP needs to know if a claimant is older than 18 they should request a boolean value, not the entire birthdate in order to evaluate age.

>**MG: is it correct to add here that this can only occur in a federated environment. If so, should mention that?**

Since the individual will have undergone an identity proofing process at enrollment and likely associated with one or more authenticators, transactions are not pseudonymous with respect to individual interactions with the CSP.

>**MG: This isn't very clear. It might be worth more clearly describing the notion that states, such as pseudonymity, are with respect to parties and not the system as a whole. That's not great languge either but captures the level at which I think we should discuss it.**

Detailed requirements for each of the IALs is given in [Section 4](#ial-section) and [Section 5](#ipv-section).
