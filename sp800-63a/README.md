# SP 800-63A

This is a working draft of NIST Special Publication 800-63A *Enrollment and Identity Proofing*. This document is a sub-document referenced by [SP 800-63-3](../sp800-63-3/README.md) covering the associated topics that had been previously in SP 800-63-2.

SP 800-63A deals with the processes by which a credential, and authenticator(s) associated with that credential can be bound to a specific individual. This typically happens when that individual is enrolled in an identity system, through the identity proofing process.

This document is broken up into sections as follows:

[Front matter](front.md)

[1. Purpose and 2. Introduction](sec1_2_introduction.md)

[3. Definitions and Abbreviations](sec3_definitions.md)

[4. Confidence Levels](sec4_confidence.md)

[5. Identity Proofing](sec5_proofing.md)

[6. Credential Lifecycle Management](sec6_lifecycle.md)

[7. Threats and Security Considerations](sec7_security.md)

[8. Privacy Considerations](sec8_privacy.md)

[9. Usability](sec9_usability.md)

[10. References](sec10_references.md)

##Deprecations
|**800-63-2 Section Number**   |     **Section Name**  | **Rationale** |
|---------------|------------------------|------------------|
|5.3.2 | Requirements for Educational and Financial Institutions and Other Organizations |The advent of trust frameworks have allowed for organizations to federate identity to government services.  Individual agencies may adopt trust frameworks or define their own, mapping organizational policies and processes to 800-63 requirements as necessary and appropriate.|
|5.3.3| Requirements for Certificates Issued under FPKI and Mapped Policies|Federal PKI is a trust framework and has defined a mapping to 800-63.  This is appropriate and should live within the auspices of FPKI, not 800-63.|
|5.3.4|Requirements for One-Time Use||
