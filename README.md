# Prompt2Video AI — free starter

A small local web app that turns a text prompt into a five-scene, 720p text-led MP4 with optional Hindi/English AI narration.

## Honest limitations
- This is **not** photorealistic text-to-video generation. It creates animated-style scene cards with a gradient background and text.
- Voice uses the free Edge TTS endpoint and therefore requires internet; availability and service terms can change.
- No API key is required. There are no usage guarantees or unlimited cloud GPU resources.
- This starter runs on your computer. It is not publicly hosted.

## Requirements
- Python 3.10+
- Internet connection for voice generation
- A computer (Windows, macOS, or Linux). Android-only hosting is not covered by this starter.

## Run on Windows
1. Install Python from https://www.python.org/downloads/ and enable "Add Python to PATH".
2. Extract the ZIP.
3. Open Command Prompt in the extracted `prompt2video_ai` folder.
4. Run:
   ```bash
   python -m venv venv
   venv\\Scripts\\activate
   pip install -r requirements.txt
   python app.py
   ```
5. Open http://127.0.0.1:5000

## Run on macOS / Linux
```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python app.py
```
Then open http://127.0.0.1:5000

## Project structure
- `app.py` — Flask backend, storyboard, voice generation, FFmpeg export
- `templates/` — web pages
- `static/style.css` — responsive dark UI
- `outputs/` — generated MP4 files
- `work/` — temporary scene and audio files

## Production notes
Before public deployment, add user authentication, rate limits, file cleanup, CSRF protection, upload validation, a task queue, and storage quotas. Do not expose Flask debug mode or the development server publicly. Check the voice provider's current terms before commercial use.


## Deploy from an Android phone (GitHub + Render)
1. Download and extract this ZIP using your phone's Files app.
2. Open GitHub in Chrome, create a new public repository named `prompt2video-ai`.
3. Use GitHub's **Add file → Upload files** to upload the contents of this folder (not the ZIP itself). Commit the files.
4. Open Render in Chrome and sign in with GitHub.
5. Choose **New → Web Service**, connect `prompt2video-ai`.
6. Use Build Command: `pip install -r requirements.txt`
7. Use Start Command: `gunicorn app:app`
8. Choose the free instance if offered, then deploy. Open the Render URL after deployment.

Important: free hosting may sleep, have CPU/time limits, and temporary files may disappear after restarts. This starter is a text-card video maker, not realistic AI footage generation. Public deployment needs rate limiting, file cleanup, and abuse protection before sharing widely.
