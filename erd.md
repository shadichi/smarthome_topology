<div dir="rtl">

# Database ER Diagram — Smart Home (Local)

## هدف
در حال حاظر ذخیره‌ سازی محلی ما از جنس **Key–Value (SharedPreferences/XML)** است. پس:
- به‌جای ERD جدولی، **مدل مفهومی خیلی ساده** می‌دهیم؛
- نگاشت به **کلیدهای واقعی SharedPreferences** را لیست می‌کنیم؛

---

## نوع ذخیره‌سازی فعلی
- **SharedPreferences (XML)**
```xml
<?xml version='1.0' encoding='utf-8' standalone='yes' ?>
<map>
    <string name="flutter.password">password</string>
    <string name="flutter.username">username</string>
</map>
```

همچنین IP و secret_key بعد از اسکن QR در همین فضای محلی ذخیره می‌شوند.

</div>