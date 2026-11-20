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

## 🚀 Getting Started

### Prerequisites
- **Windows 10/11**
- **.NET 8 SDK** ([download](https://dotnet.microsoft.com/download/dotnet/8.0))
- Visual Studio 2022 + **Desktop development with C#** workload (or VS Code + C# Dev Kit)

---
---

## 🛣️ Roadmap (Post-M4)

- [ ] **PowerPoint (.pptx) import/export** via OpenXML
- [ ] **Slide master / layouts** editing
- [ ] **Collaboration** (real-time co-editing via SignalR)
- [ ] **Quiz analytics** dashboard (per-question stats, export CSV)
- [ ] **Cloud sync** for settings & recent files
- [ ] **Plugin system** for custom element types

---

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
