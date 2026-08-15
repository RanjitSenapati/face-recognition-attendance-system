# 🎯 Face Recognition Attendance System

A real-time, end-to-end face recognition attendance system built with **Python + OpenCV + Jupyter Notebook**.

## ✨ Features

- ✅ Detects faces in real time using your webcam
- ✅ **Recognizes** registered individuals (not just "a face" — but *whose* face)
- ✅ Automatically logs **Entry Time**, **Exit Time**, **Date**, and **Total Hours**
- ✅ Prevents duplicate entries in a single session
- ✅ Exports attendance automatically to a formatted **Excel file**
- ✅ Includes a simple daily **dashboard** (attendance %, late arrivals, summary charts)
- ✅ Optional low-confidence alert so unregistered faces aren't marked present

## 🧠 How It Works (Pipeline)

```
Step 1: Register people   → capture ~60 face images per person (dataset/)
Step 2: Train recognizer  → train an LBPH model on those faces (trainer/)
Step 3: Run attendance    → webcam detects + recognizes faces live
Step 4: Auto-logging      → first detection = Entry, last seen = Exit
Step 5: Export            → attendance auto-saved to Excel (.xlsx)
Step 6: Dashboard         → view/analyze attendance stats
```

## 🛠️ Why LBPH instead of `face_recognition` / `dlib`?

`dlib` is powerful but notoriously painful to install on Windows (needs CMake + C++ build tools) and is slow to set up. This project uses OpenCV's built-in **LBPH Face Recognizer** (`opencv-contrib-python`), which:

- Installs with a single `pip install`, no compiler needed
- Runs fast enough for real-time webcam recognition
- Is accurate enough for attendance-style use cases (controlled, front-facing camera)

> 💡 Want higher accuracy later? The notebook is structured so you can swap in `face_recognition` (dlib-based) with minimal changes.

## 📁 Project Structure

```
face-recognition-attendance-system/
├── notebooks/
│   └── Face_Recognition_Attendance_System.ipynb   # main notebook (all steps)
├── dataset/               # captured face images, one subfolder per person (not tracked in git)
├── trainer/                # trained recognition model + label map (not tracked in git)
├── attendance_records/     # exported Excel attendance sheets (not tracked in git)
├── requirements.txt
├── .gitignore
└── README.md
```

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/face-recognition-attendance-system.git
cd face-recognition-attendance-system
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the notebook
```bash
jupyter notebook notebooks/Face_Recognition_Attendance_System.ipynb
```

Follow the steps inside the notebook in order:
1. Register each person's face
2. Train the recognizer
3. Run live attendance recognition
4. View the dashboard anytime to check records

Attendance is saved automatically to `attendance_records/Attendance_<Month>_<Year>.xlsx`, with one sheet per date containing **ID, Name, Date, Entry Time, Exit Time, Total Hours, Status**.

## 🧰 Tech Stack

- Python
- OpenCV (`opencv-contrib-python`) — face detection & LBPH recognition
- Pandas / OpenPyXL — attendance logging & Excel export
- Matplotlib — dashboard charts
- Jupyter Notebook

## 🚧 Going Further

Ideas to extend this project:

- Swap LBPH for the `face_recognition` (dlib) library for higher accuracy
- Add email/WhatsApp alerts for repeated "Unknown" face detections
- Wrap the dashboard in a **Streamlit** app for a shareable live view
- Add liveness/blink detection to prevent photo spoofing
- Support IP cameras (RTSP) for CCTV-based attendance
- Move from Excel to a SQLite/MySQL database for larger organizations
- Package into a Tkinter/PyQt desktop app for non-technical users

## 📌 Note

This project was built as part of my internship at **Central Tool Room and Training Centre (CTTC)**.

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
