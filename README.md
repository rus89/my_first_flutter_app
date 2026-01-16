# Flutter Application

A Flutter application that generates random word pairs and allows users to mark favorites. Built with Flutter 3.x using the Provider state management pattern and Material Design 3.

## Features

- **Random Word Generator**: Generates random English word pairs using the `english_words` package
- **Favorites Management**: Mark/unmark word pairs as favorites
- **Responsive Navigation**: Adaptive NavigationRail that expands on wider screens
- **Multi-page Navigation**: Home (Generator) and Favorites pages
- **Material Design 3**: Modern UI with seed-based theming (Green Accent)
- **State Management**: Provider pattern for reactive state updates

## Project Structure

```
lib/
├── main.dart              # App entry point with MyApp, MyAppState, MyHomePage, GeneratorPage, FavoritesPage, BigCard
test/
├── widget_test.dart       # Widget tests
android/                   # Android platform-specific code
ios/                       # iOS platform-specific code
macos/                     # macOS platform-specific code
windows/                   # Windows platform-specific code
linux/                     # Linux platform-specific code
web/                       # Web platform-specific code
```

## Requirements

- **Dart SDK**: `^3.10.7`
- **Flutter**: 3.x or later

## Dependencies

### Production

- `flutter` - Framework SDK
- `english_words: ^4.0.0` - English word pair generation
- `provider: ^6.1.5` - State management
- `cupertino_icons: ^1.0.8` - iOS-style icons

### Development

- `flutter_test` - Testing framework
- `flutter_lints: ^6.0.0` - Lint rules

## Getting Started

### Prerequisites

Ensure Flutter is installed and up-to-date:

```bash
flutter --version
flutter upgrade
```

### Installation

1. **Clone or open the project**:

```bash
cd /path/to/flutter_application_1
```

2. **Get dependencies**:

```bash
flutter pub get
```

3. **Run the app**:

```bash
flutter run
```

On a physical device or emulator, this will hot-reload on save for rapid development.

## Usage

### Home Page (Generator)

- Displays a random word pair in a large card
- **Like button** (`♡` / `♥`) — Mark the current pair as a favorite
- **Next button** — Generate and display the next random word pair

### Favorites Page

- View all saved favorite word pairs
- Shows count and list of bookmarked pairs
- Each favorite has a favorite icon indicator

### Navigation

- Use the **NavigationRail** on the left to switch between Home and Favorites
- On narrow screens, the rail collapses to icons
- On wider screens (600+ dp), labels expand for clarity

## Architecture & State Management

The app uses **Provider** for reactive state management via `ChangeNotifier`:

```dart
class MyAppState extends ChangeNotifier {
  var current = WordPair.random();
  var favorites = <WordPair>[];

  void getNext() {
    current = WordPair.random();
    notifyListeners();  // Rebuilds dependent widgets
  }

  void toggleFavorite() {
    if (favorites.contains(current)) {
      favorites.remove(current);
    } else {
      favorites.add(current);
    }
    notifyListeners();
  }
}
```

All pages access state via `context.watch<MyAppState>()`, ensuring reactive updates.

## Theming

The app uses Material Design 3 with a seed-based color scheme:

```dart
theme: ThemeData(
  colorScheme: ColorScheme.fromSeed(seedColor: Colors.greenAccent),
),
```

To customize colors, modify the `seedColor` in [lib/main.dart](lib/main.dart#L20).

## Testing

Run the test suite:

```bash
flutter test
```

Current tests are in [test/widget_test.dart](test/widget_test.dart). Tests validate widget behavior and state updates.

## Building for Release

### Android

```bash
flutter build apk          # APK for direct installation
flutter build aab          # App Bundle for Google Play
```

### iOS

```bash
flutter build ios
```

### Web

```bash
flutter build web
```

### macOS, Windows, Linux

```bash
flutter build macos
flutter build windows
flutter build linux
```

## Code Quality

- **Linting**: Run `flutter analyze` to check code quality
- **Formatting**: Run `flutter format .` to format Dart code
- **Version**: App version is `1.0.0+1` in [pubspec.yaml](pubspec.yaml)

## Common Commands

| Command                | Purpose                                  |
| ---------------------- | ---------------------------------------- |
| `flutter run`          | Run the app on connected device/emulator |
| `flutter test`         | Run all tests                            |
| `flutter analyze`      | Static code analysis                     |
| `flutter format .`     | Auto-format Dart code                    |
| `flutter pub get`      | Install dependencies                     |
| `flutter pub upgrade`  | Upgrade dependencies to latest versions  |
| `flutter pub outdated` | Check for available updates              |
| `flutter clean`        | Clean build artifacts                    |

## Development Notes

- The app is currently set to **not publish** to pub.dev (`publish_to: 'none'`)
- All app logic is in a single `main.dart` file for simplicity
- State is preserved during the session but not persisted to disk
- The responsive layout uses `LayoutBuilder` for adaptive UI

## Future Enhancements

- **Persistence**: Save favorites using `shared_preferences` or `hive`
- **Routing**: Add named routes with `MaterialApp.router`
- **Modularization**: Split `main.dart` into separate files by widget
- **Testing**: Expand unit and integration tests
- **Dark mode**: Add brightness awareness to theme
- **Pagination**: Load favorites incrementally for large lists

## Resources

- [Flutter Official Documentation](https://docs.flutter.dev/)
- [Dart Language Guide](https://dart.dev/guides)
- [Provider Package](https://pub.dev/packages/provider)
- [English Words Package](https://pub.dev/packages/english_words)

## License

(Add your license here, e.g., MIT, Apache 2.0, etc.)

## Support

For issues or questions, refer to the Flutter documentation or open an issue in this repository.
