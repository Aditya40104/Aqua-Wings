# Aqua Wings

Aqua Wings is a Python computer-vision project that runs a Roboflow model (`aqua-wings/2`) for drowning-person detection.

## 1) Clone the project

```powershell
git clone <your-repo-url>
cd aqua-wings
```

If you already have the folder, just open it:

```powershell
cd C:\Users\shivn\OneDrive\Desktop\aqua-wings
```

## 2) Create virtual environment (Python 3.12 recommended)

```powershell
py -3.12 -m venv .venv
```

## 3) Activate virtual environment

PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

If activation is blocked by policy:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\.venv\Scripts\Activate.ps1
```

## 4) Install packages

```powershell
python -m pip install --upgrade pip
python -m pip install opencv-python numpy inference-sdk dronekit future
```

## 5) Run the programs

### A) Video file detection (Roboflow on prerecorded video)

```powershell
python video.py
```

- Input video in current code: `output_video.mp4`
- Press `q` to close display window.

### B) Webcam real-time detection

```powershell
python esp.py
```

- Uses camera index `0` (`cv2.VideoCapture(0)`).
- Press `q` to close display window.

### C) Images folder to video conversion

```powershell
python imgtovideo.py
```

- Current script expects a folder named `imgtovideo` in project root.
- Put `.png/.jpg/.jpeg` files there before running.

### D) Drone navigation script

```powershell
python dronenav.py
```

Notes:
- Requires compatible DroneKit + MAVLink/Pixhawk setup.
- On many modern Python versions, DroneKit may still need compatibility fixes.
- Requires camera and Roboflow API connectivity.

## 6) Run without activation (optional)

```powershell
.\.venv\Scripts\python.exe video.py
.\.venv\Scripts\python.exe esp.py
.\.venv\Scripts\python.exe imgtovideo.py
.\.venv\Scripts\python.exe dronenav.py
```

## 7) Common troubleshooting

### OpenCV window error (`cv2.imshow` not implemented)

Install full OpenCV package (not headless):

```powershell
python -m pip uninstall -y opencv-python-headless
python -m pip install --upgrade opencv-python
```

### Camera light stays on

Stop all Python processes:

```powershell
Get-Process python,python3,py -ErrorAction SilentlyContinue | Stop-Process -Force
```

### `inference_sdk` import error

Usually wrong interpreter is being used. Verify you are in `.venv`:

```powershell
python -c "import sys; print(sys.executable)"
```

## 8) Deactivate environment

```powershell
deactivate
```
