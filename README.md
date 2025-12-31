# Hybris – MuleSoft – AX/SAP Integration (Real-Time)

This repo shows a real-time integration flow using a colored flowchart.

```mermaid
flowchart TD

  %% COLORS
  classDef ui fill:#D6EAF8,stroke:#1B4F72,stroke-width:2px,color:#1B4F72;
  classDef mule fill:#D5F5E3,stroke:#1E8449,stroke-width:2px,color:#1E8449;
  classDef backend fill:#FCF3CF,stroke:#B7950B,stroke-width:2px,color:#7D6608;

  C[Customer]:::ui --> H[Hybris (Website)]:::ui

  H -->|1) Price request| M[MuleSoft API]:::mule
  M --> AXDWH[AX Data Warehouse\n(Pricing Mapping)]:::backend
  M --> SAP[SAP\n(Tax / Stock)]:::backend
  M -->|Final price| H

  H -->|2) Place order| M
  M --> AX[Dynamics AX\n(Create Order)]:::backend
  AX -->|Order number| M
  M -->|Confirmation| H
