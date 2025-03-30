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

ThemeData lightTheme = ThemeData(
  useMaterial3: true,
  brightness: Brightness.light,
  colorScheme: ColorScheme.fromSeed(
    seedColor: Colors.blue,
    brightness: Brightness.light,
  ),
  textTheme: TextTheme(
    headlineLarge: TextStyle(fontSize: 24, fontWeight: FontWeight.bold, color: Colors.black),
    bodyLarge: TextStyle(fontSize: 16, color: Colors.black),
    bodyMedium: TextStyle(fontSize: 14, color: Colors.grey[800]),
  ),
  appBarTheme: AppBarTheme(
    backgroundColor: Colors.blue.shade700,
    foregroundColor: Colors.white,
    elevation: 4,
  ),
);
```

### 🌑 تم تاریک (Dark Theme)
```dart
ThemeData darkTheme = ThemeData(
  useMaterial3: true,
  brightness: Brightness.dark,
  colorScheme: ColorScheme.fromSeed(
    seedColor: Colors.blue,
    brightness: Brightness.dark,
  ),
  textTheme: TextTheme(
    headlineLarge: TextStyle(fontSize: 24, fontWeight: FontWeight.bold, color: Colors.white),
    bodyLarge: TextStyle(fontSize: 16, color: Colors.white),
    bodyMedium: TextStyle(fontSize: 14, color: Colors.grey[400]),
  ),
  appBarTheme: AppBarTheme(
    backgroundColor: Colors.grey[900],
    foregroundColor: Colors.white,
    elevation: 0,
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

