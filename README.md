# Onboarding Form Kit

الفورم دي بتتنشر على Vercel، وأي عميل يملاها، إجاباته بتنزل على طول كصف جديد في Google Sheet بتاعتك.

## الملفات
- **index.html**: الفورم نفسها.
- **apps-script.gs**: الكوبري اللي بيوصّل الفورم بالـ Sheet.
- **README.md**: الخطوات دي.

## الخطوات

### 1. اعمل Google Sheet جديدة
افتح sheets.new، وسمّيها مثلاً "Client Onboarding".

### 2. حط الـ Script
- من جوه الـ Sheet: **Extensions › Apps Script**.
- امسح أي كود موجود، والزق محتوى **apps-script.gs** كله.
- دوس **Save**.

### 3. اعمل Deploy كـ Web app
- **Deploy › New deployment**.
- من **Select type** اختار **Web app**.
- **Execute as: Me**.
- **Who has access: Anyone** (لازم Anyone، وإلا الفورم مش هتعرف تبعت).
- دوس **Deploy**، ووافق على الصلاحيات (لو ظهرلك "Google hasn't verified this app": دوس **Advanced** وبعدين **Go to project**).
- انسخ الـ **Web app URL** (بيبدأ بـ https://script.google.com/macros/s/...).

### 4. ارفع الفورم على GitHub
- اعمل حساب على github.com (لو مش عندك).
- **New repository**، سمّيه مثلاً `onboarding-form`، ودوس **Create repository**.
- دوس **uploading an existing file** (أو **Add file › Upload files**)، ارفع **index.html**، ودوس **Commit changes**.

### 5. حط اللينك في الفورم (من GitHub نفسه)
- افتح **index.html** جوه الـ Repository، ودوس **القلم ✏️**.
- في سطر 7 فوق خالص هتلاقي:
  `<meta name="apps-script-url" content="PASTE_YOUR_APPS_SCRIPT_URL_HERE">`
- ظلّل `PASTE_YOUR_APPS_SCRIPT_URL_HERE` بس، والزق مكانها الـ Web app URL، وسيب علامتين التنصيص.
- **اتأكد إن اللينك آخره `/exec` مش `/dev`**.
- دوس **Commit changes**.

### 6. انشر على Vercel
- ادخل vercel.com، واعمل **Sign up with GitHub**.
- **Add New › Project**، واختار الـ Repository بتاعك، ودوس **Import** وبعدين **Deploy**.
- بعد ثواني هيطلعلك لينك زي `onboarding-form.vercel.app`. ده اللي هتبعته لعملائك.
- (اختياري) من **Settings › Domains** تقدر تربطه بدومين بتاعك، زي `onboarding.youragency.com`.

### 7. جرّبها
املا الفورم بنفسك ودوس **Submit**، وافتح الـ Sheet: هتلاقي تاب اسمه **Responses** فيه صف جديد.

## لو حاجة مش شغالة
- **مفيش صف نزل في الـ Sheet:** اتأكد إن اللينك آخره **/exec**، وإن **Who has access = Anyone**. افتح اللينك في نافذة Incognito: لازم يظهر "Onboarding form bridge is live." من غير تسجيل دخول.
- **رسالة You’re all set بتظهر دايماً**، حتى لو الإجابة ماوصلتش، فاعتمد على الـ Sheet نفسها في التأكد.
- **عدّلت في الـ Script:** لازم **Deploy › Manage deployments › Edit (القلم) › Version: New version › Deploy**، وإلا التعديل مش هيشتغل.
- **عدّلت في index.html على GitHub:** Vercel بيعمل Deploy جديد لوحده خلال ثواني.
- **عايز تغيّر الأسئلة:** عدّل في index.html. أي سؤال جديد هيتعمله عمود جديد في الـ Sheet أوتوماتيك.
