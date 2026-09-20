# 📖 راهنمای کامل راه‌اندازی - گام به گام

## ✅ چک‌لیست کامل

### مرحله ۱: نصب اپلیکیشن‌های موبایل (۵ دقیقه)

#### 1.1 نصب Tailscale
1. از [Google Play Store](https://play.google.com/store/apps/details?id=com.tailscale.ipn) دانلود کنید
2. باز کنید و روی **Get Started** بزنید
3. با Google یا ایمیل ثبت‌نام کنید (رایگان)
4. اجازه‌های VPN رو بدید
5. منتظر بمونید تا Connected بشه (نوتیفیکیشن میاد)

**چک کنید:** یک آیکون کلید 🔑 در نوتیفیکیشن‌ها باید ببینید

#### 1.2 نصب Windows App (Microsoft Remote Desktop)
1. از [Google Play Store](https://play.google.com/store/apps/details?id=com.microsoft.rdc.androidx) دانلود کنید
2. باز کنید (هنوز نیازی به تنظیم نیست)

---

### مرحله ۲: دریافت Tailscale Auth Key (۲ دقیقه)

1. روی گوشی یا کامپیوتر برید به: https://login.tailscale.com/admin/settings/keys
2. اگه لاگین نکردید، با همون اکانتی که تو اپ ساختید لاگین کنید
3. روی دکمه **Generate auth key...** کلیک کنید
4. **مهم:** تیک **Reusable** رو حتماً بزنید ✅
5. (اختیاری) Expiration رو میتونید ۹۰ روز بذارید
6. **Generate key** بزنید
7. کلید ظاهر میشه (شبیه `tskey-auth-kXXXXXXXXXXXX`)
8. روی **Copy** بزنید - **خیلی مهم: این کلید فقط یک‌بار نمایش داده میشه!**

**یادداشت کنید:** این کلید رو یه‌جایی کپی کنید (نوت‌پد یا ...) چون بعداً نیاز دارید

---

### مرحله ۳: تنظیم GitHub Secrets (۳ دقیقه)

#### 3.1 ورود به صفحه Secrets
1. به ریپوی GitHub برید: https://github.com/MOBL99/roblox-studio-remote
2. تب **Settings** (بالا راست)
3. سمت چپ: **Secrets and variables** → **Actions**
4. دکمه سبز **New repository secret**

#### 3.2 اضافه کردن Secret اول - TAILSCALE_AUTH_KEY
- **Name:** `TAILSCALE_AUTH_KEY`
- **Secret:** کلیدی که از Tailscale کپی کردید (tskey-auth-k...)
- **Add secret** بزنید

#### 3.3 اضافه کردن Secret دوم - RDP_USERNAME
- **New repository secret** دوباره
- **Name:** `RDP_USERNAME`
- **Secret:** یک یوزرنیم دلخواه (مثلاً `matin` یا `admin`)
- **یادداشت کنید** چون موقع اتصال نیاز دارید
- **Add secret**

#### 3.4 اضافه کردن Secret سوم - RDP_PASSWORD
- **New repository secret** دوباره
- **Name:** `RDP_PASSWORD`  
- **Secret:** یک پسورد قوی بسازید (حداقل ۸ کاراکتر، مثلاً `Roblox@2026`)
- **یادداشت کنید** چون موقع اتصال نیاز دارید
- **Add secret**

**چک کنید:** باید ۳ تا Secret ببینید:
- ✅ TAILSCALE_AUTH_KEY
- ✅ RDP_USERNAME
- ✅ RDP_PASSWORD

---

### مرحله ۴: اجرای Workflow (۱ دقیقه)

1. برید به تب **Actions** در ریپو
2. اگه پیام زرد رنگ میبینید، روی **I understand my workflows, go ahead and enable them** بزنید
3. سمت چپ: **Windows 11 RDP with Roblox Studio** رو انتخاب کنید
4. سمت راست بالا: دکمه **Run workflow** (خاکستری)
5. یک منوی dropdown باز میشه
6. **Run workflow** (سبز) رو بزنید

**صبر کنید:** workflow شروع میشه (یک دایره زرد 🟡 ظاهر میشه)

---

### مرحله ۵: منتظر ماندن و دریافت اطلاعات (۳-۴ دقیقه)

#### 5.1 مشاهده پروسه
1. روی workflow جدید (بالای لیست) کلیک کنید
2. روی job **setup-rdp** کلیک کنید
3. لاگ‌ها رو مشاهده می‌کنید

#### 5.2 پیدا کردن Tailscale IP
وقتی به مرحله **Connect to Tailscale** رسید (حدود ۲ دقیقه):

```
===================================
TAILSCALE CONNECTION INFO
===================================
Tailscale IP: 100.x.x.x    ← این رو کپی کنید!
Hostname: github-roblox-xxxxx
Username: matin    ← یوزرنیمی که تو Secret گذاشتید
===================================
```

**خیلی مهم:** عدد `100.x.x.x` رو کپی کنید و یادداشت کنید

#### 5.3 منتظر "Keep session alive" بمونید
وقتی به این مرحله رسید، یعنی آماده‌ست:
```
===================================
RDP SESSION IS READY!
===================================
```

---

### مرحله ۶: اتصال از گوشی (۲ دقیقه)

#### 6.1 چک کردن Tailscale
1. اپ **Tailscale** رو روی گوشی باز کنید
2. بالای صفحه باید **Connected** ببینید (سبز)
3. اگه Inactive هست، روی **Connect** بزنید

#### 6.2 اضافه کردن PC در Windows App
1. اپ **Windows App** (Microsoft Remote Desktop) رو باز کنید
2. پایین روی **+** (علامت جمع) بزنید
3. **Add PC** رو انتخاب کنید

#### 6.3 وارد کردن اطلاعات
1. **PC Name:** IP ای که کپی کردید رو paste کنید (مثلاً `100.64.1.5`)
2. **User account** → **Add user account**
   - Username: یوزرنیمی که تو Secret گذاشتید (مثلاً `matin`)
   - Password: پسوردی که تو Secret گذاشتید
   - **Save** بزنید
3. **Friendly name** (اختیاری): `Roblox Studio`
4. **Save** (بالا راست)

#### 6.4 اتصال
1. روی کارت PC جدید tap کنید
2. اگه گواهی امنیتی پرسید، **Connect** یا **Accept** بزنید
3. صبر کنید... باید دسکتاپ Windows 11 رو ببینید! 🎉

---

### مرحله ۷: استفاده از Roblox Studio (۱ دقیقه)

1. روی دسکتاپ Windows، یک shortcut به نام **Roblox Studio** هست
2. دوبار روش tap کنید (یا یک‌بار tap نگه دارید و باز کنید)
3. Roblox Studio باز میشه
4. با اکانت Roblox خودتون لاگین کنید
5. شروع به ساخت بازی کنید! 🎮

---

## 🎮 نکات کنترلی برای موبایل

### کنترل‌های لمسی
- **یک انگشت:** حرکت موس
- **تپ:** کلیک چپ
- **نگه داشتن:** کلیک راست
- **دو انگشت - بازوبسته کردن:** زوم
- **دو انگشت - اسکرول:** حرکت صفحه

### کیبورد مجازی
- روی **کیبورد آیکون** (بالای صفحه) بزنید
- کیبورد گوشی ظاهر میشه

### بهبود کیفیت
در Windows App:
- منو (۳ نقطه) → **Settings** → **Display**
- **Resolution:** بذارید **Fit to screen**
- **Color depth:** **True color (32-bit)**

---

## 🔧 عیب‌یابی

### نمیتونم وصل بشم - خطای Connection failed

**راه‌حل 1:** چک کنید Tailscale Connected هست
- اپ Tailscale رو باز کنید
- اگه Inactive هست، Connect بزنید
- منتظر بمونید تا سبز بشه

**راه‌حل 2:** IP رو دوباره چک کنید
- به GitHub Actions برگردید
- لاگ Connect to Tailscale رو دوباره باز کنید
- IP رو دوباره کپی کنید

**راه‌حل 3:** Secrets رو چک کنید
- Settings → Secrets → Actions
- مطمئن بشید هر ۳ secret هستند
- اگه اشتباه وارد کردید، Edit کنید و workflow رو دوباره Run کنید

### خطای Authentication failed

یوزرنیم یا پسورد اشتباهه:
- Settings → Secrets → Actions
- RDP_USERNAME و RDP_PASSWORD رو چک کنید
- درست وارد کنید و workflow رو دوباره Run کنید

### تصویر لگ داره یا کند هست

**راه‌حل 1:** اینترنت
- به Wi-Fi وصل شید (نه 4G/5G)
- سرعت اینترنت حداقل ۱۰ Mbps باشه

**راه‌حل 2:** تنظیمات کیفیت
- Windows App → Settings → Display
- Resolution رو کمتر کنید (مثلاً ۱۲۸۰x۷۲۰)
- یا Frame rate رو کم کنید

### Workflow با خطا متوقف شد

**خطای "TAILSCALE_AUTH_KEY secret is not set":**
- Secret رو اضافه نکردید یا اسم اشتباهه
- دقیقاً `TAILSCALE_AUTH_KEY` باید باشه (حروف بزرگ)

**خطای "Tailscale installation failed":**
- مشکل موقت GitHub Actions - دوباره Run workflow کنید

---

## 📊 محدودیت‌ها

### زمان
- **هر سشن:** تا ۶ ساعت
- **رایگان ماهانه:** ۲۰۰۰ دقیقه (۳۳ ساعت)
- **استفاده شما:** workflow هر بار که Run میکنید از محدودیت کم میشه

### همزمانی
- فقط ۱ workflow میتونه هم‌زمان اجرا بشه
- اگه workflow قبلی هنوز Running هست، اول اون رو Cancel کنید

### ذخیره‌سازی
- فایل‌هایی که تو Roblox Studio میسازید موقع اتمام سشن پاک میشن
- **حتماً** پروژه‌ها رو Publish کنید یا فایل‌ها رو دانلود کنید

---

## 🎯 نکات کاربردی

### کار با پروژه‌های Roblox

1. **ذخیره پروژه:**
   - File → Publish to Roblox
   - یا File → Save to Roblox

2. **دانلود فایل‌ها:**
   - فایل رو در Windows ذخیره کنید
   - از Tailscale Files یا Google Drive آپلود کنید

3. **کار با Git:**
   - میتونید Git نصب کنید و push کنید

### کار با چند نفر

اگه میخواید دوستاتون هم بتونن وصل بشن:
- همون Tailscale Auth Key رو بهشون بدید
- همون username/password
- همون IP

**توجه:** فقط یک نفر میتونه هم‌زمان کنترل داشته باشه

### افزایش مدت سشن

در Run workflow:
- Timeout hours رو از ۵ به ۶ تغییر بدید
- ولی از محدودیت ماهانه بیشتر استفاده میکنید

---

## ❓ سوالات متداول

**س: چرا باید Secrets بسازم؟**
ج: برای امنیت. پسورد و کلیدها در لاگ عمومی نمایش داده نمیشن.

**س: آیا ریپوی Private بسازم؟**
ج: میتونید. ولی Public هم مشکلی نداره چون Secrets مخفی هستند.

**س: محدودیت ۲۰۰۰ دقیقه کجاست؟**
ج: Settings → Billing and plans → Plans and usage

**س: میتونم Roblox Player هم نصب کنم؟**
ج: بله! تو Windows از Microsoft Store نصبش کنید.

**س: آیا اکانتم ban میشه؟**
ج: استفاده از GitHub Actions برای این کار خلاف قوانین نیست ولی زیاد استفاده نکنید.

---

## 🆘 پشتیبانی

اگه مشکلی داشتید:
1. همه مراحل عیب‌یابی بالا رو امتحان کنید
2. Workflow رو Cancel کنید و دوباره Run کنید
3. لاگ کامل GitHub Actions رو چک کنید

---

**موفق باشید! 🚀**

ساخته شده برای @MOBL99
