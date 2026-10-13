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
