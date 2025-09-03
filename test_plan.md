# Tests Plan — Smart Home (Flutter)

## وضعیت فعلی
- در حال حاضر **هیچ تست خودکاری نوشته نشده**.
- این سند فقط مسیر پیشنهادی برای اضافه کردن تست‌ها در آینده است.

---

## هدف تست‌ها
- مطمئن شدن از درستی ارتباط با API محلی (device, section, rpc).
- بررسی همگام‌سازی صحیح داده‌ها با SSE.
- تضمین سلامت کش داده‌ها در SharedPreferences.
- تست ساده برای UI (صفحه‌ها بدون کرش باز شوند).

---

## انواع تست‌ها

### 1) Unit Tests (اولویت بالا)
- **RequestsManager**:
  - بررسی ساخت درست Base URL از IP و Port.
  - متد `getAllDeviceRequest` → وقتی سرور لیست خالی برگرداند.
  - متد `relayStatusRequest` → وقتی خطا بدهد.
- **SSEService**:
  - وصل شدن و ارسال event mock.
  - تست reconnect در حالت قطع.

### 2) Widget Tests (بعد از Unit)
- **صفحه لاگین/QR Scan**: نمایش صحیح ورودی‌ها و خطایابی.
- **صفحه Devices**: نمایش درست لیست دستگاه‌ها.
- **صفحه Lighting**: اعمال تغییر سطح نور → state UI به‌روزرسانی شود.

### 3) Integration Tests
- سناریوی کامل:
  - اسکن QR → ساخت Base URL → ثبت گوشی.
  - GET device → دریافت داده و کش.
  - POST rpc (SwitchOnLight) → پاسخ ok → تغییر در UI.
  - دریافت event SSE → UI آپدیت شود.

### 4) Manual QA Checklist (فعلاً برای هر ریلیز)
- اپ نصب می‌شود و بدون کرش بالا می‌آید.
- اسکن QR → Base URL درست ست می‌شود.
- می‌توان Device و Section گرفت.
- فرمان روشنایی/AC کار می‌کند.
- SSE بعد از چند دقیقه فعال و event دریافت می‌شود.

---

## اولویت‌بندی عملی
1. هفته ۱–۲: نوشتن ۵ تست Unit برای RequestsManager (موک HTTP).
2. هفته ۳: نوشتن ۲ تست برای SSEService (موک event).
3. هفته ۴: اضافه کردن یک تست Integration (happy path).
4. هفته ۵: اضافه کردن ۲ Widget Test برای UI.

---

## ابزار پیشنهادی
- `flutter_test` (داخلی فلاتر)
- `mocktail` برای موک HTTP و SSE
- `fake_async` برای تست reconnect و delay
- (اختیاری) `golden_toolkit` برای تست‌های UI تصویری

---

## اجرا
- همه تست‌ها:
flutter test
- فقط یک فایل:
flutter test test/services/requests_manager_test.dart

---

## نمونه اسکلت تست (Unit)

```dart
import 'package:flutter_test/flutter_test.dart';
import 'package:myapp/services/requests_manager.dart';

void main() {
test('builds correct base url from ip', () {
  final staticIp = "10.38.9.65";
  final url = "http://$staticIp:1234/api/v1";
  expect(url, contains("10.38.9.65"));
});
}
