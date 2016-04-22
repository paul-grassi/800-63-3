##1. Purpose

This recommendation and its companion documents, SP 800-63-3, SP 800-63A, and SP 800-63B, provide technical guidelines to credential service providers for the implementation of remote authentication.

##2. Introduction

Assertions are statements from a verifier to a relying party (RP) that contain information about a subscriber. Assertions are used when the RP and the verifier are not co-located (i.e., they are connected through a shared network). The RP uses the information in the assertion to identify the subscriber and make authorization decisions about their access to resources controlled by the RP. An assertion may include identification and authentication statements regarding the subscriber, and may additionally include attribute statements that further characterize the subscriber and support the authorization decision at the RP.

Assertions regarding the subscriber serve several important goals. They supports the process of Single Sign On, allowing subscribers to authenticate once to a verifier and subsequently obtain services from multiple RPs without necessarily repeating the authentication process at each RP.

Assertion mechanisms support the provision of a federated identity for a subscriber, allowing the linkage of multiple identities/accounts held by the subscriber with different RPs through the use of common “federated” attributes. In this context, a federation is a group of entities (RPs, Verifiers and CSPs) that are bound together through common agreed-upon business practices, policies, trust mechanisms, profiles and protocols. These may be maintained on a static basis or may be established through an accreditation framework.

Finally, assertion mechanisms can also facilitate authentication schemes that are based on the attributes or characteristics of the subscriber. Attributes are often used in determining access privileges for Attribute Based Access Control (ABAC) or Role Based Access Control (RBAC).

It is important to note that assertion schemes are fairly complex
multiparty protocols, and therefore have fairly subtle security requirements which must be satisfied. When evaluating a particular assertion scheme, it may be instructive to break it down into its component interactions. Generally speaking, interactions between the user (claimant/subscriber) and the verifier and between the user and RP are similar to the authentication mechanisms presented SP 800-63B, while interactions between the verifier and RP convey attributes such as those established using procedures in SP 800-63A. Many of the requirements presented in this document will, therefore, have some relationship with corresponding requirements in those two documents.
