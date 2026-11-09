# auth-app — Authentication Starter (JWT + Google OAuth)

A minimal **Express + MongoDB** authentication service with email/password signup-login (bcrypt + JWT) and **Sign in with Google** via Passport.js. Includes a static frontend and is configured for **Vercel** deployment.

## ✨ Features

- **Register / Login** — `POST /api/register`, `POST /api/login`
  - Passwords hashed with **bcryptjs**
  - Stateless sessions via **JSON Web Tokens**
- **Google OAuth 2.0** — `GET /auth/google` → callback, powered by **passport-googleauth20**
  - Auto-provisions a user record on first sign-in
- **Session middleware** — `express-session` for passport session persistence
- **CORS + dotenv** config
- **Static frontend** — `public/index.html` + `style.css` (signup/login UI)
- **Vercel-ready** — `vercel.json` + `api/index.js` entry wrapper

## 🛠️ Stack

| Layer | Tech |
| :--- | :--- |
| Runtime | Node.js |
| Framework | Express 5 |
| Database | MongoDB (Mongoose) |
| Auth | bcryptjs · jsonwebtoken · Passport (Google OAuth 2.0) |
| Deploy | Vercel |

## 🚀 Local Setup

```bash
npm install
```

Create a `.env` file:

```env
MONGO_URI=your_mongodb_connection_string
SESSION_SECRET=your_session_secret
JWT_SECRET=your_jwt_secret
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
```

> Google OAuth ke liye [Google Cloud Console](https://console.cloud.google.com/) mein create karo aur callback URL set karo: `http://localhost:3000/auth/google/callback`

```bash
npm start
```

Open `http://localhost:3000` — register, login, ya Google se sign in karo.

## 📁 Structure

```
auth-app/
├── server.js            # Express app + routes + Passport config
├── models/User.js       # Mongoose user schema
├── api/index.js         # Vercel serverless entry
├── vercel.json          # Vercel routing config
├── public/              # Static auth UI
│   ├── index.html
│   └── style.css
└── package.json
```

## 🔐 Security Notes

- Passwords never stored in plaintext (bcrypt hashing)
- JWT issued only after credential verification
- Secrets loaded from environment variables — never hard-coded

---

*B.Tech CSE (Cybersecurity) · Parul University*
