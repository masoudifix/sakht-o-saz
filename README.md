# ساخت و ساز مربعی

سازنده: بنیامین بگیان — مشاور: بهراد بگیان

## فایل‌های بازی
| فایل | کار |
|---|---|
| `index.html` | خود بازی (همه چیز داخل همین یک فایل است) |
| `manifest.json` | مشخصات برنامه (اسم، آیکون، تمام‌صفحه، افقی) |
| `sw.js` | ذخیره برای اجرای آفلاین |
| `icon-192.png` | آیکون کوچک (۱۹۲×۱۹۲) |
| `icon-512.png` | آیکون بزرگ (۵۱۲×۵۱۲) |
| `.nojekyll` | فایل خالی برای GitHub Pages |

> آیکون‌ها فعلاً موقت‌اند. آیکون خودت را با همین دو اسم و همین اندازه‌ها جایگزین کن.

## ۱) بارگذاری در GitHub (بدون برنامه‌نویسی)
1. در github.com حساب بساز و وارد شو.
2. بالا سمت راست `+` ← **New repository**. اسم: `sakht-o-saz`. گزینه **Public** را بزن ← **Create repository**.
3. در صفحه مخزن روی **uploading an existing file** بزن.
4. هر ۶ فایل بالا (از جمله `.nojekyll`) را بکش و رها کن. (اگر `.nojekyll` در گوشی دیده نمی‌شود، بی‌خیالش شو.)
5. پایین صفحه **Commit changes** را بزن.
6. برو **Settings ← Pages**. در Source بزن **Deploy from a branch**، شاخه `main` و پوشه `/ (root)` ← **Save**.
7. بعد از ۱ تا ۲ دقیقه آدرس بازی ظاهر می‌شود:
   `https://USERNAME.github.io/sakht-o-saz/`
   (به جای USERNAME اسم کاربری خودت.) آن را در مرورگر کروم گوشی باز کن و تست کن.

## ۲) ساخت APK
**روش ساده (PWABuilder):**
1. برو `pwabuilder.com`، آدرس بازی را وارد کن و **Start** بزن.
2. **Package for stores ← Android** را انتخاب کن.
3. اسم بسته را بنویس (مثلاً `com.bagian.sakhtosaz`) و **Generate** بزن.
4. فایل ZIP را دانلود کن. داخلش APK برای تست و AAB برای گوگل‌پلی هست.
5. APK را روی گوشی نصب کن. (در تنظیمات گوشی نصب از منبع ناشناخته را اجازه بده.)

> برای اینکه نوار آدرس مرورگر داخل برنامه دیده نشود، باید فایل `assetlinks.json` که PWABuilder می‌دهد را در مسیر `.well-known/assetlinks.json` همین مخزن بگذاری. راهنمایش داخل ZIP هست.

**روش دوم (Capacitor، برای کسی که Android Studio دارد):**
```
npm init -y
npm i @capacitor/core @capacitor/cli @capacitor/android
npx cap init "ساخت و ساز مربعی" com.bagian.sakhtosaz --web-dir=.
npx cap add android
npx cap sync
npx cap open android      # در Android Studio: Build > Build APK
```

## ۳) به‌روزرسانی بازی
فایل `index.html` جدید را در GitHub جایگزین کن (Add file ← Upload files). تا چند دقیقه بازی در همه جا به‌روز می‌شود. اگر نسخه قدیمی می‌ماند، در `sw.js` عدد `sakht-v2` را به `sakht-v3` تغییر بده.

## نکته
بازی برای اولین اجرا به اینترنت نیاز دارد (کتابخانه Three.js از cdnjs)، بعد از آن آفلاین هم کار می‌کند.
