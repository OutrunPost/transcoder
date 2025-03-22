# 🎞️ Watchfolder Transcoder for macOS

A lightweight Bash-based transcoding system for macOS that watches designated input folders and automatically transcodes videos to Apple ProRes using FFmpeg and VideoToolbox. 
Includes native macOS notifications, live queue monitoring in Terminal, and organized logging.

---

## 🔧 Prerequisites

Make sure the following are installed and configured before running the script:

### ✅ macOS Environment
- Tested on **macOS Monterey, Ventura, and Sonoma**
- Terminal access and basic shell knowledge

### ✅ FFmpeg (with VideoToolbox support)

You need FFmpeg installed and compiled with `--enable-videotoolbox` for hardware-accelerated ProRes encoding.

To install via Homebrew:

```bash
brew install ffmpeg
```

To check if VideoToolbox is supported:

```bash
ffmpeg -encoders | grep videotoolbox
```

You should see entries like `prores_videotoolbox`.

---

## 🚀 Features

- 🖥️ **macOS-native notifications** (start, finish, errors)
- 🎛️ **Live terminal dashboard** showing queue and status
- 🗂️ Supports 3 separate input folders:
  - `Input_30fps` → Forces 30fps output
  - `Input_60fps` → Forces 60fps output
  - `Input_Native` → Preserves source framerate
- 📁 Clean folder structure with Output and Processed directories
- 📝 Per-folder logging and real-time `.current_task.txt` tracking
- 💨 Hardware-accelerated encoding using `prores_videotoolbox`

---

## 📂 Folder Structure

Place the script inside this directory structure (auto-created on first run):

```
_Transcoder/
├── Input_30fps/          # Drop files here to force 30fps transcode
├── Input_60fps/          # Drop files here to force 60fps transcode
├── Input_Native/         # Drop files here to preserve source FPS
├── Output/               # All exported ProRes files go here
├── Processed/            # Source files moved here after successful encode
└── Logs/
    ├── log_30fps.txt
    ├── log_60fps.txt
    ├── log_native.txt
    ├── log_errors.txt
    └── current_task.txt
```

---

## ⚙️ Setup

1. Place `watchfolder.sh` in your project or scripts folder.
2. Make it executable:
```bash
chmod +x watchfolder.sh
```
3. Run it:
```bash
./watchfolder.sh
```
4. The script will launch a new Terminal window automatically and begin monitoring.

---

## 🔔 Notifications

The script uses `osascript` to trigger native macOS notifications:
- ✅ Start / Finish alerts
- ❌ Error alerts (with sound)

---

## 📈 Live Terminal Dashboard

While running, the terminal window will display:

- Current timestamp
- Queued files per folder
- Currently processing file (if any)
- Status updates for each operation

---

## 🧪 Customization

You can easily tweak:
- Frame rate targets
- Output codec
- Log formatting
- Add more input folders for different profiles
- Replace `prores_videotoolbox` with other FFmpeg codecs

---

## 📦 Future Ideas

- Add a menu bar toggle or GUI front-end (SwiftUI or Electron)
- Add email or webhook alerts
- Support for H.264, Proxy, and other export formats

---

## 🧑‍💻 Author

Made by [Outrun Post LLC]  
🎛️ Optimized for audio/video workflows on macOS

---

## 📄 License

MIT License — free to use and modify.

---
