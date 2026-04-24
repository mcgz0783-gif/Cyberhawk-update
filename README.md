# 🛡️ CyberSec Updates

**A modern, AI-powered cybersecurity intelligence platform.**

Real-time threat news · Expert insights · Security blogs · Book library · Google Gemini AI chatbot

---

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ ([download](https://nodejs.org))
- npm 9+ (comes with Node.js)
- A Google Gemini API key ([get one free](https://aistudio.google.com/app/apikey))

### 1 — Clone & Install

```bash
# Install dependencies
npm install
```

### 2 — Configure Google Gemini AI

```bash
# Copy the example env file
cp .env.example .env

# Edit .env and add your Gemini API key:
# VITE_GEMINI_API_KEY=AIzaSy...your_key_here
```

> **No key?** The chatbot automatically falls back to the Anthropic Claude API
> when previewing inside Claude.ai. For production deployment, a Gemini key is required.

### 3 — Run Locally

```bash
npm run dev
# Opens at http://localhost:3000
```

### 4 — Build for Production

```bash
npm run build
# Output in /dist — ready to deploy
```

---

## 🌐 Deploy to Production

### Option A: Netlify (Recommended — Free)

1. Push your project to GitHub
2. Go to [netlify.com](https://netlify.com) → "Add new site" → "Import from Git"
3. Set build settings:
   - **Build command:** `npm run build`
   - **Publish directory:** `dist`
4. Add environment variable in Netlify dashboard:
   - `VITE_GEMINI_API_KEY` = your Gemini API key
5. Deploy → your site goes live instantly

### Option B: Vercel (Free)

```bash
npm install -g vercel
vercel

# Follow prompts, then add env var in Vercel dashboard:
# VITE_GEMINI_API_KEY = your_key
```

### Option C: GitHub Pages

```bash
# Install gh-pages
npm install --save-dev gh-pages

# Add to package.json scripts:
# "deploy": "gh-pages -d dist"

npm run build
npm run deploy
```

### Option D: Docker

```dockerfile
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
ARG VITE_GEMINI_API_KEY
ENV VITE_GEMINI_API_KEY=$VITE_GEMINI_API_KEY
RUN npm run build

FROM nginx:alpine
COPY --from=builder /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

```bash
docker build --build-arg VITE_GEMINI_API_KEY=your_key -t cybersec-updates .
docker run -p 80:80 cybersec-updates
```

---

## 🤖 AI Chatbot Configuration

The **CyberBot** AI assistant is pre-configured to answer:
- Any cybersecurity question (threats, tools, frameworks, career advice)
- Questions about platform content (news, blogs, books, insights)
- CVE explanations, malware analysis, APT attribution
- Security certifications and career guidance (CISSP, CEH, OSCP)
- MITRE ATT&CK techniques and defenses

### AI Provider Logic

| Environment | API Used |
|------------|---------|
| Claude.ai preview (no key) | Anthropic Claude (automatic) |
| Production with `VITE_GEMINI_API_KEY` set | **Google Gemini 1.5 Pro** |

The system prompt is in `src/App.jsx` → `SYSTEM_PROMPT` — customize it to adjust the chatbot's personality, knowledge scope, and response style.

---

## 📁 Project Structure

```
cybersec-updates/
├── index.html          # HTML entry point (SEO optimized)
├── vite.config.js      # Vite bundler config
├── package.json        # Dependencies & scripts
├── .env.example        # Environment variable template
├── .env                # Your secrets (DO NOT commit)
├── src/
│   ├── main.jsx        # React root mount
│   └── App.jsx         # Full application (single-file)
└── dist/               # Production build output (auto-generated)
```

---

## 🎨 Features

| Feature | Details |
|---------|---------|
| **7 Pages** | Home, News, Insights, Blog, Books, About, Contact |
| **AI Chatbot** | Google Gemini 1.5 Pro / Claude fallback |
| **Read Modals** | Full articles, book previews, key takeaways |
| **Search & Filter** | All content pages have live search + category filters |
| **Live Ticker** | Real-time threat news scrolling ticker |
| **Newsletter** | Email subscription with confirmation |
| **Responsive** | Mobile-first design, works on all screen sizes |
| **Dark Theme** | Cyberpunk aesthetic: navy, neon cyan, neon green |
| **Security Tools** | 6 quick-access security utility cards |
| **SEO Optimized** | Meta tags, OG tags, Twitter cards, semantic HTML |

---

## 🔧 Customization

### Updating Content
All content (news, blogs, books, insights) is in `src/App.jsx` in the `DATA` section.
Replace the placeholder data with your real content or connect to a CMS/API.

### Changing Colors
Edit the `T` (theme) object at the top of `src/App.jsx`:
```js
const T = {
  bg: "#060b14",      // Background
  accent: "#00e5ff",  // Neon cyan
  green: "#00ff9d",   // Neon green
  // ...
};
```

### Connecting a Real API
Replace the static data arrays with `useEffect` API calls:
```js
const [news, setNews] = useState([]);
useEffect(() => {
  fetch('/api/news').then(r => r.json()).then(setNews);
}, []);
```

---

## 📞 Contact

- **Email:** kevlarmackenzie@gmail.com
- **Phone:** 0783699626
- **WhatsApp:** 078823106

---

## 📄 License

MIT License — free to use, modify, and deploy.

---

*Built with React + Vite · AI by Google Gemini · Designed for the global security community*
