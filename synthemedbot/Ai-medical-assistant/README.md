# SyntheMedBot — Medical Image Education Prototype

A small Streamlit/Python experiment that accepts a user-selected medical image and requests an image-based explanation from Google's Gemini API.

> **Medical safety:** Educational prototype only. It is not a medical device, diagnostic system or substitute for a qualified clinician. AI-generated content may be incorrect or incomplete. Do not use it to make treatment decisions or delay urgent care.

## Current implementation

The inspected app.py builds a Streamlit interface, accepts PNG/JPG/JPEG uploads, sends the image and a fixed prompt to a configured Gemini model, and displays generated text. This is an exploratory single-page prototype; it does not demonstrate clinical validation or secure clinical workflow integration.

## Local setup

Requirements: Python 3.10+ and a Gemini API key. Verify the selected SDK/model combination before deployment.

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

Credentials must stay in the local .env file and must never be committed. The tracked apikey.py file intentionally contains no credential. A key-like value was found in earlier Git content; revoke/rotate it with Google AI Studio because removing a value from the latest file does not erase it from Git history.

## Known limitations

- The code uses a fixed Gemini model identifier; confirm that it is available to your API project and SDK version.
- Uploaded image bytes are sent with a JPEG MIME type even for PNG uploads. Derive MIME type from the actual file.
- Add graceful handling for missing credentials, quota errors, unsupported files and model failures.
- Add upload size limits, validation, tests and a documented privacy/retention policy.
- Avoid medical-practitioner role prompts and treatment recommendations. Restrict responses to cautious educational explanations and encourage consultation with qualified clinicians.

## Files

- app.py — Streamlit application
- requirements.txt — Python dependencies
- .env.example — safe environment template
- ai-assistant--that--looks-like--nurse.png / .ico — UI assets

Pavan Kumar — [GitHub](https://github.com/kumar0745) · [LinkedIn](https://www.linkedin.com/in/pavan-kumar-1803a128b/)
