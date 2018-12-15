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
var sample_data = [
    {"value": 100, "name": "Iquique", "group": "Región I"},
    {"value": 70, "name": "Antofagasta", "group": "Región II"},
    {"value": 40, "name": "Santa Elena", "group": "Región II"},
    {"value": 15, "name": "Calama", "group": "Región II"},
    {"value": 5, "name": "Alto Hospicio", "group": "Región I"},
    {"value": 1, "name": "Huara", "group": "Región I"}
  ]
  var visualization = d3plus.viz()
    .container("#viz")
    .data(sample_data)
    .type("tree_map")
    .id(["group","name"])
    .size("value")
    .draw()
</script>


### Categorias de Desempeño con Diagrama de Sankey.

Los digagramas de Sankey...
