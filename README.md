# 💌 Cute Birthday Website Template

*[Baca versi Bahasa Indonesia](README.id.md)*

A cute, interactive digital birthday website you can fully customize for your girlfriend (or anyone you love) — no coding experience required! Built to be used as a **template**: just swap in your own photos, GIFs, and text, then deploy.

**The flow:** intro page → interactive photo gallery → "100 reasons why I love you" → birthday letter with a confetti burst 🎉

It also includes a music button (the song keeps playing as she moves between pages) and a little editable note button where she can write back to you — her message auto-saves right in her browser.

---

## 📁 Folder structure

```
my-birthday-site/
├── index.html          → Page 1: intro / hero
├── gallery.html         → Page 2: interactive photo gallery (swipe/click)
├── reasons.html          → Page 3: "100 reasons why i love you"
├── letter.html           → Page 4: birthday letter + confetti
├── css/
│   └── style.css         → all styling & colors, shared across every page
├── js/
│   ├── script.js          → logic that runs on every page (transitions, music, note, letter, confetti)
│   ├── gallery.js          → logic specific to the photo gallery
│   └── reasons.js          → logic specific to the 100-reasons page (photo lightbox + auto-scroll)
├── assets/                → put your GIFs and music here
│   ├── hero.gif
│   ├── sparkle1.gif
│   ├── sparkle2.gif
│   ├── celebration.gif
│   ├── gif1.gif
│   ├── gif2.gif
│   └── music.mp3
└── photos/                → put your own photos here
    ├── photo1.jpg ... photo4.jpg      (for the gallery)
    └── reason1.jpg ... reason6.jpg     (for the 100-reasons page)
```

> Every GIF, photo, and music file included right now is a **dummy placeholder** (a pastel-colored box that says "REPLACE ME"), so you know exactly what needs to be swapped out.

---

## 🚀 Getting started (step-by-step for beginners)

### 1. Download this project
If you got this from GitHub, click **Code → Download ZIP**, then extract it anywhere on your computer. Or, even easier, click the green **"Use this template"** button on the repo page to create your own copy on GitHub first.

### 2. Replace the photos & GIFs
Open the `photos/` and `assets/` folders, then **overwrite the existing files using the exact same filenames** (capitalization matters!). For example:
- Want new gallery photos? Overwrite `photos/photo1.jpg`, `photo2.jpg`, etc. with your own (`.jpg` or `.png` both work, but if you change the extension, you'll also need to update the filename referenced in the HTML — see step 4).
- Want a different intro GIF? Overwrite `assets/hero.gif`.
- Want your own song? Overwrite `assets/music.mp3` with your own track (mp3 format).

**If your filenames or extensions are different**, just look for the `<!-- INSERT YOUR GIF/PHOTO HERE -->` comments in the relevant HTML file and update the `src="..."` there.

### 3. Edit all the text
This is the most personal part — the text lives in a few different places:

| What do you want to edit? | Open this file | Look for |
|---|---|---|
| Title & subtitle on the intro page | `index.html` | `<h1 class="hero-title">` and `<p class="hero-subtitle">` |
| Captions under each gallery photo | `js/gallery.js` | the `photos` array near the top of the file |
| The "100 reasons" list | `reasons.html` | find `<ol class="reasons-list">` — each reason is one `<li>...</li>` line. It currently ships with placeholder text ("reason 1", "reason 2", etc.) — replace with your own (fewer than 100 is fine too, just delete the extra `<li>` lines) |
| The typewriter birthday letter | `js/script.js` | the `letterMessage` variable in the middle of the file |
| The signature on the letter | `letter.html` | `<p class="signature">` |

### 4. Preview it in your browser (local testing)
Just double-click `index.html` — it should open right up in your default browser.

⚠️ **Important note:** the "music keeps playing across pages" feature and the note button's saved state rely on the browser's `sessionStorage`/`localStorage`. If you open the files by **double-clicking** them (`file://...`), some browsers (especially Chrome) treat each local file as its own separate origin, so those features might not carry over perfectly during local testing. This is **normal** and will work smoothly once the site is deployed (step 5), since all pages will then share one real website address.

For more accurate local testing, run a simple local server instead. If you have Python installed, open a terminal in this project folder and run:
```
python3 -m http.server
```
then open `http://localhost:8000` in your browser.

### 5. Deploy to Netlify (free)
The easiest way:
1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag this project's folder (make sure `index.html` is at the top level/root) onto the page
3. Netlify instantly gives you a live link, like `random-name.netlify.app`
4. You can rename that link under **Site settings → Change site name**

For something more polished (auto-updates every time you push a change), upload this project to a GitHub repo, then in Netlify choose **Add new site → Import an existing project** and connect it to that repo. No build command needed — this is a plain static site.

---

## 🎨 Changing the color theme

All colors are defined in one place: open `css/style.css`, look at the very top (`:root { ... }`). Change the hex color codes (e.g. `#ffd6e8`) to whatever you like — it updates across every page automatically.

---

## ❓ FAQ / Troubleshooting

**My GIF/photo isn't showing up — just a broken image icon.**
Double-check the filename matches EXACTLY what's in the code (including capitalization and file extension — `.jpg` is different from `.JPG` on some systems). Also make sure the file actually exists inside `assets/` or `photos/`.

**The music doesn't play automatically when the page loads.**
That's intentional — modern browsers block audio from autoplaying with sound before there's been any user interaction. That's why the music only starts once the music button (🎵, bottom-right corner) is clicked.

**The note she wrote using the 📝 button isn't showing up on my phone/laptop.**
That's expected — the note is saved in that specific browser (`localStorage`), not on a server or shared database. So if she writes it on her phone, it only lives on her phone's browser. If you'd like a version that syncs across devices, that would require adding a small backend/database (outside the scope of this static template).

**I want to add/remove photos in the gallery or the clothesline on the reasons page.**
- Gallery (`gallery.html`): edit the `photos` array in `js/gallery.js`, adding or removing objects from it. Also update the number of `<button class="dot">` elements in `gallery.html` to match.
- Clothesline photos on the reasons page (`reasons.html`): add or remove `<div class="hang-photo">...</div>` blocks inside `.hanging-photos`.

---

## 📜 License

Free to use, modify, and share for personal purposes (like surprising someone you love!). If you improve on this, feel free to fork it and share it with others too 💕
