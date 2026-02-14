---
title: Supplement Stack
tab_label: Supplements
tag: Active Protocol
order: 2
---

<p>
  These are supplements I believe nearly everyone can take safely, with well-studied benefits.
  This is not medical advice — do your own research and consult a healthcare professional.
</p>

<div class="supplement-group">
  <h3>🟢 Core Daily Stack</h3>
  {% for item in site.data.supplements %}
    {% include supplement-item.html item=item %}
  {% endfor %}
</div>

<div class="supplement-group">
  <h3>🟡 Optional: GlyNAC Stack</h3>
  {% for item in site.data.optional_supplements %}
    {% include supplement-item.html item=item %}
    {% if item.warning %}
    <div class="note" style="margin-top: 12px;">{{ item.warning }}</div>
    {% endif %}
  {% endfor %}
</div>

<div class="supplement-group">
  <h3>📋 Staging Protocol</h3>
  <p style="font-size: 0.88rem; margin-bottom: 10px; color: var(--text-secondary); position: relative; z-index: 1;">
    Start in stages so you can identify what's working and isolate any issues:
  </p>
  {% include staging-list.html stages=site.data.staging %}
</div>

<div class="supplement-group">
  <h3>⏰ Timing Summary</h3>
  {% for slot in site.data.timing %}
  <div class="supplement-item">
    <strong>{{ slot.label }}</strong> {{ slot.detail }}
  </div>
  {% endfor %}
</div>
