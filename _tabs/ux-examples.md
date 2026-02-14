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

<p style="font-size: 0.9rem; color: var(--text-secondary); margin-bottom: 20px;">
  Brand list styling options for the "Where can I buy?" FAQ entry.
</p>

<!-- Option 1: Stacked Cards -->
<div class="supplement-group">
  <h3>Option 1: Stacked Cards</h3>
  <div class="faq-answer">
    <div class="ux-brand-card">
      <strong><a href="https://www.nowfoods.com" target="_blank">NOW Foods</a></strong>
      <span class="ux-brand-role">Best all-rounder</span>
      <span class="detail">In-house + third-party tested, GMP-certified, non-GMO. Good prices without cutting corners.</span>
      <span class="ux-brand-use">Use for: magnesium glycinate, melatonin, NAC, omega-3</span>
    </div>
    <div class="ux-brand-card">
      <strong><a href="https://www.bulksupplements.com" target="_blank">BulkSupplements</a></strong>
      <span class="ux-brand-role">Budget pick ⚠️</span>
      <span class="detail">Lowest prices, single-ingredient. But: unpublished CoAs, ~28% ConsumerLab failure rate, 2024 mislabeling lawsuit.</span>
      <span class="ux-brand-use">Use for: creatine, glycine (commodity powders only)</span>
    </div>
  </div>
</div>

<!-- Option 2: Compact Table Rows -->
<div class="supplement-group">
  <h3>Option 2: Compact Table Rows</h3>
  <div class="faq-answer">
    <div class="ux-brand-row">
      <div class="ux-brand-name"><a href="https://www.nowfoods.com" target="_blank">NOW Foods</a></div>
      <div class="ux-brand-desc">Best all-rounder · GMP, third-party tested, non-GMO</div>
    </div>
    <div class="ux-brand-row">
      <div class="ux-brand-name"><a href="https://www.thorne.com" target="_blank">Thorne</a></div>
      <div class="ux-brand-desc">Premium · NSF for Sport, published CoAs, 2–3x price</div>
    </div>
    <div class="ux-brand-row ux-brand-row--warn">
      <div class="ux-brand-name"><a href="https://www.bulksupplements.com" target="_blank">BulkSupplements</a></div>
      <div class="ux-brand-desc">Budget ⚠️ · 2024 lawsuit, unpublished CoAs, commodity powders only</div>
    </div>
  </div>
</div>

<!-- Option 3: Pill Tags with Tooltip -->
<div class="supplement-group">
  <h3>Option 3: Pill Tags</h3>
  <div class="faq-answer">
    <div class="ux-pill-grid">
      <a href="https://www.nowfoods.com" target="_blank" class="ux-brand-pill">NOW Foods <span>All-rounder</span></a>
      <a href="https://www.nutricost.com" target="_blank" class="ux-brand-pill">Nutricost <span>Bulk value</span></a>
      <a href="https://www.thorne.com" target="_blank" class="ux-brand-pill ux-brand-pill--premium">Thorne <span>Premium</span></a>
      <a href="https://www.bulksupplements.com" target="_blank" class="ux-brand-pill ux-brand-pill--warn">BulkSupplements <span>⚠️ Caveats</span></a>
    </div>
  </div>
</div>

<!-- Option 4: Bordered List with Accent Left -->
<div class="supplement-group">
  <h3>Option 4: Bordered List</h3>
  <div class="faq-answer">
    <ul class="ux-brand-list">
      <li class="ux-bl-green"><strong><a href="https://www.nowfoods.com" target="_blank">NOW Foods</a></strong> — Best all-rounder. GMP, third-party tested, non-GMO. Use for: mag glycinate, melatonin, NAC, omega-3.</li>
      <li class="ux-bl-green"><strong><a href="https://www.nutricost.com" target="_blank">Nutricost</a></strong> — Best value for bulk powders. GMP, third-party verified. Use for: creatine, glycine.</li>
      <li class="ux-bl-blue"><strong><a href="https://www.thorne.com" target="_blank">Thorne</a></strong> — Premium. NSF for Sport, published CoAs. 2–3x price but highest confidence.</li>
      <li class="ux-bl-amber"><strong><a href="https://www.bulksupplements.com" target="_blank">BulkSupplements</a></strong> — Cheapest, but: unpublished CoAs, ~28% failure rate, 2024 lawsuit. Commodity powders only.</li>
    </ul>
  </div>
</div>

<!-- Option 5: Mini Profile Cards -->
<div class="supplement-group">
  <h3>Option 5: Mini Profile Cards</h3>
  <div class="faq-answer">
    <div class="ux-profile-grid">
      <a href="https://www.nowfoods.com" target="_blank" class="ux-profile">
        <span class="ux-profile-name">NOW Foods</span>
        <span class="ux-profile-tag ux-ptag-green">All-rounder</span>
        <span class="ux-profile-desc">GMP, tested, non-GMO</span>
      </a>
      <a href="https://www.thorne.com" target="_blank" class="ux-profile">
        <span class="ux-profile-name">Thorne</span>
        <span class="ux-profile-tag ux-ptag-blue">Premium</span>
        <span class="ux-profile-desc">NSF for Sport, CoAs</span>
      </a>
      <a href="https://www.bulksupplements.com" target="_blank" class="ux-profile">
        <span class="ux-profile-name">BulkSupplements</span>
        <span class="ux-profile-tag ux-ptag-amber">⚠️ Caveats</span>
        <span class="ux-profile-desc">Cheap but lawsuit, failures</span>
      </a>
    </div>
  </div>
</div>

<style>
  /* === Option 1: Stacked Cards === */
  .ux-brand-card {
    padding: 12px 16px;
    border-radius: 12px;
    border: 1px solid var(--border-light);
    background: rgba(255,255,255,0.7);
    margin-bottom: 8px;
  }
  .ux-brand-card strong { color: var(--text-main); }
  .ux-brand-card a { color: var(--accent); text-decoration: none; }
  .ux-brand-card a:hover { text-decoration: underline; }
  .ux-brand-role {
    display: inline-block;
    margin-left: 8px;
    padding: 2px 8px;
    border-radius: 999px;
    background: var(--accent-soft);
    color: var(--accent);
    font-size: 0.72rem;
    font-weight: 500;
  }
  .ux-brand-use {
    display: block;
    margin-top: 4px;
    font-size: 0.78rem;
    color: var(--accent);
    font-weight: 500;
  }

  /* === Option 2: Compact Table Rows === */
  .ux-brand-row {
    display: flex;
    gap: 12px;
    padding: 10px 14px;
    border-bottom: 1px solid var(--border-light);
    font-size: 0.85rem;
    align-items: baseline;
  }
  .ux-brand-row:last-child { border-bottom: none; }
  .ux-brand-name { font-weight: 600; min-width: 130px; flex-shrink: 0; }
  .ux-brand-name a { color: var(--accent); text-decoration: none; }
  .ux-brand-name a:hover { text-decoration: underline; }
  .ux-brand-desc { color: var(--text-secondary); font-size: 0.82rem; }
  .ux-brand-row--warn { background: rgba(249,168,37,0.06); }

  /* === Option 3: Pill Tags === */
  .ux-pill-grid { display: flex; flex-wrap: wrap; gap: 8px; }
  .ux-brand-pill {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 6px 14px;
    border-radius: 999px;
    border: 1.5px solid var(--accent);
    color: var(--accent);
    font-size: 0.8rem;
    font-weight: 500;
    text-decoration: none;
    transition: all 0.2s;
  }
  .ux-brand-pill span { font-weight: 400; font-size: 0.72rem; opacity: 0.7; }
  .ux-brand-pill:hover { background: var(--accent-soft); }
  .ux-brand-pill--premium { border-color: #1565c0; color: #1565c0; }
  .ux-brand-pill--premium:hover { background: rgba(21,101,192,0.08); }
  .ux-brand-pill--warn { border-color: #f9a825; color: #6d5b00; }
  .ux-brand-pill--warn:hover { background: rgba(249,168,37,0.1); }

  /* === Option 4: Bordered List === */
  .ux-brand-list {
    list-style: none;
    position: relative;
    z-index: 1;
  }
  .ux-brand-list li {
    padding: 10px 14px;
    margin-bottom: 6px;
    border-left: 3px solid;
    border-radius: 0 10px 10px 0;
    font-size: 0.85rem;
    color: var(--text-secondary);
  }
  .ux-brand-list li a { color: var(--accent); text-decoration: none; }
  .ux-brand-list li a:hover { text-decoration: underline; }
  .ux-bl-green { border-color: var(--accent); background: rgba(46,125,82,0.04); }
  .ux-bl-blue { border-color: #1565c0; background: rgba(21,101,192,0.04); }
  .ux-bl-amber { border-color: #f9a825; background: rgba(249,168,37,0.04); }

  /* === Option 5: Mini Profile Cards === */
  .ux-profile-grid { display: flex; flex-wrap: wrap; gap: 8px; }
  .ux-profile {
    flex: 1;
    min-width: 140px;
    padding: 12px;
    border-radius: 12px;
    border: 1px solid var(--border-light);
    background: rgba(255,255,255,0.7);
    text-decoration: none;
    text-align: center;
    transition: box-shadow 0.2s;
  }
  .ux-profile:hover { box-shadow: 0 4px 12px rgba(0,0,0,0.08); }
  .ux-profile-name { display: block; font-weight: 600; color: var(--text-main); font-size: 0.88rem; }
  .ux-profile-tag {
    display: inline-block;
    margin-top: 4px;
    padding: 2px 8px;
    border-radius: 999px;
    font-size: 0.7rem;
    font-weight: 500;
  }
  .ux-ptag-green { background: var(--accent-soft); color: var(--accent); }
  .ux-ptag-blue { background: rgba(21,101,192,0.1); color: #1565c0; }
  .ux-ptag-amber { background: rgba(249,168,37,0.15); color: #6d5b00; }
  .ux-profile-desc { display: block; margin-top: 4px; font-size: 0.75rem; color: var(--text-secondary); }
</style>
