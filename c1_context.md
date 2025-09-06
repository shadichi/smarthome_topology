<div dir="rtl">

# C1 — System Context (Smart Home)

## هدف
نمای کلی سیستم اسمارت‌ هوم: اپ موبایل و TV برای کنترل روشنایی، صوتی، گرمایش/سرمایش، پرده و آبیاری؛ با ارتباط بلادرنگ از طریق سرویس SSE و هسته‌ ی مشترک رابط کاربری. (State Management: GetX، Shared UI: Arsit Core) 

---

## سرویس ها
- **Mobile App (Flutter)**: اپ اصلی برای کنترل؛ از GetX و Core Package مشترک استفاده می‌ کند. 
- **TV App (Flutter)**: نسخه‌ ی مخصوص تلویزیون، با Core مشترک. 
- **SSE Service**: ارتباط بلادرنگ.  
- **External Services**: وضعیت هوا(هنوز پیاده سازی نشده است) 

---

## نمودار کانتکست (C1)

![نمودار کانتکست](images/Context_diagram.png)

</div>
