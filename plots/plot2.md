---
layout: single
title: "Hospodaření v buku - odrostlý porost"
sidebar:
  nav: "main"
permalink: /plots/plot2/
---



## Popis  

  **Popis lokality:** buková mlazina až tyčkovina ve věku cca 20 let na souboru lesních typů 3W (živná bazická stanoviště třetího lesního vegetačního stupně.    
  
  **Datum měření:** 18.07.2024, 22.01.2026

## Měřené hodnoty hluku - Vegetační sezóna
{% assign data = site.data.noise.plot2_on %}

<div class="table-wrapper">
<table class="excel">

<thead>
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
Útlum pásu jako celku (s vlivem vzdálenosti)
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

## Měřené hodnoty hluku - Mimo vegetační sezónu
{% assign data_off = site.data.noise.plot2_off %}

<div class="table-wrapper">
<table class="excel">

<thead>
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
Útlum pásu jako celku (s vlivem vzdálenosti)
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

## Strukturní charakteristiky derivované z laserového skenování
{% assign data_lidar = site.data.lidar.plot2 %}

<div class="table-wrapper">
<table class="excel">

  <thead>

    <!-- 1. řádek hlavičky -->
    <tr>
      <th rowspan="2">Stav</th>
      <th colspan="3">Pokryvnost 0–2,5 m (%)</th>
      <th colspan="3">Pokryvnost 0–5,5 m (%)</th>
      <th colspan="3">Pokryvnost 0–p98 (%)</th>
      <th colspan="3">Výškové charakteristiky (m)</th>
      <th colspan="4">Struktura</th>
    </tr>

    <!-- 2. řádek hlavičky -->
    <tr>
      <th>0–7,5 m</th>
      <th>0–15 m</th>
      <th>0–30 m</th>

      <th>0–7,5 m</th>
      <th>0–15 m</th>
      <th>0–30 m</th>

      <th>0–7,5 m</th>
      <th>0–15 m</th>
      <th>0–30 m</th>

      <th>Max. výška</th>
      <th>p98 koruny</th>
      <th>Průměrná výška koruny</th>

      <th>Průměrná výška voxelů</th>
      <th>Směrodatná odchylka</th>
      <th>Koeficient variability</th>
      <th>Index vertikální diverzity</th>
    </tr>

  </thead>

  <tbody>
    {% for row in data_lidar %}
    <tr>
      <td>{{ row.stav }}</td>

      <td>{{ row["0-2.5_0-7.5"] }}</td>
      <td>{{ row["0-2.5_0-15"] }}</td>
      <td>{{ row["0-2.5_0-30"] }}</td>

      <td>{{ row["0-5.5_0-7.5"] }}</td>
      <td>{{ row["0-5.5_0-15"] }}</td>
      <td>{{ row["0-5.5_0-30"] }}</td>

      <td>{{ row["0-p98_0-7.5"] }}</td>
      <td>{{ row["0-p98_0-15"] }}</td>
      <td>{{ row["0-p98_0-30"] }}</td>

      <td>{{ row.max_height }}</td>
      <td>{{ row.p98_canopy }}</td>
      <td>{{ row.mean_canopy_height }}</td>

      <td>{{ row.mean_voxel_height }}</td>
      <td>{{ row.sd_voxel_height }}</td>
      <td>{{ row.cv_voxel_height }}</td>
      <td>{{ row.FHD }}</td>
    </tr>
    {% endfor %}
  </tbody>

</table>
</div>

## Meteorologická data
{% assign data = site.data.meteodata.plot2 %}

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

## Fotogalerie  
### Ve vegetační sezóně

<div style="display:flex; flex-wrap:wrap; gap:10px; align-items:flex-start;">

{% for file in site.data.images.plots %}
  <div>
    <a href="{{ '/assets/images/plot2/on/' | append: file | relative_url }}" target="_blank">
      <img 
        src="{{ '/assets/images/plot2/on/' | append: file | relative_url }}" 
        style="height:100px;">
    </a>
  </div>
{% endfor %}

</div>

### Mimo vegetační sezónu  

<div style="display:flex; flex-wrap:wrap; gap:10px; align-items:flex-start;">

{% for file in site.data.images.plots %}
  <div>
    <a href="{{ '/assets/images/plot2/off/' | append: file | relative_url }}" target="_blank">
      <img 
        src="{{ '/assets/images/plot2/off/' | append: file | relative_url }}" 
        style="height:100px;">
    </a>
  </div>
{% endfor %}

</div>