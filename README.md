# UnCord 🎉

> A fully self-hosted Discord-like platform. No subscriptions, no limits, no external database.

---

## Installation

### Requirements
- [Git](https://git-scm.com/)
- [Node.js](https://nodejs.org/) v18 or higher
- npm v8 or higher

### 1. Clone the repository

```bash
git clone https://github.com/uncordapp/uncord.git
cd uncord
```

### 2. Install dependencies

```bash
npm run install:all
```

### 3. Configure environment

```bash
cp .env.example .env
```

Open `.env` and set a strong `JWT_SECRET`:

```env
PORT=3001
JWT_SECRET=your-long-random-secret-here
NODE_ENV=production
```

### 4. Run UnCord

**Development** (backend on :3001, frontend on :3000 with hot reload):
```bash
npm run dev
```

**Production** (everything served from one port):
```bash
npm run start:prod
```

Then open `http://localhost:3001` in your browser.

> The **first account to register** automatically becomes admin.

---

## Exposing UnCord to the Internet

We recommend using **Cloudflare Tunnel** to share your UnCord instance publicly without opening ports or needing a static IP. It's free and takes under 5 minutes to set up.

### 1. Install cloudflared

**Windows:**
```bash
winget install Cloudflare.cloudflared
```

**macOS:**
```bash
brew install cloudflared
```

**Linux:**
```bash
curl -L https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64 -o cloudflared
chmod +x cloudflared
sudo mv cloudflared /usr/local/bin/
```

### 2. Start a quick tunnel (no account needed)

Make sure UnCord is already running on port 3001, then run:

```bash
cloudflared tunnel --url http://localhost:3001
```

Cloudflare will give you a public URL like:
```
https://something-random.trycloudflare.com
```

Share that URL with anyone and they can use UnCord from anywhere.

> ⚠️ Quick tunnels are temporary — the URL changes every time you restart. For a permanent URL, use a named tunnel with a Cloudflare account (free).

### 3. Permanent tunnel (recommended)

```bash
cloudflared login
cloudflared tunnel create uncord
cloudflared tunnel route dns uncord your-domain.com
cloudflared tunnel run --url http://localhost:3001 uncord
```

---

## Updating

```bash
git pull
npm run install:all
npm run start:prod
```

---

## Links

- GitHub: [github.com/uncordapp/uncord](https://github.com/uncordapp/uncord)
- Issues: [github.com/uncordapp/uncord/issues](https://github.com/uncordapp/uncord/issues)
- Cloudflare Tunnel docs: [developers.cloudflare.com/cloudflare-one/connections/connect-networks](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks)
