---
layout: post
title: "Visualización de datos en Educación"
author: "Jaime"
---
Se presenta algunas visualizaciones, con el fin de poder transmitir de manera distinta datos en el contexto educacional, utilizando la librería de javascript [D3plus](https://d3plus.org/).

### Matrícula escolar con TreeMap
En el primer ejemplo se presenta un gráfico jerárquico [TreeMap](https://en.wikipedia.org/wiki/Treemapping)

<div id="viz"></div>

<script>
d3.json({{site.data.matricula | jsonify}}, function(data) {
  make_viz(matricula);
});

function make_viz(data){
  var visualization = d3plus.viz()
    .container("#viz")
    .data(matricula)
    .type("tree_map")
    .id(["REGION","COMUNA"])
    .size("MATRICULA")
    .format("es_ES")
    .draw()
  }
</script>


### Categorias de Desempeño con Diagrama de Sankey.

Los digagramas de Sankey...
