---
layout: page
title: Home
id: home
permalink: /
---

# Welcome! 🌱

<p style="padding: 3em 1em; background: #f5f7ff; border-radius: 4px;">
  Aqui está um conjunto de anotações que tomei durante a faculdade de Medicina, 
seguirei atualizando este site, para torná-lo cada vez mais completo! 
</p>

# Grandes Áreas
<div class="grid-container">
  <a href="/Atenção%20Primária%20em%20Saúde%20(APS)" class="grid-item">Atenção Primária</a>
  <a href="/Clínica%20Médica" class="grid-item">Clínica Médica</a>
  <a href="/Cirurgia" class="grid-item">Cirurgia</a>
  <a href="/Pediatria" class="grid-item">Pediatria</a>
  <a href="/Ginecologia%20%26%20Obstetrícia" class="grid-item">GO</a>
  <a href="/Pesquisa" class="grid-item">Pesquisa</a>
</div>



<strong>Anotações Recentemente Atualizadas</strong>

<ul>
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
  background-color: #4caf50;
  color: white;
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
