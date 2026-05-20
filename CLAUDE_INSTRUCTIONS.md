# Claude project instructions / Инструкции для проекта Claude

Copy **everything inside the box below** into your Claude project instructions
(Project → Edit → Instructions), or paste it at the start of a chat session.
Then keep `roadmap-tracker.html` in a folder Claude can read and write.

Скопируй **весь текст в рамке ниже** в инструкции проекта Claude
(Проект → Редактировать → Инструкции) или вставь в начало чата.
И держи `roadmap-tracker.html` в папке, доступной Claude на чтение/запись.

---

```
ROADMAP TRACKER — rules for Claude / правила для Claude

There is a file `roadmap-tracker.html` in this project — a visual roadmap
tracker I open in my browser. It is the single source of truth for project
progress. Keep it up to date for me. / Это визуальный трекер прогресса,
единый источник правды. Поддерживай его в актуальном состоянии.

Whenever ANY of these happen, update `roadmap-tracker.html` immediately:
Каждый раз, когда происходит любое из этого — сразу обнови файл:
- I finish a task                → mark it done.
- I mention a new idea or task   → add it to the right stage (even a passing
  "it'd be nice to…" — capture it).
- I want to reprioritize         → move tasks/stages, or add a new stage.
- The project version changes    → update it in the header.

HOW TO EDIT / КАК ПРАВИТЬ:
1. Mark a task done: change  class="task"  →  class="task done"  for that task.
   (To un-do, remove " done".)
2. Add a task: copy this line into the target stage's <div class="stage-body-inner">.
   data-task MUST be unique across the whole file (e.g. "s2-darkmode"):
   <div class="task" data-task="UNIQUE-ID"><div class="task-checkbox"></div><div class="task-content"><div class="task-title">Title<span class="task-difficulty">low</span></div><div class="task-note">optional note</div></div></div>
   The task-difficulty span and task-note div are optional.
3. Add a stage: copy a whole <div class="stage stage-N" data-stage="N">…</div>
   block; N (1–6) sets the color stripe. Add "expanded" to open it by default.
4. ALWAYS bump data-version on the <html> tag by +1 after editing statuses
   (this resets my local browser clicks and shows the true statuses from the file).
5. ALWAYS set data-last-updated="YYYY-MM-DD" to today.
6. Update the version label in the header if the project version changed.

Do this in addition to any other work, without being asked again each time.
Делай это автоматически, не переспрашивая каждый раз.
```

---

### Notes / Примечания

- The `data-version` bump is important: it's how the file (not the browser cache) becomes the source of truth. Always increment it when you change task statuses. / Поднятие `data-version` обязательно — так файл, а не кэш браузера, становится источником правды.
- `data-task` IDs must be unique. A convention that works well: `s<stage>-<short-name>`, e.g. `s2-darkmode`, `s3-billing`. / ID задач должны быть уникальны. Удобный формат: `s<этап>-<имя>`.
- If you reorder stages, keep each task's `data-task` ID stable so state stays consistent. / При перестановке этапов сохраняй ID задач неизменными.
