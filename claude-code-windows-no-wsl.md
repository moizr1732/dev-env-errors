# Claude Code Global Setup on Windows (Without WSL)

This guide explains how to use **Claude Code (`ccr`) globally on Windows** **without installing or using WSL**.

This is called **Solution B (Windows‑Only Setup)**.

---

## 📌 When Should You Use This Solution?

Use this solution if:
- You **do not want to install WSL**
- You prefer **pure Windows development**
- You are testing or doing light usage
- You want `ccr` to work in **every folder on Windows**

⚠️ This setup is **not recommended for heavy or production AI workflows**, but it works correctly.

---

## ❌ Common Problem (What Users Face)

Users see errors like:

```
ccr : The term 'ccr' is not recognized as the name of a cmdlet
```

Even after installing Claude Code.

This happens because:
- Node.js is missing OR
- Claude Code is not installed globally OR
- npm global path is not in Windows PATH

---

## ✅ Complete Step‑by‑Step Solution (Windows Only)

Follow **all steps in order**.

---

## Step 1: Install Node.js on Windows

1. Go to:
   https://nodejs.org
2. Download **LTS version**
3. Install with **default settings**
4. Restart your computer (important)

### Verify installation
Open **PowerShell** and run:

```powershell
node -v
npm -v
```

If versions appear → Node.js is installed correctly.

---

## Step 2: Install Claude Code Globally

In **PowerShell** (NOT inside WSL):

```powershell
npm install -g @anthropic-ai/claude-code
```

Wait until installation finishes.

---

## Step 3: Verify Claude Code Installation

Run:

```powershell
ccr --help
```

If help text appears → Claude Code is installed globally.

If it fails, continue to Step 4.

---

## Step 4: Fix npm Global PATH (Most Important Step)

Sometimes Windows does not automatically add npm global binaries to PATH.

### Find npm global path
Run:

```powershell
npm config get prefix
```

Usually it returns something like:

```
C:\Users\YourName\AppData\Roaming\npm
```

---

### Add npm path to Windows PATH

1. Press **Win + R** → type `sysdm.cpl` → Enter
2. Go to **Advanced** tab
3. Click **Environment Variables**
4. Under **User variables**, select `Path`
5. Click **Edit** → **New**
6. Paste the npm path
7. Click **OK** on all windows
8. Restart PowerShell

---

## Step 5: Confirm Global Availability

Run:

```powershell
where ccr
```

You should see a path like:

```
C:\Users\YourName\AppData\Roaming\npm\ccr.cmd
```

Now test:

```powershell
ccr start
```

✅ Claude Code now works in **any folder**.

---

## Step 6: Use Claude Code in VS Code

1. Open **VS Code** normally
2. Open **any folder** (Windows path is fine)
3. Open terminal (PowerShell)
4. Run:

```powershell
ccr start
```

No WSL required.

---

## ⚠️ Important Limitations (Be Honest)

- Some AI tools work better on Linux
- Windows paths may cause edge‑case bugs
- Docker & ML tooling is harder
- Slightly more PATH‑related issues

This is why WSL is recommended for advanced users.

---

## ✅ When This Solution Is Good

✔ Beginners
✔ Testing & learning
✔ Small projects
✔ No Linux knowledge

---

## ❌ When NOT to Use This Solution

✖ Production AI workflows
✖ Docker‑based projects
✖ Linux‑only tools
✖ Heavy automation

---

## 🧠 Key Takeaway

> Claude Code can be global on Windows **without WSL**,
> but the environment must be **fully Windows‑based**.

Mixing Windows + WSL is what causes most errors.

---

Happy coding 🚀

