#<a name="privacy-section-header"></a> 8. Privacy Requirements and Considerations

>Under Construction

## 8.1. General Requirements

1. All entities responsible for establishing a digital authentication process or system SHALL consult OMB Guidance for Implementing the Privacy Provisions of the E-Government Act of 2002 [OMB M-03-22](references.md/#M-03-22).
2. An RP SHALL only request the minimum number of attributes required to provide a service and SHOULD request attribute claims rather than full attribute values.
3. An RP MAY ask the user for additional information not available by the CSP.
4. The CSP SHALL NOT assert attribute information that is not requested by the RP and consented to by the individual.
5. The CSP SHALL allow the user to view the attribute values it will assert to an RP upon user consent.
5. The CSP SHALL support attribute claims requests. For example, if an RP only needs to know if a subject is older than a specific age, the CSP would assert a boolean value.
6. A CSP SHOULD allow a claimaint to use a credential that is bound to an IAL higher than required by the RP.  However, the CSP SHALL retain pseudonymity of the claimant unless release of attributes is explicitly consented by the claimant.  *(Non-normative)* For example, a claimant may chose to use a smartcard to access an AAL/IAL 1 RP.  In this instance, the CSP will not reveal anything other than a pseudonymous identifier to the RP.
