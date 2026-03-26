# HTML Templates

All HTML: single self-contained `.html`, inline CSS, no external dependencies.

## Design System

Dark UI, glassmorphism, subtle animations. Banned: blue-purple gradients, `#7c5cfc`.

### Accent Palette (choose per topic)

| Vibe | accent-1 | accent-2 |
|------|----------|----------|
| Warm | `#f59e0b` | `#ef4444` |
| Nature | `#10b981` | `#06b6d4` |
| Elegant | `#e2e8f0` | `#f59e0b` |
| Bold | `#f43f5e` | `#fb923c` |
| Technical | `#06b6d4` | `#34d399` |

### Shared Rules

- CSS custom properties only — never hardcode colors
- Max width: `720px` centered, responsive `@media (max-width: 480px)`
- Glassmorphism: `backdrop-filter: blur(12px)` on surfaces
- Transitions: `cubic-bezier(0.4, 0, 0.2, 1)`
- Mesh gradient background (2-3 radial gradients with accent colors at low opacity)

## Roadmap Template (`roadmap.html`)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Learning Roadmap — {{TOPIC}}</title>
  <style>
    :root {
      --bg: #08080c;
      --surface: rgba(255,255,255,0.03);
      --surface-hover: rgba(255,255,255,0.08);
      --border: rgba(255,255,255,0.06);
      --text: #ededef;
      --text-secondary: rgba(255,255,255,0.55);
      --text-tertiary: rgba(255,255,255,0.3);
      --accent-1: /* CHOOSE */;
      --accent-2: /* CHOOSE */;
      --accent-gradient: linear-gradient(135deg, var(--accent-1), var(--accent-2));
      --green: #34d399; --amber: #fbbf24; --red: #f87171;
      --font-mono: 'SF Mono','Fira Code','JetBrains Mono',monospace;
      --font-sans: -apple-system,'Inter',system-ui,sans-serif;
      --radius: 12px;
      --mastered-pct: 0;
    }
    *{margin:0;padding:0;box-sizing:border-box}
    body{background:var(--bg);color:var(--text);font-family:var(--font-sans);
      min-height:100vh;display:flex;justify-content:center;
      background-image:
        radial-gradient(ellipse at 20% 0%, color-mix(in srgb, var(--accent-1) 8%, transparent) 0%, transparent 60%),
        radial-gradient(ellipse at 80% 100%, color-mix(in srgb, var(--accent-2) 6%, transparent) 0%, transparent 60%)}
    .container{max-width:720px;width:100%;padding:48px 24px}
    .header{text-align:center;margin-bottom:48px}
    .header h1{font-size:28px;background:var(--accent-gradient);-webkit-background-clip:text;-webkit-text-fill-color:transparent}
    .chips{display:flex;gap:8px;justify-content:center;margin-top:12px;flex-wrap:wrap}
    .chip{font-size:12px;color:var(--text-secondary);border:1px solid var(--border);border-radius:20px;padding:4px 12px}
    .ring-wrap{margin:24px auto;width:96px;height:96px;position:relative}
    .ring-wrap svg{transform:rotate(-90deg)}
    .ring-bg{fill:none;stroke:var(--border);stroke-width:6}
    .ring-fg{fill:none;stroke:url(#gradient);stroke-width:6;stroke-linecap:round;
      stroke-dasharray:264;stroke-dashoffset:calc(264 - 264 * var(--mastered-pct) / 100);transition:stroke-dashoffset .6s cubic-bezier(.4,0,.2,1)}
    .ring-label{position:absolute;inset:0;display:flex;align-items:center;justify-content:center;font-size:20px;font-weight:600}
    .timeline{position:relative;padding-left:32px}
    .timeline::before{content:'';position:absolute;left:7px;top:0;bottom:0;width:2px;
      background:linear-gradient(to bottom, var(--accent-1) calc(var(--mastered-pct) * 1%), var(--border) calc(var(--mastered-pct) * 1%))}
    .node{position:relative;margin-bottom:20px;padding:16px 20px;
      background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);
      backdrop-filter:blur(12px);transition:all .2s cubic-bezier(.4,0,.2,1)}
    .node:hover{background:var(--surface-hover);transform:translateX(4px)}
    .node::before{content:'';position:absolute;left:-29px;top:22px;width:12px;height:12px;border-radius:50%;border:2px solid var(--border);background:var(--bg)}
    .node.mastered::before{background:var(--green);border-color:var(--green)}
    .node.active::before{background:var(--accent-1);border-color:var(--accent-1);box-shadow:0 0 8px var(--accent-1);animation:pulse 2s infinite}
    .node.active{border-color:color-mix(in srgb, var(--accent-1) 30%, transparent)}
    .node.upcoming{opacity:.45}
    .node-title{font-size:15px;font-weight:600;margin-bottom:6px}
    .badge{font-size:11px;padding:2px 8px;border-radius:10px;display:inline-block;margin-right:8px}
    .badge.mastered{background:color-mix(in srgb, var(--green) 15%, transparent);color:var(--green)}
    .badge.active{background:color-mix(in srgb, var(--accent-1) 15%, transparent);color:var(--accent-1)}
    .badge.upcoming{background:var(--surface);color:var(--text-tertiary)}
    .mini-bar{height:3px;border-radius:2px;background:var(--border);margin-top:8px;overflow:hidden}
    .mini-bar-fill{height:100%;border-radius:2px;background:var(--accent-gradient);transition:width .4s}
    .score{font-size:12px;color:var(--text-secondary);float:right}
    .footer{margin-top:40px;text-align:center}
    .progress-bar{height:6px;border-radius:3px;background:var(--border);overflow:hidden;margin-top:8px}
    .progress-fill{height:100%;background:var(--accent-gradient);transition:width .6s}
    .footer-text{font-size:13px;color:var(--text-secondary);margin-top:8px}
    @keyframes pulse{0%,100%{box-shadow:0 0 4px var(--accent-1)}50%{box-shadow:0 0 16px var(--accent-1)}}
    @media(max-width:480px){.container{padding:24px 16px}.header h1{font-size:22px}}
  </style>
</head>
<body>
<svg style="position:absolute;width:0;height:0"><defs>
  <linearGradient id="gradient" x1="0%" y1="0%" x2="100%" y2="100%">
    <stop offset="0%" stop-color="var(--accent-1)"/>
    <stop offset="100%" stop-color="var(--accent-2)"/>
  </linearGradient>
</defs></svg>
<div class="container">
  <div class="header">
    <h1>{{TOPIC}}</h1>
    <div class="chips">
      <span class="chip">Level: {{LEVEL}}</span>
      <span class="chip">Started: {{DATE}}</span>
      <span class="chip">Mode: {{MODE}}</span>
    </div>
    <div class="ring-wrap">
      <svg viewBox="0 0 96 96"><circle class="ring-bg" cx="48" cy="48" r="42"/><circle class="ring-fg" cx="48" cy="48" r="42"/></svg>
      <div class="ring-label">{{PCT}}%</div>
    </div>
  </div>
  <div class="timeline" style="--mastered-pct:{{PCT}}">
    <!-- Repeat per concept: class="node mastered|active|upcoming" -->
    <div class="node mastered">
      <span class="badge mastered">Mastered</span><span class="score">90%</span>
      <div class="node-title">{{CONCEPT}}</div>
      <div class="mini-bar"><div class="mini-bar-fill" style="width:90%"></div></div>
    </div>
  </div>
  <div class="footer">
    <div class="progress-bar"><div class="progress-fill" style="width:{{PCT}}%"></div></div>
    <div class="footer-text">{{MASTERED}} / {{TOTAL}} concepts mastered</div>
  </div>
</div>
</body>
</html>
```

Replace `{{...}}` with session data. Choose accent colors per topic from palette above.

## Summary Template (`summary.html`)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Session Summary — {{TOPIC}}</title>
  <style>
    :root {
      --bg: #08080c;
      --surface: rgba(255,255,255,0.03);
      --surface-hover: rgba(255,255,255,0.08);
      --border: rgba(255,255,255,0.06);
      --text: #ededef;
      --text-secondary: rgba(255,255,255,0.55);
      --text-tertiary: rgba(255,255,255,0.3);
      --accent-1: /* CHOOSE */;
      --accent-2: /* CHOOSE */;
      --accent-gradient: linear-gradient(135deg, var(--accent-1), var(--accent-2));
      --green: #34d399; --amber: #fbbf24; --red: #f87171;
      --font-mono: 'SF Mono','Fira Code','JetBrains Mono',monospace;
      --font-sans: -apple-system,'Inter',system-ui,sans-serif;
      --radius: 12px;
    }
    *{margin:0;padding:0;box-sizing:border-box}
    body{background:var(--bg);color:var(--text);font-family:var(--font-sans);
      min-height:100vh;display:flex;justify-content:center;
      background-image:
        radial-gradient(ellipse at 20% 0%, color-mix(in srgb, var(--accent-1) 8%, transparent) 0%, transparent 60%),
        radial-gradient(ellipse at 80% 100%, color-mix(in srgb, var(--accent-2) 6%, transparent) 0%, transparent 60%)}
    .container{max-width:720px;width:100%;padding:48px 24px}
    .header{text-align:center;margin-bottom:40px}
    .header h1{font-size:28px;background:var(--accent-gradient);-webkit-background-clip:text;-webkit-text-fill-color:transparent}
    .header .subtitle{color:var(--text-secondary);font-size:14px;margin-top:8px}
    .completion-badge{display:inline-flex;align-items:center;gap:6px;margin-top:16px;padding:6px 16px;
      border-radius:20px;font-size:13px;font-weight:600;
      background:color-mix(in srgb, var(--green) 12%, transparent);color:var(--green);border:1px solid color-mix(in srgb, var(--green) 20%, transparent)}
    .completion-badge.in-progress{background:color-mix(in srgb, var(--amber) 12%, transparent);
      color:var(--amber);border-color:color-mix(in srgb, var(--amber) 20%, transparent)}
    .stats-grid{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin:32px 0}
    .stat-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);
      padding:24px;text-align:center;backdrop-filter:blur(12px);transition:all .2s cubic-bezier(.4,0,.2,1)}
    .stat-card:hover{background:var(--surface-hover);transform:translateY(-2px)}
    .stat-value{font-size:32px;font-weight:700;background:var(--accent-gradient);
      -webkit-background-clip:text;-webkit-text-fill-color:transparent}
    .stat-label{font-size:13px;color:var(--text-secondary);margin-top:4px}
    .section{margin:32px 0}
    .section-title{font-size:16px;font-weight:600;margin-bottom:16px;padding-bottom:8px;
      border-bottom:1px solid var(--border)}
    .concept-row{display:flex;align-items:center;gap:12px;padding:12px 16px;
      background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);
      margin-bottom:8px;backdrop-filter:blur(12px)}
    .concept-name{flex:1;font-size:14px;font-weight:500}
    .concept-score{font-size:13px;font-weight:600;min-width:40px;text-align:right}
    .concept-score.high{color:var(--green)}
    .concept-score.mid{color:var(--amber)}
    .concept-score.low{color:var(--red)}
    .concept-bar{flex:0 0 120px;height:4px;border-radius:2px;background:var(--border);overflow:hidden}
    .concept-bar-fill{height:100%;border-radius:2px;transition:width .4s}
    .concept-bar-fill.high{background:var(--green)}
    .concept-bar-fill.mid{background:var(--amber)}
    .concept-bar-fill.low{background:var(--red)}
    .insight-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);
      padding:16px 20px;margin-bottom:12px;backdrop-filter:blur(12px);font-size:14px;line-height:1.6}
    .insight-card .label{font-size:11px;text-transform:uppercase;letter-spacing:1px;
      color:var(--accent-1);margin-bottom:8px;font-weight:600}
    .next-steps{list-style:none;counter-reset:steps}
    .next-steps li{counter-increment:steps;position:relative;padding:12px 16px 12px 44px;
      background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);
      margin-bottom:8px;font-size:14px;backdrop-filter:blur(12px)}
    .next-steps li::before{content:counter(steps);position:absolute;left:16px;top:12px;
      width:20px;height:20px;border-radius:50%;background:var(--accent-gradient);
      color:var(--bg);font-size:11px;font-weight:700;display:flex;align-items:center;justify-content:center}
    .footer{margin-top:40px;text-align:center;color:var(--text-tertiary);font-size:12px}
    @media(max-width:480px){.container{padding:24px 16px}.stats-grid{grid-template-columns:1fr}
      .header h1{font-size:22px}.concept-bar{flex:0 0 80px}}
  </style>
</head>
<body>
<div class="container">
  <div class="header">
    <h1>{{TOPIC}}</h1>
    <div class="subtitle">Session summary — {{DATE}}</div>
    <!-- Use class="completion-badge" for completed, add "in-progress" for mid-session -->
    <div class="completion-badge"><!-- ✓ Completed | ◐ In Progress --></div>
  </div>

  <div class="stats-grid">
    <div class="stat-card"><div class="stat-value">{{MASTERED}}/{{TOTAL}}</div><div class="stat-label">Concepts Mastered</div></div>
    <div class="stat-card"><div class="stat-value">{{QUESTIONS}}</div><div class="stat-label">Questions Answered</div></div>
    <div class="stat-card"><div class="stat-value">{{RATE}}%</div><div class="stat-label">Mastery Rate</div></div>
    <div class="stat-card"><div class="stat-value">{{DURATION}}</div><div class="stat-label">Session Duration</div></div>
  </div>

  <div class="section">
    <div class="section-title">Concept Progress</div>
    <!-- Repeat per concept. Score class: >=80 "high", 40-79 "mid", <40 "low" -->
    <div class="concept-row">
      <div class="concept-name">{{CONCEPT}}</div>
      <div class="concept-bar"><div class="concept-bar-fill high" style="width:{{SCORE}}%"></div></div>
      <div class="concept-score high">{{SCORE}}%</div>
    </div>
  </div>

  <div class="section">
    <div class="section-title">Key Insights</div>
    <!-- One card per insight -->
    <div class="insight-card">
      <div class="label">Strength</div>
      {{INSIGHT_TEXT}}
    </div>
    <div class="insight-card">
      <div class="label">Growth Area</div>
      {{INSIGHT_TEXT}}
    </div>
  </div>

  <div class="section">
    <div class="section-title">Next Steps</div>
    <ol class="next-steps">
      <li>{{NEXT_STEP}}</li>
    </ol>
  </div>

  <div class="footer">Generated by Jarvis Tutor</div>
</div>
</body>
</html>
```

Replace `{{...}}` with session data. Score thresholds: ≥80% = `high` (green), 40-79% = `mid` (amber), <40% = `low` (red).

## Visual Explanation (`visuals/*.html`)

Additional CSS for code walkthroughs:

```css
.step-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);
  padding:20px;margin-bottom:16px;backdrop-filter:blur(12px)}
pre{background:rgba(0,0,0,.4);border-radius:8px;padding:16px;overflow-x:auto;font-family:var(--font-mono);font-size:14px;line-height:1.6}
.kw{color:var(--accent-1)} .fn{color:var(--accent-2)} .str{color:var(--green)}
.num{color:var(--amber)} .cmt{color:var(--text-tertiary);font-style:italic}
.annotation{border-left:3px solid var(--accent-1);background:var(--surface);padding:12px 16px;
  border-radius:0 var(--radius) var(--radius) 0;margin:12px 0;font-size:14px;color:var(--text-secondary)}
```
