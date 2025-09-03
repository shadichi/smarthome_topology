# SSE and HTTP Agreements — Smart Home

## هدف
توضیح قراردادهای ارتباطی اپ Smart Home با سرور محلی:
- **SSE (Server-Sent Events):** برای رویدادهای لحظه‌ای مثل تغییر وضعیت رله یا دما.
- **HTTP API:** برای فرمان‌ها، CRUD روی سکشن‌ها، سناریوها و RPC.

---

## 1. HTTP API

### Base URL
http://<ip>:1234/api/v1
(از QR گرفته می‌شود)

### هدرهای استاندارد
- `Accept: application/json`
- `Content-Type: application/json`
- (اختیاری) `Authorization: Bearer <token>` برای مسیرهای حساس

### مسیرهای اصلی (نمونه‌ها از کد)

| Path | Method | توضیح |
|------|--------|-------|
| /device/get-all | GET | فهرست دستگاه‌ها |
| /section/get-all | GET | همه سکشن‌ها |
| /section/create | POST | ساخت سکشن |
| /section/update/{id} | PUT | بروزرسانی سکشن |
| /section/delete/{id} | DELETE | حذف سکشن |
| /sub-section/create | POST | ساخت زیر‌بخش |
| /sub-section/get/{id} | GET | دریافت زیر‌بخش |
| /sub-section/update/{id} | PUT | بروزرسانی |
| /sub-section/delete/{id} | DELETE | حذف |
| /rpc | POST | فرمان‌های دستگاه (SwitchOnLight, AcPanelControl, …) |
| /scenario | GET | گرفتن سناریوها (includeToken: true) |
| /scenario/run/{id} | POST | اجرای سناریو (includeToken: true) |
| /setting | GET | گرفتن تنظیمات (includeToken: true) |
| /phone/create | POST | ثبت گوشی با secretKey (از QR) |

---

## 2. SSE (Server-Sent Events)

### Endpoint
GET http://<ip>:1234/api/v1/sse/stream

### هدرها
- `Accept: text/event-stream`
- `Cache-Control: no-cache`


توضیح کامل و نمونه کد ها و عملکرد داخل فایل swagger موجود می باشد