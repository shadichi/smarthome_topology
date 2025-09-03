# Database ER Diagram — Smart Home (Local)

## هدف
الان ذخیره‌سازی محلی ما از جنس **Key–Value (SharedPreferences/XML)** است. پس:
1) به‌جای ERD جدولی، **مدل مفهومی خیلی ساده** می‌دهیم؛
2) نگاشت به **کلیدهای واقعی SharedPreferences** را لیست می‌کنیم؛
3) نکات امنیتی ذخیره‌سازی محلی را می‌نویسیم.

---

## نوع ذخیره‌سازی فعلی
- **SharedPreferences (XML)**
- نمونه‌ای که الان داری:
```xml
<?xml version='1.0' encoding='utf-8' standalone='yes' ?>
<map>
    <string name="flutter.password">password</string>
    <string name="flutter.username">username</string>
</map>
```

همچنین IP و secret_key بعد از اسکن QR در همین فضای محلی ذخیره می‌شوند.
