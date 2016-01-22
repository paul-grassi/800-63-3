## 8. Authentication Process
    
### 8.1. Overview

The authentication process establishes the identity of the Claimant to
the Verifier with a certain degree of assurance. It is implemented
through an authentication protocol message exchange, as well as
management mechanisms at each end that further constrain or secure the
authentication activity. One or more of the messages of the
authentication protocol may need to be carried on a protected session.
This is illustrated in Figure 3.

![](media/image5.png)

Figure 3 - *Authentication Process Model*

*An authentication protocol is a defined sequence of messages between a
Claimant and a Verifier that demonstrates that the Claimant has control
of a valid token to establish his or her identity, and optionally,
demonstrates to the Claimant that he or she is communicating with the
intended Verifier*. An exchange of messages between a Claimant and a
Verifier that results in authentication (or authentication failure)
between the two parties is an authentication protocol run. During or
after a successful authentication protocol run, a protected
communication session may be created between the two parties; this
protected session may be used to exchange the remaining messages of the
authentication protocol run, or to exchange session data between the two
parties.

Management mechanisms may be implemented on the Claimant and the
Verifier to further enhance the authentication process. For example,
trust anchors may be established at the Claimant to enable the
authentication of the Verifier using public key mechanisms such as TLS.
Similarly, mechanisms may be implemented on the Verifier to limit the
rate of online guessing of passwords by an Attacker who is trying to
authenticate as a legitimate Claimant. Further, detection of
authentication transactions originating from an unexpected location or
channel for a Claimant, or indicating use of an unexpected hardware or
software configuration, may indicate increased risk levels and motivate
additional confirmation of the Claimant’s identity.

At the conclusion of the authentication protocol run, the verifier might
issue a secondary authentication credential, such as a cookie, to the
Claimant and rely upon it to authenticate the claimant in the near
future. Requirements for doing this securely are in Section 9.

### 8.2. Authentication Process Threats

In general, attacks that reveal long-term token secrets are worse than
attacks that reveal short-term authentication secrets or session data,
because in the former, the Attacker can then use the token secret to
assume a Subscriber’s identity and do greater harm.

RAs, CSPs, and Verifiers are ordinarily trustworthy (in the sense of
being correctly implemented and not deliberately malicious). However,
Claimants or their systems may not be trustworthy (or else their
identity claims could simply be trusted). Moreover, while RAs, CSPs, and
Verifiers are normally trustworthy, they are not invulnerable, and could
become corrupted. Therefore, authentication protocols that expose
long-term authentication secrets more than is absolutely required, even
to trusted entities, should be avoided. Table 10 lists the types of
threats posed to the authentication process.

Table 10 - Authentication Process Threats

| **Type of Attack** | **Description** | **Example** |
|--------------------|-----------------|-------------|
| Online guessing | An Attacker performs repeated logon trials by guessing possible values of the token authenticator. | An Attacker navigates to a web page and attempts to log in using a Subscriber's username and commonly used passwords, such as “password” and “secret”.
| Phishing | A Subscriber is lured to interact with a counterfeit Verifier, and tricked into revealing his or her token secret, sensitive personal data or authenticator values that can be used to masquerade as the Subscriber to the Verifier. | A Subscriber is sent an email that redirects him or her to a fraudulent website and is asked to log in using his or her username and password.
| Pharming | A Subscriber who is attempting to connect to a legitimate Verifier, is routed to an Attacker’s website through manipulation of the domain name service or routing tables. | A Subscriber is directed to a counterfeit website through DNS poisoning, and reveals or uses his or her token believing he or she is interacting with the legitimate Verifier.
| Eavesdropping | An Attacker listens passively to the authentication protocol to capture information which can be used in a subsequent active attack to masquerade as the Claimant. | An Attacker captures the transmission of a password or password hash from a Claimant to a Verifier.
| Replay | An Attacker is able to replay previously captured messages (between a legitimate Claimant and a Verifier) to authenticate as that Claimant to the Verifier. | An Attacker captures a Claimant’s password or password hash from an actual authentication session, and replays it to the Verifier to gain access at a later time.
| Session hijack | An Attacker is able to insert himself or herself between a Subscriber and a Verifier subsequent to a successful authentication exchange between the latter two parties. The Attacker is able to pose as a Subscriber to the Verifier/RP or vice versa to control session data exchange. | An Attacker is able to take over an already authenticated session by eavesdropping on or predicting the value of authentication cookies used to mark HTTP requests sent by the Subscriber.
| Man-in-the-middle | The Attacker positions himself or herself in between the Claimant and Verifier so that he or she can intercept and alter the content of the authentication protocol messages. The Attacker typically impersonates the Verifier to the Claimant and simultaneously impersonates the Claimant to the Verifier. Conducting an active exchange with both parties simultaneously may allow the Attacker to use authentication messages sent by one legitimate party to successfully authenticate to the other. | An Attacker breaks into a router that forwards messages between the Verifier and a Claimant. When forwarding messages, the Attacker substitutes his or her own public key for that of the Verifier. The Claimant is tricked into encrypting his or her password so that the Attacker can decrypt it.
| | | An Attacker sets up a fraudulent website impersonating the Verifier. When an unwary Claimant tries to log in using his or her one-time password device, the Attacker’s website simultaneously uses the Claimant’s one-time password to log in to the real Verifier.

#### 8.2.1. Other Threats

Attacks are not limited to the authentication protocol itself. Other
attacks include:

-   Denial of Service attacks in which the Attacker overwhelms the
    Verifier by flooding it with a large amount of traffic over the
    authentication protocol;

-   Malicious code attacks that may compromise or otherwise exploit
    authentication tokens;

-   Attacks that fool Claimants into using an insecure protocol, when
    the Claimant thinks that he or she is using a secure protocol, or
    trick the Claimant into overriding security controls (for example,
    by accepting server certificates that cannot be validated).

The purpose of flooding attacks is to overwhelm the resources used to
support an authentication protocol to the point where legitimate
Claimants cannot reach the Verifier or to slow down the process to make
it more difficult for the Claimant to reach the Verifier. For example, a
Verifier that implements an authentication protocol that uses
encryption/decryption is sent a large number of protocol messages
causing the Verifier to be crippled due to the use of excessive system
resources to encrypt/decrypt. Nearly all authentication protocols are
susceptible to flooding attacks; possible ways to resist such attacks is
through the use of distributed Verifier architectures, use of load
balancing techniques to distribute protocol requests to multiple
mirrored Verifier systems, or other similar techniques.

Malicious code could be introduced into the Claimant’s computer system
for the purpose of compromising or otherwise exploiting the Claimant’s
token. The malicious code may be introduced by many means, including the
threats detailed below. There are many countermeasures (e.g., virus
checkers and firewalls) that can mitigate the risk of malicious code on
Claimant systems. General good practice to mitigate malicious code
threats is outside the scope of this document[^26]. Hardware tokens
prevent malicious software from extracting and copying the token secret.
However, malicious code may still misuse the token, particularly if
activation data is presented to the token via the computer.

#### 8.2.2. Threat Mitigation Strategies

The following are strategies that can be incorporated in authentication
processes to mitigate the attacks listed in the previous section:

-   *Online guessing resistance* – An authentication process is
    resistant to online guessing attacks if it is impractical for the
    Attacker, with no a priori knowledge of the token authenticator, to
    authenticate successfully by repeated authentication attempts with
    guessed authenticators. The entropy of the authenticator, the nature
    of the authentication protocol messages, and other management
    mechanisms at the Verifier contribute to this property. For example,
    password authentication systems can make targeted password guessing
    impractical by requiring use of high-entropy passwords and limiting
    the number of unsuccessful authentication attempts, or by
    controlling the rate at which attempts can be carried out. (See
    [](#_Appendix_A:_Estimating_Entropy and ) and Table 6 in
    Section 6.3.1.). Similarly, to resist untargeted password attacks, a
    Verifier may supplement these controls with network
    security controls.

-   *Phishing and pharming resistance (verifier impersonation)* – An
    authentication process is resistant to phishing and pharming (also
    known as Verifier impersonation,) if the impersonator does not learn
    the value of a token secret or a token authenticator that can be
    used to act as a Subscriber to the genuine Verifier. In the most
    general sense, this assurance can be provided by the same mechanisms
    that provide the strong man-in-the-middle resistance described later
    in this section; however, long term secrets can be protected against
    phishing and pharming simply by the use of a tamper resistant token,
    provided that the long term secret cannot be reconstructed from a
    Token Authenticator. To decrease the likelihood of phishing and
    pharming attacks, it is recommended that the Claimant authenticate
    the Verifier using cryptographic mechanisms prior to submitting the
    token authenticator to the supposed Verifier. Additionally,
    management mechanisms can be implemented at the Verifier to send a
    Claimant personalized content after successful authentication of the
    Claimant or the Claimant’s device. (Refer to Section 8.2.4 for
    further details on personalization.) This allows the Claimant to
    achieve a higher degree of assurance of the authenticity of the
    Verifier before proceeding with the remainder of the session with
    the Verifier or RP. It should be mentioned, however, that there is
    no foolproof way to prevent the Claimant from revealing any
    sensitive information to which he or she has access.

-   *Eavesdropping resistance* – An authentication process is resistant
    to eavesdropping attacks if an eavesdropper who records all the
    messages passing between a Claimant and a Verifier finds it
    impractical to learn the Claimant’s token secret or to otherwise
    obtain information that would allow the eavesdropper to impersonate
    the Subscriber in a future authentication session.
    Eavesdropping-resistant protocols make it impractical[^27] for an
    Attacker to carry out an off-line attack where he or she records an
    authentication protocol run and then analyzes it on his or her own
    system for an extended period to determine the token secret or
    possible token authenticators. For example, an Attacker who captures
    the messages of a password-based authentication protocol run may try
    to crack the password by systematically trying every password in a
    large dictionary, and comparing it with the protocol run data.
    Protected session protocols, such as TLS, provide
    eavesdropping resistance.

-   *Replay resistance* – An authentication process resists replay
    attacks if it is impractical to achieve a successful authentication
    by recording and replaying a previous authentication message.
    Protocols that use nonces or challenges to prove the “freshness” of
    the transaction are resistant to replay attacks since the Verifier
    will easily detect that the old protocol messages replayed do not
    contain the appropriate nonces or timeliness data related to the
    current authentication session.

-   *Hijacking resistance* – An authentication process and data transfer
    protocol combination are resistant to hijacking if the
    authentication is bound to the data transfer in a manner that
    prevents an adversary from participating actively in the data
    transfer session between the Subscriber and the Verifier or RP
    without being detected. This is a property of the relationship of
    the authentication protocol and the subsequent session protocol used
    to transfer data. This binding is usually accomplished by generating
    a per-session shared secret during the authentication process that
    is subsequently used by the Subscriber and the Verifier or RP to
    authenticate the transfer of all session data.

	It is important to note that web applications, even those protected by
	SSL/TLS, can still be vulnerable to a type of session hijacking attack
	called Cross Site Request Forgery (CSRF). In this type of attack, a
	malicious website contains a link to the URL of the legitimate RP. The
	malicious website is generally constructed so that a web browser will
	automatically send an HTTP request to the RP whenever the browser
	visits the malicious website. If the Subscriber visits the malicious
	website while he or she has an open SSL/TLS session with the RP, the
	request will generally be sent in the same session and with any
	authentication cookies intact. While the Attacker never gains access
	to the session secret, the request may be constructed to have side
	effects, such as sending an email message or authorizing a large
	transfer of money.

	CSRF attacks may be prevented by making sure that neither an Attacker
	nor a script running on the Attacker’s website has sufficient
	information to construct a valid request authorizing an action (with
	significant consequences) by the RP. This can be done by inserting
	random data, supplied by the RP, into any linked URL with side effects
	and into a hidden field within any form on the RP’s website. This
	mechanism, however, is not effective if the Attacker can run scripts
	on the RP’s website (Cross Site Scripting or XSS). To prevent XSS
	vulnerabilities, the RP should sanitize inputs from Claimants or
	Subscribers to make sure they are not executable, or at the very least
	not malicious, before displaying them as content to the Subscriber’s
	browser.

-   *Man-in-the-middle resistance* – Authentication protocols are
    resistant to a man-in-the-middle attack when both parties (i.e.,
    Claimant and Verifier) are authenticated to the other in a manner
    that prevents the undetected participation of a third party. There
    are two levels of resistance:

1.  *Weak man-in-the-middle resistance* – A protocol is said to be
    weakly resistant to man-in-the-middle attacks if it provides a
    mechanism for the Claimant to determine whether he or she is
    interacting with the real Verifier, but still leaves the opportunity
    for the non-vigilant Claimant to reveal a token authenticator (to an
    unauthorized party) that can be used to masquerade as the Claimant
    to the real Verifier. For example, sending a password over server
    authenticated TLS is weakly resistant to man-in the middle attacks.
    The browser allows the Claimant to verify the identity of the
    Verifier; however, if the Claimant is not sufficiently vigilant, the
    password will be revealed to an unauthorized party who can abuse
    the information. Weak man-in-the-middle resistance can also be
    provided by a zero-knowledge password protocol, such as Encrypted
    Key Exchange (EKE), Simple Password Exponential Key Exchange
    (SPEKE), or Secure Remote Password Protocol (SRP), which enables the
    Claimant to authenticate to a Verifier without disclosing the
    token secret. However, it is possible for the Attacker to trick the
    Claimant into passing his or her password into a less secure
    protocol, thereby revealing the password to the Attacker.
    Furthermore, if it is unreasonably difficult for the Claimant to
    verify that the proper protocol is being used, then the overall
    authentication process does not even provide weak man-in-the-middle
    resistance (for example, if a zero-knowledge password protocol is
    implemented by an unsigned java applet displayed on a plaintext
    HTTP page).

2.  *Strong man-in-the-middle resistance*: A protocol is said to be
    strongly resistant to man-in-the-middle attack if it does not allow
    the Claimant to reveal, to an Attacker masquerading as the Verifier,
    information (token secrets, authenticators) that can be used by the
    latter to masquerade as the true Claimant to the real Verifier. An
    example of such a protocol is client authenticated TLS, where the
    browser and the web server authenticate one another using PKI. Even
    an unwary Claimant cannot easily reveal to an Attacker masquerading
    as the Verifier any information that can be used by the Attacker to
    authenticate to the real Verifier. Specialized protocols where the
    Claimant’s token device will only release an authenticator to a
    preset list of valid Verifiers may also be strongly resistant to
    man-in-the-middle attacks.

Note that systems can supplement the mitigation strategies listed above
by enforcing appropriate security policies. For example, device
identity, system health checks, and configuration management can be used
to mitigate the risk that the Claimant’s system has been compromised.

#### 8.2.3. Throttling Mechanisms

When using a token that produces low entropy token Authenticators, it is
necessary to implement controls at the Verifier to protect against
online guessing attacks. An explicit requirement for such tokens is
given in Table 6: the Verifier shall effectively limit online Attackers
to 100 failed attempts on a single account in any 30 day period.

The simplest way of implementing a throttling mechanism (which is not
the recommended approach) would be to keep a counter of failed attempts
that is reset at the beginning of each calendar month, and to lock the
account for the rest of the month, when the counter exceeds 50. Aside
from the fact that this system would not technically meet the
requirement on the first of March in non-leap years, this throttling
mechanism has a number of more severe problems. Most notably, it leaves
the Verifier open to a very easy denial of service attack (on the first
day of the month, an Attacker simply makes 50 failed attempts on each
Subscriber account he or she knows about, and the system is unusable for
the next 29 days.)

The above simple implementation is also sufficiently limiting that it
may suffer from usability problems, where the legitimate Subscriber is
penalized for behavior that could reasonably be identified as benign and
should not be counted as failed attempts by an Attacker. For example, if
the Verifier records a dozen failed authentication attempts followed by
a successful attempt from the same IP address over a few minutes to a
few hours, it would be reasonable to assume that those attempts did not
come from an Attacker.

Additional techniques can be used to prioritize authentication attempts
that are likely to come from the Subscriber over those that are more
likely to come from an Attacker.

-   Requiring the Claimant to complete a Completely Automated Public
    Turing test to tell Computers and Humans Apart (CAPTCHA) before
    attempting authentication.

-   Requiring the Claimant to wait for a short period of time (anything
    from 30 seconds to an hour, depending on how close the system is to
    its maximum allowance for failed attempts) before attempting
    Authentication following a failed attempt.

-   Only accepting authentication requests from a white list of IP
    addresses at which the Subscriber has been successfully
    authenticated before.

Since these measures often create user inconvenience, it is best to
allow a certain number of failed authentication attempts before
employing the above techniques. For example, a system which enforces the
30-day failed attempt limit, by dividing the calendar into 10-day
sub-periods and only allowing 25 failed attempts in each sub-period,
could allocate failed attempts as follows: in a given 10 day period, the
Verifier could allow 2 failed attempts each day regardless of any other
considerations, allow an additional 5 failed attempts over the whole
period with no additional protections, require CAPTCHAs for the next 5
failed attempts (beyond the 2-per-day quota), and only allow the final 5
attempts to come from a white-listed IP address after the Claimant has
completed a CAPTCHA.

Finally, if the Verifier accepts authentication attempts for a large
number of Subscribers, it is possible that an Attacker will attempt on
online attack on all Subscriber accounts simultaneously, hoping to gain
access to one of them, thus circumventing the throttling mechanisms
employed on the individual accounts. No specific guideline is given for
protecting against such attacks, but Verifiers with a large number of
Subscribers should take measures to detect such attacks and either
respond to them automatically or alert system administrators to the
threat.

#### 8.2.4. Phishing and Pharming (Verifier Impersonation): Supplementary Countermeasures

It is important to note that phishing and pharming are attacks that use
different techniques to achieve the same goal. Effectively, the Claimant
is tricked into believing that he or she is interacting with the
Verifier when in actuality, the Verifier is being impersonated by an
Attacker attempting to collect token information or other sensitive
information.

In a successful phishing attack, the Attacker sends an official looking
email to a Subscriber claiming to be a Verifier. The email usually
contains a link to a counterfeit Verifier and will ask the Subscriber to
click on the link and authenticate to the Verifier[^28]. The Subscriber
proceeds to authenticate to the counterfeit Verifier and the login
information and token authenticator is captured. At this point, the
Subscriber is unaware that he or she has been phished, and proceeds with
the actions requested by the original email. Once the Subscriber logs
off, he or she is unaware that his or her login information has been
captured and that potentially sensitive data has been captured.

In a successful pharming attack, the Attacker corrupts either the domain
name service (using a technique called DNS poisoning) or the local
routing tables (by modifying the host files on a Claimant’s computer to
point to a bogus DNS server). When the Subscriber attempts to connect to
a legitimate Verifier on the Internet, the corrupted DNS tables or
routing tables take the Subscriber to a counterfeit Verifier on the
Internet. The Subscriber unknowingly reveals token authenticators and
other sensitive information to the counterfeit Verifier.

The strongest mechanism for preventing phishing and pharming of
authentication secrets, such as token authenticators, is to make sure
that some authentication secrets are not directly accessible to the
Claimant (as described in Section 8.2.2). However, to help mitigate a
wider variety of phishing and pharming attacks, the following techniques
may be used:

-   *Out of band confirmation of transaction details* – Details (e.g.,
    account number, amount) of sensitive transactions authorized by the
    Subscriber may be sent by the RP to the Subscriber’s out of band
    token and displayed along with a confirmation code. The confirmation
    code may either be cryptographically derived from the Subscriber’s
    token secret and the transaction details, or it may be a random
    value that is sent to the Subscriber’s out of band token along with
    the transaction details. Alternatively, transaction details may be
    typed in by the Subscriber as manual inputs to a one-time
    password device. In order to complete the transaction, the
    Subscriber shall send the correct one-time password or confirmation
    code to the Verifier or RP.

-   *Adding a “Last Login” feature by the Verifier to inform the
    Subscriber of his or her last login* – If the Subscriber logged in
    at 8:00am and then logs in at 4:00pm but the Last Login feature
    states that the last login was at 2:00pm, the Subscriber may suspect
    that he or she has been phished and take appropriate action.

Personalization is the process of customizing a webpage or email for a
user to enhance the user experience. For the purpose of this document,
personalization schemes can assist the user to determine if he or she is
interacting with the correct entity. It is important to note that
personalization is at best a low assurance mechanism for mitigating
Phishing and Pharming threats, especially when delivered over a
communication protocol that is not strongly resistant to
man-in-the-middle attacks. However, personalization may provide
additional assurance when combined with other techniques.

There are three types of personalization in the context of this
guideline:

-   *Pre-authentication personalization* – The Verifier displays to the
    Claimant some personalized indicator (such as an image or
    user-chosen phrase picked at registration) prior to the latter
    submitting the token authenticator to the former. This indicator may
    be established by the Subscriber at the time of registration. When
    the Claimant views the personalized indicator, the Claimant has an
    increased sense of assurance that he or she is interacting with the
    correct Verifier. For example, a Verifier may require the Claimant
    to submit the username first; in response, the Verifier provides the
    personalized indicator for the claimed username. If the Claimant
    recognizes the personalized indicator as his or her own, the
    Claimant submits his or her token authenticator to the Verifier.
    Pre-authentication personalization does not eliminate Phishing
    attacks, but requires the Attacker to use a more complex technique
    to succeed in a Phishing attack.

-   *Post-authentication personalization* – The Verifier displays a
    personalized indicator to the Subscriber after successful
    authentication of the latter. The personalized indicator provides
    assurance to the Subscriber that he or she has in fact logged in to
    the correct site. This indicator may be established by the
    Subscriber at the time of registration. For example, after a
    Subscriber authenticates to the Verifier, the Verifier provides a
    personalized indicator (such as a picture, a phrase, or a greeting)
    that the Subscriber can readily recognize as his or her own. If the
    personalized indicator is not shown, or is not recognized by the
    Subscriber, the Subscriber suspects that he or she has been phished
    and takes appropriate action. Post-authentication personalization
    does not protect any secrets used by the Subscriber in the initial
    authentication process. Nonetheless, if some or all of these secrets
    are protected by hardware or software that runs a protocol with
    strong man-in-the-middle resistance, then the personalization will
    assist the Subscriber in recognizing that he or she is interacting
    with a bogus site and refraining from revealing any further
    sensitive information. If personalization appears before the
    Subscriber is prompted for a password, but after the Verifier
    strongly authenticates the Subscriber’s local system, then the
    Subscriber’s password may also be protected from phishing.

-   *Personalization of email sent to the Subscriber by a valid
    Verifier* – This type of personalization is employed to help the
    Subscriber differentiate between email from a valid Verifier, and
    email from a Phisher. For example, an email from a Verifier may
    contain a picture which the Subscriber selected in the
    registration process. This type of personalization forces the
    Phisher to use a fairly difficult attack and in effect forces the
    Phisher to either use a targeted attack against each Subscriber or
    hope that the Subscriber will not notice the incorrect or missing
    personalization identifier.

	It is important to note that using a Subscriber’s name (first or last)
	as the only method of personalization is a relatively weak method to
	thwart a phishing attack since it is fairly easy for an Attacker to
	gain this type of information and display it in an email or display it
	after logging into a site. Information of a non-public nature is a
	better candidate for use during personalization.

### 8.3. Authentication Process Assurance Levels

The stipulations for authentication process assurance levels are
described in the following sections.

#### 8.3.1. Threat Resistance per Assurance Level

Authentication process assurance levels can be defined in terms of
required threat resistance. Table 11 lists the threat resistance requirements per assurance level:

Table 11 – Required Authentication Protocol Threat Resistance per Assurance Level

| **Authentication Process Attacks/Threats** | **Level 1** | **Level 2** | **Level 3** | **Level 4** |
|--------------------------------------------|:-----------:|:-----------:|:-----------:|:-----------:|
| Online guessing | Yes | Yes | Yes | Yes |
| Replay | Yes | Yes | Yes | Yes |
| Session hijacking | No | Yes | Yes | Yes |
| Eavesdropping | No | Yes | Yes | Yes |
| Phishing/pharming(verifier impersonation) | No | No | Yes^29 | Yes |
| Man in the middle | No | Weak | Weak | Strong |
| Denial of service/flooding[^30] | No | No | No | No |

#### 8.3.2. Requirements per Assurance Level

This section states the requirements levied on the authentication
process to achieve the required threat resistance at each assurance
level. At Levels 2 and above, the authentication process shall provide
sufficient information to the Verifier to uniquely identify the
appropriate registration information that was (i) provided by the
Subscriber at the time of registration, and (ii) verified by the RA in
the issuance of the token and credential. It is important to note that
the requirements listed below will not protect the authentication
process if malicious code is introduced on the Claimant’s machine or at
the Verifier.

##### 8.3.2.1. Level 1

Although there is no identity proofing requirement at this level, the
authentication mechanism provides some assurance that the same Claimant
who participated in previous transactions is accessing the protected
transaction or data. It allows a wide range of available authentication
technologies to be employed and permits the use of any of the token
methods of Levels 2, 3 or 4. Successful authentication requires that the
Claimant prove, through a secure authentication protocol, that he or she
possesses and controls the token.

Plaintext passwords or secrets shall not be transmitted across a network
at Level 1. However this level does not require cryptographic methods
that block offline analysis by eavesdroppers. For example, password
challenge-response protocols that combine a password with a challenge to
generate an authentication reply satisfy this requirement although an
eavesdropper who intercepts the challenge and reply may be able to
conduct a successful off-line dictionary or password exhaustion attack
and recover the password. Since an eavesdropper who intercepts such a
protocol exchange will often be able to find the password with a
straightforward dictionary attack, and this vulnerability is independent
of the strength of the operations, there is no requirement at this level
to use Approved cryptographic techniques. At Level 1, long-term shared
authentication secrets may be revealed to Verifiers.

A wide variety of technologies should be able to meet the requirements
of Level 1. For example, a Verifier might obtain a Subscriber password
from a CSP and authenticate the Claimant by use of a challenge-response
protocol. A password sent through a TLS protocol session is another
example. Other common protocols that meet Level 1 requirements include
APOP \[[RFC 1939](#RFC1939)\], S/KEY \[[RFC 1760](#SKEY)\], and
password-based versions of Kerberos \[[KERB](#KERB)\].

##### 8.3.2.2. Level 2 

Level 2 allows a wide range of available authentication technologies to
be employed and permits the use of any of the token methods of Levels 2,
3 and 4. Successful authentication requires that the Claimant shall
prove, through a secure authentication protocol, that he or she controls
the token. Session hijacking (when required based on the FIPS 199
security category of the systems as described below), replay, and online
guessing attacks shall be resisted. Approved cryptography is required to
resist eavesdropping to capture authentication data. Protocols used at
Level 2 and above shall be at least weakly man-in-the-middle resistant,
as described in the threat mitigation strategies subsection.

Session data transmitted between the Claimant and the RP following a
successful Level 2 authentication shall be protected as described in the
NIST FISMA guidelines. Specifically, all session data exchanged between
information systems that are categorized as FIPS 199 “Moderate” or
“High” for confidentiality and integrity, shall be protected in
accordance with NIST SP 800-53 Control SC-8 (which requires transmission
confidentiality) and SC-9 (which requires transmission integrity).

A wide variety of technologies can meet the requirements of Level 2. For
example, a Verifier might authenticate a Claimant who provides a
password through a secure (encrypted) TLS protocol session (tunneling).

##### 8.3.2.3. Level 3 

Level 3 provides multi-factor remote network authentication. At least
two authentication factors are required. Level 3 authentication is based
on proof of possession of the allowed types of tokens through a
cryptographic protocol. Level 3 also permits any of the token methods of
Level 4. Refer to Section 6 for requirements for single tokens and token
combinations that can achieve Level 3 authentication assurance.
Additionally, At Level 3, strong cryptographic mechanisms shall be used
to protect token secret(s) and authenticator(s). Long-term shared
authentication secrets, if used, shall never be revealed to any party
except the Claimant and CSP; however, session (temporary) shared secrets
may be provided to Verifiers by the CSP, possibly via the Claimant.
Approved cryptographic techniques shall be used for all operations
including the transfer of session data.

Level 3 assurance may be satisfied by client authenticated TLS
(implemented in all modern browsers), with Claimants who have public key
certificates. Other protocols with similar properties may also be used.

Level 3 authentication
assurance may also be met by tunneling the output of a MF OTP Token, or
the output of a SF OTP Token in combination with a Level 2 personal
password, through a TLS session.

##### 8.3.2.4. Level 4 

Level 4 is intended to provide the highest practical remote network
authentication assurance. Refer to Section 6 for single tokens and token
combinations that are allowed to be used to achieve Level 4
authentication assurance.

Level 4 requires strong cryptographic authentication of all parties, and
all sensitive data transfers between the parties. Either public key or
symmetric key technology may be used. The token secret shall be
protected from compromise through the malicious code threat as described
in Section 8.2.1 above. Long-term shared authentication secrets, if
used, shall never be revealed to any party except the Claimant and CSP;
however session (temporary) shared secrets may be provided to Verifiers
or RPs by the CSP. Strong, Approved cryptographic techniques shall be
used for all operations including the transfer of session data. All
sensitive data transfers shall be cryptographically authenticated using
keys that are derived from the authentication process in such a way that
MitM attacks are strongly resisted.

Level 4 assurance may be satisfied by client authenticated TLS
(implemented in all modern browsers), with Claimants who have public key
MF Hardware Cryptographic Tokens. Other protocols with similar
properties can also be used.

It should be noted that, in multi-token schemes, the token used to
provide strong man-in-the-middle resistance need not be a hardware
token. For example, if a software cryptographic token is used to open a
client-authenticated TLS session, and the output of a multifactor OTP
device is sent by the claimant in that session, then the resultant
protocol will still provide Level 4 assurance.
