##7. Assertion Threats

***Move normative content out of this section; this should just be a discussion.***

*This section is non-normative.*

In this section, it is assumed that the two endpoints of the assertion
transmission (namely, the Verifier and the RP) are uncompromised. [ ** This is a big assumption to make. I think we should call out what a compromised RP can do, for instance, or the catastrophic effects of a compromised IdP. ** ]
However, the Claimant is not assumed to be entirely trustworthy as the
Claimant may have an interest in modifying or replacing an assertion to
obtain a greater level of access to a resource/service provided by the
RP. Other attackers are assumed to lurk within the shared transmission
medium (e.g., internet) and may be interested in obtaining or modifying
assertions and assertion references to impersonate a Subscriber or
access unauthorized data or services. Furthermore, it is possible that
two or more entities may be colluding to attack another party. An
attacker may attempt to subvert assertion protocols by directly
compromising the integrity or confidentiality of the assertion data. For
the purpose of this type of threat, authorized parties who attempt to
exceed their privileges may be considered Attackers.

-   *Assertion manufacture/modification* – An Attacker may generate a
    bogus assertion or modify the assertion content (such as the
    authentication or attribute statements) of an existing assertion,
    causing the RP to grant inappropriate access to the Subscriber. For
    example, an Attacker may modify the assertion to extend the validity
    period; a Subscriber may modify the assertion to have access to
    information that they should not be able to view.

-   *Assertion disclosure* – Assertions may contain authentication and
    attribute statements that include sensitive Subscriber information.
    Disclosure of the assertion contents can make the Subscriber
    vulnerable to other types of attacks.

-   *Assertion repudiation by the Verifier* – An assertion may be
    repudiated by a Verifier if the proper mechanisms are not in place.
    For example, if a Verifier does not digitally sign an assertion, the
    Verifier can claim that it was not generated through the services of
    the Verifier.

-   *Assertion repudiation by the Subscriber* – Since it is possible for
    a compromised or malicious subscriber to issue assertions to the
    wrong party, a subscriber can repudiate any transaction with the RP
    that was authenticated using only a bearer assertion.

-   *Assertion redirect*: An Attacker uses the assertion generated for
    one RP to obtain access to a second RP.

-   *Assertion reuse* – An Attacker attempts to use an assertion that
    has already been used once with the intended RP.

In addition to reliable and confidential transmission of assertion data
from the Verifier to the RP, assertion protocols have a further goal: in
order for the Subscriber to be recognized by the RP, he or she shall be
issued some secret information, the knowledge of which distinguishes the
Subscriber from Attackers who wish to impersonate the Subscriber. In the
case of holder-of-key assertions, this secret is generally the
Subscriber’s long term token secret, which would already have been
established with the CSP prior to the initiation of the assertion
protocol.<sup>[31](#note31)</sup>

In other cases, however, the Verifier will generate a temporary secret
and transmit it to the authenticated Subscriber for this purpose. Since,
when this secret is used to authenticate to the RP, it generally
replaces the token authenticator in the type of protocols described in
Section 8, this temporary secret will be referred to here as a secondary
authenticator. Secondary authenticators include assertions in the direct
model, session keys in Kerberos, assertion references in the indirect
model, and cookies used for authentication. The threats to the secondary
authenticator are as follows:

-   *Secondary authenticator manufacture* – An Attacker may attempt to
    generate a valid secondary authenticator and use it to impersonate
    a Subscriber.

-   *Secondary authenticator capture* – The Attacker may use a session
    hijacking attack to capture the secondary authenticator when the
    Verifier transmits it to the Subscriber after the primary
    authentication step, or the Attacker may use a man-in-the-middle
    attack to obtain the secondary authenticator as it is being used by
    the Subscriber to authenticate to the RP. If, as in the indirect
    model, the RP needs to send the secondary authenticator back to the
    Verifier in order to check its validity or obtain the corresponding
    assertion data, an Attacker may similarly subvert the communication
    protocol between the Verifier and the RP to capture a
    secondary authenticator. In any of the above scenarios, the
    secondary authenticator can be used to impersonate the Subscriber.

Finally, in order for the Subscriber’s authentication to the RP to be
useful, the binding between the secret used to authenticate to the RP
and the assertion data referring to the Subscriber shall be strong.

-   *Assertion substitution* – A subscriber may attempt to impersonate a
    more privileged subscriber by subverting the communication channel
    between the Verifier and RP, for example by reordering the messages,
    to convince the RP that his or her secondary authenticator
    corresponds to assertion data sent on behalf of the more
    privileged subscriber. This is primarily a threat to the indirect
    model, since in the direct model, assertion data is directly encoded
    in the secondary authenticator. [ ** That's not really true, the indirect model is actually more robust against this because you can require more stringent controls around the request for the assertion itself. ** ]

[ ** We're leaving off an important section: session hijacking. The attacker waits until the authentication event occurs, usually through the presentation of an assertion, and then steals the secondary session binding (such as a cookie) and goes from there. This is starting to make me think we need a whole separate section on session management. ** ]

### 7.2. Threat Mitigation Strategies

Mitigation techniques are described below for each of the threats
described in the last subsection.

Logically speaking, an assertion is issued by a Verifier [ ** OK, can we just call this the IdP? ** ] and consumed by
an RP – these are the two end points of the session that needs to be
secured to protect the assertion. In the direct model, the session in
which the assertion is passed traverses the Subscriber. Furthermore, in
the current web environment, the assertion may pass through two separate
secure sessions (one between the Verifier and the Subscriber, and the
other between the Subscriber and the RP), with a break in session
security on the Subscriber’s browser. This is reflected in the
mitigation strategies described below. In the indirect model, the
assertion flows directly from the Verifier to the RP; this protocol
session needs to be protected. [ ** But so do the other two sessions that bring you the artifact used to get the assertion. This is dangerous and misleading advice! ** ] All of the threat mitigation strategies
in Section 8 apply to the protocols used to request, retrieve and submit
assertions and assertion references.

-   *Assertion manufacture/modification*: To mitigate this threat, one
    of the following mechanisms may be used:

1.  The assertion may be digitally signed by the Verifier. The RP should
    check the digital signature to verify that it was issued by a
    legitimate Verifier.

2.  The assertion may be sent over a protected session such as TLS. In
    order to protect the integrity of assertions from malicious attack,
    the Verifier shall be authenticated.
    
    [ ** BOTH of these mechanisms MUST be used for it to be trustworthy. ** ]

-   *Assertion disclosure* – To mitigate this threat, one of the
    following mechanisms may be implemented:

1.  The assertion may be sent over a protected session to an
    authenticated RP. Note that, in order to protect assertions against
    both disclosure and manufacture/modification using a protected
    session, both the RP and the Verifier need to be authenticated. [ ** This seems to imply mutual TLS. Let's not go there, please. I would rather say they are *validted* than *authenticated* here. ** ]

2.  If assertions are signed by the Verifier, they may be encrypted for
    a specific RP with no additional integrity protection. [ ** This doesn't talk about key establishment requirements, should it? ** ] It should be
    noted that any protocol that requires a series of messages between
    two parties to be signed by their source and encrypted for their
    recipient provides all the same guarantees as a mutually
    authenticated protected session, and may therefore be
    considered equivalent. The general requirement for protecting
    against both assertion disclosure and assertion
    manufacture/modification may therefore be described as a mutually
    authenticated protected session or equivalent between Verifier
    and RP. [ ** This doesn't seem to really help here. You can get the same level of protection from a signed statement with audience restrictions over server-validated TLS. ** ]

-   *Assertion repudiation by the Verifier* – To mitigate this threat,
    the assertion may be digitally signed by the Verifier using a key
    that supports non-repudiation. The RP should [ ** MUST? ** ]check the digital
    signature to verify that it was issued by a legitimate Verifier.

-   *Assertion repudiation by the Subscriber* – To mitigate this threat,
    the Verifier may issue holder of key, rather than bearer assertions.
    The Subscriber can then prove possession of the asserted key to
    the RP. If the asserted key matches the subscriber’s long term
    credential (as provided by the CSP) it will be clear to all parties
    involved that it was the Subscriber who authenticated to the RP
    rather than a compromised Verifier impersonating the Subscriber.

-   *Assertion redirect* – To mitigate this threat, the assertion may
    include the identity of the RP for whom it was generated. The RP
    verifies that incoming assertions include its identity as the
    recipient of the assertion. [ ** Audience restriction should really be mandated, otherwise you have cross-domain assertion injection. ** ]

-   *Assertion reuse* – To mitigate this threat, the following
    mechanisms may be used:

1.  The assertion includes a timestamp and has a short lifetime
    of validity. The RP checks the timestamp and lifetime values to
    ensure that the assertion is currently valid. The lifetime value may
    either be in the assertion or set by the RP. [ ** It seems dangerous for the RP to set its own lifetime on a whim. ** ]

2.  The RP keeps track of assertions that were consumed within
    a (configurable) time window to ensure that an assertion cannot be
    used more than once within that time window. [ ** But above in the direct assertion model you've got one assertion being replayed to the RP on multiple requests and even to multiple RPs. ** ]

-   *Secondary authenticator manufacture* – To mitigate this threat, one
    of the following mechanisms may be implemented:

1.  The secondary authenticator may contain sufficient entropy that an
    Attacker without direct access to the Verifier’s random number
    generator cannot guess the value of a valid secondary authenticator.

2.  The secondary authenticator may contain timely assertion data that
    is signed by the Verifier or integrity protected using a key shared
    between the Verifier and the RP.

3.  The Subscriber may authenticate to the RP directly using his or her
    long term token and avoid the need for a secondary
    authenticator altogether. [ ** This seems like dangerous advice. ** ]

-   *Secondary authenticator capture* – To mitigate this threat,
    adequate protections shall be in place throughout the lifetime of
    any secondary authenticators used in the assertion protocol.

1.  In order to protect the secondary authenticator while it is in
    transit between the Verifier and the Subscriber, the secondary
    authenticator shall be sent via a protected session established
    during the primary authentication of the Subscriber using his or
    her token. This requirement is the same as the requirement in
    Section 8, regarding the Authentication Process, to protect
    sensitive data (in this case the secondary authenticator) from
    session hijacking attacks.

2.  In order to protect the secondary authenticator from capture as it
    is submitted to the RP, the secondary authenticator shall be used in
    an authentication protocol which protects against eavesdropping and
    man-in-the-middle attacks as described in Section 8.

3.  In order to protect the secondary authenticator after it has been
    used, it shall never be transmitted on an unprotected session or to
    an unauthenticated party while it is still valid. The secondary
    authenticator may be sent in the clear only if the sending party has
    strong assurances that the secondary authenticator will not
    subsequently be accepted by any other RP. [ ** Why would you do this?? EVER?? You're just creating a race condition here. ** ] This is possible if the
    secondary authenticator is specific to a single RP, and if that RP
    will not accept secondary authenticators with the same value until
    the maximum lifespan of the corresponding assertion has passed.

-   *Assertion substitution* – To mitigate this threat, one of the
    following mechanisms may be implemented:

1.  Responses to assertion requests, signed or integrity protected by
    the Verifier, may contain the value of the assertion reference used
    in the request or some other nonce that was cryptographically bound
    to the request by the RP.

2.  Responses to assertion requests may be bound to the corresponding
    requests by message order, as in HTTP, provided that assertions and
    requests are protected by a protocol such as TLS that can detect and
    disallow malicious reordering of packets.
