# Mood Music Recommender (Starter Kit)

Full-stack example based on your workflow.

## Stack
- **Frontend**: React (Vite), react-router, react-player
- **Backend**: Flask + CORS
- **Data**: `backend/songs.csv` (local WAVs + YouTube URLs)

## Run Backend
```bash
cd backend
python -m venv .venv && source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python app.py
```
Backend runs at http://localhost:5000

## Run Frontend
```bash
cd frontend
npm install
npm run dev
```
Frontend dev server: http://localhost:5173

## How it Works
1. Home page lets you type mood text or click mood chips.
2. POST to `/recommend` → backend detects mood (keyword rules).
3. Backend returns `mood` and `recommendations` (title + url).
4. Frontend uses:
   - **ReactPlayer** to play **YouTube** links (embedded).
   - **<audio>** element to play **local** WAV files served from Flask static.
5. History page stores last 50 queries in `localStorage`.
6. Login page hits `/auth/login` (dummy) and stores token in `localStorage`.

## Why audio might not play
- YouTube links **don’t work** in `<audio>`; they must be embedded with ReactPlayer.
- Local files must be absolute URLs (the backend normalizes `/static/...` to full URL).
- Check browser autoplay policies; click **Play** if muted/blocked.

## Customizing
- Add/remove songs in `backend/songs.csv`. For local files, put WAV/MP3 in `backend/static/songs/`.
- Expand `detect_mood()` for better NLP (spaCy/transformers).
- Replace `/auth/login` with real auth and DB if needed.
