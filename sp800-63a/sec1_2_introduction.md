
# 1. Purpose

This document provides requirements for enrollment and identity proofing of subscribers that wish to gain access to online resources.  The requirements detail the acceptability, validation, and verification of identity evidence that will be presented by an individual to support their claim of identity. This documents also detail the responsibilities of credential service providers (CSPs) with respect to establishing and maintaining enrollment records and user credentials. 

#2. Introduction

One of the challenges associated with authenticating people is the association of their online activities with a specific physical person. While there are situations where this is not required or is even undesirable (i.e., use cases where anonymity or pseudonymity are required), there are others where it is important to reliably establish the association with a physical person. Examples include obtaining health care and executing financial transactions. There are also situations where the association is required for regulatory reasons (e.g., Know Your Customer requirements in the financial community) or to establish accountability for high-risk actions (e.g., the release of water from a hydroelectric dam).

There are also instances where it is desirable for a relying party to know something about a user executing a transaction, but not know the real human identity of the person.  For example, in order to maintain integrity of the service, it may be desirable to know the home ZIP Code of a user for purposes of census taking or petitioning an elected official but where it is not necessary or desirable to know the underlying identity of the person. Identity assurance levels provide a method for expressing the level of assurance associated with attributes established by the credential service provider during the proofing process.

##2.1 Expected Outcomes of Identity Proofing
The outcome of identity proofing is to:    

* Resolve a claimed identity to a single, unique identity within the context of the population of users the CSP serves
* Validate that all evidence that is supplied is valid (correct) and genuine (not counterfeit or misappropriated)
* Validate that the claimed identity exists in the real world
* Verify that the claimed identity is associated with the real person supplying identity evidence

##2.2 Identity Assurance Levels
Assurance in a subscriber's identity is described using one of three Identity Assurance Levels (IALs):

**Identity Assurance Level 1**:
At this level, there is no requirement for a Subscriber's identity to be proven.  Any attributes provided in conjunction with the authentication process are self-asserted. **@privacy**

**Identity Assurance Level 2**:
At IAL 2, the claimed identity is proven with evidence that supports the real world existence of the claimed identity and identifies and verifies the person to whom the claimed identity belongs.  IAL 2 introduces the need for either remote or in-person identity proofing.  At IAL 2, attributes other than identifying attributes such as name MAY also be asserted by CSPs to RPs in support of pseudonymous identity with verified attributes. **@privacy**

**Identity Assurance Level 3**:
At Identity Assurance Level 3, in-person identity proofing is required. Identifying attributes must be verified by an authorized and trained representative of the CSP. As at IAL 2, IAL 3 attributes other than identifying attributes such as name MAY also be asserted by CSPs to RPs in support of pseudonymous identity with verified attributes.

At IAL 2 and IAL 3, pseudonymity results from the non-assertion of identifying attributes to the RP. Since the user will have undergone an identity proofing process at enrollment and associated that with one or more authenticators, transactions are not pseudonymous with respect to the CSP.

Detailed requirements for each of the IALs is given in Section 5.


##2.3 Process Flow
The paradigm of this document is that individuals (referred to as *applicants* at this stage) are enrolled and undergo a registration process, consisting principally of identity proofing, in which their identity attributes are collected and verified. These attributes are then bound to an authenticator (described in SP 800-63B). The attributes MAY also be placed on a physical authenticator, usually in a signed form; such an authenticator is referred to as a credential. Higher Identity Assurance Levels require stronger enrollment and identity proofing procedures.

![](media/Proofing_process.png)


###Requirements Notation and Conventions
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](http://tools.ietf.org/html/rfc2119).