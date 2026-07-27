# Testing the myScout prototypes in Maze

This repo holds interactive **myScout** chat prototypes built as Claude Design
components (`Task N - ….dc.html`). This guide explains how to run them as
[Maze](https://maze.co) usability tests.

A Maze test needs a **live, public URL** it can load. These prototypes are plain
static files (HTML + JS + CSS + fonts), so the simplest host is **GitHub Pages**,
which is already wired up in this repo.

---

## 1. Publish the prototypes (one-time setup)

1. Push to `main` (or the working branch). The
   [`Deploy prototypes to GitHub Pages`](.github/workflows/deploy-pages.yml)
   workflow auto-enables Pages (GitHub Actions build type) on its first run and
   publishes the whole repo as-is.
   - *Fallback:* if your org blocks workflows from enabling Pages, turn it on
     manually once via **Settings → Pages → Build and deployment → Source →
     “GitHub Actions”**, then re-run the workflow.
2. Your site base URL will be:

   ```
   https://<owner>.github.io/<repo>/
   ```

   e.g. `https://tanisha-garg-coder.github.io/health-coach-prototypes/`

Notes:
- `.nojekyll` is committed so the `_ds/` design-system folder (fonts, CSS, JS)
  is served — Jekyll would otherwise skip underscore-prefixed folders.
- The prototypes load React from a public CDN at runtime, so test devices need
  normal internet access. (No corporate-VPN-only assets.)
- This is a **public** site. It contains only synthetic demo content — keep it
  that way; never put real member data in a prototype you publish here.

**Launcher page:** once published, open
`https://<owner>.github.io/<repo>/maze/` for a click-to-copy list of every
task URL below.

---

## 2. Task entry points (deep links)

Each prototype reads a query parameter and drops the participant **straight into
the chat**, with the task's question pre-filled, the scenario bar hidden, and the
matching scripted answer ready. Point each Maze block/mission at the URL for that
task (append to your Pages base URL; spaces encode as `%20`):

### Diabetes study
| Task | URL suffix |
|------|-----------|
| 1 · Diabetes basics       | `Task 1 - Diabetes Basics.dc.html?task=1` |
| 2 · Metformin             | `Task 2 - Metformin.dc.html?task=2` |
| 3 · Diet changes          | `Task 3 - Diet Changes.dc.html?task=3` |
| 4 · Insurance / programs  | `Task 4 - Insurance Programs.dc.html?task=4` |
| Full flow (all 4, one chat) | `Task 1 - Diabetes Basics.dc.html?test=1` |

### Stress & mental-health study
| Task | URL suffix |
|------|-----------|
| 5 · Manage stress       | `Task 5 - Manage Stress.dc.html?test=2` |
| 6 · Depression symptoms | `Task 6 - Depression Symptoms.dc.html?test=2` |
| 7 · Crisis escalation   | `Task 7 - Escalation.dc.html?test=2` |

> The stress tasks use `?test=2` (not `?task=`). The prototype matches the
> pre-filled question to the right scripted answer by keyword, so each stress
> file surfaces its own task response.

`?task` / `?test` also switch the prototype into **Maze mode**, which hides the
in-canvas scenario switcher so participants see only the real UI.

---

## 3. How Maze knows a task is complete

When the AI's scripted answer for a task appears, the prototype does two things:

1. **Adds `#task-complete` to the URL** (e.g. `…?task=1#task-complete`).
2. Posts a `{ type: "maze-task-complete" }` message to a parent frame, if any.

Use whichever your Maze plan supports:

- **URL / success-screen match** — set the mission's success condition to a URL
  that **contains `task-complete`**. Maze marks the task done automatically when
  the answer lands.
- **Observed completion** — the chat also shows a visible
  *“Task completed — continue in Maze”* divider, so moderated sessions and
  screen recordings have an unambiguous end-of-task marker.

These signals only fire on a deep-linked (`?task` / `?test`) session — they never
run in the Claude Design canvas or the Explore demo.

---

## 4. Optional: Maze tracking snippet

For Maze's click/heatmap analytics you can paste your workspace's Maze snippet
into each prototype. Every `Task N - ….dc.html` has a marked slot inside
`<helmet>`:

```html
<!-- MAZE TRACKING: paste your Maze snippet on the next line (keep it inside <helmet>
<title>myScout — Diabetes chat prototype</title>). -->
```

Paste the `<script>…</script>` Maze gives you on the line below that comment.
It's optional — URL/success-screen tracking (section 3) works without it.

---

## 5. Pacing

The AI "thinks" for ~1.4s before answering (the `typingDelay` prop). Give Maze
missions a little headroom so participants aren't scored as failing while the
answer is still typing.
