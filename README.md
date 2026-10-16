<!-- ... existing code ... -->
### 🛠️ Tech Stack
* HTML5, CSS3, ES6+ JavaScript Modules
* Tailwind CSS (CDN) & Vazirmatn Persian Font
* Firebase Authentication & Cloud Firestore (v11)
* Chart.js & Web Speech API

---

### 🔥 Firebase Setup & Configuration Guide (Cloud Sync)

To enable real-time synchronization between devices using your own free Google Firebase account, follow these simple steps:

#### 1. Create a Firebase Project
1. Go to the [Firebase Console](https://console.firebase.google.com/) and sign in with your Google account.
2. Click **Add project** (or **Create a project**), choose a project name (e.g., `my-todo-app`), and click **Continue**.
3. (Optional) Disable Google Analytics for simplicity, then click **Create project**.

#### 2. Register a Web App
1. On your project overview page, click the **Web icon (`</>`)**.
2. Give your app a nickname (e.g., `Todo Web`) and click **Register app**.
3. You will see a `firebaseConfig` snippet that looks like this:
   ```javascript
   const firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
     projectId: "YOUR_PROJECT_ID",
     storageBucket: "YOUR_PROJECT_ID.firebasestorage.app",
     messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
     appId: "YOUR_APP_ID"
   };
   ```
4. Copy these keys and paste them into the `firebaseConfig` object inside `mobile_todo_app.html`.

#### 3. Enable Authentication (Google Sign-In)
1. In the left navigation menu, go to **Build** > **Authentication**.
2. Click **Get started**, select the **Sign-in method** tab.
3. Choose **Google**, enable it, pick your project support email, and click **Save**.

#### 4. Enable Cloud Firestore Database
1. In the left menu, go to **Build** > **Firestore Database**.
2. Click **Create database**, choose a nearby server location, and click **Next**.
3. Select **Start in test mode** (or set up security rules as shown below) and click **Create**.

#### 5. Recommended Security Rules (Firestore Rules)
Under **Firestore Database** > **Rules**, replace existing rules with the following to allow users to read and write their own task data securely:
```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
      // Or to allow custom room keys without auth:
      // allow read, write: if true;
    }
  }
}
```
Click **Publish**. Your app is now fully connected and synced in real time across mobile and desktop!

---

<a name="fa-farsi"></a>
## 🇮🇷 فارسی

یک وب‌اپلیکیشن مدرن، سبک و مستقل (PWA) برای مدیریت هوشمند کارهای روزانه، پروژه‌ها و زمان‌بندی شخصی با قابلیت همگام‌سازی لحظه‌ای بین گوشی و کامپیوتر.

### ✨ قابلیت‌های کلیدی
<!-- ... existing code ... -->
### 🚀 نحوه اجرا
1. **اجرای مستقیم:** فایل `mobile_todo_app.html` را در مرورگر دسکتاپ یا موبایل باز کنید.
2. **نصب به عنوان اپ موبایل (PWA):** فایل را روی هاست یا گیت‌هاب پیج قرار داده و در مرورگر گوشی گزینه **«افزودن به صفحه اصلی / Add to Home Screen»** را بزنید.

---

### 🔥 راهنمای گام‌به‌گام اتصال و راه‌اندازی فایربیس (Firebase)

برای فعال‌سازی همگام‌سازی ابری و سینک شدن آنی تسک‌ها بین گوشی و لپ‌تاپ با اکانت رایگان گوگل خودتان، مراحل زیر را طی کنید:

#### ۱. ساخت پروژه جدید در فایربیس
1. به کنسول فایربیس در آدرس [console.firebase.google.com](https://console.firebase.google.com/) بروید و با جیمیل خود وارد شوید.
2. روی دکمه **Add project** (یا **Create project**) کلیک کنید.
3. یک نام برای پروژه وارد کنید (مثلاً `my-todo-sync`) و روی **Continue** بزنید.
4. بخش Google Analytics را در صورت تمایل غیرفعال کنید و دکمه **Create project** را بزنید تا پروژه ساخته شود.

#### ۲. ثبت اپلیکیشن وب و دریافت کلیدها (Config)
1. در صفحه اصلی پروژه، روی آیکون وب (**`</>`**) کلیک کنید.
2. یک نام دلخواه (مثلاً `Todo App`) بنویسید و دکمه **Register app** را بزنید.
3. فایربیس کدی شبیه به این به شما نمایش می‌دهد:
   ```javascript
   const firebaseConfig = {
     apiKey: "کلید_اختصاصی_شما",
     authDomain: "your-id.firebaseapp.com",
     projectId: "your-id",
     storageBucket: "your-id.firebasestorage.app",
     messagingSenderId: "شماره_فرستنده",
     appId: "شناسه_اپ"
   };
   ```
4. این مقادیر را کپی کرده و در فایل `mobile_todo_app.html` در بخش شیء `firebaseConfig` جایگزین کنید.

#### ۳. فعال‌سازی ورود با اکانت گوگل (Authentication)
1. از منوی سمت چپ، بخش **Build** و سپس **Authentication** را انتخاب کنید.
2. روی **Get started** کلیک کرده و وارد تب **Sign-in method** شوید.
3. گزینه **Google** را انتخاب، آن را فعال (Enable) کنید، ایمیل پشتیبانی خود را انتخاب کرده و دکمه **Save** را بزنید.

#### ۴. فعال‌سازی پایگاه داده ابری (Cloud Firestore)
1. از منوی سمت چپ، بخش **Build** و سپس **Firestore Database** را انتخاب کنید.
2. روی **Create database** کلیک کرده و موقعیت سرور را انتخاب کنید.
3. حالت شروع را روی **Start in test mode** بگذارید و دکمه **Create** را بزنید.

#### ۵. تنظیم قوانین امنیتی (Firestore Rules)
برای امنیت بیشتر داده‌ها، در تب **Rules** داخل Firestore کدهای زیر را قرار داده و دکمه **Publish** را بزنید:
```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
      // اگر از شناسه سفارشی بدون ورود به گوگل استفاده می‌کنید:
      // allow read, write: if true;
    }
  }
}
```
پس از زدن دکمه انتشار، اتصال برنامه کامل شده و داده‌ها بدون قطعی بین تمام دستگاه‌ها سینک خواهند شد.

---

## 📌 Active Version / نسخه فعال
* **`v1.5.0`**
