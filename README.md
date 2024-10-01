# Billing System Data Flow

```mermaid
flowchart TD
    %% EMR to Billing System
    A[EMR] -->|Extract Clinical Data (FHIR/HL7)| B[Billing System]
    B -->|Uses clinical data to generate bills| B

    %% Billing System to HIS
    B -->|Push finalized bills| C[HIS]
    C -->|Financial reconciliation, invoicing, reporting| C

    %% Billing System to Payers
    B -->|Generate and submit claims (X12)| D[Payers (Medicare/Medicaid/Private Insurance)]
    D -->|Send payment status| B
    B -->|Process payment adjustments| B
