- [Determining Commercial Agreements in ECIF](#determining-commercial-agreements-in-ecif)
- [Determining Related PAK Commercial Accounts in ECIF](#determining-related-pak-commercial-accounts-in-ecif)

## Determining Commercial Agreements in ECIF
The following values should be checked:
*  ECIF product line of business should be one of "Business (Commercial)" -OR- "Commercial Account"

    -OR-

* ECIF source system should be one of the following: "CL Policy Center", "CL Direct PolicyCenter", "CL Direct PolicyCenter Account", "CL Direct BillingCenter"

## Determining Related PAK Commercial Accounts in ECIF
The following values should be checked:
* Breaking the agreement number into parts:

| Product Code | ?    | Group Number | Account Number |
| ------------ | ---- | ------------ | -------------- |
| FNCP         | BAMF | 123          | 4567890        |

* The Product Code and Group Number should be the same across all accounts within a PAK. The ? and Account Number fields will differ.
* Looking at the ECIF xpath ```*/rolesInAgreementSummary/RoleInContract/billingAccount/externalReference``` will provide the billing account number that a PAK agreement is related to.