# 📱 دليل تحويل QR Pro Scanner إلى APK

## 📂 محتوى هذه الحزمة
```
index.html       ← التطبيق الكامل
manifest.json    ← ملف PWA (يجعله قابلاً للتثبيت)
sw.js            ← Service Worker (يشغّله بدون إنترنت)
icon-192.png     ← أيقونة التطبيق (صغيرة)
icon-512.png     ← أيقونة التطبيق (كبيرة)
```

---

## 🚀 الطريقة الأولى: APK بدون برمجة (5 دقائق)

### الخطوة 1 — رفع الملفات على GitHub Pages (مجاني)

1. افتح **github.com** وأنشئ حساباً مجانياً (أو سجّل دخولك)
2. اضغط **New repository** → اسمه: `qr-scanner`
3. فعّل خيار **Public** ثم اضغط **Create repository**
4. اضغط **uploading an existing file** (أو Add file → Upload)
5. ارفع جميع الملفات من هذه الحزمة دفعة واحدة
6. اضغط **Commit changes**
7. اذهب لـ **Settings → Pages → Source → main branch** ← اضغط **Save**
8. بعد دقيقة سيكون رابطك:
   ```
   https://اسم_المستخدم.github.io/qr-scanner/
   ```

### الخطوة 2 — تحويل الرابط إلى APK

#### الموقع الأسهل: **WebIntoApp.com**
1. افتح: https://webintoapp.com
2. الصق رابط GitHub Pages
3. اكتب اسم التطبيق: `QR Pro Scanner`
4. اضغط **Generate APK**
5. انتظر دقيقتين → حمّل ملف `.apk`

#### بديل مجاني: **AppsGeyser.com**
1. افتح: https://appsgeyser.com
2. اختر **Website** → الصق رابطك → اضغط **Next**
3. اضغط **Generate** → حمّل الـ APK

---

## 🔧 الطريقة الثانية: APK احترافي بـ Capacitor

> مثالية لو تريد نشره على Google Play

### المتطلبات
- [Node.js](https://nodejs.org) (v18+)
- [Android Studio](https://developer.android.com/studio)
- Java 17+

### الخطوات
```bash
# 1. ثبّت Capacitor
npm install -g @capacitor/cli
npm init -y
npm install @capacitor/core @capacitor/android

# 2. هيّئ المشروع
npx cap init "QR Pro Scanner" "com.qrpro.scanner" --web-dir .

# 3. أضف Android
npx cap add android

# 4. انسخ الملفات
npx cap copy

# 5. افتح في Android Studio
npx cap open android
```
في Android Studio:
- **Build → Generate Signed Bundle/APK → APK**
- أنشئ keystore جديد
- اختر **release** → اضغط **Finish**
- ستجد الـ APK في: `android/app/release/app-release.apk`

---

## 📲 الطريقة الثالثة: تثبيت مباشر كـ PWA (الأسرع)

> بعد رفع الملفات على GitHub Pages:

**Android Chrome:**
1. افتح الرابط في Chrome
2. اضغط ⋮ → **"إضافة إلى الشاشة الرئيسية"**
3. اضغط **إضافة** ← يُثبَّت كأيقونة تطبيق!

**iPhone Safari:**
1. افتح الرابط في Safari
2. اضغط ↑ Share → **"Add to Home Screen"**
3. اضغط **إضافة**

---

## ❓ الفرق بين الطرق

| | WebIntoApp | PWA | Capacitor |
|---|---|---|---|
| السهولة | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐ |
| APK حقيقي | ✅ | ❌ | ✅ |
| يعمل بدون نت | ✅ | ✅ | ✅ |
| Google Play | ❌ | ❌ | ✅ |
| مجاني | نسبياً | تماماً | تماماً |

---

## ⚠️ ملاحظة مهمة للـ APK
عند تثبيت الـ APK يدوياً على Android:
- اذهب لـ **الإعدادات → الأمان → السماح بمصادر مجهولة**
- أو في Android 8+: **الإعدادات → التطبيقات → المتصفح → تثبيت تطبيقات غير معروفة → سماح**
