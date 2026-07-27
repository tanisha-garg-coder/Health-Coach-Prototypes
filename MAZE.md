# Testing the myScout prototypes with Maze

The seven **Task N** prototypes in this repo are wired to run as isolated
[Maze](https://maze.co) usability missions. This guide covers how to host them,
grab the per-task URLs, and turn on tracking.

## What each prototype does for Maze

Every `Task N - *.dc.html` file is a self-contained chat prototype. Opened with
the query string **`?maze=1`** it:

- lands the participant **directly in the chat** for that one task,
- **pre-fills the task prompt** so they only have to hit send,
- **hides the scenario switcher** so the mission stays isolated, and
- shows a **“Task completed — continue in Maze”** banner once the task's answer
  is delivered — this is the moment a participant reaches the goal.

Each file also carries the **Maze universal tracking snippet** in its `<head>`,
so once you add your project API key, Maze records clicks, paths, and heatmaps
automatically.

## 1. Host the prototypes

Maze tests a **live URL**, so the files must be served over http(s) — they will
not run from `file://` because React is loaded from a CDN at runtime.

The simplest option is **GitHub Pages**:

1. Repo **Settings → Pages**.
2. **Source:** *Deploy from a branch*. Pick your branch and the repo **root**
   (`/`), then **Save**.
3. Wait for the build, then open `https://<owner>.github.io/<repo>/` — you'll
   land on `index.html`, the mission launcher.

Any static host (Netlify, Vercel, S3, an internal server) works too — just serve
the repo root so `support.js`, `image-slot.js`, and the `_ds/` design-system
folder sit alongside the HTML files.

## 2. Add your Maze API key

Open each `Task N - *.dc.html` file, find the `MAZE TRACKING` block near the top,
and replace the placeholder with your project's key:

```js
// before
})(window, document, 'https://snippet.maze.co/maze-universal-loader.js', 'PASTE-YOUR-MAZE-PROJECT-API-KEY');
// after
})(window, document, 'https://snippet.maze.co/maze-universal-loader.js', 'a1b2c3d4-....');
```

Find the key in Maze under **Project settings** (or the **Snippet** block when
you add a *code / live-website* prototype). The snippet is safe to ship with the
placeholder — with no real key the loader simply no-ops.

## 3. Mission URLs

Point each Maze mission at the matching URL. Replace `BASE` with your hosted root
(e.g. `https://<owner>.github.io/<repo>`). Spaces in the filenames are
URL-encoded as `%20`.

| Task | Prototype | Mission URL |
|------|-----------|-------------|
| 1 | Diabetes basics | `BASE/Task%201%20-%20Diabetes%20Basics.dc.html?maze=1` |
| 2 | Metformin | `BASE/Task%202%20-%20Metformin.dc.html?maze=1` |
| 3 | Diet changes | `BASE/Task%203%20-%20Diet%20Changes.dc.html?maze=1` |
| 4 | Insurance programs | `BASE/Task%204%20-%20Insurance%20Programs.dc.html?maze=1` |
| 5 | Manage stress | `BASE/Task%205%20-%20Manage%20Stress.dc.html?maze=1` |
| 6 | Depression symptoms | `BASE/Task%206%20-%20Depression%20Symptoms.dc.html?maze=1` |
| 7 | Crisis escalation | `BASE/Task%207%20-%20Escalation.dc.html?maze=1` |

The hosted `index.html` builds these links for you — open it and copy the link
from each card.

## 4. Deep-link reference

All prototypes understand the same query params, so you can also compose flows
that differ from a file's own task:

| Param | Effect |
|-------|--------|
| `?maze=1` | Launch **this file's own task** (recommended for missions). |
| `?task=1` … `?task=7` | Launch **any** task by number, from any file. |
| `?test=1` / `?test=2` | Launch a full multi-task flow in one chat (Test 1 = diabetes 1→4, Test 2 = stress → depression → crisis). |
| *(none)* | Demo mode — opens on the Explore screen with the scenario switcher available. |

`?screen=chat` / `?screen=explore` can override the starting screen in demo mode.

## Task ↔ scenario map

| Task | Scenario id | Topic |
|------|-------------|-------|
| 1 | `task1` | Type 2 diabetes diagnosis / daily life |
| 2 | `task2` | Metformin |
| 3 | `task3` | Diet changes |
| 4 | `task4` | Insurance programs & benefits |
| 5 | `task5` | Managing stress |
| 6 | `task6` | Depression symptoms |
| 7 | `task7` | Crisis escalation (988 Lifeline) |

## Measuring success in Maze

Because the flow is scripted, the reliable goal signal is the **“Task completed
— continue in Maze”** banner. In your mission, treat reaching that state (the
final answer screen) as the success screen, or use a Maze **success screen** /
follow-up question block right after it.

## Note on the `maze/` folder

`maze/myscout-diabetes.html` and `maze/myscout-stress.html` are older
**single-file exports** (all assets inlined). They predate this Maze wiring — no
`?maze=1` launcher and no tracking snippet — so prefer the seven `Task N` files
above for testing. Keep the bundles only if you specifically need a
dependency-free single file.
