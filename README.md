# Syria Press — Starter (Next.js + Tailwind)

نسخة جاهزة للنشر على Vercel.
- RTL عربي
- أقسام (عاجل/محلي/دولي) — قابل للتخصيص
- صفحات: الرئيسية، الأقسام، المقال، من نحن
- مصدر بيانات مبدئي: `data/posts.json`

## الاستخدام

```bash
npm i
npm run dev
```

افتح: http://localhost:3000

## الإضافة السريعة لخبر جديد
حرّر `data/posts.json` وأضف عنصرًا جديدًا بالشكل التالي:

```json
{
  "id": "3",
  "title": "عنوان الخبر",
  "slug": "new-article",
  "category": "عاجل",
  "date": "2025-10-19T02:00:00Z",
  "excerpt": "ملخص قصير...",
  "image": "/logo.jpg",
  "content": "نص الخبر يمكن أن يتضمن **تشديد**."
}
```

## النشر على Vercel
1. أنشئ مستودع Git جديد وارفع الملفات.
2. ادخل إلى [Vercel](https://vercel.com) واختر "Import from Git".
3. الإعدادات الافتراضية تكفي (Framework: Next.js).
4. بعد النشر، افتح المسار `/api/health` للتأكد من الصحة.

> لاحقاً يمكن ربط الأخبار بـ Facebook Graph أو RSS أو CMS مثل Sanity/Strapi/WordPress headless.

## ربط صفحة فيسبوك
1) احصل على **Page ID** لصفحتك: https://findmyfbid.in أو من إعدادات الصفحة الجديدة (معرّف الصفحة).  
2) أنشئ **Facebook App** واحصل على **Page Access Token** مع الصلاحيات `pages_read_engagement` و`pages_read_user_content`، ويفضّل تحويله إلى **توكن طويل الأمد**.  
3) انسخ `.env.example` إلى `.env` وعدّل القيم:
```
FACEBOOK_PAGE_ID=YOUR_PAGE_ID
FACEBOOK_PAGE_TOKEN=YOUR_PAGE_ACCESS_TOKEN
```
4) شغّل التطبيق محلياً، وستظهر منشورات صفحتك في قسم "منشورات الصفحة على فيسبوك".  
5) على Vercel: أضف المتغيّرات نفسها في **Project → Settings → Environment Variables**.  
6) إذا ظهرت أخطاء، تفقد لوج السيرفر في Vercel ومعاينة `GET /api/facebook`.

> التوكن يظل على السيرفر فقط؛ لا يتم كشفه للمتصفح.
