---
title: UX Examples
tab_label: UX Preview
tag: Dev Only
order: 99
dev_only: true
---

<p style="color: var(--accent); font-weight: 600; margin-bottom: 20px;">
  ⚠️ This tab is for local preview only — it will not appear on the published site.
</p>

<!-- Option 1: Pill Button -->
<div class="supplement-group">
  <h3>Option 1: Pill Button</h3>
  <div class="supplement-item">
    <strong>Creatine Monohydrate</strong> — <span class="dose">10 g/day</span>
    <span class="detail">Take in the morning. On days after poor sleep, 15–20 g may help offset cognitive effects.</span>
    <details class="note-collapsible">
      <summary class="note-toggle ux-pill">📋 More info & research</summary>
      <div class="note">Example research note content with <a href="#">citation links</a>.</div>
    </details>
  </div>
</div>

<!-- Option 2: Subtle Card Strip -->
<div class="supplement-group">
  <h3>Option 2: Subtle Card Strip</h3>
  <div class="supplement-item">
    <strong>Creatine Monohydrate</strong> — <span class="dose">10 g/day</span>
    <span class="detail">Take in the morning. On days after poor sleep, 15–20 g may help offset cognitive effects.</span>
    <details class="note-collapsible">
      <summary class="note-toggle ux-strip">📋 More info & research</summary>
      <div class="note">Example research note content with <a href="#">citation links</a>.</div>
    </details>
  </div>
</div>

<!-- Option 3: Outlined Chip -->
<div class="supplement-group">
  <h3>Option 3: Outlined Chip</h3>
  <div class="supplement-item">
    <strong>Creatine Monohydrate</strong> — <span class="dose">10 g/day</span>
    <span class="detail">Take in the morning. On days after poor sleep, 15–20 g may help offset cognitive effects.</span>
    <details class="note-collapsible">
      <summary class="note-toggle ux-chip">📋 More info & research</summary>
      <div class="note">Example research note content with <a href="#">citation links</a>.</div>
    </details>
  </div>
</div>

<!-- Option 4: Left-bordered Accent Bar -->
<div class="supplement-group">
  <h3>Option 4: Left-bordered Accent Bar</h3>
  <div class="supplement-item">
    <strong>Creatine Monohydrate</strong> — <span class="dose">10 g/day</span>
    <span class="detail">Take in the morning. On days after poor sleep, 15–20 g may help offset cognitive effects.</span>
    <details class="note-collapsible">
      <summary class="note-toggle ux-bar">📋 More info & research</summary>
      <div class="note">Example research note content with <a href="#">citation links</a>.</div>
    </details>
  </div>
</div>

<!-- Option 5: Icon-forward Minimal -->
<div class="supplement-group">
  <h3>Option 5: Icon-forward Minimal</h3>
  <div class="supplement-item">
    <strong>Creatine Monohydrate</strong> — <span class="dose">10 g/day</span>
    <span class="detail">Take in the morning. On days after poor sleep, 15–20 g may help offset cognitive effects.</span>
    <details class="note-collapsible">
      <summary class="note-toggle ux-minimal">📋 More info & research</summary>
      <div class="note">Example research note content with <a href="#">citation links</a>.</div>
    </details>
  </div>
</div>

<style>
  /* === Option 1: Pill Button === */
  .ux-pill {
    display: inline-block;
    margin-top: 8px;
    padding: 5px 14px;
    background: var(--accent);
    color: #fff !important;
    border-radius: 999px;
    font-size: 0.75rem;
    font-weight: 500;
    letter-spacing: 0.02em;
    transition: background 0.2s ease;
  }
  .ux-pill::before { content: "" !important; }
  .ux-pill:hover { background: var(--accent-hover); }
  [open] > .ux-pill { background: var(--accent-hover); }

  /* === Option 2: Subtle Card Strip === */
  .ux-strip {
    display: block;
    margin-top: 10px;
    padding: 8px 12px;
    background: var(--accent-soft);
    border-radius: 8px;
    font-size: 0.78rem;
    font-weight: 500;
    color: var(--accent) !important;
    transition: background 0.2s ease;
  }
  .ux-strip::before { content: "▸ " !important; }
  [open] > .ux-strip::before { content: "▾ " !important; }
  .ux-strip:hover { background: rgba(46, 125, 82, 0.16); }

  /* === Option 3: Outlined Chip === */
  .ux-chip {
    display: inline-block;
    margin-top: 8px;
    padding: 4px 12px;
    border: 1.5px solid var(--accent);
    border-radius: 999px;
    font-size: 0.75rem;
    font-weight: 500;
    color: var(--accent) !important;
    background: transparent;
    transition: all 0.2s ease;
  }
  .ux-chip::before { content: "" !important; }
  .ux-chip:hover { background: var(--accent-soft); }
  [open] > .ux-chip { background: var(--accent-soft); }

  /* === Option 4: Left-bordered Accent Bar === */
  .ux-bar {
    display: block;
    margin-top: 10px;
    padding: 8px 12px;
    border-left: 3px solid var(--accent);
    background: rgba(46, 125, 82, 0.04);
    border-radius: 0 8px 8px 0;
    font-size: 0.78rem;
    font-weight: 500;
    color: var(--accent) !important;
    transition: background 0.2s ease;
  }
  .ux-bar::before { content: "▸ " !important; }
  [open] > .ux-bar::before { content: "▾ " !important; }
  .ux-bar:hover { background: rgba(46, 125, 82, 0.08); }

  /* === Option 5: Icon-forward Minimal === */
  .ux-minimal {
    display: inline-block;
    margin-top: 8px;
    padding: 2px 0;
    font-size: 0.78rem;
    font-weight: 500;
    color: var(--accent) !important;
    background: transparent;
    border-bottom: 1.5px dotted var(--accent);
    transition: border-color 0.2s ease;
  }
  .ux-minimal::before { content: "" !important; }
  .ux-minimal:hover { border-bottom-style: solid; }
  [open] > .ux-minimal { border-bottom-style: solid; }
</style>
