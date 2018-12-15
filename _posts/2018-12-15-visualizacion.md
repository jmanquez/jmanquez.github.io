---
layout: post
title: "Visualización de datos en Educación"
author: "Jaime"
---
Se presenta algunas visualizaciones, con el fin de poder transmitir de manera distinta datos en el contexto educacional, utilizando la librería de javascript [D3plus](https://d3plus.org/).

### Matrícula escolar con TreeMap
En el primer ejemplo visualizaremos los datos de matrícula escolar, a trabes de un gráfico jerárquico [TreeMap](https://en.wikipedia.org/wiki/Treemapping)

<!-- create container element for visualization -->
<div id="viz"></div>

<script>
  // sample data array
  var sample_data = [
    {"value": 100, "name": "alpha"},
    {"value": 70, "name": "beta"},
    {"value": 40, "name": "gamma"},
    {"value": 15, "name": "delta"},
    {"value": 5, "name": "epsilon"},
    {"value": 1, "name": "zeta"}
  ]
  // instantiate d3plus
  var visualization = d3plus.viz()
    .container("#viz")  // container DIV to hold the visualization
    .data(sample_data)  // data to use with the visualization
    .type("tree_map")   // visualization type
    .id("name")         // key for which our data is unique on
    .size("value")      // sizing of blocks
    .draw()             // finally, draw the visualization!
</script>


### Categorias de Desempeño con Diagrama de Sankey.

Los digagramas de Sankey...
