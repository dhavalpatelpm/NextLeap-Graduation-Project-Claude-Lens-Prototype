# ✳ Claude Lens — Prototype README

> **NL Claude | NextLeap PM Fellowship | Cohort C-45 | May 2026**  
> **Product:** Claude (Anthropic) | **Role:** Growth PM  
> **Problem:** AI outputs look convincing but may contain weak reasoning. Users can't evaluate quality, trust, or when to rely on their own judgment.

---

## 🧠 What is Claude Lens?

**Claude Lens** is an inline transparency panel that surfaces Claude's assumptions, flags uncertain parts specifically, and gives users an actionable verify checklist — all alongside every response. It is collapsible by default so users who don't need it aren't slowed down.

Claude Lens solves the **Legibility Gap** — not a capability gap. The problem isn't that Claude is wrong. The problem is that users **can't tell when it might be**.

---

## 🎯 The Problem it Solves

| Hypothesis | What We Found | Evidence |
|---|---|---|
| H1 — Confidence Illusion | 68% trust polished outputs more even when they know they shouldn't | Survey Q6, n=54 |
| H2 — Verification Gap | 0/7 interviewees had a structured evaluation method | Interviews |
| H3 — Stakes Mismatch | All users calibrate trust by perceived stakes, not actual output quality | Survey Q4 + Interviews |
| H4 — Calibration Loop | No one improved at evaluating AI — only at prompting it | Himanshi, Dhairya, Interviews |

---

## ✨ Core Features

### 1. 📌 Assumption Surfacing (Blue)
Claude shows what it **assumed** about your intent, context, or domain before generating the response. If the assumption is wrong, the entire response may be wrong.

> *"62.5% of survey respondents want Claude's assumptions surfaced"* — Survey Q14, n=54

### 2. ⚠️ Uncertainty Flagging (Amber)
Claude highlights the **exact sentence or claim** it is less certain about — not a generic page-level disclaimer. Inline, specific, and visible.

> *"All AI tools have a warning at the bottom. No one sees. Specific inline flagging is what I'd love."* — Meet Patel, Interview

### 3. 🔍 Verify Checklist (Red)
Claude tells users **specifically what to check, where to check it, and why** — converting verification intent into verification action.

> *"32.5% don't verify because they don't know what to check or where to look"* — Survey Q9, n=54

### 4. ⊕ Dig Deeper
When users click **Dig Deeper**, Claude asks a targeted follow-up question. Based on the user's answer, it generates a **completely new refined response** in the chat — with fewer flags and more accuracy.

> *"Show me the parameters — the evals — it used. Then I can filter and trust it better."* — Apoorv, Interview

### 5. 📈 Calibration Tracker
Tracks user engagement with Lens over time. As users engage more deeply (Dig Deeper > Accept), their calibration score improves — building evaluation judgment, not just AI dependence.

> *"Intellectually we are going dumb. AI has made a limit for humans."* — Himanshi Mongia, APM

### 6. 🔄 Toggle On/Off
Lens is collapsible by default — zero friction for fast users, fully available for cautious ones. Toggle Lens and Calibration independently from the sidebar.

---

## 🖥️ How to Use the Prototype

### Option 1 — Open Locally
```bash
# Download the file
# Open in any modern browser (Chrome recommended)
open claude_lens_prototype.html
```

### Option 2 — Host on Lovable
Use the prompt below to deploy a hosted version:

> *"Build a working prototype of Claude Lens — an AI output trust and evaluation feature. It should look like the Claude chat interface with a sidebar for scenarios (Career Prep, Research, Writing, Code). After each AI response, show a collapsible Claude Lens Panel with 3 sections: blue Assumption cards, amber Uncertain cards, and red Verify cards. Add 3 action buttons: Dismiss, Looks Good, Dig Deeper. Include a right panel with interview quotes and survey statistics. Use Claude's brand colors — orange #C85A2A, cream background #F7F5F2. Make it fully interactive and mobile responsive."*

---

## 🧪 Test Scenarios

### Scenario 1 — 💼 Career Prep
**Test prompt:**
```
Write a cover letter for a Senior Product Manager role at a fintech startup. I have 3 years of experience.
```
**What Lens will flag:**
- 📌 Assumed you have cross-functional leadership experience
- ⚠️ "Data-driven PM" is a generic claim — hard to differentiate
- 🔍 Check the JD for specific fintech domain requirements

**Dig Deeper question:** *"Do you have specific metrics from your past roles?"*

---

### Scenario 2 — 🔬 Research Task
**Test prompt:**
```
Summarise the key reasons why AI adoption in Indian enterprises is growing rapidly in 2025.
```
**What Lens will flag:**
- 📌 Summary based on training data up to early 2025 — stats may have changed
- ⚠️ Government AI Mission funding figure — verify with official sources
- 🔍 Cross-check NASSCOM 2025 report and TRAI data

**Dig Deeper question:** *"What will you use this research for?"*

---

### Scenario 3 — ✍️ Content Writing
**Test prompt:**
```
Write a LinkedIn post announcing that I'm launching a PM newsletter focused on AI product strategy.
```
**What Lens will flag:**
- 📌 Used [Newsletter Name] placeholder — must be filled before posting
- ⚠️ "For the past few years" — verify this matches your real timeline
- 🔍 Check that your newsletter signup link is ready before posting

**Dig Deeper question:** *"Who is your primary LinkedIn audience?"*

---

### Scenario 4 — 💻 Code Review
**Test prompt:**
```
Review this Python function and tell me if it's production-ready: def get_user(id): return db.query('SELECT * FROM users WHERE id=' + str(id))
```
**What Lens will flag:**
- 📌 Assumed db.query() accepts positional arguments — verify your driver
- ⚠️ ? vs %s placeholder syntax differs by database
- 🔍 Run bandit security scan to catch other vulnerabilities

**Dig Deeper question:** *"Which database are you using?"*

---

## 🔁 The Dig Deeper Flow

```
User clicks "⊕ Dig Deeper"
        ↓
Claude asks a targeted follow-up question
        ↓
User selects one of 4 options
        ↓
✳ "Claude is generating your refined response..."
        ↓
New ✅ Claude message appears in chat
        ↓
Refined Lens Panel shows FEWER flags than original
        ↓
User clicks "✓ Accept this refined output"
        ↓
Calibration score updates +15 points
```

---

## 🎨 Design Decisions

| Decision | Rationale |
|---|---|
| **Inline panel, not bottom disclaimer** | Meet: "Warnings at the bottom — no one sees." |
| **Specific flags, not generic score** | Apoorv: "A number I can't act on doesn't help me." |
| **Collapsible by default** | Shubhi: "I just want to get my work done." |
| **New response, not just a note** | Users need to see the actual improvement, not a tooltip |
| **3-colour system (Blue/Amber/Red)** | Intuitive severity — matches mental model of traffic lights |
| **Calibration tracker** | Fixes H4 — builds judgment, not just dependence |

---

## 📊 Research Backing

| Metric | Value | Source |
|---|---|---|
| Users want assumptions shown | 62.5% | Survey Q14, n=54 |
| Positive reaction to Lens panel | 65% | Survey Q15, n=54 |
| Top trust signal | AI admits uncertainty (3.80/5) | Survey Q7, n=54 |
| Trust polished outputs more | 68% | Survey Q6, n=54 |
| Copy-paste without checking | 30% | Survey Q3, n=54 |
| Over-skepticism has slowed them | 69% | Survey Q12, n=54 |
| Structured evaluation method | 0/7 | Interviews, n=7 |

---

## 🛠️ Technical Details

| Property | Value |
|---|---|
| **Type** | Single-file HTML prototype |
| **Dependencies** | Google Fonts (Sora, JetBrains Mono) — CDN only |
| **Framework** | Vanilla HTML, CSS, JavaScript — no build step required |
| **Browser support** | Chrome, Firefox, Safari, Edge (modern versions) |
| **File size** | ~85KB |
| **Responsive** | Yes — works on desktop and tablet |

---

## 📁 File Structure

```
claude_lens_prototype.html   ← Main prototype file (open this)
README.md                    ← This file
```

---

## 🔗 Links

| Resource | Link |
|---|---|
| Prototype | [claude_lens_prototype.html] |
| Survey (n=54) | [Google Sheets Link] |
| Interview Transcripts | [Google Drive Link] |
| Detailed Segment | [Google Drive Link] |
| Solution Ideation Doc | [Google Drive Link] |
| Slide Deck | [Canva Link] |

---

## 👤 About This Project

**Fellowship:** NextLeap PM Fellowship | Cohort C-45  
**Product:** Claude by Anthropic  
**Role:** PM, Growth Team  
**Research:** Survey n=54 + Interviews n=7 | May 2026  
**Submission deadline:** June 3, 2026 — 2:59 PM IST  

---

*Claude Lens — because the path to verification should never be invisible.*
