В Flutter для десктопных приложений (Windows, macOS, Linux) можно запретить изменение размера окна с помощью плагина window_size. Для мобильных платформ это не требуется, а для web — невозможно.
Пошагово:
Добавьте зависимость window_size в pubspec.yaml:

```dart
dependencies:
  window_size: ^0.1.0
```

В main.dart, после runApp, вызовите setWindowMinSize и setWindowMaxSize с одинаковыми значениями (например, 400x800).
Пример кода для main.dart:

```dart
import 'package:flutter/material.dart';
import 'package:window_size/window_size.dart';

void main() {
  WidgetsFlutterBinding.ensureInitialized();
  setWindowMinSize(const Size(400, 800));
  setWindowMaxSize(const Size(400, 800));
  runApp(MyApp());
}
```

Это заблокирует изменение размера окна на десктопе. Не забудьте выполнить flutter pub get после изменения pubspec.yaml.
