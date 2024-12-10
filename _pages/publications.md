---
layout: page
permalink: /publications/
title: Publications
description: Publications in reversed chronological order.
sections:
  - bibquery: "@unpublished"
    text: "Working Papers"


  - bibquery: "@preprints"
    text: "Preprints"

  - bibquery: "@article"
    text: "Conference/Journal Proceedings"

years: [2024, 2023, 2022, 2021, 2020]

nav: true
nav_order: 2
---

<!-- _pages/publications.md -->
<div class="publications">

{%- for section in page.sections %}
  <a id="{{section.text}}"></a>
  <p class="bibtitle">{{section.text}}</p>
  {%- for y in page.years %}

    {%- comment -%}  Count bibliography in actual section and year {%- endcomment -%}
    {%- capture citecount -%}
    {%- bibliography_count -f {{site.scholar.bibliography}} -q {{section.bibquery}}[year={{y}}] -%}
    {%- endcapture -%}

    {%- comment -%} If exist bibliography in actual section and year, print {%- endcomment -%}
    {%- if citecount !="0" %}

      {% bibliography -f {{site.scholar.bibliography}} -q {{section.bibquery}}[year={{y}}] %}

    {%- endif -%}

  {%- endfor %}

{%- endfor %}

</div>
