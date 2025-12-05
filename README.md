# Hand-Gesture-Output

Short instructions to set up the environment and run this repository's notebook (`main.ipynb`). These steps are written for Windows PowerShell users but include cross-platform alternatives where useful.

**Contents**
- **Prerequisites**: Python and basic tools
- **Create virtual environment**: steps for PowerShell and other shells
- **Install dependencies**: install from `requirements.txt`
- **Run the notebook**: open in Jupyter or VS Code
- **Troubleshooting**: common fixes for OpenCV / webcam and activation issues

**Prerequisites**
- Python 3.8–3.11 recommended. This repository was tested with Python 3.10+.
- `git` (optional) to clone the repo.
- A webcam (if the notebook uses live camera input).

If you do not have Python installed, download it from https://www.python.org/ and make sure `python` is on your PATH.

**Install (Windows PowerShell)**

Open PowerShell in the project folder (where `main.ipynb` and `requirements.txt` live).

1) Create a virtual environment

```powershell
python -m venv .venv
```

2) Activate the virtual environment (PowerShell)

```powershell
# For PowerShell
.\.venv\Scripts\Activate.ps1

# If activation is blocked by execution policy, run as Administrator or set for current user:
# Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Alternative activation commands:
- Command Prompt (cmd.exe): `\.venv\Scripts\activate.bat`
- Git Bash / WSL / macOS / Linux: `source .venv/bin/activate`

3) Install dependencies

```powershell
pip install --upgrade pip
pip install -r requirements.txt
```

The `requirements.txt` in this repository contains the exact packages used during development, for example:

```
mediapipe==0.10.14
opencv-python==4.12.0.88
opencv-contrib-python==4.12.0.88
numpy==2.2.6
matplotlib==3.10.7
# (and others — see `requirements.txt` for full list)
```

If installation fails due to binary wheels (for example with `opencv` or `mediapipe`), try upgrading `pip` and `wheel`, or consult the package's platform-specific install docs.

**Run the project**

Option A — Jupyter Notebook (recommended for exploring `main.ipynb`):

```powershell
jupyter notebook main.ipynb
```

Option B — VS Code: open the repository folder, install the Python and Jupyter extensions, then open `main.ipynb` and select the `.venv` kernel.

Option C — Execute the notebook headlessly (will run all cells):

```powershell
pip install nbconvert
jupyter nbconvert --to notebook --execute main.ipynb --output executed.ipynb
```

Notes:
- If the notebook accesses your webcam, allow camera access and ensure no other app is using it.
- If you see a blank image or camera error, try switching camera index values in the notebook or test the webcam with a simple OpenCV script.

**Troubleshooting**
- Activation errors: If `Activate.ps1` is blocked, set execution policy for current user: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` (you may need to run PowerShell as Administrator to change system-wide policy).
- OpenCV cannot open camera: make sure the camera index is correct and other programs (Zoom, Teams) are not using the camera.
- Mediapipe errors: Mediapipe can be sensitive to platform and Python version; if you get build errors, ensure you use a supported Python version and install the prebuilt wheel with pip.
- If a package fails to install because of missing build tools, install the Visual C++ Build Tools (Windows) or appropriate compiler for your OS.

**Next steps (choose one)**
- Run `main.ipynb` locally (recommended).
- Ask me to create a small runnable Python script that runs the same pipeline as the notebook.
- Ask me to create a `requirements.lock` or a Dockerfile to make the environment reproducible.

If you want, I can also run a quick environment check and report any missing packages.

---
Project structure (top-level):

- `main.ipynb` — primary notebook to run.
- `requirements.txt` — Python dependencies used by the project.

If anything in these instructions doesn't work for you, tell me what OS and Python version you're using and I'll help debug.
