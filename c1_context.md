# C1 — System Context (Smart Home)

## هدف
نمای کلی سیستم اسمارت‌هوم: اپ موبایل و TV برای کنترل روشنایی، صوتی، گرمایش/سرمایش، پرده و آبیاری؛ با ارتباط بلادرنگ از طریق سرویس SSE و هسته‌ی مشترک رابط کاربری. (State Management: GetX، Shared UI: Arsit Core) 

---

## نقش‌ها و سامانه‌ها
- **User / Resident**: استفاده از اپ‌ها و کنترل بخش‌ها. 
- **Mobile App (Flutter)**: اپ اصلی برای کنترل؛ از GetX و Core Package مشترک استفاده می‌کند. 
- **TV App (Flutter)**: نسخه‌ی مخصوص تلویزیون، با Core مشترک. 
- **SSE Service**: ارتباط بلادرنگ و واکنشی.  
- **External Services**: داده‌ی وضعیت هوا و موقعیت برای داشبورد. 

---

## نمودار کانتکست (C1)

```mermaid
flowchart LR
  User[User] --> Mobile[Mobile App]
  User --> TV[TV App]
  User --> Wall[Wall Control Panel]

  Mobile --> SSE[SSE Service]
  TV --> SSE
  TV --> Weather

  SSE --> Lights[Lighting]
  SSE --> Audio[Audio]
  SSE --> HVAC[Heating Cooling]
  SSE --> Curtains[Curtains]
  SSE --> Irrigation[Irrigation]

  Mobile --> Weather[Weather Service]

  ```

  ## مرزبندی

داخل محدوده: اپ موبایل و TV، تعامل با SSE، هسته‌ی مشترک UI، کنترل بخش‌ها. 

خارج از محدوده: Backend کلاد (در حال حاضر وجود ندارد)، پیاده‌سازی Security نهایی، پردازش ویدیو دوربین.
