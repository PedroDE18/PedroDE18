---
layout: page
title: Home
id: home
permalink: /
---

# Welcome! 🌱

<p style="padding: 3em 1em; background: #f5f7ff; border-radius: 4px;">
  Take a look at <span style="font-weight: bold">[[Your first note]]</span> to get started on your exploration.
</p>

Aqui está um conjunto de anotações que tomei durante a faculdade de Medicina, 
seguirei atualizando este site, para torná-lo cada vez mais completo! 

# Matérias
[[Anatomia]]
[[Anestesiologia]]
[[Atenção Primária em Saúde (APS)]]
[[Cardiologia]]
[[Cirurgia Cardiotorácica]]
[[Cirurgia de Cabeça e Pescoço (CCP)]]
[[Cirurgia]]
[[Cirurgia Plástica]]
[[Cirurgia Vascular]]
[[Cuidados Paliativos]]
[[Dermatologia]]
[[Endocrinologia]]
[[Emergência]]
[[Gastroenterologia]]
[[Geriatria]]
[[Ginecologia & Obstetrícia]]
[[Hepatologia]]
[[Infectologia]]
[[Imunologia]]
[[Medicina Legal]]
[[Medicina Ocupacional]]
[[Nefrologia]]
[[Neurologia]]
[[Obstetrícia]]
[[Oftalmologia]]
[[Oncologia]]
[[Ortopedia]]
[[Otorrinolaringologia (ORL)]]
[[Patologia]]
[[Pediatria]]
[[Pneumologia]]
[[Propedêutica]]
[[Psiquiatria]]
[[Reumatologia]]
[[Urologia]]

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
  .wrapper {
    max-width: 46em;
  }
</style>
