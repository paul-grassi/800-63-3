##5. Assertion Models

There are three basic models for assertion-based authentication. After successful authentication with the Verifier, the Subscriber is issued an assertion or an assertion reference, which the Subscriber uses to authenticate to the RP.

###5.1. The Direct Model

In the direct model, the Claimant uses his or her e-authentication token to authenticate to the Verifier. Following successful authentication of the Claimant, the Verifier creates an assertion, and sends it to the Subscriber to be forwarded to the RP. The assertion is used by the Claimant/Subscriber to authenticate to the RP. (This is usually handled automatically by the Subscriber’s browser.) Figure 1 illustrates this model.

![](media/direct_assertion.png)

Figure 1 - *Direct Assertion Model*

###5.2. The Indirect Model

In the indirect model, the Claimant uses his or her token to authenticate to the Verifier. Following successful authentication, the Verifier creates an assertion as well as an assertion reference (which identifies the Verifier and includes a pointer to the full assertion held by the Verifier). The assertion reference is sent to the Subscriber to be forwarded to the RP. In this model, the assertion reference is used by the Claimant/Subscriber to authenticate to the RP. The RP then uses the assertion reference to explicitly request the assertion from the Verifier. Figure 2 illustrates this model.

![](media/indirect_assertion.png)

Figure 2 - *Indirect Assertion Model*

[ ** I think it would be very useful to have a compare/contrast of the direct and indirect methods of assertion presentation, and in particular discuss the benefits and drawbacks of each. For example, in the direct method a assertion is visible to the user, which could potentially cause leakage of system information included in the assertion. It also allows the assertion to be replayed to other RPs. In the indirect method, there are more round trips, but the information is potentially more limited to the parties that need it. In both cases, the assertion needs to be validated in a number of common ways such as issuer verification, signature validation, audience restriction, etc. We should have good guidelines on this in here. ** ]

###5.3. The Proxy Model

In the proxy model, the Claimant uses his or her e-authentication token to authenticate to the Verifier. Following successful authentication of the Claimant, the Verifier creates an assertion and includes it when interacting directly with the RP, acting as an intermediary between the Claimant and the RP. Figure 3 illustrates this model. [ ** there's nothing special about this model, it's just an additional component acting as an IdP on one side and an RP on the other side. We should call it out based on this fact. ** ]

![](media/proxy_model.png)

Figure 3 – *Proxy Model*

The RP grants or denies the request based, at least in part, on the authentication assertion made by the Verifier. There are several common reasons for such proxies:

- Portals that provide users access to multiple RPs that require user authentication

- Web caching mechanisms that are required to satisfy the RP’s access control policies, especially when client-authenticated TLS with the Claimant is required

- Network monitoring and/or filtering mechanisms that terminate TLS in order to inspect and manipulate the traffic

It is good practice to protect communications between the Verifier and the RP. Current commercial implementations tend to do this by having the proxy use client-authenticated TLS with the Verifier and pass the authentication assertion in the HTTP header.

Note that the Verifier may have access to information that may be useful to the RP in enforcing security policies, such as device identity, location, system health checks, and configuration management. If so, it may be a good idea to pass this information along to the RP. ***Consider privacy here***



