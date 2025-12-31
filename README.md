flowchart TD

  %% COLORS / STYLES
  classDef ui fill:#D6EAF8,stroke:#1B4F72,stroke-width:2px,color:#1B4F72;
  classDef mule fill:#D5F5E3,stroke:#1E8449,stroke-width:2px,color:#1E8449;
  classDef backend fill:#FCF3CF,stroke:#B7950B,stroke-width:2px,color:#7D6608;

  %% NODES
  C[Customer]
  H[Hybris (Website)]
  M[MuleSoft API]
  AXDWH[AX Data Warehouse<br/>(Pricing Mapping)]
  SAP[SAP<br/>(Tax / Stock)]
  AX[Dynamics AX<br/>(Create Order)]

  %% FLOWS
  C --> H
  H -->|1) Price request| M
  M --> AXDWH
  M --> SAP
  M -->|Final price| H

  H -->|2) Place order| M
  M --> AX
  AX -->|Order number| M
  M -->|Confirmation| H

  %% APPLY COLORS
  class C,H ui
  class M mule
  class AXDWH,SAP,AX backend
