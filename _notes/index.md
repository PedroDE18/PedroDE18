---
layout: page
title: Home
id: home
permalink: /
---

# Bem-Vindo!

> Este é o meu repertório de anotações de medicina.
> Aqui atualizo minhas notas, originalmente organizadas segundo o sistema Zettelkasten.

<!-- Search Bar -->
<div class = "search-container">
  <input
    type="text"
    id="search-bar"
    placeholder="Busque notas..."
    onkeyup="searchNotes()"
    style="width: 100%; padding: 0.5em; font-size: 1em; border-radius: 4px; border: 1px solid #ccc;"
  />
  <ul 
    id="search-results" 
    style="list-style: none; margin: 0; padding: 0; position: absolute; top: 100%; left: 0; width: 100%; background: white; border: 1px solid #ccc; border-radius: 4px; max-height: 200px; overflow-y: auto; display: none; z-index: 1000;">
  </ul>
</div>

## Grandes Áreas
<div class="grid-container">
  <div class="grid-item">[[Atenção Primária em Saúde (APS)]]</div>
  <div class="grid-item">[[Clínica Médica]]</div>
  <div class="grid-item">[[Cirurgia]]</div>
  <div class="grid-item">[[Pediatria]]</div>
  <div class="grid-item">[[Ginecologia & Obstetrícia]]</div>
  <div class="grid-item">[[Pesquisa]]</div>
</div>


## Anotações Recentes
<ul class="recent-notes">
  {% assign recent_notes = site.notes | sort: "last_modified_at_timestamp" | reverse %}
  {% for note in recent_notes limit: 10 %}
    <li>
      {{ note.last_modified_at | date: "%Y-%m-%d" }} — <a class="internal-link" href="{{ site.baseurl }}{{ note.url }}">{{ note.title }}</a>
    </li>
  {% endfor %}
</ul>

<style>
  .grid-container{
  display: grid;
  grid-template-columns: repeat(2,1fr);
  gap: 1em;
  margin: 2em 0;
  }
  .grid-item{
  background-color: #808080;
  color: #808080;
  padding: 1.5em;
  text-align: center;
  border-radius: 8px;
  text-decoration: none;
  font-size: 1.2em;
  font-weight: bold;
  transition: transform 0.2s, background-color 0.3s;
  }
  .grid-item: hover{
  background-color: #388e3c;
  transform: translateY(-5px);
  }

  }
  .wrapper {
    max-width: 46em;
  }
</style>
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

    if (query.trim() === "") {
      resultsContainer.style.display = "none";
      return;
    }

    const filteredNotes = notes.filter(note =>
      note.title.toLowerCase().includes(query)
    );

    if (filteredNotes.length > 0) {
      resultsContainer.style.display = "block";
      filteredNotes.forEach(note => {
        const listItem = document.createElement("li");
        listItem.innerHTML = `<a href="${note.url}" style="text-decoration: none; display: block; padding: 0.5em; color: #333;">${note.title}</a>`;
        resultsContainer.appendChild(listItem);
      });
    } else {
      resultsContainer.style.display = "block";
      resultsContainer.innerHTML = `<li style="padding: 0.5em; color: #777;">No results found</li>`;
    }
  }

  // Close dropdown if user clicks outside
  document.addEventListener("click", (event) => {
    const searchBar = document.getElementById("search-bar");
    const resultsContainer = document.getElementById("search-results");

    if (!searchBar.contains(event.target) && !resultsContainer.contains(event.target)) {
      resultsContainer.style.display = "none";
    }
  });
</script>