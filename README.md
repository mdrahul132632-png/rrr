# RRR – Free AI Video Generator 🎬

> **[rrr.free.com](http://rrr.free.com)** · 100% Free · Unlimited · No Login Required

A Veo3-inspired AI video generation website — built with open AI APIs, completely free for everyone.

---

## ✨ Features

- 🆓 **100% Free** — No subscription, no credit card, no limits
- 🔓 **No Login** — Open and generate instantly
- ∞ **Unlimited Videos** — Generate as many as you want
- 🎨 **Multiple Styles** — Cinematic, Anime, 3D, Realistic, Cartoon, Watercolor, Retro
- 📐 **Multiple Ratios** — 16:9, 9:16, 1:1
- 📺 **Up to 4K** — 720p, 1080p, 4K Ultra
- 🌐 **Open Source** — Fork & self-host freely

---

## 🚀 Deploy on GitHub Pages (Free)

### Step 1 — Fork this repo
Click the **Fork** button on the top right.

### Step 2 — Add your AI API key

Open `index.html` and find the config section:

```javascript
// Replace with your API key
const CONFIG = {
  apiKey: 'YOUR_API_KEY_HERE',
  apiEndpoint: 'https://your-video-api-endpoint.com/generate',
  model: 'your-model-name'
};
```

**Recommended free/cheap AI video APIs:**
- [Replicate](https://replicate.com) — Pay per use, very cheap
- [Hugging Face](https://huggingface.co/inference-api) — Free tier available
- [Stability AI](https://stability.ai/api) — Free credits on signup
- [RunPod](https://runpod.io) — Self-hostable

### Step 3 — Enable GitHub Pages
1. Go to your repo **Settings**
2. Click **Pages** in the left sidebar
3. Under **Source**, select `main` branch → `/ (root)` folder
4. Click **Save**

Your site will be live at: `https://YOUR_USERNAME.github.io/rrr/`

### Step 4 — (Optional) Custom Domain
Add a `CNAME` file with your domain name and configure DNS to point to GitHub Pages.

---

## 🔧 Connect Your Video API

In `index.html`, replace the `startGenerate()` function's simulation code with a real API call:

```javascript
async function callVideoAPI(prompt, duration, style) {
  const response = await fetch(CONFIG.apiEndpoint, {
    method: 'POST',
    headers: {
      'Authorization': 'Bearer ' + CONFIG.apiKey,
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      prompt: prompt,
      duration: duration,
      style: style,
      aspect_ratio: document.getElementById('aspect').value
    })
  });
  
  const data = await response.json();
  return data.video_url; // URL to the generated video
}
```

Then in `showResult()`, load the real video:

```javascript
function showResult(videoUrl) {
  const wrap = document.getElementById('videoWrap');
  wrap.innerHTML = `<video controls autoplay loop style="width:100%;height:100%;object-fit:cover;">
    <source src="${videoUrl}" type="video/mp4">
  </video>`;
}
```

---

## 📁 File Structure

```
rrr/
├── index.html      ← Main website (single file, self-contained)
├── README.md       ← This file
└── CNAME           ← (optional) custom domain
```

---

## 🌍 Live Demo

Visit: **[rrr.free.com](http://rrr.free.com)**

---

## 📜 License

MIT License — Free to use, modify, and distribute.

---

## 🤝 Contributing

Pull requests welcome! Open an issue first to discuss major changes.

---

Made with ❤️ · Open Source · Free Forever
