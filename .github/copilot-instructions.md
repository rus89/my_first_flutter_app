## Copilot Project Instructions (flutter_application_1)

- Project type: stock Flutter 3.x counter app scaffold. Entry point `runApp(const MyApp())` wires `MaterialApp` → `MyHomePage` counter screen in [lib/main.dart](lib/main.dart).
- State: local `setState` counter in `_MyHomePageState`; keep simple state local unless introducing a deliberate state manager. `MyApp` is the stateless root; prefer adding new screens as separate widgets and route them from `MaterialApp`.
- Theming: Material 3 seed theme via `ThemeData.fromSeed` with deep purple; AppBar uses `inversePrimary`. Adjust theme centrally in `ThemeData` inside `MyApp`.
- Routing: no named routes yet; `home` points to `MyHomePage`. Add new pages via `routes`/`onGenerateRoute` on `MaterialApp` and keep navigation logic there.
- UI pattern: Scaffold with AppBar, Column body, and `FloatingActionButton` increment handler. Follow the same pattern for new simple screens.
- Tests: widget smoke test in [test/widget_test.dart](test/widget_test.dart) pumps `MyApp`, taps the FAB, and expects the counter to increment. Keep widget tests fast (pumpWidget, minimal frames) and update expectations if labels change.
- Lints: [analysis_options.yaml](analysis_options.yaml) includes `package:flutter_lints/flutter.yaml`; respect its defaults and toggle rules here when needed.
- Dependencies: only `flutter` and `cupertino_icons` in [pubspec.yaml](pubspec.yaml); add new packages there and run `flutter pub get`.
- Builds/run: common commands — `flutter run` for local dev (hot reload), `flutter test` for the suite, `flutter analyze` for static checks, `flutter format .` (or `dart format .`) before commits.
- Platforms: platform folders for Android/iOS/web/macos/windows/linux are scaffolded; keep cross-platform logic in `lib/` and isolate platform-specific tweaks under their respective platform directories.
- Assets/fonts: Material Icons already enabled; register additional assets or fonts under the `flutter:` section of [pubspec.yaml](pubspec.yaml) when needed.
- Versioning: app version is `1.0.0+1` in [pubspec.yaml](pubspec.yaml); bump name/code together for releases.
