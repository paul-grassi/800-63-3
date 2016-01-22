## Appendix B: Mapping of Federal PKI Certificate Policies and PIV Credentials to E-authentication Assurance Levels

Agencies are, in general, issuing certificates under the policies
specified in the Common Policy Framework \[FBCA3\] to satisfy FIPS 201.
Organizations outside the US Government have begun issuing credentials
under a parallel set of policies and requirements known collectively as
PIV Interoperability specifications (PIV-I). Agencies that were early
adopters of PKI technology, and organizations outside the Federal
government, issue PKI certificates under organization specific policies
instead of the Common Policy Framework. The primary mechanism for
evaluating the assurance provided by public key certificates issued
under organization specific policies is the policy mapping of the
Federal Policy Authority to the Federal Bridge CA policies. These
policies include the Rudimentary, Basic, Medium, Medium-HW, and High
assurance policies specified in \[FBCA1\] and the Citizen and Commerce
class policy specified in \[FBCA2\].

These policies incorporate all aspects of the credential lifecycle,
often in greater detail than specified here. These policies also include
security controls (e.g., multi-party control and system auditing for
CSPs) that are outside the scope of this document. However, the FPKI
policies are based on work that largely predates this specification, and
the security requirements are not always strictly aligned with those
specified here. As a result, this appendix provides an overall mapping
between FPKI certificate policies and the e-authentication Levels
instead of a strict evaluation of compliance. There are known
discrepancies, such as FIPS 201’s allowance for pseudonyms on
credentials issued to personnel in dangerous jobs, or the ability to
issue PIV credentials based on a single federal government issued
identity credential. While these discrepancies are recognized, the
overall level of assurance provided by these policies is deemed to meet
the requirements based on the additional controls.

The table below summarizes how certificates issued under the Common
Policy Framework correspond to the e-authentication assurance levels.
Note that the Common Device policy is not listed; this policy supports
authentication of a system rather than a person. In addition, table B.1
summarizes how organization specific certificate policies correspond to
e-authentication assurance levels. At Level 2 agencies may use
certificates issued under policies that have not been mapped by the
Federal policy authority, but are determined to meet the Level 2
identify proofing, token and status reporting requirements. (For this
evaluation, a strict compliance mapping should be used, rather than the
rough mapping used for the FPKI policies.) For Levels 3 and 4, agencies
shall depend upon the mappings provided by the Federal PKI.

The Federal PKI has also added two policies, Medium Commercial Best
Practices (Medium-CBP) and Medium Hardware Commercial Best Practices
(MediumHW-CBP) to support recognition of non-Federal PKIs. In terms of
e-authentication levels, the Medium CBP and MediumHW-CBP are equivalent
to Medium and Medium-HW, respectively.

Agencies are required \[OMB M-11-11\] to broadly enable PIV credentials
for user authentication to Federal information systems. PIV credentials
are PKI certificates issued under policies that typically meet level 4,
as specified in Table B.1. Most Federal employees and many Federal
contractors possess PIV credentials and agencies are expected to enable
the use of PIV credentials for authentication at levels 1 through 4.

Table B.1 – Certificate Policies and the E-authentication Assurance
Levels

| **Certificate Policy** | **Identity Proofing** | **Token** | **Token and Credential Management^38** | **Overall Equivalence** |
|------------------------|----------------------|------------|---------------------|--------|
| Common-Auth | Meets Level 4 | Meets Level 4 | Meets Level 4 | Meets Level 4 |
| PIVI-Auth | Meets Level 4 | Meets Level 4 | Meets Level 4 | Meets Level 4 |
| SHA1-Auth^39 | Meets Level 4 | Meets Level 4 | Meets Level 4 | Meets Level 4 |
| Common-SW | Meets Level 4 | Meets Level 3 | Meets Level 4 | Meets Level 3 |
| Common-HW | Meets Level 4 | Meets Level 4 | Meets Level 4 | Meets Level 4 |
| PIVI-HW | Meets Level 4 | Meets Level 4 | Meets Level 4 | Meets Level 4 |
| SHA1-HW^39 | Meets Level 4 | Meets Level 4 | Meets Level 4 | Meets Level 4 |
| Common-High | Meets Level 4 | Meets Level 4 | Meets Level 4 | Meets Level 4 |
| FBCA-Basic^40 | Meets Level 3 | Meets Level 3 | Meets Level 3 | Meets Level 3 |
| FBCA-Medium^40 | Meets Level 4 | Meets Level 3 | Meets Level 4 | Meets Level 3 |
| FBCA-Medium-HW^40 | Meets Level 4 | Meets Level 4 | Meets Level 4 | Meets Level 4 |
| FBCA-High^40 | Meets Level 4 | Meets Level 4 | Meets Level 4 | Meets Level 4 |
| Common-cardAuth | Meets Level 4 | Meets Level 2 | Meets Level 4 | Meets Level 2 |
| PIVI-cardAuth | Meets Level 4 | Meets Level 2 | Meets Level 4 | Meets Level 2 |
| SHA1-cardAuth^39 | Meets Level 4 | Meets Level 2 | Meets Level 4 | Meets Level 2 |

