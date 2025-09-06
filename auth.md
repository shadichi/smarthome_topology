<div dir="rtl">

# Authentication / Authorization — Smart Home

- **Base URL:** بعد از اسکن QR ساخته می‌شود  
  `http://ip:1234/api/v1`
- **secretKey:**  برای «ثبت کلاینت» استفاده می‌شود.
---

## سناریو A — ثبت کلاینت QR 

1) **اسکن QR**  
   اپ `ip` و `secretKey` را می‌خواند و `BASE_URL = http://<ip>:1234/api/v1` می‌سازد.

2) **ثبت کلاینت**  
POST /phone/create

1) **ذخیره امن**  
- `BASE_URL`، `secretKey` در SharedPrefrences ذخیره شود.

---

## سناریو B — استفاده از API

###  (مثال‌هایی از کد)
- `GET /device/get-all` 
- `GET /section/get-all`
- `GET /sub-section/get-by-section-id-and-type/{sectionID}/{type}`
- `GET /scenario`
- `POST /scenario/run/{id}`

---

## سناریو C — RPC

همه RPCها از یک مسیر استفاده می‌کنند:  
`POST /rpc`

**Payload نمونه‌ها:**
```json
// روشنایی
{
"method_name": "Core.SwitchOnLight",
"params": {
  "data": { "channelNo": 1, "brightness": 100, "runningTime": 0 },
  "device": { "deviceId": 123, "deviceName": "test" }
}
}

// کنترل پنل AC (تغییر دما)
{
"method_name": "Core.AcPanelControl",
"params": {
  "data": { "type": "cool", "value": "23" },
  "device": { "deviceId": 123 }
}
}

// خواندن وضعیت فعلی AC
{
"method_name": "Core.ACReadCurrentStatus",
"params": {
  "data": { "additionalProp1": {} },
  "device": { "deviceId": 123, "deviceName": "string" }
}
}

</div>

