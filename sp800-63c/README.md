# SP 800-63C

This is a working draft of NIST Special Publication 800-63C *Authentication and Attribute Assertions*. This document is a sub-document referenced by [SP 800-63-3](../sp800-63-3/README.md) covering the associated topics that had been previously in SP 800-63-2.

SP 800-63C deals with the processes by which the result of an authentication process can be securely communicated to another party. Assertions are used in federated identity systems where the authentication is performed by one party (sometimes called an Identity Provider) and used by a different party, sometimes called a Relying Party. However, assertions are also used internally to maintain and reestablish user state over a series of interactions. 

This document is broken up into sections as follows:

[Front matter](front.md)

[1. Purpose and 2. Introduction](sec1_2_introduction.md)

[3. Definitions and Abbreviations](sec3_definitions.md)

[4. Assertion Strength](sec4_strength.md)

    4.1. Bearer assertions
    4.2. Holder of key assertions
    4.3. Shared secrets
    4.4. Signed assertions

[5. Types of Assertions](sec5_types.md)

    5.1 Internal assertions (cookies, etc.) 
    5.2 External assertions (to external relying parties)

[6. Examples](sec6_examples.md)

    6.1. SAML
    6.2. Kerberos
    6.3. OpenID Connect and OAuth

[7. Assertion Threats](sec7_threats.md)

[8. Privacy Considerations](sec8_privacy.md)

[9. Usability](sec9_usability.md)

[10. References](sec10_references.md)
