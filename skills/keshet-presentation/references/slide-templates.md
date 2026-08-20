# Slide Templates Reference (Formatter Layer)

Copy, combine, and customize these production-tested HTML snippets for each slide inside `<div id="deck">`.

---

## 1. Logo Header Snippet (Mandatory on Every Slide)

### For Light Slides (`.aurora` / `.clean-bordered`)
```html
<div class="wm">
  <img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.15));">
</div>
```

### For Dark Slides (`.dark`)
```html
<div class="wm on-dark">
  <img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.35));">
</div>
```

---

## 2. Template 1 — Cover Slide (Centered, Dark Glow or Aurora)

```html
<div class="page dark fx col ac jc">
  <div class="wm on-dark"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.35));"></div>
  <div class="fx col ac" style="gap:32px;text-align:center;max-width:1400px;">
    <div class="eyebrow on-dark"><span class="dot"></span>הדרכה מקצועית · <span dir="ltr">AI Solutions Architecture</span></div>
    <h1 class="title on-dark" style="font-size:96px;line-height:1.05;">שם ההדרכה או המצגת עם <span class="spec">דגש בקשת</span></h1>
    <p class="sub on-dark" style="font-size:32px;text-align:center;max-width:1080px;">משפט פתיחה תמציתי שמגדיר את מטרת המפגש וקהל היעד.</p>
    <div class="specbar" style="width:280px;height:8px;border-radius:999px;"></div>
  </div>
</div>
```

---

## 3. Template 2 — Section Divider (Dark Glow)

```html
<div class="page dark fx col ac jc">
  <div class="wm on-dark"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.35));"></div>
  <div class="fx col ac" style="gap:26px;text-align:center;max-width:1300px;">
    <div class="eyebrow on-dark"><span class="dot"></span>פרק 01</div>
    <h1 class="title on-dark" style="font-size:84px;">נושא הפרק הבא עם <span class="spec">הדגשת מפתח</span></h1>
    <p class="sub on-dark" style="text-align:center;max-width:960px;">תיאור קצר של מה שנלמד בחלק זה.</p>
    <div class="specbar" style="width:220px;height:8px;border-radius:999px;"></div>
  </div>
</div>
```

---

## 4. Template 3 — Bullet Points Content Slide (Aurora Light)

```html
<div class="page aurora">
  <div class="wm"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.15));"></div>
  <div class="hd">
    <div class="eyebrow"><span class="dot"></span>נושא עיקרי</div>
    <h1 class="title">כותרת השקופית המרכזית</h1>
    <p class="sub">משפט מוביל המסכם את תמצית הנושא לפני הפירוט.</p>
  </div>
  <div class="glass f1 fx col" style="padding:46px 56px;gap:24px;margin-top:32px;justify-content:center;">
    <div class="fx ac" style="gap:18px;">
      <span style="width:12px;height:12px;border-radius:50%;background:#E4002B;flex-shrink:0;"></span>
      <span class="ink-t fw6" style="font-size:26px;">נקודה מרכזית ראשונה — ברורה וממוקדת (עד שורה וחצי).</span>
    </div>
    <div class="fx ac" style="gap:18px;">
      <span style="width:12px;height:12px;border-radius:50%;background:#FF6D00;flex-shrink:0;"></span>
      <span class="ink-t fw6" style="font-size:26px;">נקודה שנייה המציגה היבט טכנולוגי או תפעולי עם <span dir="ltr">Claude Sonnet 3.7</span>.</span>
    </div>
    <div class="fx ac" style="gap:18px;">
      <span style="width:12px;height:12px;border-radius:50%;background:#00A651;flex-shrink:0;"></span>
      <span class="ink-t fw6" style="font-size:26px;">נקודה שלישית המסבירה יתרון עסקי ישיר לקבוצת קשת.</span>
    </div>
  </div>
  <div class="take" style="margin-top:24px;">תובנה מרכזית — <span class="hi">הדגש הקריטי שחייבים לזכור</span>.</div>
</div>
```

---

## 5. Template 4 — Two-Column Comparison (Glass vs. Inkcard)

```html
<div class="page aurora">
  <div class="wm"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.15));"></div>
  <div class="hd">
    <div class="eyebrow"><span class="dot"></span>השוואה ארכיטקטונית</div>
    <h1 class="title">השוואת גישות ופתרונות</h1>
  </div>
  <div class="grid f1 ac" style="grid-template-columns:1fr 1fr;gap:36px;margin-top:32px;">
    <!-- Column 1: Standard / Light -->
    <div class="glass" style="padding:44px;">
      <div class="chip" style="background:rgba(90,106,122,.12);color:#5A6A7A;margin-bottom:20px;">הגישה הקלאסית / Basic</div>
      <div class="ink-t fw8" style="font-size:32px;line-height:1.2;margin-bottom:24px;">פתרון מקומי ללא סקילים</div>
      <div class="fx col" style="gap:16px;">
        <div class="fx ac" style="gap:12px;"><span style="width:10px;height:10px;border-radius:50%;background:#5A6A7A;flex-shrink:0;"></span><span class="muted fw6" style="font-size:23px;">הוראות פרומפט חוזרות בכל שיחה</span></div>
        <div class="fx ac" style="gap:12px;"><span style="width:10px;height:10px;border-radius:50%;background:#5A6A7A;flex-shrink:0;"></span><span class="muted fw6" style="font-size:23px;">בזבוז טוקנים וזמן בדיקה ידני</span></div>
      </div>
    </div>
    <!-- Column 2: Recommended / Inkcard -->
    <div class="inkcard" style="padding:44px;">
      <div class="chip" style="background:rgba(255,255,255,.14);color:#fff;margin-bottom:20px;">הגישה המומלצת / <span dir="ltr">Self-Verifying Skills</span></div>
      <div class="white fw8" style="font-size:32px;line-height:1.2;margin-bottom:24px;">ארכיטקטורת 4 שכבות מבוססת ראיות</div>
      <div class="fx col" style="gap:16px;">
        <div class="fx ac" style="gap:12px;"><span class="dot" style="width:12px;height:12px;flex-shrink:0;"></span><span class="white-2 fw6" style="font-size:23px;">אימות אוטומטי בינארי ותיקון שגיאות</span></div>
        <div class="fx ac" style="gap:12px;"><span class="dot" style="width:12px;height:12px;flex-shrink:0;"></span><span class="white-2 fw6" style="font-size:23px;">חיסכון של 85% בזמן עיבוד ועריכה</span></div>
      </div>
    </div>
  </div>
</div>
```

---

## 6. Template 5 — Stat & Metric Slide (Bars + Big Number)

```html
<div class="page aurora">
  <div class="wm"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.15));"></div>
  <div class="hd">
    <div class="eyebrow"><span class="dot"></span>ביצועים ומדדים</div>
    <h1 class="title">אימפקט עסקי ומדדי יעילות</h1>
  </div>
  <div class="grid f1 ac" style="grid-template-columns:1.4fr 1fr;gap:40px;margin-top:36px;">
    <div class="glass" style="padding:44px 50px;">
      <div class="fx col" style="gap:26px;">
        <div class="fx col" style="gap:10px;">
          <div class="fw7 ink-t" style="font-size:23px;">עבודה ידנית ללא סקיל (דקות לשקופית)</div>
          <div class="bartrack"><div class="barfill f-red" style="width:90%;">45 דק'</div></div>
        </div>
        <div class="fx col" style="gap:10px;">
          <div class="fw7 ink-t" style="font-size:23px;">עם סקיל מבוסס <span dir="ltr">AI Skills</span> (דקות למצגת מלאה)</div>
          <div class="bartrack"><div class="barfill f-green" style="width:20%;">2 דק'</div></div>
        </div>
      </div>
    </div>
    <div class="inkcard fx col ac jc" style="padding:40px;text-align:center;gap:10px;">
      <div class="bignum spec">×22</div>
      <div class="white fw7" style="font-size:26px;line-height:1.35;">האצת זמני ההפקה והדיוק של מצגות קשת</div>
    </div>
  </div>
  <div class="take" style="margin-top:28px;">שורה תחתונה — <span class="hi">מעבר מאוטומציה פשוטה למערכת אימות אוטונומית</span>.</div>
</div>
```

---

## 7. Template 6 — Step-by-Step Flow (Aurora Light)

```html
<div class="page aurora">
  <div class="wm"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.15));"></div>
  <div class="hd" style="margin-bottom:34px;">
    <div class="eyebrow"><span class="dot"></span>תהליך עבודה</div>
    <h1 class="title">שלבי היישום של הפתרון</h1>
  </div>
  <div class="glass f1 fx col" style="padding:44px 54px;gap:26px;justify-content:center;">
    <div class="fx ac" style="gap:22px;">
      <div class="numchip" style="background:#E4002B;">1</div>
      <div><div class="ink-t fw8" style="font-size:28px;">הגדרת בריף ותוכן מקור</div><div class="muted fw5" style="font-size:22px;margin-top:4px;">קליטת מסמך או נקודות מפתח ע"י הסקיל.</div></div>
    </div>
    <div class="fx ac" style="gap:22px;">
      <div class="numchip" style="background:#FF6D00;">2</div>
      <div><div class="ink-t fw8" style="font-size:28px;">המרת תוכן לתבניות מעוצבות</div><div class="muted fw5" style="font-size:22px;margin-top:4px;">בניית קובץ HTML מלא בעל מבנה 1920×1080.</div></div>
    </div>
    <div class="fx ac" style="gap:22px;">
      <div class="numchip" style="background:#00A651;">3</div>
      <div><div class="ink-t fw8" style="font-size:28px;">אימות מבוסס ראיות ותיקון שגיאות</div><div class="muted fw5" style="font-size:22px;margin-top:4px;">בדיקה בינארית מלאה לפי הצ'קליסט.</div></div>
    </div>
  </div>
</div>
```

---

## 8. Template 7 — Closing Summary Grid (Aurora Light)

```html
<div class="page aurora fx col ac jc">
  <div class="wm"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.15));"></div>
  <div style="width:100%;">
    <div class="fx col ac" style="gap:12px;text-align:center;margin-bottom:28px;">
      <div class="eyebrow"><span class="dot"></span>לסיכום</div>
      <h1 class="title" style="font-size:56px;">עקרונות המפתח להטמעה</h1>
    </div>
    <div class="grid" style="grid-template-columns:repeat(3,1fr);gap:20px;">
      <div class="glass fx col" style="padding:30px 24px;gap:14px;background:rgba(255,255,255,.94);">
        <div class="numchip specbar" style="width:48px;height:48px;font-size:24px;">1</div>
        <div class="ink-t fw8" style="font-size:22px;line-height:1.25;">סטנדרט מותג קשיח</div>
        <div class="muted fw6" style="font-size:18px;line-height:1.45;">שמירה על פלטת קשת, לוגו רשמי וגופן Heebo בלבד.</div>
      </div>
      <div class="glass fx col" style="padding:30px 24px;gap:14px;background:rgba(255,255,255,.94);">
        <div class="numchip specbar" style="width:48px;height:48px;font-size:24px;">2</div>
        <div class="ink-t fw8" style="font-size:22px;line-height:1.25;">אימות בינארי אוטונומי</div>
        <div class="muted fw6" style="font-size:18px;line-height:1.45;">בדיקת כל שקופית לפי ראיות וקריטריונים ברורים.</div>
      </div>
      <div class="glass fx col" style="padding:30px 24px;gap:14px;background:rgba(255,255,255,.94);">
        <div class="numchip specbar" style="width:48px;height:48px;font-size:24px;">3</div>
        <div class="ink-t fw8" style="font-size:22px;line-height:1.25;">תאימות מלאה להדפסה</div>
        <div class="muted fw6" style="font-size:18px;line-height:1.45;">קובץ HTML עצמאי המוכן ל-Print-to-PDF ב-16:9.</div>
      </div>
    </div>
  </div>
</div>
```
