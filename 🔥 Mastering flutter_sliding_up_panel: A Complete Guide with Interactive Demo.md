# 

## Learn how to use the flutter_sliding_up_panel package like a pro! This in-depth tutorial breaks down every property, controller usage…

June 29, 2025

> ***Learn how to use the*** ***`flutter_sliding_up_panel`*** ***package like a pro!*** *This in-depth tutorial breaks down every property, controller usage, lifecycle, and customization trick you need to build interactive sliding panels in Flutter.*

### ✨ Introduction

Sliding panels are intuitive UX components that can slide over or under the main content, providing users with a powerful way to view additional information without leaving the current screen. Flutter's UI capabilities make this seamless, and the `flutter_sliding_up_panel` package lets you build elegant, interactive panels easily.

![None](https://miro.medium.com/v2/resize:fit:700/1*5zf8_MhrF6Y1_L-O9k-wTw.png)

Visual representation of the three primary states of a sliding panel in Flutter — **Collapsed**, **Anchored**, and **Expanded** — with user interaction flow shown using directional arrows.

In this article, we'll build a complete interactive example (shown in the code above), where the panel:

- Expands and collapses on button press or scroll
- Reacts to gesture events
- Dynamically updates bounds
- Provides a modern, card-style overlay

### 🚀 What is `flutter_sliding_up_panel`?

This package provides a widget `SlidingUpPanelWidget` that acts like a modal or bottom sheet, with fine-grained control over:

- gesture callbacks (drag down, drag start, etc.)
- visibility (hide, show)
- anchor points (midway stops)
- programmatic control using `SlidingUpPanelController`

### ⚙️ Installing the Package

In your `pubspec.yaml`:

```dart
dependencies:
  flutter:
    sdk: flutter
  flutter_sliding_up_panel: ^2.1.1
```

Run:

```dart
flutter pub get
```

### 🧱 Anatomy of the Sliding Panel

### Main Widget: `SlidingUpPanelWidget`

The panel overlays your existing screen layout, meaning you can place it on top of any `Scaffold`, `Stack`, or even inside a `PageView`.

#### Example Structure

```dart
Stack(
  children: [
    Scaffold(...),
    SlidingUpPanelWidget(...),
  ],
)
```

### 🔧 Core Properties Explained

#### `panelController`

```dart
final SlidingUpPanelController panelController = SlidingUpPanelController();
```

Use this to:

- `expand()`
- `collapse()`
- `anchor()`
- `hide()`

This gives you full programmatic control over the panel's state.

#### `minimumBound`, `upperBound`

These control how far the panel can collapse and expand:

```dart
minimumBound: 0.0,
upperBound: 1.0,
```

You can change these dynamically with `setState()` for responsive layouts.

#### `anchor`

The midpoint the panel snaps to:

```dart
anchor: 0.4,
```

This means after dragging, the panel will rest at 40% height unless you expand or collapse it fully.

#### `controlHeight`

This defines the visible "control bar" area of the panel when it's collapsed.

```dart
controlHeight: 50.0,
```

Often styled with drag handles or icons.

### 🔁 Full Interaction Lifecycle

#### `onTap`

Toggles panel states when user taps the control bar:

```dart
onTap: () {
  if (panelController.status == SlidingUpPanelStatus.expanded)
    panelController.collapse();
  else
    panelController.expand();
}
```

#### Drag Gestures

```dart
dragDown: (details) => print('dragDown'),
dragStart: (details) => print('dragStart'),
dragUpdate: (details) => print('dragUpdate'),
dragCancel: () => print('dragCancel'),
dragEnd: (details) => print('dragEnd'),
```

These provide granular feedback during panel movement. Great for analytics or triggering animations.

### 📜 Scroll-Triggered Actions

You attached a `ScrollController` to the internal `ListView`. This lets you expand the panel when the user scrolls to the bottom:

```dart
if (scrollController.offset >= scrollController.position.maxScrollExtent) {
  panelController.expand();
}
```

Similarly, when scrolling up to the top:

```dart
if (scrollController.offset <= scrollController.position.minScrollExtent) {
  panelController.anchor();
}
```

This builds a very natural UX!

### 🎨 Styling the Panel

Your panel uses a `Container` with a card-like look:

```dart
decoration: ShapeDecoration(
  color: Colors.white,
  shadows: [BoxShadow(...)],
  shape: RoundedRectangleBorder(
    borderRadius: BorderRadius.only(
      topLeft: Radius.circular(10.0),
      topRight: Radius.circular(10.0),
    ),
  ),
),
```

You can even replace this with `Material`, gradients, or images.

### 📊 Performance Overlay

You've added:

```dart
showPerformanceOverlay: showPerformance,
```

When toggled via the settings icon, this displays Flutter's internal performance metrics — handy for debugging jank or slow builds.

### 💥 Dynamic Bound Updates

Button presses update the `minimumBound` and `upperBound` in real-time:

```dart
setState(() {
  minBound = 0.3;
});
```

This allows live reconfiguration of the panel's behavior — helpful in responsive UIs or A/B testing.

### 🧪 Buttons for Manual Control

You added several `TextButton`s:

- `Expand panel`
- `Collapse panel`
- `Anchor panel`
- `Hide panel`
- `Set minimumBound`
- `Set upperBound`

Each triggers the corresponding controller method or UI state change.

### 🎯 Use Cases

This panel is perfect for:

- Music player overlays
- Filter panels
- Chat details
- Context menus
- Interactive tutorials
- Sheet-based navigation

### ✅ Best Practices

- Always wrap `SlidingUpPanelWidget` in a `Stack`.
- Use `Flexible` inside the panel for scrollable content.
- Handle gesture callbacks to improve user feedback.
- Anchor points are your friend — use them to reduce cognitive load.
- Animate bounds with `AnimatedContainer` for smoother UX.

### 🧩 Full Working Code

(Use your original code here, formatted neatly using Markdown code blocks.)

### 📌 Final Thoughts

The `flutter_sliding_up_panel` package is powerful, flexible, and easy to use. Whether you're building music apps, maps, or dashboards, this widget brings delight to your UX with minimal setup. By understanding the controller, gestures, bounds, and interactions — you can design truly modern interfaces.

#Flutter #SlidingPanel #FlutterUI #MobileUX #Dart #FlutterWidgets #StateManagement #FlutterPackages #FlutterTutorial
