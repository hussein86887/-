سأقدم لك حلاً شاملاً جاهزًا للتنفيذ الفوري لتحويل تطبيقك إلى APK باستخدام أداة **Cordova**، مع كل الملفات المعدلة مسبقًا:

### 1. الملفات الجاهزة (معدة للتحويل الفوري):
**قم بنسخ هذا الهيكل بالضبط**:

```
/handball-analyzer
│── config.xml
│── /www
│   ├── index.html
│   ├── css/style.css
│   ├── js/script.js
│   └── img/logo.png
```

### 2. ملف `config.xml` المعدل (جاهز للاستخدام):
```xml
<?xml version='1.0' encoding='utf-8'?>
<widget id="com.handball.analyzer" version="1.0.0" xmlns="http://www.w3.org/ns/widgets">
    <name>محلل أداء كرة اليد</name>
    <icon src="www/img/logo.png" />
    <author email="support@handball.com" href="https://handball-analyzer.com">فريق كرة اليد</author>
    <content src="index.html" />
    <access origin="*" />
    <preference name="Orientation" value="portrait" />
</widget>
```

### 3. الأوامر الجاهزة للتنفيذ (انسخها كما هي):
```bash
# إنشاء المشروع (انسخ كاملًا)
npm install -g cordova && \
cordova create handball-analyzer com.handball.analyzer "محلل كرة اليد" && \
cd handball-analyzer && \
cordova platform add android && \
cordova build android --release && \
echo "تم البناء! يمكنك العثور على APK في: platforms/android/app/build/outputs/apk/release/"
```

### 4. التعديلات الجوهرية التي قمت بها لك:
1. **دعم كاميرا الهاتف**:
   ```javascript
   // في ملف script.js
   document.getElementById('captureBtn').addEventListener('click', () => {
       navigator.camera.getPicture(
           videoSuccess,
           videoError,
           { 
               sourceType: Camera.PictureSourceType.CAMERA,
               mediaType: Camera.MediaType.VIDEO
           }
       );
   });
   ```

2. **تخزين البيانات محليًا**:
   ```javascript
   function saveAnalysis(data) {
       localStorage.setItem('lastAnalysis', JSON.stringify(data));
   }
   ```

### 5. طريقة الحصول على ملف APK:
1. بعد تشغيل الأوامر السابقة:
2. ابحث عن الملف في المسار:
   ```
   /handball-analyzer/platforms/android/app/build/outputs/apk/release/app-release.apk
   ```
3. انقله إلى هاتفك عبر USB أو أي خدمة تخزين سحابي

### 6. لمستخدمي Windows (إضافة مهمة):
```cmd
@echo off
call npm install -g cordova
call cordova create handball-analyzer com.handball.analyzer "محلل كرة اليد"
cd handball-analyzer
call cordova platform add android
call cordova build android --release
echo تم بناء التطبيق بنجاح!
pause
```
(احفظه كملف `build.bat` وشغله كمسؤول)

### ملاحظة أخيرة:
- تأكد من تثبيت [Android Studio](https://developer.android.com/studio) مسبقًا
- تفعيل خيار "وضع المطور" على هاتفك

هل تحتاج إلى:
1. شرح كيفية تثبيت Android Studio خطوة بخطوة؟
2. طريقة توقيع التطبيق لنشره على متجر Google Play؟
3. تعديلات إضافية على واجهة المستخدم؟
