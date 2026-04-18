---
layout: page
title: Publications
---

<div class="publications" markdown="0">

<p class="pubs-meta">
  For a full list: <a href="https://scholar.google.com/citations?user=_mJ4dr0AAAAJ&hl=en" rel="noopener external">Google Scholar</a>. Download all citations as <a href="{{ '/tamagusko.bib' | relative_url }}" download="tamagusko.bib">tamagusko.bib</a>.
</p>

{% for entry in site.data.publications %}
  {% if entry.section %}
    <h2>{{ entry.section }}</h2>
    <ul class="pubs-list">
  {% else %}
    {% assign authors_html = entry.authors %}
    {% if entry.highlight %}
      {% assign authors_html = entry.authors | replace: entry.highlight, '<strong>' | append: entry.highlight | append: '</strong>' %}
    {% endif %}
    <li class="pub" id="{{ entry.key }}">
      <p class="pub-line">
        {{ authors_html }} ({{ entry.year }}). {{ entry.title }}. <em>{{ entry.venue }}</em>{% if entry.volume %}, <em>{{ entry.volume }}</em>{% if entry.number %}({{ entry.number }}){% endif %}{% endif %}{% if entry.pages %}, {{ entry.pages }}{% endif %}.{% if entry.doi %} <a href="https://doi.org/{{ entry.doi }}" rel="noopener external">https://doi.org/{{ entry.doi }}</a>{% endif %}
      </p>
      <p class="pub-actions">
        <button type="button" class="btn-cite" data-bibtex-key="{{ entry.key }}" aria-label="Copy BibTeX for {{ entry.title | escape }}">Copy BibTeX</button>
        <script type="application/x-bibtex" id="bib-{{ entry.key }}">{{ entry.bibtex | strip }}</script>
      </p>
    </li>
    {% assign next_index = forloop.index %}
    {% assign next = site.data.publications[next_index] %}
    {% if next.section or forloop.last %}</ul>{% endif %}
  {% endif %}
{% endfor %}

</div>

<script>
(function () {
  function flash(btn, text) {
    var original = btn.dataset.label || btn.textContent;
    btn.dataset.label = original;
    btn.textContent = text;
    btn.disabled = true;
    setTimeout(function () { btn.textContent = original; btn.disabled = false; }, 1600);
  }
  document.addEventListener('click', function (event) {
    var btn = event.target.closest('.btn-cite');
    if (!btn) return;
    var key = btn.getAttribute('data-bibtex-key');
    var node = document.getElementById('bib-' + key);
    if (!node) return;
    var text = node.textContent.trim();
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(
        function () { flash(btn, 'Copied'); },
        function () { flash(btn, 'Copy failed'); }
      );
    } else {
      var ta = document.createElement('textarea');
      ta.value = text;
      ta.setAttribute('readonly', '');
      ta.style.position = 'absolute';
      ta.style.left = '-9999px';
      document.body.appendChild(ta);
      ta.select();
      try { document.execCommand('copy'); flash(btn, 'Copied'); }
      catch (e) { flash(btn, 'Copy failed'); }
      document.body.removeChild(ta);
    }
  });
})();
</script>
