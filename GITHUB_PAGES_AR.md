# طريقة رفع المشروع على GitHub وتشغيله على GitHub Pages

## 1) الرفع
1. أنشئي مستودعًا جديدًا (Repository) على GitHub بحسابك، وليكن اسمه مثلًا `smart-study-buddy`.
2. ارفعي كل محتويات هذا المجلد إلى الفرع `main` (بما فيها المجلد المخفي `.github`).

## 2) تفعيل GitHub Pages (مرة واحدة فقط)
1. افتحي المستودع ← **Settings** ← **Pages**.
2. في خانة **Source** اختاري **GitHub Actions**.
3. افتحي تبويب **Actions** وانتظري حتى تظهر علامة ✅.
4. الموقع سيكون على: `https://اسم-حسابك.github.io/اسم-المستودع/`

كل مرة ترفعين تعديلًا على `main` يُنشر الموقع تلقائيًا.

## 3) تسجيل الدخول واسترجاع كلمة المرور
في لوحة تحكم Supabase الخاصة بقاعدة البيانات ← **Authentication** ← **URL Configuration**:
- **Site URL**: `https://اسم-حسابك.github.io/اسم-المستودع/`
- أضيفي نفس الرابط في **Redirect URLs** مع `**` في آخره.

## 4) قاعدة البيانات والذكاء الاصطناعي
- الموقع نفسه (الواجهة) يعمل على GitHub Pages.
- البيانات وتسجيل الدخول والملفات ووظائف الذكاء الاصطناعي تعمل عبر Supabase (المجلد `supabase/`).
- الإعدادات موجودة في ملف `.env`. لنقل المشروع إلى حساب Supabase خاص بك:
  1. أنشئي مشروعًا على supabase.com.
  2. ضعي قيم مشروعك الجديد في `.env` (`VITE_SUPABASE_URL` و`VITE_SUPABASE_PUBLISHABLE_KEY` و`VITE_SUPABASE_PROJECT_ID`).
  3. باستخدام Supabase CLI: `supabase db push` ثم `supabase functions deploy`.
  4. أضيفي مفتاح Gemini: `supabase secrets set GEMINI_API_KEY=...`

## التشغيل على جهازك
```
npm install
npm run dev
```
