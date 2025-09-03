# Data Flow Diagram — Smart Home

## هدف
نمای جریان داده از لحظه اسکن QR تا مصرف API ها و دریافت رویدادهای لحظه ای با SSE.

---

## DFD سطح صفر

```mermaid
flowchart LR
  subgraph App[App]
    ScanQR[Scan QR]
    SetBase[Set Base Url and Secret]
    Register[POST phone create]
    GetDevices[GET device get all]
    GetSections[GET section get all]
    GetScenarios[GET scenario]
    RunScenario[POST scenario run :id]
    SendRpc[POST rpc Core SwitchOnLight or AcPanelControl]
    HandleEvents[Handle SSE events]
    UpdateUI[Update UI State]
    CacheData[Cache Data Local]
  end

  ScanQR --> SetBase --> Register
  Register --> GetDevices
  GetDevices --> CacheData
  GetSections --> CacheData
  GetScenarios --> CacheData
  RunScenario --> UpdateUI
  SendRpc --> UpdateUI
  HandleEvents --> UpdateUI

  App -->|HTTP| API[(HTTP API v1)]
  App -->|SSE| SSE[(SSE Service)]

  Register -->|POST /phone/create| API
  GetDevices -->|GET /device/get-all| API
  GetSections -->|GET /section/get-all| API
  GetScenarios -->|GET /scenario| API
  RunScenario -->|POST /scenario/run/:id| API
  SendRpc -->|POST /rpc Core SwitchOnLight| API
  SendRpc -->|POST /rpc Core AcPanelControl| API

  App --> CacheData
  App --> HandleEvents
  HandleEvents <-->|GET /sse/stream| SSE
