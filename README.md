# dQuiz

A **PowerPoint 365/2026-style** presentation and quiz editor built with **WPF (.NET 8)**. Create interactive slides, add quiz questions with scoring, present with live HUD, and export to PNG — all in a modern Windows 11 Fluent UI.

![dQuiz](https://img.shields.io/badge/WPF-.NET%208-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Platform](https://img.shields.io/badge/platform-Windows%2010%2F11-lightgrey)

---

## ✨ Features

### 🎨 **Presentation Editor**
- **Ribbon UI** (File, Home, Insert, Design, Transitions, Animations, Slide Show)
- **Slide thumbnails** with drag-to-reorder
- **Canvas editor** with zoom (25%–400%), smart guides, and snap-to-grid
- **Text, shapes, images, and answer choices** as editable elements
- **Format pane** for fill, stroke, text color, rotation, opacity, corner radius

### 🧠 **Quiz Mode**
- Mark any slide as a **quiz question**
- Add **answer choices** and mark the correct one
- **True/False** and **multiple choice** layouts
- Set **points** and **time limits** per question
- Live **Quiz HUD** during presentation (score, timer, progress)

### 🎬 **Slide Show / Presenter**
- Full-screen presenter with keyboard navigation
- **8 transitions**: Fade, Push, Wipe, Zoom, Cover, Flip, etc.
- **11 entrance animations**: Appear, Fade, Fly, Zoom, Spin, Bounce, Float
- Speaker notes pane (toggle with **Notes** button)

### 🌙 **Theming & Personalization**
- **Light / Dark / System** theme modes
- **7 accent colors** (Blue, Graphite, Teal, Green, Purple, Orange, Pink)
- **9 built-in slide themes** (Office, Midnight, Ocean, Sunset, Forest, Mint, Lavender, Charcoal, Blue)
- **Canvas background** presets (Theme, Light, Neutral, Dark, Charcoal)
- **UI font** selector (any system font)
- **Language support**: English, Français, العربية (RTL)

### 💾 **File & Export**
- Native `.dquiz` JSON format
- **Export current slide as PNG** (1280×720)
- Recent files list in Backstage (File tab)
- Import legacy `quizzes.json`

### ⌨️ **Keyboard Shortcuts**
| Key | Action |
|-----|--------|
| `Ctrl+N` | New presentation |
| `Ctrl+O` | Open |
| `Ctrl+S` | Save |
| `Ctrl+Shift+S` | Save As |
| `Ctrl+M` | New slide |
| `Ctrl+D` | Duplicate element/slide |
| `Ctrl+B/I/U` | Bold / Italic / Underline |
| `Delete` | Delete selected |
| `Arrow` / `Shift+Arrow` | Nudge 1px / 10px |
| `F5` | Present from beginning |
| `Shift+F5` | Present from current |
| `Esc` | Close dialogs/overlays |

---

## 🏗️ Architecture

```
dQuiz/
├── App.xaml / App.xaml.cs           # App entry, theme initialization
├── MainWindow.xaml / .cs            # Ribbon, canvas, thumbnails, format pane, status bar
├── PresenterWindow.xaml / .cs       # Full-screen slideshow + Quiz HUD
├── Models/
│   ├── Presentation.cs              # Presentation, Slide, SlideElement, enums
│   └── Quiz.cs                      # Legacy quiz model
├── Services/
│   ├── AppSettings.cs               # Persisted user preferences (%LocalAppData%\dQuiz\settings.json)
│   ├── ThemeManager.cs              # Live Light/Dark/System + accent brushes
│   ├── Themes.cs                    # 9 slide themes + SlideFactory (6 layouts)
│   ├── PresentationService.cs       # Save/Load .dquiz, clone, import
│   ├── RecentFilesService.cs        # Recent files (max 10)
│   ├── LocalizationService.cs       # EN/FR/AR strings + RTL flow
│   └── QuizDataService.cs           # Legacy service
├── Rendering/
│   ├── SlideRenderer.cs             # Model → WPF visuals (1280×720)
│   └── Animator.cs                  # Entrance animations + slide transitions
├── Controls/
│   ├── SlideView.cs                 # Thumbnail live preview
│   └── Converters.cs                # PlusOneConverter, BoolToVisibility
├── Views/
│   ├── BackstageView.xaml / .cs     # PowerPoint-style File backstage (Home, New, Open, Save, Export, Options)
│   ├── SettingsView.xaml / .cs      # Windows 11 Settings UI (all 9 AppSettings)
│   └── FluentDialog.xaml / .cs      # Fluent confirm/info dialogs
├── Themes/
│   ├── Light.xaml                   # Light palette + Win11 control templates
│   ├── Dark.xaml                    # Dark palette
│   └── Fluent.xaml                  # Shared styles (buttons, menus, inputs, scrollbars)
└── tests/dQuiz.E2E/                 # 163 E2E tests + 20 DPI/Theme render checks
```

---

## 🚀 Getting Started

### Prerequisites
- **Windows 10/11**
- **.NET 8 SDK** ([download](https://dotnet.microsoft.com/download/dotnet/8.0))
- Visual Studio 2022 + **Desktop development with C#** workload (or VS Code + C# Dev Kit)

### Build & Run
```powershell
# Clone
git clone https://github.com/<your-username>/dQuiz.git
cd dQuiz

# Kill any running instance (locks the exe)
Stop-Process -Name dQuiz -Force -ErrorAction SilentlyContinue

# Build
dotnet build --nologo

# Run
dotnet run --project dQuiz.csproj
```

### Run E2E Tests (163 tests + 20 render captures)
```powershell
dotnet run --project tests\dQuiz.E2E\dQuiz.E2E.csproj --no-launch-profile
```

---

## 📁 Settings Location
All preferences persist to:
```
%LocalAppData%\dQuiz\settings.json
```

Example:
```json
{
  "Theme": "System",
  "Accent": "Teal",
  "Language": "en",
  "UiFont": "Segoe UI",
  "CanvasBackground": "Theme",
  "SmartGuides": true,
  "ShowNotes": false,
  "UiAnimations": true,
  "StartOnHome": true,
  "ShowQuizHud": true
}
```

---

## 🧪 Testing

The project includes a **zero-NuGet STA test harness** (`tests/dQuiz.E2E/`) with 163 tests across 5 tiers:

| Tier | Focus |
|------|-------|
| 1 | Theme switching, settings persistence, editor sharpness |
| 2 | Boundary conditions (empty slides, max elements, etc.) |
| 3 | Cross-feature (quiz + transitions + animations) |
| 4 | Real-world scenarios (create → edit → present → export) |
| 5 | Win32 maximize (rcWork), multi-DPI (100%/130%) RenderTargetBitmap captures |

---

## 🛣️ Roadmap (Post-M4)

- [ ] **PowerPoint (.pptx) import/export** via OpenXML
- [ ] **Slide master / layouts** editing
- [ ] **Collaboration** (real-time co-editing via SignalR)
- [ ] **Quiz analytics** dashboard (per-question stats, export CSV)
- [ ] **Cloud sync** for settings & recent files
- [ ] **Plugin system** for custom element types

---

## 🤝 Contributing

1. Fork the repo
2. Create a feature branch (`git checkout -b feat/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feat/amazing-feature`)
5. Open a Pull Request

**Code style**: Follow existing patterns — `DynamicResource` for theming, `UseLayoutRounding="False"` for text sharpness, Fluent UI control templates.

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

---

## 🙏 Acknowledgments

- **Fluent UI / Windows 11** design language inspiration
- **Segoe Fluent Icons** for iconography
- **WPF** for the rendering foundation
- Community feedback & testing

---

> Built with ❤️ for presenters, educators, and quiz masters who want PowerPoint-level polish in a hackable, open-source package.
