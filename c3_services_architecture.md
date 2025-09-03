# C3 — Services Architecture (Smart Home)

## هدف
نمای معماری سرویس‌ها

---

## Component Map 

```mermaid
flowchart LR
  subgraph UI[UI Layer]
    SCR[screens]
    WID[widgets]
  end

  subgraph CTRL[Controllers]
    CTR[controllers]
    PAR[params]
  end

  subgraph CORE[Core]
    CORELIB[core lib]
    COREASSETS[core assets]
    UTL[utilities]
  end

  subgraph REMOTE[Remote Services]
    SSE[SSE Service]
    API[HTTP API v1]
  end

  SCR --> CTR
  WID --> CTR
  CTR --> CORELIB
  CTR --> PAR
  CTR --> UTL
  CORELIB --> COREASSETS

  CORELIB --> API
  CORELIB --> SSE
