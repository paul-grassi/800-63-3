# SP 800-63A

This is a working draft of NIST Special Publication 800-63A *Identity Proofing*. This document is a sub-document referenced by [SP 800-63-3](../sp800-63-3/README.md) covering the associated topics that had been previously in SP 800-63-2.

SP 800-63A deals with the processes by which an individual can prove their identity to a CSP prior to credential issuance.

This document is broken up into sections as follows:

[Front matter](cover.md)

[1. Purpose and 2. Introduction](sec1_2_introduction.md)

[2. Definitions and Abbreviations](sec3_definitions.md)

[3. Identity Proofing](sec5_proofing.md)

[4. Threats and Security Considerations](sec7_security.md)

[5. Privacy Requirements & Considerations](privacy.md)

[6. Usability](sec9_usability.md)

[7. References](sec10_references.md)

##Deprecations
The following sections have been removed in their entirety.

|**800-63-2 Section Number**   |     **Section Name**  | **Rationale** |
|---------------|------------------------|------------------|
|5.3.2 | Requirements for Educational and Financial Institutions and Other Organizations |The advent of trust frameworks have allowed for organizations to federate identity to government services.  Individual agencies may adopt trust frameworks or define their own, mapping organizational policies and processes to 800-63 requirements as necessary and appropriate.|
|5.3.3| Requirements for Certificates Issued under FPKI and Mapped Policies|Federal PKI is a trust framework and has defined a mapping to 800-63.  This is appropriate and should live within the auspices of FPKI, not 800-63.|
|5.3.4|Requirements for One-Time Use||
|5.3.5|Requirements for Derived Credentials|Removed LOA4 text. Refer to SP 800-157|