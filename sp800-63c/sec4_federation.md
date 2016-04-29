##4. Federation
This section provides an overview of common models of identity federation. Many models of federated identity are currently in use. In these models, trust is established between members of the federation in several different ways. Some models mandate that federated parties have a high level of trust. Other models allow for parties with a diversity of trust relationships.
###Central Authority
Some federated parties trust a central authority to make trust decisions for them and communicate metadata between parties. In this model, the central authority generally conducts some level of vetting on each party in the federation to verify compliance with predetermined security and integrity standards.
###Manual Registration
In the manual registration model of federation, system administrators communicate metadata and test system interoperability before transactions take place between users over the wire. Metadata for each party who wishes to participate is manually input into a registry of federaated parties.
####Without federation operator
Manual registration can take place on a case by case basis without any authority or federation operator in place. In this case, an existing trust relationship is generally already in place between the CSP and the RP. 
####With federation operator
Manual registration is more efficient if the CSP and the RP both trust a federation operator. In this case, all parties who belong to the federation register with the operator, who can then push out metadata for all federated parties. This creates a larger trust network with the ability to propagate changes in metadata quickly and easily.
###Dynamic Registration
In the dynamic registration model of federation, systems have a well-known location where other systems can find their metadata and endpoints where new systems can register themselves without human involvement.
####Software statements
Because dynamic registration does not require an existing trust relationship, it is beneficial for federated parties to cryptographically verify some attributes of the parties involved in dynamic registration. Software statements are lists of attributes such as endpoints, cryptographically signed by certifying bodies so that trust can be established or elevated between two federated parties.
####Graylists
Many federated parties establish whitelists of federated parties who may dynamically register with a high level of trust. They also establish blacklists of federated parties who may dynamically register with a low level of trust, or who may not be allowed to dynamically register at all. Everything that is not on a whitelist or a blacklist can be considered to be in a gray area or on a "graylist." Graylisted parties generally start out with a low level of trust until they can be reviewed by a human.
###Broker
For privacy reasons, some federated parties choose to blind themselves from other members of the federation. For example, a government-run RP might wish to use a bank as a CSP, but would prefer not to know where its users have bank accounts. In this model, a third-party sits in the middle of the transaction and communicates the success or failure of an authentication event without communicating the source of that information.
####Traditional Broker
A traditional broker blinds the RP and the CSP from each other, but is able to monitor and track all user transactions at both parties.
####Blind Broker
A blind broker uses some combination of opaque identifiers and encrypted attribute bundles to help the CSP and RP communicate, but is intentionally limited in its ability to deduce information about specific user behavior.

