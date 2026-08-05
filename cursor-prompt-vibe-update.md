# Cursor Prompt — Full Rebuild of vibe-coding-guide.html

## Context

You are working on `vibe-coding-guide.html` — a Hebrew RTL slide deck for Keshet's internal builder training.

The reference file is `token-economics-guide.html`. It is the **canonical Keshet presentation** and defines the visual standard all guides must follow. Your job is to bring `vibe-coding-guide.html` to full visual and structural parity with that reference, while applying the content changes listed below.

---

## Part 1 — Full CSS & Structure Migration (apply first, before any content changes)

### 1.1 Canvas: upgrade from 1280×720 to 1920×1080

In `vibe-coding-guide.html`, change every occurrence of:
- `width: 1280px` → `width: 1920px`
- `height: 720px` → `height: 1080px`
- `size: 1280px 720px` → `size: 1920px 1080px`
- In the JS resize function: `window.innerWidth / 1280, window.innerHeight / 720` → `window.innerWidth / 1920, window.innerHeight / 1080`

### 1.2 Slide padding
Change `.page` padding from `56px 72px` to `74px 104px 56px` (matches token-economics).

### 1.3 Logo size and position
Every `.wm` logo image: change `height: 44px` → `height: 56px`.
`.wm` CSS: change `top:32px; left:48px` → `top:52px; left:104px`.

### 1.4 Replace the entire CSS block
Open `token-economics-guide.html` and copy its full `<style>` block verbatim into `vibe-coding-guide.html`, replacing the existing `<style>` block. This imports the canonical class system: `.aurora`, `.dark`, `.glass`, `.inkcard`, `.spec`, `.specbar`, `.hd`, `.take`, `.eyebrow`, `.title`, `.sub`, `.dot`, `.wm`, `.barrow`, `.barfill`, `.numchip`, `.bignum`, `.fx`, `.col`, `.ac`, `.jc`, `.f1`, `.grid`, `.chip`, `.tok`, `.fw5–.fw8`, `.ink-t`, `.muted`, `.white`, `.white-2`, `.f-red`, `.f-orange`, `.f-blue`, `.f-cyan`, `.f-green`, `.f-purple` — plus the `@media print` and animation rules.

### 1.5 Fix color tokens across all slides
After copying the CSS, do a find-and-replace in the HTML slide markup (only inside `<div id="deck">`) to unify the color palette:
- `#6CC24A` → `#00A651` (canonical Keshet green)
- `#00A3E0` → `#00B4D8` (canonical Keshet cyan)
- `#6F2DA8` → `#7B2D8E` (canonical Keshet purple)
- `#F7941D` → `#FF6D00` (canonical Keshet orange)
- `#6C6E72` → `#5A6A7A` (muted text token)

### 1.6 Migrate inline styles to classes
Go through every slide `<div class="page ...">`. Where the code uses heavy inline style attributes to recreate layouts that match `.glass`, `.inkcard`, `.hd`, `.take`, `.eyebrow`, `.title`, `.sub`, etc., replace them with the class equivalents from the token-economics CSS system.

Key patterns to replace:
- A `<div>` with `background:rgba(255,255,255,.6); border-radius:20px; box-shadow:...` → `class="glass"`
- A `<div>` with `background:linear-gradient(150deg,#0A1930,#13294c); color:#fff; border-radius:20px` → `class="inkcard"`
- A stacked column of eyebrow + title + sub → wrap in `<div class="hd">` and use `<div class="eyebrow">`, `<h1 class="title">`, `<p class="sub">`
- A rainbow gradient text span → `class="spec"`
- A rainbow gradient fill div → `class="specbar"`
- A bottom strip with dark background → `class="take"` with `<span class="hi">` for yellow highlights
- On `.dark` slides: add `.on-dark` to `.wm`, `.eyebrow`, `.title`, `.sub`

---

## Part 2 — Content Changes (apply after the migration above)

### Change 1 — Remove slide 13: "מצפן הפלטפורמות"
Delete the entire `<div class="page aurora">` that contains the platform compass (X/Y axis chart with Replit, Lovable, Base44, Claude Cowork). Remove it completely.

---

### Change 2 — Insert new intro slide before slide 3 (before "האנטומיה של אפליקציה")
Insert a new Aurora slide immediately before the current "האנטומיה של אפליקציה: מסעדת הנתונים" slide.

Content:
- Eyebrow: `"02 · האנטומיה"`
- Title: `"לפני שמתחילים — התמונה הגדולה"`
- Sub: `"כל אפליקציה בנויה משלושה אזורים. הנה ההקבלה הוויזואלית שתוביל אותנו בכל המדריך."`
- A large centered image placeholder: `<img src="assets/vibe/restaurant-full.png" alt="מסעדה — האנלוגיה המלאה">` with `height: 420px; width: auto; object-fit: contain;`. If the file doesn't exist, show a styled placeholder `<div>` with `background: rgba(10,25,48,.06); border-radius:20px; height:420px; display:flex; align-items:center; justify-content:center;` and a label: `"[תמונה: מסעדה שלמה עם שלושת האזורים]"`.
- Use `.glass` card as wrapper if needed for visual balance.
- Logo `.wm` on slide, rainbow top stripe.

---

### Change 3 — Slide 7 (summary table): update Frontend functional role
In the anatomy summary table, find the cell containing `"אינטראקציה ובדיקות קלט בסיסיות"` (under the Frontend / תפקיד פונקציונלי column) and replace the text with:
**`"שכבת התקשורת והאינטגרציה מול הלקוח, הנגשת הנתונים וקליטתם"`**

---

### Change 4 — Slide 8 (model selection): update title and eyebrow
- Change the eyebrow label from `"03 · המנוע"` (or similar) to: `"03 · כלכלת מודלים"`
- Change the slide title from `"בחירת המנוע החכם: משפחת Claude"` to: **`"כלכלת מודלים: בחירת המנוע המתאים לכל משימה"`**

---

### Change 5 — Slide 9 (knowledge hierarchy): move + rename + add takeaway
Move the slide currently titled `"היררכיית הנגשת הידע: איך קלוד לומד עלינו?"` (Dark slide, 3 stacked rows) to appear **after** the MCP slide (current slide 10), not before it.

Also:
- Change the title to: **`"כיצד מלמדים את קלוד להכיר את הארגון שלנו?"`**
- Add a `.take` strip at the bottom of that slide:
  `"רמת ההקשר שתתנו לקלוד קובעת ישירות את איכות הפלט. "` + `<span class="hi">"ככל שהמידע מובנה ועקבי יותר — התשובות מדויקות יותר."</span>`

---

### Change 6 — Slide 10 (MCP): add bottom takeaway strip
At the end of the MCP slide's inner content, before the closing `</div>`, add a `.take` strip:

```html
<div class="take" style="margin-top:24px;">אנו נפתח וננגיש את כלי החיבוריות בהתאם לצרכים שלכם ולאישורי אבטחת המידע. <span class="hi">שתפו אותנו כשאתם נתקלים בבקשות שלא קיימות עדיין.</span></div>
```

---

### Change 7 — Slide 11 (CI/CD): update title + add bottom takeaway
- Change the slide title from `"מארגז החול לסביבת ייצור: מסוע ה-CI/CD"` to: **`"הפצה של פרויקט: מארגז החול לסביבת ייצור"`**
- Add a `.take` strip at the bottom:
  `"תהליך ההפצה דורש מכם מחויבות לתיעוד ואישור מנהלים. "` + `<span class="hi">"אנחנו נעביר את הפרויקט תהליכי בקרת קוד ואבטחה אוטומטיים."</span>`

---

### Change 8 — Slide 12 ("האנטומיה של פרויקט Vibe Coding מוצלח"): full rewrite
The current slide is unclear. Replace it entirely with a **Dark** slide structured as follows:

**Title:** `"תכננו נכון: האנטומיה של פרויקט Vibe Coding מוצלח"`
**Sub (yellow):** `"לא מספיק שזה עובד — זה צריך להיות בנוי נכון מהיסוד."`

**Body:** A 2×2 grid of `.glass` cards (on dark background, use `background:rgba(255,255,255,.09); border:1px solid rgba(255,255,255,.14); border-radius:20px; padding:36px 32px;`):

| Card | Title | Body |
|------|-------|------|
| 1 | `"הגדירו כוכב צפון ברור"` | `"יעד מדיד, הבנת הארכיטקטורה ורכיבי המערכת — כולל דשבורד עלויות. הגדרה ברורה = פיתוח מהיר ומדויק."` |
| 2 | `"Plan & Review לפני קוד"` | `"לפני כל פיצ'ר: תכננו עם קלוד, בקשו ממנו לסקור את הקוד הקיים. כך תמנעו חוב טכני שמצטבר."` |
| 3 | `"אבטחה ותיעוד"` | `"סיסמאות ב-.env בלבד, לא בקוד. תעדו כל פיצ'ר ובקשו אישור מנהל. Audit log אוטומטי ב-Claude Enterprise."` |
| 4 | `"הפצה מבוקרת"` | `"CI/CD לבדיקות אוטומטיות. בהמשך נוסיף Skills לדיבאג ומעקב — כולל מערכת Audit log ייעודית."` |

Add a `.take` strip at the bottom:
`"בהמשך "` + `<span class="hi">"נוסיף סקילים שיעזרו לכם לעקוב ולדאבג"</span>` + `" — כולל מערכת Audit log."`

---

### Change 9 — Slide 14 ("ספר המהלכים"): three updates

**9a — Update Step 1 (North Star):**
Change step 1 body text from `"הגדירו יעד מדיד: דשבורד המציג 5 חריגות לחודש."` to:
`"הגדירו יעד מדיד ובינו את הארכיטקטורה ורכיבי המערכת — כולל דשבורד עלויות. הגדרה ברורה = פיתוח מהיר יותר."`

**9b — Add new step between step 2 and step 3: "Plan & Review":**
After the existing step 2 card, insert a new step card with border color `#FFD100`:
- Number: `3` (renumber subsequent steps accordingly: old 3→4, old 4→5)
- Title: `"Plan & Review (לפני שמתחילים לכתוב)"`
- Body: `"בקשו מקלוד לתכנן ולסקור את הקוד הקיים לפני כל פיצ'ר חדש. זה מונע חוב טכני שמצטבר."`

**9c — Fix the debugging card (step 2 in the dark right panel):**
Find the text: `"לא נלחצים ולא מנסים לקרוא אותה."` (currently debugging step 2)
Replace with: **`"שואלים את ה-AI על מה מדברת השגיאה, מבקשים הסבר ומבקשים לתקן."`**

---

### Change 10 — Insert new slide: "מילון הבילדר"
Insert a new **Aurora** slide after the CI/CD slide (slide 11) and before the "תכננו נכון" slide.

**Eyebrow:** `"מילון הבילדר"`
**Title:** `"מושגי יסוד שכדאי להכיר"`
**Sub:** `"לא חייבים לדעת לכתוב קוד — אבל חייבים להכיר את השפה כדי לתקשר עם Claude ועם ה-IT."`

**Body:** A 2×3 grid of `.glass` cards, each with a term and explanation:

| Term | Explanation |
|------|-------------|
| **Git & Repository** | `"ה'ספריה' של הפרויקט — כל שינוי בקוד נשמר בהיסטוריה. ה-Repo הוא התיקיה המרכזית שמכילה הכל."` |
| **Commit** | `"שמירת שינויים עם הודעה מתארת — כמו Ctrl+S עם הערה בשוליים. מאפשר לחזור לכל גרסה קודמת."` |
| **Terminal / Bash** | `"חלון שמאפשר פקודות ישירות למחשב. Claude יכתוב לכם את הפקודות — אתם רק מדביקים ומריצים."` |
| **Stack** | `"שכבות הטכנולוגיה של הפרויקט — שפה, מסגרת עבודה, בסיס נתונים. Claude יבחר עבורכם."` |
| **API Key & .env file** | `"המפתח לשירות חיצוני. לעולם לא מכניסים לקוד — שומרים בקובץ .env שנשאר פרטי."` |
| **Cache** | `"שמירה זמנית של נתונים לגישה מהירה. יכול להיות מקומי, ברשת, או בענן."` |

**Takeaway strip:**
`"כשאתם שואלים את Claude שאלות על הפרויקט — "` + `<span class="hi">"השתמשו בשמות הנכונים."</span>` + `" זה מה שמייצר תשובות מדויקות."`

---

## Part 3 — Final Checks

After all changes:

1. **Renumber eyebrow labels** (`"01 ·"`, `"02 ·"`, etc.) sequentially from top to bottom in the new slide order.
2. **Verify every slide** has the logo `.wm` with `height: 56px` and the rainbow top stripe (`height:3px; background: var(--ks)`).
3. **Verify `.on-dark`** is applied to `.wm`, `.eyebrow`, `.title`, `.sub` on every `.dark` slide.
4. **No inline color values** outside the Keshet palette. Check for any stray `#6CC24A`, `#00A3E0`, `#6F2DA8`, `#F7941D`, `#6C6E72` and replace as per Part 1.5.
5. **No emoji** anywhere in the file.
6. **All foreign terms** (Claude, Cursor, Git, Commit, API, Backend, Frontend, CI/CD, MCP, etc.) wrapped in `<span dir="ltr">...</span>`.
7. The JS `resizeDeck()` function must scale to `1920 / 1080` (not 1280/720).
8. Save the file as `vibe-coding-guide.html` in the same folder.

---

## Final slide order (after all changes)

1. Cover (Dark)
2. Democratization — Past / Future (Aurora)
3. *(NEW)* Big picture — restaurant visual intro (Aurora)
4. Anatomy — restaurant 3 zones (Aurora)
5. Frontend detail (Aurora)
6. Backend detail (Aurora)
7. API detail (Aurora)
8. Anatomy summary table (Aurora)
9. Model economics — Haiku / Sonnet / Opus (Aurora)
10. MCP protocol (Aurora)
11. *(MOVED)* How Claude learns about our org / knowledge hierarchy (Dark)
12. CI/CD deployment (Aurora)
13. *(NEW)* Builder's glossary — Git, Commit, Terminal, Stack, API Key, Cache (Aurora)
14. "Plan it right" — anatomy of a successful Vibe project (Dark)
15. Playbook — steps + debugging card (Aurora)
16. Closing — "The power to build is in your hands" (Dark)
