# S Loop PWA setup

این بسته برای مسیر GitHub Pages زیر ساخته شده است:
https://11sherinv-stack.github.io/sherinv.github.io/

## 1) فایل‌ها را در ریشه مخزن قرار بده
این فایل‌ها و پوشه `icons` را کنار `index.html` آپلود کن:
- manifest.webmanifest
- sw.js
- icons/

## 2) در index.html داخل بخش <head> اضافه کن
```html
<meta name="theme-color" content="#586a2b">
<link rel="manifest" href="./manifest.webmanifest">
<link rel="icon" type="image/png" sizes="192x192" href="./icons/icon-192.png">
<link rel="apple-touch-icon" href="./icons/icon-192.png">
```

## 3) پیش از </body> اضافه کن
```html
<script>
if ("serviceWorker" in navigator) {
  window.addEventListener("load", () => {
    navigator.serviceWorker.register("./sw.js", { scope: "./" })
      .catch((error) => console.error("S Loop service worker:", error));
  });
}
</script>
```

## 4) انتشار و آزمایش
- تغییرات را در GitHub ذخیره کن و منتظر بمان GitHub Pages به‌روزرسانی شود.
- سایت را با Chrome اندروید باز کن.
- از منوی Chrome گزینه Install app یا Add to Home screen را بزن.

## 5) ساخت فایل APK
بعد از اینکه PWA درست نصب شد، در PWABuilder آدرس سایت را وارد کن:
https://www.pwabuilder.com/
سپس بخش Android را برای بسته‌بندی دنبال کن.

توجه: آیکون PNG این بسته از نشان حرف S در سربرگ فعلی سایت الهام گرفته و یک خروجی سازگار با اندازه‌های رایج اندروید است. Service worker فقط فایل‌های هم‌مبدأ را کش می‌کند؛ بازی‌هایی که در تب جدید یا از دامنه‌های دیگر باز می‌شوند ممکن است برای اجرای آفلاین به پشتیبانی جداگانه نیاز داشته باشند.
