# ✨ Flutter Theming Guide (Material 3) ✨

## 🌟 درباره این پروژه
این پروژه یک راهنمای کامل برای پیاده‌سازی تم (Theme) در فلاتر با جدیدترین روش‌ها (Material 3) است. این راهنما شامل:

- تعریف **تم روشن و تاریک** 🌟🌑
- استفاده از **ColorScheme.fromSeed** برای تنظیم رنگ‌ها 💟
- سفارشی‌سازی **متون، دکمه‌ها، ورودی‌ها، کارت‌ها** و سایر اجزای UI 🖌️
- **سوییچ بین تم‌ها** با یک دکمه 🔄

---

## 💪 تعریف تم‌ها در فلاتر

### 🌟 تم روشن (Light Theme)
```dart
import 'package:flutter/material.dart';

// تعریف تم روشن (Light Theme)  
ThemeData lightTheme = ThemeData(
  useMaterial3: true, // فعال‌سازی Material 3 برای داشتن طراحی مدرن و رنگ‌های هماهنگ‌تر
  brightness: Brightness.light, // تعیین روشن بودن تم (برای تم روشن)
  colorScheme: ColorScheme.fromSeed( // استفاده از SeedColor برای ایجاد پالت رنگی خودکار
    seedColor: Colors.blue, // رنگ اصلی که بقیه رنگ‌ها از آن مشتق می‌شوند
    brightness: Brightness.light, // تعیین روشن بودن پالت رنگ‌ها
  ),
  textTheme: TextTheme( // تنظیمات مربوط به فونت‌ها و استایل‌های متنی
    headlineLarge: TextStyle(fontSize: 24, fontWeight: FontWeight.bold, color: Colors.black), // تنظیم تیتر بزرگ
    bodyLarge: TextStyle(fontSize: 16, color: Colors.black), // تنظیم متن معمولی
    bodyMedium: TextStyle(fontSize: 14, color: Colors.grey[800]), // تنظیم متن با اندازه کوچک‌تر
  ),
  appBarTheme: AppBarTheme( // تنظیمات نوار بالای اپلیکیشن (AppBar)
    backgroundColor: Colors.blue.shade700, // رنگ پس‌زمینه نوار بالا
    foregroundColor: Colors.white, // رنگ متن نوار بالا
    elevation: 4, // ارتفاع نوار بالا
  ),
  elevatedButtonTheme: ElevatedButtonThemeData( // تنظیمات دکمه‌های مرتفع (ElevatedButton)
    style: ElevatedButton.styleFrom(
      backgroundColor: Colors.blue, // رنگ پس‌زمینه دکمه
      foregroundColor: Colors.white, // رنگ متن دکمه
      shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(12)), // شکل دکمه
      padding: EdgeInsets.symmetric(horizontal: 16, vertical: 12), // تنظیمات فاصله‌های دکمه
    ),
  ),
  inputDecorationTheme: InputDecorationTheme( // تنظیمات ورودی‌ها (مثل TextField)
    filled: true, // پر کردن پس‌زمینه ورودی
    fillColor: Colors.grey[200], // رنگ پس‌زمینه ورودی‌ها
    border: OutlineInputBorder(borderRadius: BorderRadius.circular(12)), // تنظیمات حاشیه ورودی‌ها
    focusedBorder: OutlineInputBorder( // تنظیمات حاشیه زمانی که ورودی فوکوس دارد
      borderSide: BorderSide(color: Colors.blue, width: 2), // رنگ و عرض حاشیه فوکوس
      borderRadius: BorderRadius.circular(12),
    ),
  ),
  cardTheme: CardTheme( // تنظیمات کارت‌ها (Card)
    color: Colors.white, // رنگ پس‌زمینه کارت‌ها
    shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(16)), // تنظیمات گوشه‌های کارت
    elevation: 4, // ارتفاع کارت
  ),
);
```

### 🌑 تم تاریک (Dark Theme)
```dart
// تعریف تم تاریک (Dark Theme)  
ThemeData darkTheme = ThemeData(
  useMaterial3: true, // فعال‌سازی Material 3 برای تم تاریک
  brightness: Brightness.dark, // تعیین تاریک بودن تم (برای تم تاریک)
  colorScheme: ColorScheme.fromSeed( // استفاده از SeedColor برای پالت رنگی خودکار در تم تاریک
    seedColor: Colors.blue, // رنگ اصلی برای تولید رنگ‌های خودکار
    brightness: Brightness.dark, // تعیین تاریک بودن پالت رنگ‌ها
  ),
  textTheme: TextTheme( // تنظیمات فونت‌ها و استایل‌های متنی برای تم تاریک
    headlineLarge: TextStyle(fontSize: 24, fontWeight: FontWeight.bold, color: Colors.white), // تیتر بزرگ با رنگ سفید
    bodyLarge: TextStyle(fontSize: 16, color: Colors.white), // متن معمولی با رنگ سفید
    bodyMedium: TextStyle(fontSize: 14, color: Colors.grey[400]), // متن کوچک با رنگ خاکی روشن
  ),
  appBarTheme: AppBarTheme( // تنظیمات نوار بالای اپلیکیشن در تم تاریک
    backgroundColor: Colors.grey[900], // رنگ پس‌زمینه نوار بالا در تم تاریک
    foregroundColor: Colors.white, // رنگ متن نوار بالا در تم تاریک
    elevation: 0, // ارتفاع نوار بالا در تم تاریک
  ),
  elevatedButtonTheme: ElevatedButtonThemeData( // تنظیمات دکمه‌های مرتفع برای تم تاریک
    style: ElevatedButton.styleFrom(
      backgroundColor: Colors.blue.shade300, // رنگ پس‌زمینه دکمه
      foregroundColor: Colors.black, // رنگ متن دکمه
      shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(12)), // شکل دکمه
    ),
  ),
  inputDecorationTheme: InputDecorationTheme( // تنظیمات ورودی‌ها (مثل TextField) در تم تاریک
    filled: true, // پر کردن پس‌زمینه ورودی
    fillColor: Colors.grey[800], // رنگ پس‌زمینه ورودی‌ها در تم تاریک
    border: OutlineInputBorder(borderRadius: BorderRadius.circular(12)), // حاشیه ورودی‌ها
    focusedBorder: OutlineInputBorder( // حاشیه ورودی‌ها زمانی که فوکوس دارند
      borderSide: BorderSide(color: Colors.blue, width: 2), // رنگ و عرض حاشیه فوکوس
      borderRadius: BorderRadius.circular(12),
    ),
  ),
  cardTheme: CardTheme( // تنظیمات کارت‌ها در تم تاریک
    color: Colors.grey[850], // رنگ پس‌زمینه کارت‌ها در تم تاریک
    shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(16)), // گوشه‌های کارت
    elevation: 4, // ارتفاع کارت‌ها
  ),
);
```

---

## 🔄 تغییر بین تم‌ها در `main.dart`
```dart
import 'package:flutter/material.dart';
import 'theme.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatefulWidget {
  @override
  State<MyApp> createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  bool isDarkMode = false;

  void toggleTheme() {
    setState(() {
      isDarkMode = !isDarkMode;
    });
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Flutter Theming',
      theme: lightTheme,
      darkTheme: darkTheme,
      themeMode: isDarkMode ? ThemeMode.dark : ThemeMode.light,
      home: HomeScreen(toggleTheme: toggleTheme),
    );
  }
}

class HomeScreen extends StatelessWidget {
  final VoidCallback toggleTheme;
  HomeScreen({required this.toggleTheme});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Flutter Theming')),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text('سلام، این یک اپلیکیشن با تم مدرن است!',
                style: Theme.of(context).textTheme.bodyLarge),
            SizedBox(height: 20),
            ElevatedButton(
              onPressed: toggleTheme,
              child: Text('تغییر تم'),
            ),
          ],
        ),
      ),
    );
  }
}
```

---

## 💡 نکات مهم
✅ **از `ThemeData` برای تعریف تم‌ها استفاده کنید.**

✅ **با `ColorScheme.fromSeed` می‌توانید رنگ‌های خودکار بسازید.**

✅ **تمام متون، دکمه‌ها، ورودی‌ها و کارت‌ها را شخصی‌سازی کنید.**

✅ **از `Theme.of(context)` برای دریافت استایل‌های تم در داخل ویجت‌ها استفاده کنید.**

✅ **با `themeMode` می‌توانید بین تم‌ها سوییچ کنید.**

✅ **از `useMaterial3: true` برای طراحی مدرن‌تر بهره ببرید.**

---

## 🎉 نتیجه‌گیری
این پروژه یک راهنمای جامع برای پیاده‌سازی تم در فلاتر است. اگر دوست دارید پروژه را ارتقا دهید یا پیشنهادی دارید، حتماً `Pull Request` ارسال کنید! 🚀

**⭐ این ریپوزیتوری را استار کنید تا همیشه به آن دسترسی داشته باشید! ⭐**

