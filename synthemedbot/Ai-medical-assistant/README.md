# SyntheMedBot — Medical Image Education Prototype

A small Streamlit/Python experiment that accepts a user-selected medical image and requests an image-based explanation from Google's Gemini API.

> **Medical safety:** This is an educational prototype only. It is not a medical device, diagnostic system or substitute for a qualified clinician. AI-generated content may be incorrect or incomplete. Never use it to make treatment decisions or delay urgent care.

## Current implementation

The inspected application entry point is app.py. It builds a Streamlit interface, accepts PNG/JPG/JPEG uploads, sends the image and a fixed prompt to a configured Gemini model, and displays generated text. This is an exploratory single-page prototype; it does not demonstrate clinical validation or secure clinical workflow integration.

## Requirements

- Python 3.10+ (verify compatibility with the selected Google SDK version)
- A Gemini API key configured locally in .env as api_key1 (see .env.example)

## Setup

From this directory:

Windows PowerShell:

```powershell
python -m venv .venv
.\\.venv\\Scripts\\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
Copy-Item .env.example .env
# Edit .env and set api_key1 to your rotated Gemini key
streamlit run app.py
```

macOS/Linux:

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
cp .env.example .env
# Edit .env and set api_key1 to your rotated Gemini key
streamlit run app.py
```

The application must read credentials from the environment. Never put a key in apikey.py, source code, notebooks, screenshots or commits. If a credential has ever been committed, revoke/rotate it with the provider; deleting it from the latest file does not remove it from Git history.

## Known limitations and recommended fixes

- The code currently requests a fixed model identifier; verify that it is supported by the installed SDK and your API project.
- Image bytes are sent with a JPEG MIME type even when a PNG is uploaded. Derive MIME type from the actual upload.
- Add graceful handling for missing credentials, quota errors, unsupported files and model failures.
- Add file-size limits, input validation and safe error messages.
- Do not prompt the model to act as a medical practitioner or issue treatment recommendations. Restrict responses to cautious educational explanations and direct users to qualified clinicians.
- Add tests and a documented privacy/retention policy before public deployment.

## Repository contents

- app.py — Streamlit application
- requirements.txt — Python dependencies
- ai-assistant--that--looks-like--nurse.png / .ico — UI assets

## Author

Pavan Kumar — [GitHub](https://github.com/kumar0745) · [LinkedIn](https://www.linkedin.com/in/pavan-kumar-1803a128b/)
