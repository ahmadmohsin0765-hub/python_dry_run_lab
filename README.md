# Python Dry-Run Lab 🧪

> **Understand Python code one step at a time** by running it live in your browser and inspecting every mutation in memory.

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Real Execution](https://img.shields.io/badge/Python%20Engine-Pyodide%20WebAssembly-blue)

Python Dry-Run Lab is a **single-file web application** (HTML + CSS + vanilla JavaScript) with **zero build steps** and **no backend server required**. It executes user Python code entirely client-side using **Pyodide (WebAssembly)** inside a dedicated Web Worker and records a real, complete execution trace via Python's `sys.settrace`.

---

## ✨ Key Features

### 1. ⚙️ Real Execution Engine (Pyodide & Web Worker)
- **Real Python in WebAssembly:** Runs standard Python 3 in the browser with `sys.settrace`.
- **Worker Isolation:** Code runs in a background Web Worker so the user interface never freezes, and runaway loops can be cleanly terminated with the **⏹ Stop** button.
- **Microsecond Snapshots:** Captures step number, line number, event type (`line`, `call`, `return`, `exception`), call stack frames, local & global variables with memory `id()`, and accumulated standard output (`stdout`).
- **Input Simulation:** Automatically detects `input()` calls and provides an interactive pre-fill drawer for repeatable dry-runs.
- **Safety Limits:** Configurable step threshold (1,000, 5,000, 10,000) and a 5-second execution watchdog to detect infinite loops with line-specific diagnostic hints.

### 2. 🖥️ Clean 3-Zone Educational Layout
- **Left Zone — Code Editor:** CodeMirror 5 with Python syntax highlighting, line numbers, active line tracking, breakpoint gutter (click to toggle red dot `●`), executed line markers, and 10 built-in curated examples.
- **Center Zone — Visualisation & Time Travel:**
  - **Step Controls:** ⏮ First, ◀ Back, ▶ Next, ⏭ Last, ▶▶ Auto-play (with speed 0.25x – 4x), Run to next breakpoint, and Step Over / Into / Out.
  - **"What Just Happened" Banner:** Real-time plain-English explanations of each line's effect.
  - **Loop Tracker:** Live loop iteration badge and loop variable state.
  - **Variables Panel:** Name | Scope | Type | Value with smooth green flash animations on value changes, `NEW` tags, and `old → new` diffs.
  - **Call Stack:** Visual stacked frames displaying active functions, arguments, caller lines, and recursive depths.
  - **Memory & Aliasing Graph:** Exposes composite objects (lists, dicts, sets, class instances) with memory IDs (e.g. `0x10a4`) and pointers to visualize aliasing (e.g. two variable names pointing to the same list).
  - **Console Output:** Live accumulating standard output.
- **Right Zone — Tabbed Workspace:**
  1. **Dry-Run Table:** Exam-style step matrix with filters, CSV/Markdown export, and an interactive **"Test Yourself"** quiz mode.
  2. **Understand (AST Static Analysis):** Program outline, complexity Big-O hints, beginner anti-pattern warnings (mutable defaults, shadowing built-ins, `is` on literals), and an auto-generated SVG Control-Flow Diagram with active node illumination.
  3. **Explain (AI Tutor via Groq):** Optional Bring-Your-Own-Key (stored only in `sessionStorage`) for streaming line-by-line explanations, "Explain like I'm 12" analogies, and bug hints.
  4. **Metrics:** Step count, execution time, maximum stack depth, line coverage %, recursion risk detector, and inline SVG hotspot execution frequency chart.
  5. **Export & History:** URL hash sharing, JSON trace export, Markdown summary export, and session history.

### 3. ⚖️ Algorithmic Compare Mode
- Side-by-side comparison of two implementations (e.g., iterative vs. recursive factorial, or custom bubble sort vs. built-in sorting).
- Measures steps, execution time, and stack depth side-by-side with automatic winner determination.

---

## 🚀 Deploy to Vercel in 1 Minute

Because Python Dry-Run Lab is completely static with zero build steps, deploying to Vercel is instantaneous.

### Option A: Deploy via Vercel CLI
```bash
# 1. Install Vercel CLI (if not already installed)
npm i -g vercel

# 2. Deploy directly from the project directory
vercel
```

### Option B: Deploy via GitHub
1. Push this directory to your GitHub repository:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: Python Dry-Run Lab"
   git branch -M main
   git remote add origin https://github.com/<your-username>/python-dry-run-lab.git
   git push -u origin main
   ```
2. Go to [vercel.com/new](https://vercel.com/new).
3. Import your repository.
4. Leave **Build Command** empty (no build step) and **Output Directory** as `./`.
5. Click **Deploy**.

---

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
| :--- | :--- |
| <kbd>→</kbd> | Step forward (Next line) |
| <kbd>←</kbd> | Step backward (Time-travel to previous line) |
| <kbd>Space</kbd> | Toggle Auto-play / Pause |
| <kbd>B</kbd> | Toggle breakpoint on editor's current line |
| <kbd>Esc</kbd> | Stop execution / Pause auto-play |

---

## 🔒 Privacy & Security
- **100% Client-Side:** Python code is executed locally in your browser's WebAssembly sandbox.
- **No Data Collection:** Zero tracking, analytics, or external server telemetry.
- **BYOK (Bring Your Own Key):** The optional Groq API key is stored strictly in your browser's ephemeral `sessionStorage` and transmitted solely to Groq's official API.

---

## 📄 License
MIT License. Free and open source for students, teachers, and developers everywhere.
