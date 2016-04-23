#<a name="privacy-section-header"></a>Privacy Requirements and Considerations

>Under Construction

When developing e-authentication processes and systems, agencies SHALL consult OMB Guidance for Implementing the Privacy Provisions of the E-Government Act of 2002 [OMB M-03-22](sec_references.md/#M-03-22)

##All Identity Assurance Levels
1.  A relying party (RP) MAY ask the subject for additional information not available by the CSP.
2. A CSP SHOULD allow a claimaint to use a credential that his higher than the IAL and/or AAL required by the RP.  However, the CSP SHALL retain pseudonymity of the claimant if the claimant choses to use a credential that is higher than required by the RP.  For example, a claimant may chose to use a smartcard to access an AAL/IAL 1 RP.  Though the CSP should not reveal anything other than a pseudonymous identifier to the RP.
##IAL1
1.  The CSP SHALL NOT require any personal information be collected.  An RP may ask the subject for additional information not available by the CSP.

##IAL2
1.  The CSP **SHALL NOT** require any personal information beyond what is required to sufficiently resolve, verify, and validate the claimed identity.  
2. The CSP SHALL NOT assert attribute information it is not asked for provide by the RP
3. The CSP SHOULD minimize disclosure of complete attribute values. For example, if a RP only needs to know if a subject is older than a specific age, the CSP **shall** assert a boolean value.  The RP **shall not** request the complete birth date.
4. 

