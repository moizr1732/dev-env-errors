# Claude Code Not Working Globally in VS Code (WSL Issue)

## 📌 Problem Statement

Many users face an issue where **Claude Code (`ccr`) works only in one specific folder**, but when they change the folder or open a new project in VS Code, the command stops working and shows errors like:

```
ccr : The term 'ccr' is not recognized as the name of a cmdlet, function,
script file, or operable program
```

This makes it look like **Claude Code is not installed globally**, even though it works perfectly in one folder.

---

## ❌ Why This Problem Happens (Root Cause)

This issue is **not caused by Claude Code**, and **not caused by npm**.

The real reason is a **Windows + WSL + VS Code mismatch**:

- Claude Code was installed **inside WSL (Linux)**
- VS Code was opening folders in **Windows mode**
- When you change folders, VS Code silently switches back to Windows
- Windows cannot see Linux commands like `ccr`

So:
- ✅ Folder opened in WSL → `ccr` works
- ❌ Folder opened in Windows → `ccr` not found

This makes it *appear* that Claude Code is not global, when in reality **VS Code is in the wrong environment**.

---

## ✅ The Correct Solution (Permanent Fix)

To make Claude Code work **in every folder**, VS Code must always run **inside WSL**.

Follow the steps below **exactly**.

---

## 🛠 Step-by-Step Solution

### Step 1: Make Sure WSL Is Installed

Open **PowerShell** and run:

```powershell
wsl --status
```

If WSL is installed, you are good to continue.

---

### Step 2: Install the WSL Extension in VS Code (MANDATORY)

1. Open **VS Code**
2. Press `Ctrl + Shift + X` (Extensions)
3. Search for:
   ```
   WSL
   ```
4. Install **WSL by Microsoft**
   - Publisher: Microsoft
   - Extension ID: `ms-vscode-remote.remote-wsl`

⚠️ Without this extension, Claude Code will NEVER work globally.

---

### Step 3: Reload VS Code

After installing the extension:

1. Press `Ctrl + Shift + P`
2. Run:
   ```
   Developer: Reload Window
   ```

---

### Step 4: Open Your Project in WSL (This Is the Most Important Step)

1. Press `Ctrl + Shift + P`
2. Select:
   ```
   WSL: Open Folder in WSL
   ```
3. Choose a Linux folder such as:
   ```
   /home/username/projects/my-project
   ```

❌ Do NOT open folders like:
```
C:\Users\YourName\Desktop\project
```

---

### Step 5: Confirm VS Code Is Running in WSL

Look at the **bottom-left corner** of VS Code.

It MUST say:
```
WSL: Ubuntu
```

If it says:
```
Windows
```
then `ccr` will not work.

---

### Step 6: Run Claude Code

Open the VS Code terminal and run:

```bash
ccr start
```

Now Claude Code will run correctly.

---

## ✅ Result (Problem Solved)

After following these steps:

- ✅ `ccr` works in **every folder**
- ✅ Claude Code is truly **global**
- ✅ No more "command not found" errors
- ✅ VS Code and WSL stay perfectly synced

---

## 📁 Recommended Project Structure

For best results, keep all projects inside WSL:

```
/home/username/projects/
  ├── project1
  ├── project2
  └── project3
```

Always open projects using **WSL: Open Folder in WSL**.

---

## 🧠 Key Takeaway

> Claude Code was never the problem.
> The issue was VS Code running in Windows instead of WSL.

Once VS Code is properly connected to WSL, **Claude Code works globally and reliably**.

---

## ⭐ Final Notes

If Claude Code works in one folder but not another:
- Check the **bottom-left corner** of VS Code
- Make sure it says **WSL: Ubuntu**

This single check prevents hours of confusion.

---

Happy coding 🚀

