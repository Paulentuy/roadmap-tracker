# 🚀 Roadmap Tracker

A single-file, zero-dependency HTML roadmap tracker that an AI assistant (Claude) keeps up to date for you. Click checkboxes to mark tasks done; ask Claude to add tasks, reorder stages, and check things off as your project moves forward.

*Однофайловый трекер дорожной карты на чистом HTML, без зависимостей. Claude поддерживает его в актуальном состоянии: отмечает сделанное, добавляет задачи, переставляет этапы.*

![one HTML file · works offline · dark mode · saves in your browser]

---

## ✨ What you get / Что внутри

- **`roadmap-tracker.html`** — the tracker. Open it in any browser. Collapsible stages, per-stage and overall progress bars, checkboxes, auto dark mode. State is saved in your browser via `localStorage`.
- **`CLAUDE_INSTRUCTIONS.md`** — copy-paste instructions for your Claude project so the assistant updates the tracker automatically.

No build step, no server, no npm. It's one file. / Никакой сборки, сервера или npm — это один файл.

---

## 🏁 Quick start / Быстрый старт

1. **Download / Скачай** `roadmap-tracker.html` (Code → Download ZIP, or clone this repo).
2. **Open it / Открой** — double-click the file, it opens in your browser.
3. **Customize / Настрой** — edit the project name, stages, and tasks (see below), or just ask Claude to do it.
4. **Connect Claude / Подключи Claude** — follow “Use it with Claude” below.

> 💡 Tip: keep the file in a folder you've connected to Claude (a **Cowork** folder, or a **Project** with the file attached) so Claude can edit it directly.

---

## 🤖 Use it with Claude / Подключение к Claude

The tracker is designed to be edited by Claude as your project evolves. To make Claude do this automatically:

**English**
1. Put `roadmap-tracker.html` in a folder Claude can access — in **Claude Desktop / Cowork**, connect the folder; or in a **Claude Project**, attach the file.
2. Open `CLAUDE_INSTRUCTIONS.md`, copy the whole block, and paste it into your **Project instructions** (Project → *Edit* → *Instructions*) — or just paste it into the chat at the start of a session.
3. From then on, when you tell Claude “I finished X” or “add a task for Y,” it edits the file: marks tasks done, adds new ones, and bumps the version so your view refreshes.

**Русский**
1. Положи `roadmap-tracker.html` в папку, к которой у Claude есть доступ — в **Claude Desktop / Cowork** подключи папку; или в **проекте Claude** прикрепи файл.
2. Открой `CLAUDE_INSTRUCTIONS.md`, скопируй весь блок и вставь в **инструкции проекта** (Проект → *Редактировать* → *Инструкции*) — или просто вставь в начало чата.
3. Дальше, когда говоришь Claude «я закончил X» или «добавь задачу Y», он сам правит файл: отмечает сделанное, добавляет новое и поднимает версию, чтобы вид обновился.

---

## ✏️ Edit by hand / Правка вручную

You don't need Claude — you can edit the HTML directly.

### Add a task / Добавить задачу
Copy this line into a stage's `<div class="stage-body-inner">`. **`data-task` must be unique** across the whole file:

```html
<div class="task" data-task="s2-darkmode"><div class="task-checkbox"></div><div class="task-content"><div class="task-title">Dark mode<span class="task-difficulty">low</span></div><div class="task-note">optional note</div></div></div>
```

- Mark it done → add ` done`: `<div class="task done" data-task="...">`
- The `<span class="task-difficulty">` and `<div class="task-note">` are optional.

### Add a stage / Добавить этап
Copy a whole `<div class="stage stage-N" data-stage="N"> … </div>` block. The number after `stage-` sets the color stripe:

| class | color |
|-------|-------|
| `stage-1` | green |
| `stage-2` | yellow |
| `stage-25` | teal |
| `stage-3` | orange |
| `stage-4` | red |
| `stage-5` | purple |
| `stage-6` | brown |

Add `expanded` to the stage div to have it open by default.

### The version trick / Трюк с версией
Your checkbox clicks are stored in the browser. When the file's `data-version` changes, those local clicks are wiped and the statuses written in the file become the source of truth. So whenever you (or Claude) edit task statuses in the file, **bump `data-version`** on the `<html>` tag:

```html
<html lang="en" data-version="2" data-last-updated="2026-02-15">
```

---

## 📄 License

MIT — do whatever you like. See `LICENSE`.

*Made from a roadmap tracker built with Claude. Fork it and make it yours.*
