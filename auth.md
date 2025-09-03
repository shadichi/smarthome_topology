# Authentication / Authorization — Smart Home

## هدف
توضیح اینکه اپ چطور خود را به گیت‌ وی محلی معرفی می‌کند (AuthN) . منبع اصلی اطلاعات، QR روی کنترل‌پنل دیواری است که `ip` و `secretKey` می‌دهد.

---

## مفاهیم پایه
- **Base URL (محلی):** بعد از اسکن QR ساخته می‌شود  
  `http://<ip>:1234/api/v1`
- **secretKey:** فقط برای «ثبت کلاینت» استفاده می‌شود.
---

## سناریو A — ثبت کلاینت با QR (Provisioning)

1) **اسکن QR**  
   اپ `ip` و `secretKey` را می‌خواند و `BASE_URL = http://<ip>:1234/api/v1` می‌سازد.

2) **ثبت کلاینت**  
POST /phone/create
Content-Type: application/json

1) **ذخیره امن**  
- `BASE_URL`، `secretKey` در SharedPrefrences ذخیره شود.

---

## سناریو B — استفاده از API

###  (مثال‌های استخراج‌شده از کد)
- `GET /device/get-all` (با Base URL محلی)
- `GET /section/get-all`
- `GET /sub-section/get-by-section-id-and-type/{sectionID}/{type}`
- هدرهای پایه:
Accept: application/json
Content-Type: application/json

- `GET /scenario`
- `POST /scenario/run/{id}`
- `GET /setting`

---

## سناریو C — RPC (فرمان‌های دستگاه)

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


