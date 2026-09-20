# 🎮 Roblox Studio Remote - دسترسی از موبایل

این ریپو به شما اجازه میده که Roblox Studio رو روی یک ماشین Windows 11 در GitHub Actions اجرا کنید و از طریق گوشی Android خودتون بهش دسترسی داشته باشید.

## ✨ ویژگی‌ها

- ✅ Windows 11 واقعی (نه VM)
- ✅ اتصال امن با Tailscale (بدون لگ)
- ✅ نصب خودکار Roblox Studio
- ✅ بهینه‌سازی برای کنترل با Windows App
- ✅ تا ۶ ساعت استفاده مداوم
- ✅ مجانی با GitHub Actions

## 📋 پیش‌نیازها

### ۱. نصب Tailscale روی گوشی
1. از [Google Play](https://play.google.com/store/apps/details?id=com.tailscale.ipn) دانلود کنید
2. اکانت Tailscale بسازید (مجانی)
3. لاگین کنید

### ۲. نصب Windows App روی گوشی
1. از [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.rdc.androidx) دانلود کنید
2. باز کنید و منتظر بمونید

## 🚀 راه‌اندازی (یک‌بار)

### مرحله ۱: دریافت Tailscale Auth Key

1. برید به [Tailscale Admin](https://login.tailscale.com/admin/settings/keys)
2. روی **Generate auth key** کلیک کنید
3. گزینه **Reusable** رو تیک بزنید
4. کلید رو کپی کنید (شکلش مثل `tskey-auth-k...` هست)

### مرحله ۲: تنظیم GitHub Secrets

1. برید به تب **Settings** این ریپو
2. **Secrets and variables** → **Actions** → **New repository secret**
3. دو Secret زیر رو اضافه کنید:

| نام | مقدار | توضیح |
|-----|------|-------|
| `TAILSCALE_AUTH_KEY` | کلیدی که از Tailscale گرفتید | برای اتصال به شبکه خصوصی |
| `RDP_USERNAME` | هر نامی که میخواید (مثلا `matin`) | یوزرنیم ویندوز |

**نکته:** پسورد خودکار ساخته میشه و توی لاگ Actions نمایش داده میشه.

## 🎯 نحوه استفاده

### راه‌اندازی سشن:

1. برید به تب **Actions** در GitHub
2. روی **Windows 11 RDP with Roblox Studio** کلیک کنید
3. **Run workflow** → **Run workflow** (سبز)
4. صبر کنید تا مرحله "Keep session alive" برسه (حدود ۳-۴ دقیقه)
5. در لاگ، Tailscale IP رو کپی کنید (مثل `100.x.x.x`)

### اتصال از گوشی:

1. **Tailscale** رو روی گوشی باز کنید و مطمئن بشید Connected هست
2. **Windows App** رو باز کنید
3. روی **+** بزنید → **Add PC**
4. IP رو وارد کنید (که از لاگ کپی کردید)
5. یوزرنیم و پسوردی که **در لاگ "Create RDP user" نشون داده شده** رو وارد کنید
6. Connect بزنید!

### استفاده از Roblox Studio:

- روی Desktop ویندوز، shortcut Roblox Studio رو میبینید
- باز کنید و با اکانت Roblox خودتون لاگین کنید
- شروع به ساخت بازی کنید! 🎮

## ⏱️ محدودیت‌ها

- **مدت سشن**: پیش‌فرض ۵ ساعت (قابل تغییر تا ۶ ساعت)
- **استفاده ماهانه**: GitHub Actions مجانی ۲۰۰۰ دقیقه میده (حدود ۳۳ ساعت)
- **همزمانی**: فقط یک سشن در یک زمان

## 🛠️ عیب‌یابی

### نمیتونم وصل بشم
- مطمئن شید Tailscale روی گوشی Connected هست
- IP رو درست کپی کردید؟
- Secrets رو درست وارد کردید؟

### لگ داره
- اینترنت گوشی ضعیفه، به WiFi وصل شید
- Tailscale بهتر از Codespaces هست ولی بستگی به اینترنت داره

### Roblox Studio باز نمیشه
- منتظر بمونید تمام مراحل نصب کامل بشه
- از Desktop باز کنید، نه از Start Menu

## 📱 بهینه‌سازی برای موبایل

این workflow بهینه شده برای:
- ✅ کاهش استفاده از CPU/RAM
- ✅ غیرفعال کردن Windows Defender
- ✅ حذف افکت‌های بصری اضافی
- ✅ تنظیم High Performance Mode

## ⚠️ هشدار

- از این روش فقط برای توسعه و تست استفاده کنید
- اکانت GitHub اصلی خودتون رو ریسک نکنید
- Secrets خودتون رو با کسی به اشتراک نگذارید

## 📝 لایسنس

MIT - استفاده آزاد

---

ساخته شده با ❤️ برای Matin (@MOBL99)
