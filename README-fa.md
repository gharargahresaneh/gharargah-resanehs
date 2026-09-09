# قرارگاه رسانه‌ای — نسخه GitHub Pages + Supabase

این نسخه برای GitHub Pages ساخته شده و برای مدیریت واقعی محتوا از Supabase استفاده می‌کند.

## امکانات
- ورود مدیر با ایمیل و رمز عبور
- افزودن، ویرایش، حذف و انتشار/مخفی‌کردن اطلاعیه
- آپلود دائمی عکس و ویدئو در Storage
- نمایش عمومی مطالب منتشرشده
- ریسپانسیو برای موبایل
- لینک‌های روبیکا، آپارات و روبینو

## نصب

### 1) ساخت پروژه Supabase
یک پروژه در Supabase بسازید و وارد SQL Editor شوید.

فایل `supabase.sql` همین پوشه را کامل اجرا کنید.

### 2) ساخت حساب مدیر
در Supabase از بخش **Authentication > Users** یک کاربر با ایمیل و رمز دلخواه بسازید.

بعد UUID همان کاربر را از جدول Users بردارید و در SQL Editor اجرا کنید:

```sql
insert into public.admin_users (id) values ('UUID-USER-HERE');
```

### 3) تنظیم config.js
فایل `config.js` را باز کنید و این دو مقدار را از **Project Settings > API** پروژه Supabase بردارید:

- Project URL
- anon / publishable key

کلید `service_role` را **هرگز** داخل سایت یا GitHub قرار ندهید.

### 4) انتشار در GitHub Pages
کل فایل‌های این پوشه را داخل repository قرار دهید و از:

**Settings → Pages → Deploy from a branch → main / root**

GitHub Pages را فعال کنید.

بعد از انتشار:

- سایت: `https://USERNAME.github.io/REPOSITORY/`
- پنل: `https://USERNAME.github.io/REPOSITORY/admin.html`

## نکته امنیتی
امنیت واقعی با Row Level Security در Supabase انجام می‌شود. `anon key` قابل قرارگیری در فرانت‌اند است؛ اما `service_role key` هرگز نباید منتشر شود.

## محدودیت آپلود
در این نسخه رابط مدیریت فایل‌های تا ۱۰۰ مگابایت را قبول می‌کند. محدودیت واقعی Storage بسته به تنظیمات پروژه Supabase است.
