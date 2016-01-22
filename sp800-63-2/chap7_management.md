## 7. Token and Credential Management

### 7.1. Overview

As introduced in Section 4, credentials are objects that bind identity
to a token. To maintain the level of assurance provided by an
e-authentication solution, credentials and tokens shall be managed to
reflect any changes in that binding. This section discusses token and
credential management activities performed by the CSP subsequent to the
registration, identity proofing and issuance activities described in
Section 5. This includes the lifecycle management activities for the
token and credential. The activities that must be performed by the CSP
depend in part upon the nature of the credentials and the token itself.

#### 7.1.1. Categorizing Credentials

This specification categorizes credentials according to two orthogonal
perspectives. Some classes of credentials can be distributed to relying
parties, while others cannot be disclosed by the CSP without
compromising the token itself. Another classification indicates whether
the binding represented in the credential is tamper-evident.

Credentials that describe the binding in a way that does not compromise
the token are referred to as *Public Credentials*. The classic example
of a Public Credential is a public key certificate; it is mathematically
infeasible to calculate the user’s private key even with knowledge of
the corresponding public key. Credentials that cannot be disclosed by
the CSP because the contents can be used to compromise the token are
considered *Private Credentials*. The classic example of a Private
Credential is the hashed value of a password, since this hash can be
used to perform an offline attack on the password.

Credentials that describe the binding between a user and token in a
tamper-evident fashion are considered *Strongly Bound Credentials*. For
example, modification of a digitally signed credential (such as a public
key certificate) can be easily detected through signature verification.
The binding between a user and token can be modified in *Weakly Bound
Credentials* without invalidating the credentials. Weakly bound
credentials require supplemental integrity protection and/or access
controls to ensure that the binding represented by the credential
remains accurate. For example, replacing the value of a hashed password
in a password file associates the user with a new password, so access to
this file is restricted to system users and processes.

Strongly bound credential mechanisms require little or no additional
integrity protection, whereas weakly bound credentials require
additional integrity protection or access controls to ensure that
unauthorized parties cannot spoof or tamper with the binding of the
identity to the token representation within the credential.

Unencrypted password files are private credentials that are weakly
bound, and hence need to be afforded confidentiality as well as
integrity protection. Signed password files are private credentials that
are strongly bound and therefore require confidentiality protection but
no additional integrity protection. An unsigned pairing of a public key
and the name of its owner or a self-signed certificate is an example of
a public credential that is weakly bound. Finally, a CA-signed public
key certificate represents a public credential that is strongly bound.

CSPs and Verifiers are trusted to obey the requirements in this section
as well as Section 8.

#### 7.1.2. Token and Credential Management Activities

The CSP manages tokens and credentials. The RA establishes the
Applicant’s identity, and the CSP is responsible for generating
credentials and supplying the Subscriber with a token or allowing the
Subscriber to register his or her own token as described in Section 5.
The CSP is responsible for some or all of the following token and
credential management activities following issuance of the token and
credential:

-   *Credential storage* – After the credential has been created, the
    CSP may be responsible for maintaining the credentials in storage.
    In cases where the credentials are stored by the CSP, the level of
    security afforded to the credential will depend on the type of
    credential issued. For private credentials, additional
    confidentiality mechanisms are required in storage, whereas for
    public credentials, this is not necessary. Similarly, for weakly
    bound credentials, additional integrity protection is needed in
    storage, unlike strongly bound credentials. Finally, credentials
    need to be available to allow CSPs and Verifiers to determine the
    identity of the corresponding token owner.

-   *Token and credential verification services* – In many
    e-authentication scenarios, the Verifier and the CSP are not part of
    the same entity. In these cases, the CSP is responsible for
    providing the Verifier with the information needed to facilitate the
    token and credential verification process. The CSP may provide token
    and credential verification services to Verifiers. For example, the
    Verifier may request the CSP to verify the password submitted by the
    Claimant against the CSP’s local password database.

-   *Token and credential renewal /re-issuance* – Certain types of
    tokens and credentials may support the process of renewal
    or re-issuance. During renewal, the usage or validity period of the
    token and credential is extended without changing the Subscriber’s
    identity or token. During re-issuance, a new credential is created
    for a Subscriber with a new identity and/or a new token.

	The CSP establishes suitable policies for renewal and re-issuance of
	tokens and credentials. The CSP may establish a time period prior to
	the expiration of the credential, when the Subscriber can request
	renewal or re-issuance following successful authentication using his
	or her existing, unexpired token and credential. For example, a CSP
	may allow a digital certificate to be renewed for another year prior
	to the expiry of the current certificate by proving possession and
	control of the existing token (i.e., the private key).

	Once the Subscriber’s credentials have expired, the Subscriber may be
	required to re-establish his or her identity with the CSP; this is
	typically the case with CSPs that issue digital certificates.
	Conversely, the CSP may establish a grace period for the renewal or
	re-issuance of an expired credential, such that the Subscriber can
	request renewal/re-issuance of his or her credential even after it has
	expired without the need to re-establish his or her identity with the
	CSP. For example, if a Claimant attempts to login to a
	username/password based system on which his or her password has
	already expired, and the system supports a grace period, the user may
	be prompted to create a new password and supply the last password for
	verification purposes. The use of expired tokens or credentials to
	invoke renewal/re-issuance is more practical when the Verifier and CSP
	are part of the same entity.

	The public key certificate for a Subscriber may be renewed with the
	same public key, or may be re-issued with a new public key. Passwords
	are seldom renewed so that the life of the existing password is
	extended for another period. Usually the account name/password
	credential for a Subscriber is renewed by having the Subscriber select
	a new password.

-   *Token and credential revocation and destruction* – The CSP is
    responsible for maintaining the revocation status of credentials and
    destroying the credential at the end of its life. Explicit and
    elaborate revocation mechanisms may be required for “public
    credentials” since these credentials are disseminated widely,
    possibly with a preset validity period. For example, public key
    certificates are revoked using Certificate Revocation Lists (CRLs)
    after the certificates are distributed.

	“Private credentials” are held closely by the CSP, and hence the
	revocation and destruction of these credentials is implemented easily
	through an update of the CSP’s local credential stores. Credentials
	that bind usernames/passwords are instantaneously revoked and
	destroyed if the CSP deletes its mapping between the username and the
	password. Certain types of tokens may need to be explicitly deleted or
	zeroized at the end of the credential life in order to permanently
	disable the token and prevent its unauthorized reuse. For example, a
	Multi-factor Hardware Cryptographic Token may need to be zeroized to
	ensure that all of the information pertaining to the Subscriber is
	deleted from the token.

	The CSP may be responsible for ensuring that hardware tokens are
	collected and cleared of any data when the Subscriber no longer has a
	need for its use. The CSP may establish policies for token collection
	to avoid the possibility of unauthorized use of the token after it is
	considered out of use. The CSP may destroy such collected tokens, or
	zeroize them to ensure that there are no remnants of information that
	can be used by an Attacker to derive the token value. For example, a
	Subscriber who is issued a hardware OTP token by a CSP may be required
	by policy to return the token to the CSP at the end of its life, or
	when the Subscriber’s association with that CSP terminates.

-   *Records retention* – The CSP or its representative is responsible
    for maintaining a record of the registration, history, and status of
    each token and credential, including revocation. CSPs operated by or
    on behalf of executive branch agencies shall also follow either the
    General Records Schedule established by the National Archives and
    Records Administration or an agency-specific schedule as applicable.
    All other entities shall comply with their respective records
    retention policies in accordance with whatever laws apply to
    those entities. A minimum record retention period is required at
    Level 2 and above.

-   *Security controls* – The CSP is responsible for implementing and
    maintaining appropriate security controls contained in NIST
    SP 800-53. The security control baseline for CSPs is specified in
    terms of a FIPS 200 impact level for each assurance level. (See
    Section 7.3, below.)

### 7.2. Token and Credential Management Threats

Tokens and credentials can only be as strong as the strength of the
management mechanisms used to secure them. The CSP is responsible for
mitigating threats to the management operations described in the last
section. Token and credential management threats are described below;
they are categorized in accordance with the management activity to which
they apply.

These threats represent the potential to breach the confidentiality,
integrity and availability of tokens and credentials during the CSP
activities, and are listed below.

Table 8 - Token and Credential Management Threats

| **Token and Credential Management Activity** | **Threat/Attack** | **Example** |
|----------------------------------------------|-------------------|-------------|
| Credential storage | Disclosure | Usernames and passwords stored in a system file are revealed.
| | Tampering | The file that maps usernames to passwords within the CSP is hacked so that the mappings are modified, and existing passwords are replaced by passwords known to the Attacker. |
| Token and credential verification services | Disclosure | An Attacker is able to view requests and responses between the CSP and the Verifier. |
| | Tampering | An Attacker is able to masquerade as the CSP and provide bogus responses to the Verifier’s password verification requests. |
| | Unavailability | The password file or the CSP is unavailable to provide password and username mappings. |
| | |Public key certificates for Claimants are unavailable to the Verifier because the directory systems are down (for example for maintenance or as a result of a denial of service attack). |
| Token and credential issuance/renewal/re-issuance | Disclosure | Password renewed by the CSP for a Subscriber is copied by an Attacker as it is transported from the CSP to the Subscriber. |
| | Tampering | New password created by the Subscriber is modified by an Attacker as it is being submitted to the CSP to replace an expired password. |
| | Unauthorized issuance | The CSP is compromised through unauthorized physical or logical access resulting in issuance of fraudulent credentials. |
| | Unauthorized renewal/re-issuance | Attacker fools the CSP into re-issuing the credential for a current Subscriber – the new credential binds the current Subscriber’s identity with a token provided by the Attacker. \
| | |Attacker is able to take advantage of a weak credential renewal protocol to extend the credential validity period for a current Subscriber. |
| Token and credential revocation/destruction | Delayed revocation/destruction of credentials | Stale CRLs allow accounts (that should have been locked as a result of credential revocation) to be used by an Attacker. |
| | | User accounts are not deleted when employees leave a company leading to a possible use of the old accounts by unauthorized persons. |
| | Token use after decommissioning | A hardware token is used after the corresponding credential was revoked or expired. |

#### 7.2.1. Threat Mitigation Strategies

Token and credential management related mechanisms that assist in
mitigating the threats identified above are summarized in Table 9.

Table 9 - Token and Credential Threat Mitigation Strategies

| **Token and Credential Management Activity** | **Threat/Attack** | **Mitigation Strategy** |
|----------------------------------------------|-------------------|-------------------------|
| Credential storage | Disclosure | Use access control mechanisms that protect against unauthorized disclosure of credentials held in storage.
| | Tampering | Use access control mechanisms that protect against unauthorized tampering of credentials and tokens.
| Token and credential verification services | Disclosure | Use a communication protocol that offers confidentiality protection.
| | Tampering | Ensure that Verifiers authenticate the CSP prior to accepting a verification response from that CSP.
| | | Use a communication protocol that offers integrity protection.
| | Unavailability | Ensure that the CSP has a well developed and tested Contingency Plan.
| Token and credential issuance/renewal/re-issuance | Disclosure | Use a communication protocol that provides confidentiality protection of session data.
| | Tampering | Use a communication protocol that allows the Subscriber to authenticate the CSP prior to engaging in token re-issuance activities and protects the integrity of the data passed.
| | Unauthorized issuance | Implement physical and logical access controls to prevent compromise of the CSP. See \[FISMA\] for details on security controls.
| | Unauthorized renewal/re-issuance | Establish policy that Subscriber shall prove possession of the old token to successfully negotiate the re-issuance process. Any attempt to negotiate the re-issuance process using an expired or revoked token should fail.
| Credential revocation/destruction | Delayed revocation/destruction of credentials | Revoke/Destroy credentials as soon as notification that the credentials should be revoked or destroyed.
| | Token use after decommissioning | Destroy tokens after their corresponding credentials have been revoked.

### 7.3. Token and Credential Management Assurance Levels

#### 7.3.1. Requirements per Assurance Level

The stipulations for management of tokens and credentials by the CSP and
Verifier are described below for each assurance level. The stipulations
described at each level in this section are incremental in nature;
requirements stipulated at lower levels are implicitly included at
higher levels.

##### 7.3.1.1. Level 1

At Level 1, the following shall be required:

-   *Credential storage* – Files of shared secrets used by Verifiers at
    Level 1 authentication shall be protected by access controls that
    limit access to administrators and only to those applications that
    require access. Such shared secret files shall not contain the
    plaintext passwords; typically they contain a one-way hash or
    “inversion” of the password. In addition, any method allowed for the
    protection of long-term shared secrets at Level 2 or above may be
    used at Level 1.

-   *Token and credential verification services* – Long term token
    secrets should not be shared with other parties unless
    absolutely necessary.

-   *Token and credential renewal / re-issuance* – No stipulation

-   *Token and credential revocation and destruction* – No stipulation

-   *Records retention* – No stipulation

-   *Security controls* – No stipulation

##### 7.3.1.2. Level 2

At Level 2, the following shall be required:

-   *Credential storage* – Files of shared secrets used by CSPs at Level
    2 shall be protected by access controls that limit access to
    administrators and only to those applications that require access.
    Such shared secret files shall not contain the plaintext passwords
    or secrets; two alternative methods may be used to protect the
    shared secret:

1.  Passwords may be concatenated to a variable salt (variable
        across a group of passwords that are stored together) and then
        hashed with an Approved algorithm so that the computations used
        to conduct a dictionary or exhaustion attack on a stolen
        password file are not useful to attack other similar
        password files. The hashed passwords are then stored in the
        password file. The variable salt may be composed using a global
        salt (common to a group of passwords) and the username (unique
        per password) or some other technique to ensure uniqueness of
        the salt within the group of passwords.

2.  Shared secrets may be encrypted and stored using Approved
        encryption algorithms and modes, and the needed secret decrypted
        only when immediately required for authentication. In addition,
        any method allowed to protect shared secrets at Level 3 or 4 may
        be used at Level 2.

-   *Token and credential verification services* – Long term shared
    authentication secrets, if used, shall never be revealed to any
    other party except Verifiers operated by the CSP; however,
    session (temporary) shared secrets may be provided by the CSP to
    independent Verifiers.

	Cryptographic protections are required for all messages between the
	CSP and Verifier which contain private credentials or assert the
	validity of weakly bound or potentially revoked credentials. Private
	credentials shall only be sent through a protected session to an
	authenticated party to ensure confidentiality and tamper protection.

	The CSP may send the Verifier a message that either asserts that a
	weakly bound credential is valid, or that a strongly bound credential
	has not been subsequently revoked. In this case, the message shall be
	logically bound to the credential, and the message, the logical
	binding, and the credential shall all be transmitted within a single
	integrity protected session between the Verifier and the authenticated
	CSP. If revocation is an issue, the integrity protected messages shall
	either be time stamped, or the session keys shall expire with an
	expiration time no longer than that of the revocation list.
	Alternatively, the time stamped message, binding, and credential may
	all be signed by the CSP, although, in this case, the three in
	combination would comprise a strongly bound credential with no need
	for revocation.

-   *Token and credential renewal/re-issuance* – The CSP shall establish
    suitable policies for renewal and re-issuance of tokens
    and credentials. Proof-of-possession of the unexpired current token
    shall be demonstrated by the Claimant prior to the CSP allowing
    renewal and re-issuance. Passwords shall not be renewed; they shall
    be re-issued. After expiry of current token and any grace period,
    renewal and re-issuance shall not be allowed. Upon re-issuance,
    token secrets shall not be set to a default or reused in any manner.
    All interactions shall occur over a protected session such
    as SSL/TLS.

-   *Token and credential revocation and destruction* – CSPs shall
    revoke or destroy credentials and tokens within 72 hours after being
    notified that a credential is no longer valid or a token is
    compromised to ensure that a Claimant using the token cannot
    successfully be authenticated. If the CSP issues credentials that
    expire automatically within 72 hours (e.g., issues fresh
    certificates with a 24 hour validity period each day) then the CSP
    is not required to provide an explicit mechanism to revoke
    the credentials. CSPs that register passwords shall ensure that the
    revocation or de-registration of the password can be accomplished in
    no more than 72 hours. CAs cross-certified with the Federal Bridge
    CA at the Citizen and Commerce Class Basic, Medium and High or
    Common Certificate Policy levels are considered to meet credential
    status and revocation provisions of this level.

-   *Records retention* – A record of the registration, history, and
    status of each token and credential (including revocation) shall be
    maintained by the CSP or its representative. The record retention
    period of data for Level 2 credentials is seven years and six months
    beyond the expiration or revocation (whichever is later) of
    the credential. CSPs operated by or on behalf of executive branch
    agencies shall also follow either the General Records Schedule
    established by the National Archives and Records Administration or
    an agency-specific schedule as applicable. All other entities shall
    comply with their respective records retention policies in
    accordance with whatever laws apply to those entities.

-   *Security controls* – The CSP must employ appropriately tailored
    security controls from the low baseline of security controls defined
    in \[[SP 800-53](#SP_800_53)\] and must ensure that the minimum
    assurance requirements associated with the low baseline
    are satisfied.

##### 7.3.1.3. Level 3

At Level 3, the following is required:

-   *Credential storage*[^25] – Files of long-term shared secrets used
    by CSPs or Verifiers at Level 3 shall be protected by access
    controls that limit access to administrators and only to those
    applications that require access. Such shared secret files shall be
    encrypted so that:

1.  The encryption key for the shared secret file is encrypted under a
    key held in a FIPS 140-2 Level 2 or higher validated hardware
    cryptographic module or any FIPS 140-2 Level 3 or 4 cryptographic
    module and decrypted only as immediately required for an
    authentication operation.

2.  Shared secrets are protected as a key within the boundary of a FIPS
    140-2 Level 2 or higher validated hardware cryptographic module or
    any FIPS 140-2 Level 3 or 4 cryptographic module and is not exported
    in plaintext from the module.

	Strongly bound credentials support tamper detection mechanisms such as
	digital signatures, but weakly bound credentials can be protected
	against tampering using access control mechanisms as described above.

-   *Token and credential verification services* – CSPs shall provide a
    secure mechanism to allow Verifiers or RPs to ensure that the
    credentials are valid. Such mechanisms may include on-line
    validation servers or the involvement of CSP servers that have
    access to status records in authentication transactions.

	Temporary session authentication keys may be generated from long-term
	shared secret keys by CSPs and distributed to third party Verifiers,
	as a part of the verification services offered by the CSP, but
	long-term shared secrets shall not be shared with any third parties,
	including third party Verifiers. This type of third-party (or
	delegated) verification is used in the realm of GSM (Global System for
	Mobile Communications) roaming; the locally available network
	authenticates the “roaming” Subscriber using a temporary session
	authentication key received from the Base Station. Such temporary
	session authentication keys are typically created by cryptographically
	combining the long term shared secret with a nonce challenge, to
	generate a session key. The challenge and session key are securely
	transmitted to the Verifier. The Verifier in turn sends only the
	challenge to the Claimant, and the Claimant applies the challenge to
	the long-term shared secret to generate the session key. Both Claimant
	and Verifier now share a session key, which can be used for
	authentication. Such verification schemes are permitted at this level
	provided that Approved cryptographic algorithms are used for all
	operations.

	Token and credential verification services categorized as FIPS 199
	“Moderate” or “High” for availability shall be protected in accordance
	with the Contingency Planning (CP) controls specified in NIST SP
	800-53 to provide an adequate level of availability needed for the
	service.

-   *Token and credential renewal /re-issuance* – Renewal and
    re-issuance shall only occur prior to expiration of the
    current credential. Claimants shall authenticate to the CSP using
    the existing token and credential in order to renew or re-issue
    the credential. All interactions shall occur over a protected
    session such as SSL/TLS.

-   *Credential revocation and destruction* – CSPs shall have a
    procedure to revoke credentials and tokens within 24 hours. The
    certificate status provisions of CAs cross-certified with the
    Federal Bridge CA at the Basic, Medium, High or Common Certificate
    Policy levels are considered to meet credential status and
    revocation provisions of this level. Verifiers shall ensure that the
    tokens they rely upon are either freshly issued (within 24 hours) or
    still valid. Shared secret based authentication systems may simply
    remove revoked Subscribers from the verification database.

-   *Records retention* – All stipulations from Level 2 apply.

-   *Security controls* – The CSP must employ appropriately tailored
    security controls from the moderate baseline of security controls
    defined in \[[SP 800-53](#SP_800_53)\] and must ensure that the
    minimum assurance requirements associated with the moderate baseline
    are satisfied.

##### 7.3.1.4. Level 4

At Level 4, the following is required:

-   *Credential storage* – No additional stipulation.

-   *Token and credential verification services* – No
    additional stipulation.

-   *Token and credential renewal/re-issuance* – Sensitive data
    transfers shall be cryptographically authenticated using keys bound
    to the authentication process. All temporary or short-term keys
    derived during the original authentication operation shall expire
    and re-authentication shall be required after not more than 24 hours
    from the initial authentication.

-   *Token and credential revocation and destruction* – CSPs shall have
    a procedure to revoke credentials within 24 hours. Verifiers or RPs
    shall ensure that the credentials they rely upon are either freshly
    issued (within 24 hours) or still valid. The certificate status
    provisions of CAs cross-certified with the Federal Bridge CA at the
    High and Common Certificate Policies shall be considered to meet
    credential status provisions of Level 4.
    \[[FBCA1](#_Certificate_Policies)\]

	It is generally good practice to destroy a token within 48 hours of
	the end of its life or the end of the Subscriber’s association with
	the CSP. Destroying includes either the physical destruction of the
	token or cleansing it of all information related to the Subscriber.

-   *Records retention* – All stipulations from Levels 2 and 3 apply.
    The minimum record retention period for Level 4 credential data is
    ten years and six months beyond the expiration or revocation of
    the credential.

-   *Security controls* – The CSP must employ appropriately tailored
    security controls from the moderate baseline of security controls
    defined in \[[SP 800-53](#SP_800_53)\] and must ensure that the
    minimum assurance requirements associated with the moderate baseline
    are satisfied.

#### 7.3.2. Relationship of PKI Policies to E-Authentication Assurance Levels

Appendix B specifies the mapping between the Federal PKI Certificate
Policies and the requirements in Section 7.
