# N51ZW-Live – Deploy-Anleitung für Werni

## Schnellweg Frontend bei Vercel

1. Neues Projekt bei Vercel aus GitHub importieren.
2. Root Directory: `frontend`
3. Framework: Create React App
4. Build Command: `yarn build` oder `npm run build`
5. Output Directory: `build`
6. Environment Variable setzen:
   - `REACT_APP_BACKEND_URL` = URL deines Backends, z.B. `https://n51zw-live-backend.onrender.com`

## Backend bei Render

1. Neues Web Service aus GitHub importieren.
2. Root Directory: `backend`
3. Build Command: `pip install -r requirements.txt`
4. Start Command: `uvicorn server:app --host 0.0.0.0 --port $PORT`
5. Environment Variables setzen:
   - `MONGO_URL`
   - `DB_NAME=n51zw_live`
   - `TRACKED_ICAO24=a6616a`
   - `TRACKED_REGISTRATION=N51ZW`

## Lokal testen

Backend:
```bash
cd backend
copy .env.example .env
pip install -r requirements.txt
uvicorn server:app --reload --host 0.0.0.0 --port 8001
```

Frontend:
```bash
cd frontend
copy .env.example .env
yarn install
yarn start
```

## Hinweis

Das Frontend braucht ein laufendes Backend. Ohne `REACT_APP_BACKEND_URL` versucht es `/api` relativ zur gleichen Domain.
