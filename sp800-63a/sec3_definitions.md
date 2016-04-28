## 3. Definitions and Abbreviations

There are a variety of definitions used in the area of authentication.
While many terms are consistent with earlier revisions version of SP 800-63, some have changed in this revision. Since there is no single, consistent definition of many of these terms, careful attention to how the terms are defined here is warranted.

The definitions in this section are primarily those that are referenced in this document. Refer to the other documents in the SP 800-63 document family for additional definitions and abbreviations specific to their content.

#### Address of Record
The official location where an individual can be found. The address of record always includes the residential street address of an individual and may also include the mailing address of the individual. In very limited circumstances, an Army Post Office box number, Fleet Post Office box number or the street address of next of kin or of another contact individual can be used when a residential street address for the individual is not available.

#### Applicant
A party undergoing the processes of registration and identity proofing.

#### Assurance
In the context of [OMB M-04-04](#GSA03) and this document, assurance is defined as 1) the degree of confidence in the vetting process used to establish the identity of an individual to whom the credential was issued, and 2) the degree of confidence that the individual who uses the credential is the individual to whom the credential was issued.

#### Attack
An attempt by an unauthorized individual to fool a Verifier or a Relying Party into believing that the unauthorized individual in question is the Subscriber or to cause a Credential Service Provider to register an impostor as the Subscriber.

#### Attacker
A party who acts with malicious intent to compromise an information system.

#### Attribute
A claim of a named quality or characteristic inherent in or ascribed to someone or something.

### Attribute Claim
`Needs work`  
The minimzed set of information assigned to an attribute regardless of formatting.  For example, for the attribute 'birthday', the claim is 'older than' or 'born in December'.

### Attribute Value
`Needs work`  
The entire set of information assigned to an attribute regardless of formatting.  For example, for the attribute 'birthday', the value is '12/1/1980' or 'December 1, 1980'.
 

#### Authentication
The process of establishing confidence in the identity of users or information systems.

#### Authenticator
Something that the Claimant possesses and controls (typically a cryptographic module or password) that is used to authenticate the Claimant’s identity. In previous versions of this guideline, this was referred to as a *token*.

#### Authenticity
The property that data originated from its purported source.

#### Authoritative Source
An authority that has access to sufficient information from an issuing source that they are able to confirm the validity of a piece of identity evidence. An issuing source may also be an authoritative source.

#### Biometrics
Automated recognition of individuals based on their behavioral and biological characteristics.

In this document, biometrics may be used to unlock authentication tokens and prevent repudiation of registration.

#### Claimant
A party whose identity is to be verified using an authentication protocol.

#### Claimed Address
The physical location asserted by an individual (e.g. an applicant) where he/she can be reached. It includes the residential street address of an individual and may also include the mailing address of the individual.

For example, a person with a foreign passport, living in the U.S., will need to give an address when going through the identity proofing process. This address would not be an “address of record” but a “claimed address.”

#### Credential
An object or data structure that authoritatively binds an identity (and optionally, additional attributes) to a token possessed and controlled by a Subscriber.

While common usage often assumes that the credential is maintained by the Subscriber, this document also uses the term to refer to electronic records maintained by the CSP which establish a binding between the Subscriber’s token and identity.

#### Credential Service Provider (CSP)
A trusted entity that issues or registers Subscriber tokens and issues electronic credentials to Subscribers. The CSP may encompass Registration Authorities (RAs) and Verifiers that it operates. A CSP may be an independent third party, or may issue credentials for its own use.

#### Derived Credential
A credential issued based on proof of possession and control of a token associated with a previously issued credential, so as not to duplicate the identity proofing process.

#### Digital Signature
An asymmetric key operation where the private key is used to digitally sign data and the public key is used to verify the signature. Digital signatures provide authenticity protection, integrity protection, and non-repudiation.

#### Identity
A set of attributes that uniquely describe a person within a given context.

#### Identity Proofing
The process by which a CSP and a Registration Authority (RA) collect and verify information about a person for the purpose of issuing credentials to that person.

#### Issuing Source
An authority that is responsible for the generation of data and/or documents that can be used as identity evidence.

#### Knowledge Based Verification
Identity proofing of an individual based on knowledge of information associated with his or her claimed identity in public databases. Often referred to as Knowledge Based Authentication (KBA) or Knowledge Based Proofing (KBP)

#### Network
An open communications medium, typically the Internet, that is used to transport messages between the Claimant and other parties. Unless otherwise stated, no assumptions are made about the security of the network; it is assumed to be open and subject to active (i.e., impersonation, man-in-the-middle, session hijacking) and passive (i.e., eavesdropping) attack at any point between the parties (e.g., Claimant, Verifier, CSP or RP).


#### Personally Identifiable Information (PII)
Defined by GAO Report 08-536 as “Any information about an individual maintained by an agency, including (1) any information that can be used to distinguish or trace an individual‘s identity, such as name, social security number, date and place of birth, mother‘s maiden name, or biometric records; and (2) any other information that is linked or linkable to an individual, such as medical, educational, financial, and employment information.”

#### Practice Statement
A formal statement of the practices followed by the parties to an authentication process (i.e., RA, CSP, or Verifier). It usually describes the policies and practices of the parties and can become legally binding.

#### Protected Session
A session wherein messages between two participants are encrypted and integrity is protected using a set of shared secrets called session keys.

A participant is said to be *authenticated* if, during the session, he, she or it proves possession of a long term token in addition to the session keys, and if the other party can verify the identity associated with that token. If both participants are authenticated, the protected session is said to be *mutually authenticated*.

#### Pseudonym
A false name. In this document, all unverified names are assumed to be pseudonyms.

#### Public Key
The public part of an asymmetric key pair that is used to verify signatures or encrypt data.

#### Registration
The process through which an Applicant applies to become a Subscriber of a CSP and an RA validates the identity of the Applicant on behalf of the CSP.

#### Remote
(*As in remote authentication or remote transaction*) An information exchange between network-connected devices where the information cannot be reliably protected end-to-end by a single organization’s security controls.

Note: Any information exchange across the Internet is considered remote.


#### Subscriber
A party who has had their credential bound to an authenticator by a CSP.

#### Token
See *Authenticator*.

#### Token Authenticator
See *Authenticator Output*.

#### Token Secret
See *Authenticator Secret*.

#### Trust Anchor
A public or symmetric key that is trusted because it is directly built into hardware or software, or securely provisioned via out-of-band means, rather than because it is vouched for by another trusted entity (e.g. in a public key certificate).

#### Unverified Name
A Subscriber name that is not verified as meaningful by identity proofing.

#### Valid
In reference to an ID, the quality of not being expired or revoked.

#### Verified Name
A Subscriber name that has been verified by identity proofing.
