---
layout: page
title: Home
id: home
permalink: /
---

# Bem-Vindo!

> Este é o meu repertório de anotações, organizado segundo o sistema Zettelkasten.

<!-- Search Bar -->
<div class = "search-container">
  <input
    type="text"
    id="search-bar"
    placeholder="Busque notas..."
    onkeyup="searchNotes()"/>
  <ul id="search-results"> </ul>
</div>

## MOCs
<div class="areas-grid">
  <a href="moc-dx-sindromico/" class="area-card">Diagnóstico Sindrômico</a>
  <a href="moc-dx-topografico/" class="area-card">Diagnóstico Topográfico</a>
  <a href="moc-fisiologia/" class="area-card">Fisiologia</a>
  <a href="moc-exames/" class="area-card">Exames Complementares</a>
  <a href="moc-tratamentos/" class="area-card">Tratamentos & Protocolos</a>
  <a href="moc-legislacao/" class="area-card">Legislação</a>
</div>

## Anotações Recentes
<ul class="recent-notes">
  {% assign recent_notes = site.notes | sort: "last_modified_at_timestamp" | reverse %}
  {% for note in recent_notes limit: 10 %}
    <li>
      {{ note.last_modified_at | date: "%d-%m-%Y" }} — <a class="internal-link" href="{{ site.baseurl }}{{ note.url }}">{{ note.title }}</a>
    </li>
  {% endfor %}
</ul>

<!-- Dynamically Generated Notes Array -->
<script>
  const notes = [
    {% for note in site.notes %}
      { title: "{{ note.title | escape }}", url: "{{ note.url | relative_url }}" },
    {% endfor %}
  ];

  function searchNotes() {
    const query = document.getElementById("search-bar").value.toLowerCase();
    const resultsContainer = document.getElementById("search-results");
    resultsContainer.innerHTML = ""; // Clear previous results

    if (!query.trim()) {
      resultsContainer.style.display = "none";
      return;
    }

    const filtered = notes.filter(n => n.title.toLowerCase().includes(query));
    resultsContainer.style.display = "block";
    if (filtered.length) {
      filtered.forEach(n => {
        const li = document.createElement("li");
        li.innerHTML = `<a href="${n.url}">${n.title}</a>`;
        resultsContainer.appendChild(li);
      });
    } else {
      const li = document.createElement("li");
      li.textContent = "Nenhum resultado encontrado";
      resultsContainer.appendChild(li);
    }
  }

  document.addEventListener("click", e => {
    const sb = document.getElementById("search-bar");
    const res = document.getElementById("search-results");
    if (!sb.contains(e.target) && !res.contains(e.target)) {
      res.style.display = "none";
    }
  });
</script>