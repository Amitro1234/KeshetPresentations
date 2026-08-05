---
name: "keshet-presentation"
description: "Create a branded Keshet HTML presentation from a document or content brief. Use when the user provides a document, PDF, notes, or topic and wants a Keshet-styled slide deck."
---

# Keshet Presentation Builder

You are a senior UI designer and presentation architect for Keshet. Your job is to receive a document (PDF, text, notes, or a topic brief) and convert it into a fully branded Keshet HTML slide deck — ready to open in Chrome and print to PDF.

---

## Step 1 — Read the source document

The user will provide one of:
- A PDF or text file (read it fully before doing anything)
- A topic/brief pasted in the chat
- A file path to read

Extract: key messages, section structure, data/stats, quotes, and any specific requests.

---

## Step 2 — Plan the slide structure

Map each piece of content to one of the 5 slide types below. A typical deck is 8–14 slides.

| Content | Slide Type |
|---|---|
| Opening title | Cover (Dark or Aurora, centered) |
| Chapter / section break | Section divider (Dark, centered) |
| Explanation / bullets | Content slide (Aurora, .hd + bullets) |
| Comparison / two topics | Two-column (Aurora, `.glass` + `.inkcard`) |
| Numbers / stats | Stat slide (Aurora, `.glass` bars + `.inkcard` bignum) |
| Process / steps | Steps (Aurora, numbered `.numchip`) |
| Strong statement | Statement (Dark, centered, `.spec` highlight) |
| Summary / recap | Closing grid (Aurora, 3-column `.glass` cards) |

Rule: max ~5 bullets, ~3 stats, ~5 steps per slide. Split if it overflows.

---

## Step 3 — Build the HTML file

### File structure

Single self-contained HTML file. Save it to `C:\Users\amit.rosen\KeshetPresentations\` with a descriptive kebab-case name (e.g. `ai-strategy-2026.html`).

### Required HTML shell

```html
<!DOCTYPE html>
<html dir="rtl" lang="he">
<head>
<meta charset="utf-8">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Heebo:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
<title><!-- Presentation Title --></title>
<style>
/* === PASTE THE FULL CSS BLOCK FROM SECTION 4 HERE === */
</style>
</head>
<body>
  <div id="deck">
    <!-- slides go here -->
  </div>
  <!-- PASTE THE NAV BAR + SCRIPT FROM SECTION 5 HERE -->
</body>
</html>
```

---

## Section 4 — Full CSS (copy verbatim into every file)

```css
@page { size: 1920px 1080px; margin: 0; }
:root {
  --ks: linear-gradient(135deg,#E4002B 0%,#FF6D00 15%,#FFD100 30%,#00A651 50%,#00B4D8 70%,#0057B8 85%,#7B2D8E 100%);
  --font: 'Heebo', 'Arial Hebrew', Arial, sans-serif;
}
*, *::before, *::after { box-sizing: border-box; -webkit-print-color-adjust: exact; print-color-adjust: exact; }
html, body { margin: 0; padding: 0; background: radial-gradient(circle at 50% -10%, #16305a 0%, #0A1930 55%); overflow: hidden; width: 100vw; height: 100vh; display: flex; align-items: center; justify-content: center; font-family: var(--font); }
#deck { position: absolute; top: 50%; left: 50%; width: 1920px; height: 1080px; transform-origin: center center; overflow: hidden; background: #FBFAF8; box-shadow: 0 25px 60px rgba(0,0,0,0.4); }
.page { position: absolute; top: 0; left: 0; width: 1920px; height: 1080px; overflow: hidden; display: flex; flex-direction: column; padding: 74px 104px 56px; direction: rtl; text-align: right; opacity: 0; visibility: hidden; transform: scale(0.96); transition: opacity 0.6s cubic-bezier(0.4,0,0.2,1), transform 0.6s cubic-bezier(0.4,0,0.2,1), visibility 0.6s; z-index: 1; }
.page.active { opacity: 1; visibility: visible; transform: scale(1); z-index: 2; }
@keyframes fadeInUp { from { opacity: 0; transform: translateY(30px); } to { opacity: 1; transform: translateY(0); } }
.page.active .hd, .page.active .grid, .page.active .take, .page.active .fx.col, .page.active .wm { animation: fadeInUp 0.8s cubic-bezier(0.25,1,0.5,1) both; }
.page.active .hd { animation-delay: 0.1s; }
.page.active .grid { animation-delay: 0.2s; }
.page.active .take { animation-delay: 0.3s; }
.nav-bar { position: fixed; bottom: 30px; left: 50%; transform: translateX(-50%); display: flex; align-items: center; gap: 20px; padding: 12px 24px; background: rgba(255,255,255,0.85); backdrop-filter: blur(12px); -webkit-backdrop-filter: blur(12px); border: 1px solid rgba(255,255,255,0.6); border-radius: 999px; box-shadow: 0 10px 30px rgba(10,25,48,0.08); z-index: 1000; direction: ltr; }
.nav-btn { width: 44px; height: 44px; border-radius: 50%; border: 1px solid rgba(10,25,48,0.1); background: #ffffff; color: #0A1930; display: flex; align-items: center; justify-content: center; cursor: pointer; transition: all 0.2s ease; font-size: 18px; box-shadow: 0 2px 8px rgba(10,25,48,0.05); }
.nav-btn:hover { background: #0A1930; color: #ffffff; transform: scale(1.05); }
.nav-btn:disabled { opacity: 0.3; cursor: not-allowed; transform: none; }
.nav-dots { display: flex; gap: 8px; align-items: center; }
.nav-dot { width: 10px; height: 10px; border-radius: 50%; background: rgba(10,25,48,0.15); cursor: pointer; transition: all 0.3s ease; }
.nav-dot.active { background: var(--ks); width: 24px; border-radius: 5px; }
.nav-counter { font-size: 16px; font-weight: 700; color: #0A1930; min-width: 60px; text-align: center; }
.aurora { background: radial-gradient(1200px 820px at 10% 6%,rgba(228,0,43,.14),transparent 58%), radial-gradient(1150px 900px at 92% 10%,rgba(255,209,0,.20),transparent 58%), radial-gradient(1250px 950px at 84% 94%,rgba(0,180,216,.20),transparent 60%), radial-gradient(1150px 900px at 12% 96%,rgba(123,45,142,.15),transparent 60%), radial-gradient(900px 720px at 50% 52%,rgba(0,166,81,.10),transparent 64%), linear-gradient(160deg,#FBFAF8,#F2EFE9); }
.dark { background: radial-gradient(1200px 900px at 82% 10%,rgba(0,180,216,.30),transparent 55%), radial-gradient(1100px 900px at 12% 92%,rgba(123,45,142,.30),transparent 58%), radial-gradient(1000px 800px at 50% 50%,rgba(0,87,184,.18),transparent 60%), linear-gradient(150deg,#0A1930,#0f2340); }
.glass { background: rgba(255,255,255,.6); border: 1px solid rgba(255,255,255,.78); border-radius: 20px; box-shadow: 0 16px 46px rgba(10,25,48,.10); }
.inkcard { background: linear-gradient(150deg,#0A1930,#13294c); color: #fff; border-radius: 20px; box-shadow: 0 18px 48px rgba(10,25,48,.30); }
.spec { background: var(--ks); -webkit-background-clip: text; background-clip: text; -webkit-text-fill-color: transparent; }
.specbar { background: var(--ks); }
.ink-t { color: #0A1930; } .muted { color: #5A6A7A; } .white { color: #fff; } .white-2 { color: rgba(255,255,255,.82); }
.eyebrow { display: inline-flex; align-items: center; gap: .55em; padding: .5em 1.15em; border-radius: 999px; background: rgba(255,255,255,.62); border: 1px solid rgba(255,255,255,.85); color: #0A1930; font-weight: 700; font-size: 21px; width: fit-content; }
.eyebrow.on-dark { background: rgba(255,255,255,.12); border-color: rgba(255,255,255,.28); color: #fff; }
.dot { width: .62em; height: .62em; border-radius: 50%; background: var(--ks); display: inline-block; }
.title { font-size: 70px; font-weight: 900; line-height: 1.06; color: #0A1930; letter-spacing: -.015em; margin: 0; }
.title.on-dark { color: #fff; }
.sub { font-size: 29px; font-weight: 500; line-height: 1.42; color: #5A6A7A; max-width: 1240px; margin: 0; }
.sub.on-dark { color: rgba(255,255,255,.82); }
.hd { display: flex; flex-direction: column; gap: 20px; }
.take { border-radius: 16px; padding: 22px 34px; font-size: 27px; font-weight: 700; line-height: 1.32; background: rgba(10,25,48,.94); color: #fff; }
.take .hi { color: #FFD100; }
.wm { position: absolute; top: 52px; left: 104px; display: flex; align-items: center; z-index: 100; }
.wm.on-dark { color: #fff; }
.barrow { display: flex; align-items: center; gap: 22px; }
.barlbl { width: 250px; font-weight: 800; font-size: 26px; color: #0A1930; text-align: right; line-height: 1.15; }
.barlbl small { display: block; font-weight: 600; font-size: 18px; color: #5A6A7A; }
.bartrack { flex: 1; height: 46px; border-radius: 999px; background: rgba(10,25,48,.07); overflow: hidden; display: flex; }
.barfill { height: 100%; border-radius: 999px; display: flex; align-items: center; padding-inline: 18px; color: #fff; font-weight: 800; font-size: 20px; min-width: 64px; }
.barval { width: 170px; font-weight: 900; font-size: 30px; color: #0A1930; }
.f-green { background: #00A651; } .f-orange { background: #FF6D00; } .f-blue { background: #0057B8; } .f-cyan { background: #00B4D8; } .f-red { background: #E4002B; } .f-purple { background: #7B2D8E; }
.chip { display: inline-flex; align-items: center; gap: 8px; padding: 9px 18px; border-radius: 999px; font-weight: 800; font-size: 20px; }
.tok { display: inline-flex; padding: 10px 16px; border-radius: 12px; font-weight: 800; font-size: 30px; color: #0A1930; }
.bignum { font-size: 150px; font-weight: 900; line-height: .9; letter-spacing: -.03em; }
.numchip { width: 56px; height: 56px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-weight: 900; font-size: 28px; color: #fff; flex-shrink: 0; }
.fx { display: flex; } .col { flex-direction: column; } .ac { align-items: center; } .jc { justify-content: center; } .jb { justify-content: space-between; } .f1 { flex: 1; } .wrap { flex-wrap: wrap; } .grid { display: grid; }
.fw5 { font-weight: 500; } .fw6 { font-weight: 600; } .fw7 { font-weight: 700; } .fw8 { font-weight: 800; }
@media print {
  html, body { background: #fff; width: auto; height: auto; overflow: visible; }
  #deck { position: static; transform: none !important; width: auto; height: auto; box-shadow: none; overflow: visible; }
  .page { position: relative; opacity: 1 !important; visibility: visible !important; transform: none !important; width: 1920px; height: 1080px; break-after: page; page-break-after: always; display: flex !important; }
  .nav-bar { display: none !important; }
}
```

---

## Section 5 — Nav bar + Script (copy verbatim into every file)

```html
  <div class="nav-bar">
    <button class="nav-btn" id="prev-btn" aria-label="Previous slide">&larr;</button>
    <div class="nav-dots" id="nav-dots"></div>
    <div class="nav-counter" id="nav-counter">1 / 1</div>
    <button class="nav-btn" id="next-btn" aria-label="Next slide">&rarr;</button>
    <button class="nav-btn" id="fs-btn" aria-label="Toggle fullscreen" title="Fullscreen (F)"></button>
  </div>
  <script>
    document.addEventListener('DOMContentLoaded', () => {
      const deck = document.getElementById('deck');
      const pages = Array.from(deck.querySelectorAll('.page'));
      const prevBtn = document.getElementById('prev-btn');
      const nextBtn = document.getElementById('next-btn');
      const dotsContainer = document.getElementById('nav-dots');
      const counter = document.getElementById('nav-counter');
      let currentIndex = 0;
      pages[currentIndex].classList.add('active');
      pages.forEach((_, index) => {
        const dot = document.createElement('div');
        dot.classList.add('nav-dot');
        if (index === currentIndex) dot.classList.add('active');
        dot.addEventListener('click', () => goToSlide(index));
        dotsContainer.appendChild(dot);
      });
      const dots = Array.from(dotsContainer.querySelectorAll('.nav-dot'));
      function resizeDeck() {
        const scale = Math.min(window.innerWidth / 1920, window.innerHeight / 1080);
        deck.style.transform = `translate(-50%, -50%) scale(${scale})`;
      }
      window.addEventListener('resize', resizeDeck);
      resizeDeck();
      function updateControls() {
        prevBtn.disabled = currentIndex === 0;
        nextBtn.disabled = currentIndex === pages.length - 1;
        dots.forEach((dot, index) => dot.classList.toggle('active', index === currentIndex));
        counter.textContent = `${currentIndex + 1} / ${pages.length}`;
      }
      function goToSlide(index) {
        if (index < 0 || index >= pages.length) return;
        pages[currentIndex].classList.remove('active');
        currentIndex = index;
        pages[currentIndex].classList.add('active');
        updateControls();
      }
      function nextSlide() { if (currentIndex < pages.length - 1) goToSlide(currentIndex + 1); }
      function prevSlide() { if (currentIndex > 0) goToSlide(currentIndex - 1); }
      prevBtn.addEventListener('click', prevSlide);
      nextBtn.addEventListener('click', nextSlide);
      const fsBtn = document.getElementById('fs-btn');
      const ICON_EXPAND = '<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 9V4h5M15 4h5v5M20 15v5h-5M9 20H4v-5"/></svg>';
      const ICON_COMPRESS = '<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 4v5H4M20 9h-5V4M15 20v-5h5M4 15h5v5"/></svg>';
      function updateFsIcon() { fsBtn.innerHTML = document.fullscreenElement ? ICON_COMPRESS : ICON_EXPAND; }
      function toggleFullscreen() {
        if (!document.fullscreenElement) { if (document.documentElement.requestFullscreen) document.documentElement.requestFullscreen(); }
        else if (document.exitFullscreen) { document.exitFullscreen(); }
      }
      fsBtn.addEventListener('click', toggleFullscreen);
      document.addEventListener('fullscreenchange', updateFsIcon);
      updateFsIcon();
      document.addEventListener('keydown', (e) => {
        if (e.key === 'ArrowLeft' || e.key === ' ') { e.preventDefault(); nextSlide(); }
        else if (e.key === 'ArrowRight') { e.preventDefault(); prevSlide(); }
        else if (e.key === 'f' || e.key === 'F') { e.preventDefault(); toggleFullscreen(); }
      });
      let touchStartX = 0, touchEndX = 0;
      document.addEventListener('touchstart', (e) => { touchStartX = e.changedTouches[0].screenX; }, { passive: true });
      document.addEventListener('touchend', (e) => { touchEndX = e.changedTouches[0].screenX; handleGesture(); }, { passive: true });
      function handleGesture() {
        const threshold = 50;
        if (touchEndX < touchStartX - threshold) nextSlide();
        if (touchEndX > touchStartX + threshold) prevSlide();
      }
      updateControls();
    });
  </script>
```

---

## Section 6 — Slide snippets (copy & adapt)

### Logo header (mandatory on EVERY slide)
```html
<div class="wm">
  <img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.15));">
</div>
```
On `.dark` slides: `<div class="wm on-dark">`.

---

### Cover slide (Aurora Light, centered)
```html
<div class="page aurora fx col ac jc">
  <div class="wm"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.15));"></div>
  <div class="fx col ac" style="gap:34px;text-align:center;max-width:1400px;">
    <div class="eyebrow"><span class="dot"></span>קטגוריה · תת-כותרת</div>
    <h1 class="title" style="font-size:104px;line-height:1.02;">כותרת ראשית עם <span class="spec">מילה בקשת</span></h1>
    <p class="sub" style="font-size:33px;text-align:center;max-width:1080px;">משפט פתיחה אחד שמסביר את הנושא.</p>
    <div class="specbar" style="width:280px;height:8px;border-radius:999px;"></div>
  </div>
</div>
```

---

### Section divider (Dark Glow, centered)
```html
<div class="page dark fx col ac jc">
  <div class="wm on-dark"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.35));"></div>
  <div class="fx col ac" style="gap:28px;text-align:center;max-width:1300px;">
    <div class="eyebrow on-dark"><span class="dot"></span>פרק 01</div>
    <h1 class="title on-dark" style="font-size:88px;">אמירה מרכזית עם <span class="spec">דגש בקשת</span></h1>
    <p class="sub on-dark" style="text-align:center;">משפט תומך קצר.</p>
    <div class="specbar" style="width:240px;height:8px;border-radius:999px;"></div>
  </div>
</div>
```

---

### Content slide — bullets (Aurora Light)
```html
<div class="page aurora">
  <div class="wm"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.15));"></div>
  <div class="hd">
    <div class="eyebrow"><span class="dot"></span>נושא</div>
    <h1 class="title">כותרת השקופית</h1>
    <p class="sub">משפט הסבר תמציתי.</p>
  </div>
  <div class="glass f1 fx col" style="padding:48px 56px;gap:22px;margin-top:34px;justify-content:center;">
    <div class="fx ac" style="gap:16px;"><span style="width:10px;height:10px;border-radius:50%;background:#E4002B;flex-shrink:0;"></span><span class="ink-t fw6" style="font-size:26px;">נקודה ראשונה — עד שורה וחצי</span></div>
    <div class="fx ac" style="gap:16px;"><span style="width:10px;height:10px;border-radius:50%;background:#E4002B;flex-shrink:0;"></span><span class="ink-t fw6" style="font-size:26px;">נקודה שנייה</span></div>
    <div class="fx ac" style="gap:16px;"><span style="width:10px;height:10px;border-radius:50%;background:#E4002B;flex-shrink:0;"></span><span class="ink-t fw6" style="font-size:26px;">נקודה שלישית</span></div>
  </div>
  <div class="take" style="margin-top:24px;">מסקנה — <span class="hi">ההדגשה החשובה</span> בצהוב.</div>
</div>
```
Max 5 bullets. Add a `.take` strip when there's a clear takeaway.

---

### Two-column comparison (Aurora Light)
```html
<div class="page aurora">
  <div class="wm"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.15));"></div>
  <div class="hd">
    <div class="eyebrow"><span class="dot"></span>השוואה</div>
    <h1 class="title">כותרת ההשוואה</h1>
  </div>
  <div class="grid f1 ac" style="grid-template-columns:1fr 1fr;gap:40px;margin-top:34px;">
    <div class="glass" style="padding:48px;">
      <div class="chip" style="background:rgba(90,106,122,.12);color:#5A6A7A;margin-bottom:22px;">עמודה א'</div>
      <div class="ink-t fw8" style="font-size:32px;line-height:1.2;margin-bottom:26px;">כותרת</div>
      <div class="fx col" style="gap:14px;">
        <div class="fx ac" style="gap:12px;"><span style="width:10px;height:10px;border-radius:50%;background:#5A6A7A;flex-shrink:0;"></span><span class="muted fw6" style="font-size:23px;">נקודה</span></div>
      </div>
    </div>
    <div class="inkcard" style="padding:48px;">
      <div class="chip" style="background:rgba(255,255,255,.14);color:#fff;margin-bottom:22px;">עמודה ב'</div>
      <div class="white fw8" style="font-size:32px;line-height:1.2;margin-bottom:26px;">כותרת</div>
      <div class="fx col" style="gap:14px;">
        <div class="fx ac" style="gap:12px;"><span class="dot" style="width:12px;height:12px;flex-shrink:0;"></span><span class="white-2 fw6" style="font-size:23px;">נקודה</span></div>
      </div>
    </div>
  </div>
</div>
```

---

### Stat slide — bars + big number (Aurora Light)
```html
<div class="page aurora">
  <div class="wm"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.15));"></div>
  <div class="hd">
    <div class="eyebrow"><span class="dot"></span>נתונים</div>
    <h1 class="title">כותרת עם מספר מרכזי</h1>
  </div>
  <div class="grid f1 ac" style="grid-template-columns:1.4fr 1fr;gap:40px;margin-top:44px;">
    <div class="glass" style="padding:48px 52px;">
      <div class="fx col" style="gap:28px;">
        <div class="fx col" style="gap:10px;">
          <div class="fw7 ink-t" style="font-size:23px;">אפשרות א'</div>
          <div class="bartrack"><div class="barfill f-blue" style="width:30%;">ערך</div></div>
        </div>
        <div class="fx col" style="gap:10px;">
          <div class="fw7 ink-t" style="font-size:23px;">אפשרות ב'</div>
          <div class="bartrack"><div class="barfill f-red" style="width:85%;">ערך גבוה</div></div>
        </div>
      </div>
    </div>
    <div class="inkcard fx col ac jc" style="padding:44px;text-align:center;gap:8px;">
      <div class="bignum spec">×20</div>
      <div class="white fw7" style="font-size:26px;line-height:1.35;">תיאור קצר</div>
    </div>
  </div>
  <div class="take" style="margin-top:28px;">מסקנה — <span class="hi">פעולה מומלצת</span> בצהוב.</div>
</div>
```

---

### Steps slide (Aurora Light)
```html
<div class="page aurora">
  <div class="wm"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.15));"></div>
  <div class="hd" style="margin-bottom:40px;">
    <div class="eyebrow"><span class="dot"></span>תהליך</div>
    <h1 class="title">שלבי הפעולה</h1>
  </div>
  <div class="glass f1 fx col" style="padding:48px 56px;gap:28px;justify-content:center;">
    <!-- Step colors: 1=red #E4002B, 2=orange #FF6D00, 3=yellow #FFD100, 4=green #00A651, 5=cyan #00B4D8 -->
    <div class="fx ac" style="gap:24px;">
      <div class="numchip" style="background:#E4002B;">1</div>
      <div><div class="ink-t fw8" style="font-size:28px;">שם השלב</div><div class="muted fw5" style="font-size:22px;margin-top:4px;">תיאור קצר</div></div>
    </div>
    <div class="fx ac" style="gap:24px;">
      <div class="numchip" style="background:#FF6D00;">2</div>
      <div><div class="ink-t fw8" style="font-size:28px;">שם השלב</div><div class="muted fw5" style="font-size:22px;margin-top:4px;">תיאור קצר</div></div>
    </div>
  </div>
</div>
```

---

### Closing grid / summary (Aurora Light)
```html
<div class="page aurora fx col ac jc">
  <div class="wm"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.15));"></div>
  <div style="width:100%;">
    <div class="fx col ac" style="gap:12px;text-align:center;margin-bottom:24px;">
      <div class="eyebrow"><span class="dot"></span>לסיכום</div>
      <h1 class="title" style="font-size:52px;">הנקודות שכדאי לזכור</h1>
    </div>
    <div class="grid" style="grid-template-columns:repeat(3,1fr);gap:16px;">
      <div class="glass fx col" style="padding:26px 22px;gap:12px;background:rgba(255,255,255,.94);"><div class="numchip specbar" style="width:48px;height:48px;font-size:24px;">1</div><div class="ink-t fw8" style="font-size:21px;line-height:1.25;">נקודה</div><div class="muted fw6" style="font-size:17px;line-height:1.45;">הסבר קצר.</div></div>
      <div class="glass fx col" style="padding:26px 22px;gap:12px;background:rgba(255,255,255,.94);"><div class="numchip specbar" style="width:48px;height:48px;font-size:24px;">2</div><div class="ink-t fw8" style="font-size:21px;line-height:1.25;">נקודה</div><div class="muted fw6" style="font-size:17px;line-height:1.45;">הסבר קצר.</div></div>
      <div class="glass fx col" style="padding:26px 22px;gap:12px;background:rgba(255,255,255,.94);"><div class="numchip specbar" style="width:48px;height:48px;font-size:24px;">3</div><div class="ink-t fw8" style="font-size:21px;line-height:1.25;">נקודה</div><div class="muted fw6" style="font-size:17px;line-height:1.45;">הסבר קצר.</div></div>
    </div>
  </div>
</div>
```

---

## Section 7 — Content rules (non-negotiable)

1. **RTL always**: `<html dir="rtl" lang="he">`. All Hebrew text right-aligned.
2. **Foreign terms**: wrap in `<span dir="ltr">Claude</span>` — e.g. `<span dir="ltr">AI</span>`, `<span dir="ltr">API</span>`.
3. **Logo on every slide** — use the image snippet above. Never render the logo as SVG polygons.
4. **Max per slide**: ~5 bullets, ~3 stats, ~5 steps. Split if it overflows.
5. **No emoji**.
6. **Colors only from the palette**: `--ks`, `#E4002B`, `#FF6D00`, `#FFD100`, `#00A651`, `#00B4D8`, `#0057B8`, `#7B2D8E`, `#0A1930`, `#5A6A7A`, `#fff`.
7. **Font only Heebo** (loaded from Google Fonts).
8. **Rainbow (`--ks` / `.spec` / `.specbar`) must appear on every slide** — as a stripe, text highlight, bar, or `.dot`.

---

## Section 8 — Output checklist

Before saving the file, verify:
- [ ] `<html dir="rtl" lang="he">`
- [ ] Heebo loaded from Google Fonts
- [ ] Full CSS block from Section 4 is present
- [ ] Nav bar + script from Section 5 is present
- [ ] Logo image tag on every slide
- [ ] Every foreign term in `<span dir="ltr">`
- [ ] Rainbow appears on every slide
- [ ] No slide overflows (max 5 bullets / 3 stats / 5 steps)
- [ ] `@media print` block included in CSS
- [ ] File saved to `C:\Users\amit.rosen\KeshetPresentations\`
- [ ] Present the file to the user with `mcp__cowork__present_files`

---

## Section 9 — How to handle the user's request

1. **Read the source** — file, PDF, or pasted text. Use `Read` or `mcp__workspace__bash` to extract content.
2. **Ask ONE clarifying question if needed** — e.g. audience, number of slides, specific emphasis. Skip if the brief is clear.
3. **Build the HTML** — write the full file in one pass. Do not show the code in chat; write it directly to disk.
4. **Save to workspace** — `C:\Users\amit.rosen\KeshetPresentations\<name>.html`
5. **Present the file** — call `mcp__cowork__present_files` so the user gets a clickable card.
6. **One-line summary** — e.g. "נוצרה מצגת של 10 שקופיות — פתח ב-Chrome להצגה."

