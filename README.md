# تركيز — Focus

تطبيق ويب متكامل (PWA) للإنتاجية: مؤقت بومودورو، عادات يومية، متابعة العبادات بمواقيت الصلاة حسب موقعك، وإحصائيات تفصيلية.
يعمل بالعربية والإنجليزية (RTL/LTR) على الموبايل والتابلت وسطح المكتب، ويمكن تثبيته كتطبيق.

## محتويات المجلد
| الملف | الوظيفة |
|---|---|
| `index.html` | التطبيق كاملًا (HTML + CSS + JS) |
| `manifest.webmanifest` · `sw.js` · `icons/` | التثبيت كتطبيق والعمل أوفلاين |
| `404.html` · `robots.txt` | صفحة الخطأ وملف محركات البحث |
| `database.rules.json` | قواعد أمان قاعدة البيانات (كل مستخدم يصل لبياناته فقط) |
| `firebase.json` · `.firebaserc` | إعدادات الاستضافة والـ headers ومشروع Firebase |

## النشر على Firebase Hosting
```bash
npm i -g firebase-tools
firebase login
firebase deploy --only hosting,database      # من داخل هذا المجلد
```
> بديل: Netlify / Cloudflare Pages / GitHub Pages — ارفع المجلد كما هو، وانسخ `database.rules.json` يدويًا من Firebase Console ← Realtime Database ← Rules.

## قائمة التحقق بعد النشر
1. **Authentication ← Settings ← Authorized domains**: أضف نطاقك لو غير `web.app`.
2. تأكد أن قواعد قاعدة البيانات منشورة وأن **Test mode** غير مفعّل.
3. افتح الموقع ثم DevTools ← Console. لو لا توجد تحذيرات CSP غيّر `Content-Security-Policy-Report-Only` إلى `Content-Security-Policy` في `firebase.json` وأعد النشر.
4. جرّب: إنشاء حساب، تسجيل دخول، جلسة تركيز، تحديد الموقع (يعمل على HTTPS فقط)، تثبيت التطبيق، تبديل اللغة.
5. عند أي تعديل على `index.html` غيّر رقم النسخة `V` في `sw.js` (مثل `tarkeez-v8`) ليتحدّث الكاش عند المستخدمين.

## ملاحظات
- مواقيت الصلاة تقديرية، وتُحسب داخل الصفحة بدون خدمات خارجية؛ اختر طريقة الحساب من تبويب العبادات.
- الأسبوع في الإحصائيات يبدأ من الأحد.
# tarkeez-app
