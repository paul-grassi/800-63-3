##6. Assertion Examples

Three types of assertion technologies will be discussed within this section: SAML (Security Assertion Markup Language) assertions, Kerberos tickets, and OpenID Connect tokens. Other assertion technologies may be used in an e-authentication environment as long as they meet the requirements set forth herein for the targeted attribute assurance level.

### 6.1. Security Assertion Markup Language (SAML)

SAML is an XML-based framework for creating and exchanging authentication and attribute information between trusted entities over the Internet. As of this writing, the latest specification for \[[SAML](#SAML)\] is SAML v2.0, issued 15 March 2005.

The building blocks of SAML include the Assertions XML schema which defines the structure of the assertion; the SAML Protocols which are used to request assertions and artifacts (that is, the assertion reference mentioned in Section 9.1); and the Bindings that define the underlying communication protocols (such as HTTP or SOAP) and that can be used to transport the SAML assertions. The three components above define a SAML profile that corresponds to a particular use case such as “Web Browser SSO”.

SAML Assertions are encoded in an XML schema and can carry up to three types of statements:

-   *Authentication statements* – Include information about the
    assertion issuer, the authenticated subject, validity period, and
    other authentication information. For example, an Authentication
    Assertion would state the subject “John” was authenticated using a
    password at 10:32pm on 06-06-2004.

-   *Attribute statements* – Contain specific additional characteristics
    related to the Subscriber. For example, subject “John” is associated
    with attribute “Role” with value “Manager”.

-   *Authorization statements* – Identify the resources the Subscriber
    has permission to access. These resources may include specific
    devices, files, and information on specific web servers. For
    example, subject “John” for action “Read” on “Webserver1002” given
    evidence “Role”.

Authorization statements are beyond the scope of this document and will not be discussed.

### 6.2. Kerberos Tickets

The Kerberos Network Authentication Service \[[RFC 4120](#RFC4120)\] was designed to provide strong authentication for client/server applications using symmetric-key cryptography. Extensions to Kerberos can support the use of public key cryptography for selected steps of the protocol. Kerberos also supports confidentiality and integrity protection of session data between the Subscriber and the RP. [ ** Yes, but the question is: do we care? Kerberos is meant for within-network authentications, and so I'm not convinced it's really apropos to be covered here. ** ]

Kerberos supports authentication of a Claimant over an untrusted, shared network using two or more Verifiers. The Claimant implicitly authenticates to the Verifier by demonstrating the ability to decrypt a random session key encrypted for the Subscriber by the Verifier. (Some Kerberos variants also require the Subscriber to explicitly authenticate to the Verifier, but this is not universal.) In addition to the encrypted session key, the Verifier also generates another encrypted object called a Kerberos ticket. The ticket contains the same session key, the identity of the Subscriber to whom the session key was issued, and an expiration time after which the session key is no longer valid. The ticket is confidentiality and integrity protected by a pre-established that is key [ ** important: this implies setup and federation. ** ]shared between the Verifier and the RP.

To authenticate using the session key, the Claimant sends the ticket to the RP along with encrypted data that proves that the Claimant possesses the session key embedded within the Kerberos ticket. Session keys are either used to generate new tickets, or to encrypt and authenticate communications between the Subscriber and the RP.

To begin the process, the Claimant sends an authentication request to
the Authentication Server (AS). The AS encrypts a session key for the
Subscriber using the Subscriber’s long term credential. The long term
credential may either be a secret key shared between the AS and the
Subscriber, or in the PKINIT variant of Kerberos, a public key
certificate. It should be noted that most variants of Kerberos based on
a shared secret key between the Subscriber and Verifier derive this key
from a user generated password. As such, they are vulnerable to offline
dictionary attack by a passive eavesdropper. [ ** honest tech question: is the key derived from the password? I thought the key was protected with a password. So the key can't be guessed but an encrypted key could be unlocked with an offline attack. ** ]

In addition to delivering the session key to the subscriber, the AS also
issues a ticket using a key it shares with the Ticket Granting Server
(TGS). This ticket is referred to as a Ticket Granting Ticket (TGT),
since the verifier uses the session key in the TGT to issue tickets
rather than to explicitly authenticate the Claimant. The TGS uses the
session key in the TGT to encrypt a new session key for the Subscriber
and uses a key it shares with the RP to generate a ticket corresponding
to the new session key. The subscriber decrypts the session key and uses
the ticket and the new session key together to authenticate to the RP.

###6.3. OpenID Connect

[[ ** If we're keeping the above sections, then I believe we'll also want a section on OpenID Connect. It would make more sense to me to have these in an example appendix to this chapter, since as they stand now they seem more normative. ]]
