---
layout: page
title: Publications
---

<div class="publications" markdown="0">

<p class="pubs-meta">
  For a full list, see
  <a href="https://scholar.google.com/citations?user=_mJ4dr0AAAAJ&hl=en" rel="noopener external">Google Scholar</a> or
  <a href="https://www.scopus.com/authid/detail.uri?authorId=57217101810" rel="noopener external">Scopus</a>.
  Download all citations as
  <a href="{{ '/tamagusko.bib' | relative_url }}" download="tamagusko.bib">tamagusko.bib</a>.
</p>

{% for entry in site.data.publications %}
  {% if entry.section %}
    <h2>{{ entry.section }}</h2>
    <ul class="pubs-list">
  {% else %}
    <li class="pub" id="{{ entry.key }}">
      <p class="pub-line">
        {%- assign authors = entry.authors -%}
        {%- if entry.highlight -%}
          {%- assign authors = authors | replace: entry.highlight, '<strong>' | append: '</strong>' -%}
          {{ entry.authors | replace: entry.highlight, '<strong>' | append: entry.highlight | append: '</strong>' }}
        {%- else -%}
          {{ entry.authors }}
        {%- endif -%}
        ({{ entry.year }}).
        {{ entry.title }}.
        <em>{{ entry.venue }}</em>{% if entry.volume %}, {{ entry.volume }}{% if entry.number %}({{ entry.number }}){% endif %}{% endif %}{% if entry.pages %}, {{ entry.pages }}{% endif %}.
        {% if entry.doi %}<a href="https://doi.org/{{ entry.doi }}" rel="noopener external">doi:{{ entry.doi }}</a>{% endif %}
      </p>
      <p class="pub-actions">
        <button type="button" class="btn-cite" data-bibtex-key="{{ entry.key }}" aria-label="Copy BibTeX for {{ entry.title | escape }}">Copy BibTeX</button>
        {% if entry.doi %}<a class="pub-link" href="https://doi.org/{{ entry.doi }}" rel="noopener external">DOI</a>{% endif %}
        <script type="application/x-bibtex" id="bib-{{ entry.key }}">{{ entry.bibtex | strip }}</script>
      </p>
    </li>
    {% if forloop.last %}</ul>{% endif %}
    {% assign next_index = forloop.index %}
    {% assign next = site.data.publications[next_index] %}
    {% if next.section %}</ul>{% endif %}
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
