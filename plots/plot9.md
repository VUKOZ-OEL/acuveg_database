---
layout: single
title: "Volné pole"
sidebar:
  nav: "main"
permalink: /plots/plot9/
---


## Popis  

  **Popis lokality:** šíření hluku ve volném poli = snížení hlučnosti zvýšením vzdálenosti bez překážky pro zvukovou vlnu.  
  
  **Datum měření:** 07.08.2024, 28.01.2026 (bez sněhové pokrývky), 21.02.2025 (se sněhovou pokrývkou)  
  **Porostní skupina:**  

## Měřené hodnoty hluku - Vegetační sezóna
  {% assign data = site.data.noise.plot9_on %}
  
  <div class="table-wrapper">
  <table class="excel">
  
<thead>

<tr>
<th></th>
<th colspan="{{ data[0].size | minus: 3 }}">Frekvence [Hz]</th>
</tr>

<tr>
<th>Vzdálenost</th>
  
  {% for key in data[0] %}
  {% unless key[0] == "sekce" or key[0] == "vzdalenost" or key[0] == "vyska" %}
  <th>{{ key[0] }}</th>
  {% endunless %}
  {% endfor %}
  
  </tr>
  </thead>
  
  <tbody>
  
  {% assign sekce_list = data | map: "sekce" | uniq %}
  
  {% for sekce in sekce_list %}
  
  <tr class="section {{ sekce }}">
  <td colspan="{{ data[0].size | minus: 2 }}">
  
  {% if sekce == "vegetace" %}
  Útlum vegetací (bez vlivu vzdálenosti)
  {% elsif sekce == "pas" %}
  Útlum vlivem vzdálenosti
  {% endif %}
  
  </td>
  </tr>
  
  {% assign vysky = data | map: "vyska" | uniq | sort_natural  %}
  
  {% for vyska in vysky %}
  
  <tr class="subsection">
  <td colspan="{{ data[0].size | minus: 2 }}">
  Výška měření {{ vyska }} m
  </td>
  </tr>
  
  {% assign vzdalenosti = "7.5,15,30" | split: "," %}
  
  {% for vzd in vzdalenosti %}
  
  {% for row in data %}
  
  {% if row.sekce == sekce and row.vyska == vyska and row.vzdalenost == vzd %}
  
  <tr>
  
  <td>{{ row.vzdalenost }} m</td>
  
  {% for key in row %}
  {% unless key[0] == "sekce" or key[0] == "vzdalenost" or key[0] == "vyska" %}
  <td>{{ key[1] }}</td>
  {% endunless %}
  {% endfor %}
  
  </tr>
  
  {% endif %}
  
  {% endfor %}
  {% endfor %}
  {% endfor %}
  {% endfor %}
  
  </tbody>
  </table>
  </div>

## Měřené hodnoty hluku - Mimo vegetační sezónu - bez sněhové pokrývky
  {% assign data_off = site.data.noise.plot9_off %}
  
  <div class="table-wrapper">
  <table class="excel">
  
<thead>

<tr>
<th></th>
<th colspan="{{ data_off[0].size | minus: 3 }}">Frekvence [Hz]</th>
</tr>

<tr>
<th>Vzdálenost</th>
  
  {% for key in data_off[0] %}
  {% unless key[0] == "sekce" or key[0] == "vzdalenost" or key[0] == "vyska" %}
  <th>{{ key[0] }}</th>
  {% endunless %}
  {% endfor %}
  
  </tr>
  </thead>
  
  <tbody>
  
  {% assign sekce_list = data_off | map: "sekce" | uniq %}
  
  {% for sekce in sekce_list %}
  
  <tr class="section {{ sekce }}">
  <td colspan="{{ data_off[0].size | minus: 2 }}">
  
  {% if sekce == "vegetace" %}
  Útlum vegetací (bez vlivu vzdálenosti)
  {% elsif sekce == "pas" %}
  Útlum vlivem vzdálenosti
  {% endif %}
  
  </td>
  </tr>
  
  {% assign vysky = data_off | map: "vyska" | uniq | sort_natural  %}
  
  {% for vyska in vysky %}
  
  <tr class="subsection">
  <td colspan="{{ data_off[0].size | minus: 2 }}">
  Výška měření {{ vyska }} m
  </td>
  </tr>
  
  {% assign vzdalenosti = "7.5,15,30" | split: "," %}
  
  {% for vzd in vzdalenosti %}
  
  {% for row in data_off %}
  
  {% if row.sekce == sekce and row.vyska == vyska and row.vzdalenost == vzd %}
  
  <tr>
  
  <td>{{ row.vzdalenost }} m</td>
  
  {% for key in row %}
  {% unless key[0] == "sekce" or key[0] == "vzdalenost" or key[0] == "vyska" %}
  <td>{{ key[1] }}</td>
  {% endunless %}
  {% endfor %}
  
  </tr>
  
  {% endif %}
  
  {% endfor %}
  {% endfor %}
  {% endfor %}
  {% endfor %}
  
  </tbody>
  </table>
  </div>

## Měřené hodnoty hluku - Mimo vegetační sezónu - se sněhovou pokrývkou
  {% assign data_snow = site.data.noise.plot9_snow %}
  
  <div class="table-wrapper">
  <table class="excel">
  
<thead>

<tr>
<th></th>
<th colspan="{{ data_snow[0].size | minus: 3 }}">Frekvence [Hz]</th>
</tr>

<tr>
<th>Vzdálenost</th>
  
  {% for key in data_snow[0] %}
  {% unless key[0] == "sekce" or key[0] == "vzdalenost" or key[0] == "vyska" %}
  <th>{{ key[0] }}</th>
  {% endunless %}
  {% endfor %}
  
  </tr>
  </thead>
  
  <tbody>
  
  {% assign sekce_list = data_snow | map: "sekce" | uniq %}
  
  {% for sekce in sekce_list %}
  
  <tr class="section {{ sekce }}">
  <td colspan="{{ data_snow[0].size | minus: 2 }}">
  
  {% if sekce == "vegetace" %}
  Útlum vegetací (bez vlivu vzdálenosti)
  {% elsif sekce == "pas" %}
  Útlum vlivem vzdálenosti
  {% endif %}
  
  </td>
  </tr>
  
  {% assign vysky = data_snow | map: "vyska" | uniq | sort_natural  %}
  
  {% for vyska in vysky %}
  
  <tr class="subsection">
  <td colspan="{{ data_snow[0].size | minus: 2 }}">
  Výška měření {{ vyska }} m
  </td>
  </tr>
  
  {% assign vzdalenosti = "7.5,15,30" | split: "," %}
  
  {% for vzd in vzdalenosti %}
  
  {% for row in data_snow %}
  
  {% if row.sekce == sekce and row.vyska == vyska and row.vzdalenost == vzd %}
  
  <tr>
  
  <td>{{ row.vzdalenost }} m</td>
  
  {% for key in row %}
  {% unless key[0] == "sekce" or key[0] == "vzdalenost" or key[0] == "vyska" %}
  <td>{{ key[1] }}</td>
  {% endunless %}
  {% endfor %}
  
  </tr>
  
  {% endif %}
  
  {% endfor %}
  {% endfor %}
  {% endfor %}
  {% endfor %}
  
  </tbody>
  </table>
  </div>

## Meteorologická data
  {% assign data = site.data.meteodata.plot9 %}
  
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
            Mimo vegetační sezónu - bez sněhové pokrývky
          {% elsif sekce == "snih" %}
            Mimo vegetační sezónu - se sněhovou pokrývkou
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

## Fotogalerie

{% assign seasons = "on,off,snow" | split: "," %}

{% for season in seasons %}

### {% if season == "on" %}Ve vegetační sezóně{% elsif season == "off" %}Mimo vegetační sezónu - bez sněhové pokrývky{% else %}Mimo vegetační sezónu - se sněhovou pokrývkou{% endif %}

<div class="gallery" style="display:flex; flex-wrap:wrap; gap:12px;">

{% for file in site.data.images.plot9 %}

{% assign name = file | remove: '.webp' %}
{% assign parts = name | split: ' (' %}
{% assign vzd = parts[0] %}
{% assign idx = parts[1] | remove: ')' %}

{% if vzd == "zdroj" %}
{% assign caption = "Zdroj hluku (" | append: idx | append: ")" %}
{% else %}
{% assign caption = "Vzdálenost od zdroje " | append: vzd | append: " m (" | append: idx | append: ")" %}
{% endif %}

<a href="{{ '/assets/images/plot9/' | append: season | append: '/' | append: file | relative_url }}"
   target="_blank"
   title="{{ caption }}">

<img
src="{{ '/assets/images/plot9/' | append: season | append: '/' | append: file | relative_url }}"
alt="{{ caption }}"
style="height:120px; width:auto; display:block;">

</a>

{% endfor %}

</div>

{% endfor %}
