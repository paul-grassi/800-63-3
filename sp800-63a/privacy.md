#Privacy Requirements and Considerations

##All Identity Assurance LEvels
1.  A relying party (RP) may ask the subject for additional information not available by the CSP.
2. 

##IAL1
1.  The CSP **shall not** require any personal information be collected.  An RP may ask the subject for additional information not available by the CSP.

##IAL2
1.  The CSP **shall not** require any personal information beyond what is required to sufficiently resolve, verify, and validate the claimed identity.  
2. The CSP **shall not** assert attribute information it is not asked for provide by the RP
3. It is recommended that the CSP assert attribute claims to a RP, not complete attribute values.  For example, if a RP only needs to know if a subject is older than a specific age, the CSP **shall** assert a boolean value.  The RP **shall not** request the complete birth date.