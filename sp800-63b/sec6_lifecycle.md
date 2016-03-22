##6. Authenticator Lifecycle Management

During the lifecycle of an authenticator bound to a subscriber's identity, a number of events may occur that affect the use of that authenticator. These events include binding, loss, theft, unauthorized duplication, expiration, and revocation. This section describes the actions that SHALL be taken in response to those events.

###6.1. Authenticator binding

In some cases, authenticators may be provided by a credential service provider (CSP) as part of a process such as registration; in other cases, the subscriber may provide their own (which includes memorized secrets and secret keys used in software cryptographic authenticators). For this reason, we refer to the *binding* of an authenticator rather than the issuance, but this does not exclude the possibility that an authenticator is issued as well.

Throughout the online identity lifecycle, CSPs MUST maintain a record of all authenticators that are or have been associated with the identity. The record MUST contain the date and time the authenticator was bound to the account and SHOULD include information about the binding, such as the IP address or other device identifier associated with the registration. It SHOULD also contain information about unsuccessful authentications attempted with the authenticator. It SHALL also maintain the information required for throttling authentication attempts when required, as described in section 5.2.2.

####6.1.1. Registration

***Is "account" the right word? Or should it be something like  "online identity"?***

At IAL 1, applicants SHALL bind at least one, and SHOULD bind at least two, authenticators to their online identity. Binding of multiple authenticators is preferred in order to recover from loss or theft of their primary authenticator. While at IAL 1 all identifying information is self-asserted, creation of online material or an online reputation makes it undesirable to lose control of an account as result of the loss of an authenticator. The second authenticator makes it possible to securely recover from that situation.

At IAL 2 and above, identifying information is associated with the online identity and the subscriber has undergone an identity proofing process as described in SP 800-63A. As a result, at least two authenticators representing different authentication factors (not two memorized secrets, for example) SHALL be bound to the account. As above, the availability of additional authenticators provides backup methods of authentication if an authenticator is lost or stolen.

During the identity proofing process, the CSP SHALL authenticate the proofing session with authenticators representing two or all three authentication factors which will be bound to the account.

####6.1.2. Post-Registration Binding

Following registration, binding an additional authenticator to an account usually requires the use of an existing authenticator of the same type (or types). For example, binding a new single-factor OTP device requires the subscriber to authenticate with another *something you have* authentication factor. If the account has only one authentication factor bound to it (which is possible only at IAL 1/AAL 1), an additional authenticator of the same factor may be bound to it.

Binding an additional authenticator MUST require the use of two different authentication factors, except as provided below.

If the subscriber has only one of the two authentication factors, they MUST repeat the identity proofing process, using the remaining authentication and SHOULD verify knowledge of some information collected during the proofing process to bind to the existing identity. In order to reestablish authentication factors at IAL 3, they MUST verify the biometric collected during the proofing process.

***Consider what proofing information the CSP is allowed to maintain. Privacy impact here?***

####6.1.3 Renewal

The CSP SHOULD bind an updated authenticator an appropriate amount of time in advance of an existing authenticator's expiration. The process for this SHOULD conform closely to the initial authenticator issuance process (e.g., confirming address of record, etc.). Following successful use of the new authenticator, the CSP MAY revoke the authenticator that it is replacing.

###6.2. Loss, Theft, and Unauthorized Duplication

Loss, theft, and unauthorized duplication of an authenticator are handled similarly, because in most cases one must assume that a lost authenticator has potentially been stolen or recovered by an untrustworthy person. One notable exception is when a memorized secret is forgotten without other indication of having been compromised (duplicated by an attacker).

Upon detecting the loss or theft of an authenticator, the subscriber SHALL contact the CSP as soon as practical to request the revocation of binding to the compromised credential. The preferred method for doing this is to authenticate to the CSP using a backup authenticator; either a memorized secret or a physical authenticator MAY be used for this purpose (only one authentication factor is required for this purpose). Alternatively, the subscriber MAY establish an encrypted online session, authenticating the CSP (e.g., using TLS) and verify information collected during the proofing process. Alternatively, the CSP MAY verify an address of record (email, telephone, or postal) and suspend authenticator(s) reported to have been compromised. The suspension SHALL be reversible if the subscriber successfully authenticates to the CSP and requests reactivation of an authenticator suspended in this manner.

###6.3. Expiration

Authenticators that are physically bound to trustable assertions of attributes (credentials), usually carry expiration dates. When such an authenticator expires, it SHALL NOT be usable for authentication nor for assertion of any bound attributes. When an authentication is attempted, the CSP SHOULD give an indication to the subscriber that the authentication failure is due to expiration rather than some other cause.

The subscriber MUST surrender any physical authenticator containing trustable attributes to the CSP as soon as practical after expiration or after receipt of a renewed authenticator.

There is no requirement for expiration of authenticators. Due to the the cognitive load of changing memorized secrets, CSPs SHOULD NOT expire memorized secrets in the absence of evidence of compromise.

***There's a grace period somewhere?***

###6.4. Revocation

CSPs MUST revoke the binding of authenticators promptly when an online identity ceases to exist or when attributes bound directly to the authenticator change (e.g., change of name, termination of employment). 

***CRLs etc?  response time limits***

