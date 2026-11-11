# Deploying SyncChat to a Live Website

This repository is already configured with Render Blueprint (`render.yaml`) to automatically provision both the **Web Service** and the **PostgreSQL Database** on Render's free tier.

Your GitHub repository is:
**https://github.com/jk9098443443-droid/syncchat1**

---

## 🚀 Instant Deployment (Render Blueprint — Recommended)

1. Open **[dashboard.render.com](https://dashboard.render.com/)** (log in or sign up with GitHub).
2. Click **New +** at the top right → select **Blueprint**.
3. Choose your repository: **`jk9098443443-droid/syncchat1`**.
   *(If not listed, click "Configure account" to grant Render access to your repo).*
4. Render will read `render.yaml` and display:
   - **Database**: `syncchat-db` (PostgreSQL)
   - **Web Service**: `syncchat` (Node.js + WebRTC + Socket.io)
5. Click **Apply**.

Render will now automatically:
- Create your PostgreSQL database.
- Connect the database connection string to `DATABASE_URL`.
- Run `npm install` and start the server.
- Issue a free SSL/TLS certificate (HTTPS is required for WebRTC camera & microphone access).

Within 2–3 minutes, your live URL will be active:
**`https://syncchat-xxxx.onrender.com`** (visible right on your Render dashboard).

---

## ⚙️ Optional Configurations

| Environment Variable | Required | Description |
|---|---|---|
| `DATABASE_URL` | Auto | Render sets this automatically from the `syncchat-db` instance. |
| `UPSTASH_REDIS_REST_URL` | No | Optional Redis cache. In-memory cache is used if left blank. |
| `UPSTASH_REDIS_REST_TOKEN` | No | Optional Redis token. |
| `GOOGLE_CLIENT_ID` | No | Optional Google OAuth login client ID. |
| `GOOGLE_CLIENT_SECRET` | No | Optional Google OAuth secret. |
| `OAUTH_BASE_URL` | No | Set to your live Render URL if Google login is enabled. |

---

## 🌐 Custom Domain (Optional)

1. In Render, open your `syncchat` web service → **Settings** → **Custom Domains**.
2. Add your domain (e.g. `chat.yourdomain.com`).
3. Add the CNAME / A DNS records provided by Render to your domain registrar (GoDaddy, Namecheap, Cloudflare, etc.). Render provisions SSL automatically.
