# نَفَس جديد – Breathe Free (مشروع ملف APK)

مشروع Capacitor جاهز لتحويل التطبيق إلى ملف APK للأندرويد. بيئة المحادثة لا تحتوي على Android SDK، لذلك لم يُبنَ الـAPK هناك، والطريقتان أدناه تبنيانه لك. لم يُختبر بناء الـAPK ولا تثبيته على جهاز بعد.

## الطريقة 1 – بدون تثبيت برامج (GitHub مجاناً)
1. أنشئ حساباً على github.com ثم مستودعاً جديداً (New repository).
2. ارفع محتويات هذا المجلد كلها (Add file ▸ Upload files) بما فيها المجلدات www وassets و.github.
   إن لم يظهر مجلد .github: Add file ▸ Create new file، واكتب الاسم `.github/workflows/build-apk.yml` والصق محتوى الملف build-apk-workflow.txt.
3. افتح تبويب Actions ثم Build APK. يستغرق نحو 10 دقائق في أول مرة (اضغط Run workflow إن لم يبدأ وحده).
4. افتح التشغيل المكتمل، ومن قسم Artifacts نزّل breathe-free-apk (ملف مضغوط بداخله breathe-free.apk).
5. انقل الملف إلى الهاتف وثبّته (فعّل «تثبيت تطبيقات من مصدر غير معروف» عند الطلب).

## الطريقة 2 – على جهازك
المتطلبات: Node 22+ وAndroid Studio 2025.2.1 أو أحدث.

    npm install
    npx cap add android
    npx --yes @capacitor/assets generate --android
    npx cap sync android
    cd android && ./gradlew assembleDebug

الناتج: android/app/build/outputs/apk/debug/app-debug.apk (أو شغّل `npx cap open android` لفتحه في Android Studio).

## ملاحظات
- هذا APK تجريبي (debug) يصلح للتثبيت والمشاركة المباشرة. للنشر في Google Play يلزم إصدار Release موقّع بمفتاحك.
- الإشعارات اليومية تصل في الوقت الذي تحدده حتى والتطبيق مغلق بعد منح إذن الإشعارات، وقد تتأخر دقائق بسبب توفير الطاقة.
- خط Cairo يُحمَّل من الإنترنت، وبدون اتصال يستخدم التطبيق خط النظام.
- كل بيانات المستخدم محفوظة على جهازه فقط.
