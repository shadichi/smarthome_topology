# SSE and HTTP Agreements — Smart Home

## هدف
 قراردادهای ارتباطی اپ با سرور :
- **SSE (Server-Sent Events):** برای رویدادهای لحظه‌ای.
- **HTTP API:** برای فرمان‌ها، CRUD روی سکشن‌ها، سناریوها و RPC.

---

## 1. HTTP API

### Base URL
http://ip:1234/api/v1


### مسیرهای اصلی (نمونه‌هایی از کد)

| Path | Method | توضیح |
|------|--------|-------|
| /device/get-all | GET | لیست دستگاه‌ ها |
| /section/get-all | GET | همه سکشن‌ ها |
| /rpc | POST | فرمان‌های دستگاه (SwitchOnLight, AcPanelControl, …) |
| /scenario | GET | گرفتن سناریوها (includeToken: true) |
| /scenario/run/{id} | POST | اجرای سناریو (includeToken: true) |
| /phone/create | POST | ثبت گوشی با secretKey (از QR) |

---

## 2. SSE (Server-Sent Events)

### Endpoint
GET http://ip:1234/api/v1/sse/stream

توضیح کامل و نمونه کد ها و عملکرد داخل فایل swagger موجود می باشد