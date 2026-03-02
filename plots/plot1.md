---
layout: single
title: "Plocha 1 – Mladý bukový les
sidebar:
  nav: "main"
permalink: /plots/plot1/
---



## Popis  
{% assign lokalita = site.data.site_description.plot1[0] %}

<ul>
  <li><strong>Název lokality:</strong> {{ lokalita.nazev_lokality }}</li>
  <li><strong>Struktura:</strong> {{ lokalita.struktura }}</li>
  <li><strong>Stáří:</strong> {{ lokalita.stari }}</li>
  <li><strong>Datum měření:</strong> {{ lokalita.datum_mereni | date: "%d.%m.%Y" }}</li>
</ul>

## Meteorologická data
{% assign data = site.data.meteodata.plot1 %}

<div class="table-wrapper">
<table class="excel">

  <thead>
    <tr>
      <th>Vzdálenost (m)</th>
      <th>Čas měření</th>
      <th>Teplota (°C)</th>
      <th>Tlak (hPa)</th>
      <th>Oblačnost (%)</th>
      <th>Vítr</th>
      <th>Vlhkost (%)</th>
    </tr>
  </thead>

  <tbody>

  {% assign sekce_list = data | map: "sekce" | uniq %}

  {% for sekce in sekce_list %}

    <!-- Sekční nadpis -->
    <tr class="section">
      <td colspan="7">
        {% if sekce == "vege" %}
          Vegetační sezóna
        {% elsif sekce == "mimo" %}
          Mimo vegetační sezónu
        {% endif %}
      </td>
    </tr>

    {% for row in data %}
      {% if row.sekce == sekce %}
      <tr>
        <td>{{ row.vzdalenost_m }}</td>
        <td>{{ row.cas_mereni }}</td>
        <td>{{ row.teplota_C }}</td>
        <td>{{ row.tlak_hPa }}</td>
        <td>{{ row.oblacnost_pct }}</td>
        <td style="text-align:left;">{{ row.vitr }}</td>
        <td>{{ row.vlhkost_pct }}</td>
      </tr>
      {% endif %}
    {% endfor %}

  {% endfor %}

  </tbody>
</table>
</div>

## Měřené hodnoty hluku - Vegetační sezóna
{% assign data = site.data.noise.plot1_on %}

<div class="table-wrapper">
<table class="excel">

  <!-- HLAVIČKA -->
  <thead>
    <tr>
      <th></th>
      {% for key in data[0] %}
        {% unless key[0] == "sekce" or key[0] == "vzdalenost" %}
          <th>{{ key[0] }}</th>
        {% endunless %}
      {% endfor %}
    </tr>
  </thead>

  <tbody>

  {% assign sekce_list = data | map: "sekce" | uniq %}

  {% for sekce in sekce_list %}

    <!-- Barevný nadpis sekce -->
    <tr class="section {{ sekce }}">
      <td colspan="{{ data[0].size | minus: 1 }}">
        {% if sekce == "vegetace" %}
          Útlum vegetací (bez vlivu vzdálenosti)
        {% elsif sekce == "pas" %}
          Útlum pásu jako celku (s vlivem vzdálenosti)
        {% elsif sekce == "vzdalenost" %}
          Útlum vzdáleností
        {% endif %}
      </td>
    </tr>

    <!-- Data -->
    {% for row in data %}
      {% if row.sekce == sekce %}
      <tr>
        <td>{{ row.vzdalenost }} m</td>

        {% for key in row %}
          {% unless key[0] == "sekce" or key[0] == "vzdalenost" %}
            <td>{{ key[1] }}</td>
          {% endunless %}
        {% endfor %}

      </tr>
      {% endif %}
    {% endfor %}

  {% endfor %}

  </tbody>
</table>
</div>

## Měřené hodnoty hluku - Mimo vegetační sezónu
{% assign data_off = site.data.noise.plot1_off %}

<div class="table-wrapper">
<table class="excel">

  <!-- HLAVIČKA -->
  <thead>
    <tr>
      <th></th>
      {% for key in data_off[0] %}
        {% unless key[0] == "sekce" or key[0] == "vzdalenost" %}
          <th>{{ key[0] }}</th>
        {% endunless %}
      {% endfor %}
    </tr>
  </thead>

  <tbody>

  {% assign sekce_list = data_off | map: "sekce" | uniq %}

  {% for sekce in sekce_list %}

    <!-- Barevný nadpis sekce -->
    <tr class="section {{ sekce }}">
      <td colspan="{{ data_off[0].size | minus: 1 }}">
        {% if sekce == "vegetace" %}
          Útlum vegetací (bez vlivu vzdálenosti)
        {% elsif sekce == "pas" %}
          Útlum pásu jako celku (s vlivem vzdálenosti)
        {% elsif sekce == "vzdalenost" %}
          Útlum vzdáleností
        {% endif %}
      </td>
    </tr>

    <!-- Data -->
    {% for row in data_off %}
      {% if row.sekce == sekce %}
      <tr>
        <td>{{ row.vzdalenost }} m</td>

        {% for key in row %}
          {% unless key[0] == "sekce" or key[0] == "vzdalenost" %}
            <td>{{ key[1] }}</td>
          {% endunless %}
        {% endfor %}

      </tr>
      {% endif %}
    {% endfor %}

  {% endfor %}

  </tbody>
</table>
</div>
  
## Fotogalerie  
### Ve vegetační sezóně

<div style="display:flex; flex-wrap:wrap; gap:10px; align-items:flex-start;">

{% for file in site.data.images.plot1 %}
  <div>
    <a href="{{ '/assets/images/plot1/on/' | append: file | relative_url }}" target="_blank">
      <img 
        src="{{ '/assets/images/plot1/on/' | append: file | relative_url }}" 
        style="height:100px;">
    </a>
  </div>
{% endfor %}

</div>


### Mimo vegetační sezónu  

<div style="display:flex; flex-wrap:wrap; gap:10px; align-items:flex-start;">

{% for file in site.data.images.plot1 %}
  <div>
    <a href="{{ '/assets/images/plot1/off/' | append: file | relative_url }}" target="_blank">
      <img 
        src="{{ '/assets/images/plot1/off/' | append: file | relative_url }}" 
        style="height:100px;">
    </a>
  </div>
{% endfor %}

</div>