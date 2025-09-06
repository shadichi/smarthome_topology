<div dir="rtl">

# Deployment — Smart Home

## هدف
این بخش نحوه‌ی استقرار (Deployment) سیستم Smart Home را توضیح می‌ دهد  

---

## محیط‌ها (Environments)
1. **Development (Dev)**  
   - در عمل اپ رو روی سیستم خودمان یا مستقیم روی تلویزیون و موبایل واقعی Build و Run می‌کنیم.
(هیچ سرور جدا وجود ندارد.) 

1. **Staging (Pre-Production)**  
   - فعلاً محیط جدا نداریم، تست‌ ها را روی همان سرور اصلی انجام می‌ دهیم.

2. **Production (Prod)**  
   - همان نسخه‌ ای که روی تلویزیون‌ و موبایل واقعی نصب می شود.
اپ Flutter با دستور flutter build apk --release ساخته و مستقیم روی دستگاه نصب می شود.  

</div>