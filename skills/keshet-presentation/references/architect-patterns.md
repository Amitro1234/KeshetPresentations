# AI Solutions Architect Patterns & Components

This guide provides specialized slide patterns tailored for an **AI Solutions Architect** creating training decks, technical reviews, system designs, and LLM economic breakdowns for Keshet.

---

## 1. System Design & AI Pipeline Flow Slide

Use this pattern to represent RAG workflows, agentic chains, or multi-model routing.

```html
<div class="page aurora">
  <div class="wm"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.15));"></div>
  <div class="hd">
    <div class="eyebrow"><span class="dot"></span><span dir="ltr">System Architecture</span></div>
    <h1 class="title">ארכיטקטורת מערכת: <span class="spec">Multi-Agent RAG Pipeline</span></h1>
    <p class="sub">זרימת מידע משלב קליטת הבקשה, דרך אחזור וקטורי ועד הפקת התוצר.</p>
  </div>
  
  <div class="grid f1 ac" style="grid-template-columns:repeat(4,1fr);gap:20px;margin-top:32px;">
    <!-- Step 1 -->
    <div class="glass fx col" style="padding:28px 22px;gap:14px;border-top:5px solid #E4002B;">
      <div class="fx jb ac">
        <span class="chip" style="background:rgba(228,0,43,0.12);color:#E4002B;font-size:16px;">שלב 01</span>
        <span class="muted fw6" style="font-size:16px;">Ingestion</span>
      </div>
      <div class="ink-t fw8" style="font-size:22px;">קליטת פרומפט</div>
      <div class="muted fw5" style="font-size:17px;line-height:1.4;">סינון תוכן ובדיקת הרשאות באמצעות Guardrails.</div>
    </div>
    
    <!-- Step 2 -->
    <div class="glass fx col" style="padding:28px 22px;gap:14px;border-top:5px solid #FF6D00;">
      <div class="fx jb ac">
        <span class="chip" style="background:rgba(255,109,0,0.12);color:#FF6D00;font-size:16px;">שלב 02</span>
        <span class="muted fw6" style="font-size:16px;">Retrieval</span>
      </div>
      <div class="ink-t fw8" style="font-size:22px;">אחזור הקשר</div>
      <div class="muted fw5" style="font-size:17px;line-height:1.4;">חיפוש היברידי ב-Vector DB ומאגרי מידע ארגוניים.</div>
    </div>

    <!-- Step 3 -->
    <div class="glass fx col" style="padding:28px 22px;gap:14px;border-top:5px solid #00A651;">
      <div class="fx jb ac">
        <span class="chip" style="background:rgba(0,166,81,0.12);color:#00A651;font-size:16px;">שלב 03</span>
        <span class="muted fw6" style="font-size:16px;">Reasoning</span>
      </div>
      <div class="ink-t fw8" style="font-size:22px;">עיבוד <span dir="ltr">LLM</span></div>
      <div class="muted fw5" style="font-size:17px;line-height:1.4;">הפעלת סוכנים אוטונומיים עם חשיבה מדורגת.</div>
    </div>

    <!-- Step 4 -->
    <div class="glass fx col" style="padding:28px 22px;gap:14px;border-top:5px solid #00B4D8;">
      <div class="fx jb ac">
        <span class="chip" style="background:rgba(0,180,216,0.12);color:#00B4D8;font-size:16px;">שלב 04</span>
        <span class="muted fw6" style="font-size:16px;">Verification</span>
      </div>
      <div class="ink-t fw8" style="font-size:22px;">אימות ופליטה</div>
      <div class="muted fw5" style="font-size:17px;line-height:1.4;">בדיקת תוצרים מול שאלון בינארי והחזרה למשתמש.</div>
    </div>
  </div>

  <div class="take" style="margin-top:24px;">תובנה ארכיטקטונית — <span class="hi">הפרדה בין שלב החשיבה לשלב האימות מבטיחה דיוק ומניעת הזיות</span>.</div>
</div>
```

---

## 2. Token Economics & Cost Breakdown Slide

Ideal for pricing breakdowns, context caching optimizations, and ROI comparisons.

```html
<div class="page dark">
  <div class="wm on-dark"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.35));"></div>
  <div class="hd">
    <div class="eyebrow on-dark"><span class="dot"></span><span dir="ltr">Token Economics</span></div>
    <h1 class="title on-dark">מודל עלויות וניצול <span class="spec">Prompt Caching</span></h1>
    <p class="sub on-dark">חיסכון של עד 90% בעלויות קריאה על ידי שמירת Context בזיכרון מטמון.</p>
  </div>

  <div class="grid f1 ac" style="grid-template-columns:1.2fr 1fr;gap:36px;margin-top:36px;">
    <!-- Pricing Matrix Table -->
    <div class="glass fx col" style="padding:36px 40px;gap:18px;background:rgba(255,255,255,0.08);border:1px solid rgba(255,255,255,0.15);">
      <div class="white fw8" style="font-size:26px;margin-bottom:8px;">השוואת מחירי טוקנים ל-1M</div>
      
      <div class="fx jb ac" style="padding-bottom:12px;border-bottom:1px solid rgba(255,255,255,0.1);">
        <span class="white-2 fw6" style="font-size:20px;">טוקנים רגילים (Input)</span>
        <span class="white fw8" style="font-size:22px;" dir="ltr">$3.00</span>
      </div>
      
      <div class="fx jb ac" style="padding-bottom:12px;border-bottom:1px solid rgba(255,255,255,0.1);">
        <span class="white-2 fw6" style="font-size:20px;">כתיבה למטמון (Cache Write)</span>
        <span class="white fw8" style="font-size:22px;" dir="ltr">$3.75</span>
      </div>

      <div class="fx jb ac" style="padding-bottom:12px;border-bottom:1px solid rgba(255,255,255,0.1);">
        <span class="spec fw8" style="font-size:22px;">קריאה ממטמון (Cache Read)</span>
        <span class="white fw8" style="font-size:24px;color:#00A651;" dir="ltr">$0.30 (-90%)</span>
      </div>

      <div class="fx jb ac">
        <span class="white-2 fw6" style="font-size:20px;">טוקנים פלט (Output)</span>
        <span class="white fw8" style="font-size:22px;" dir="ltr">$15.00</span>
      </div>
    </div>

    <!-- Key Metric Highlight -->
    <div class="inkcard fx col ac jc" style="padding:40px;text-align:center;gap:12px;background:linear-gradient(150deg,#0e2344,#1b3c6f);">
      <div class="chip" style="background:rgba(0,166,81,0.2);color:#00A651;font-size:18px;">חיסכון מוכח לקשת</div>
      <div class="bignum spec" style="font-size:130px;">88%</div>
      <div class="white fw7" style="font-size:24px;">ירידה בעלויות ה-API החודשיות בעבודה עם סקילים מותאמים</div>
    </div>
  </div>
</div>
```

---

## 3. AI Security & Guardrails Architecture Slide

```html
<div class="page dark">
  <div class="wm on-dark"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.35));"></div>
  <div class="hd">
    <div class="eyebrow on-dark"><span class="dot"></span><span dir="ltr">Enterprise AI Security</span></div>
    <h1 class="title on-dark">מדיניות אבטחה והגנת מידע בקשת</h1>
    <p class="sub on-dark">שלושת עמודי התווך להפעלת מודלי שפה בסביבה ארגונית מוגנת.</p>
  </div>

  <div class="grid f1 ac" style="grid-template-columns:repeat(3,1fr);gap:24px;margin-top:36px;">
    <div class="glass fx col" style="padding:32px 26px;gap:14px;background:rgba(255,255,255,0.07);border-color:rgba(228,0,43,0.4);">
      <div class="numchip" style="background:#E4002B;width:44px;height:44px;font-size:22px;">01</div>
      <div class="white fw8" style="font-size:24px;">אפס אימון על מידע</div>
      <div class="white-2 fw5" style="font-size:18px;line-height:1.45;">הסכמי <span dir="ltr">Zero Data Retention</span> עם ספקי המודלים. אין שימוש במידע לצורכי אימון.</div>
    </div>

    <div class="glass fx col" style="padding:32px 26px;gap:14px;background:rgba(255,255,255,0.07);border-color:rgba(0,166,81,0.4);">
      <div class="numchip" style="background:#00A651;width:44px;height:44px;font-size:22px;">02</div>
      <div class="white fw8" style="font-size:24px;">הגנת פרטיות ו-PII</div>
      <div class="white-2 fw5" style="font-size:18px;line-height:1.45;">אנונימיזציה אוטומטית של נתונים רגישים לפני שליחה למודל.</div>
    </div>

    <div class="glass fx col" style="padding:32px 26px;gap:14px;background:rgba(255,255,255,0.07);border-color:rgba(0,180,216,0.4);">
      <div class="numchip" style="background:#00B4D8;width:44px;height:44px;font-size:22px;">03</div>
      <div class="white fw8" style="font-size:24px;">בקרת גישה והרשאות</div>
      <div class="white-2 fw5" style="font-size:18px;line-height:1.45;">אינטגרציה מלאה עם <span dir="ltr">SSO / RBAC</span> של ארגון קשת.</div>
    </div>
  </div>
</div>
```
