---
layout: post
title: "Visualización de datos en Educación"
author: "Jaime"
---
Se presenta algunas visualizaciones, utilizando datos abiertos del [MINEDUC](http://datosabiertos.mineduc.cl/) y de la [Agencia de Calidad de la Educación](http://informacionestadistica.agenciaeducacion.cl/#/bases) y la librería de javascript [D3plus](https://d3plus.org/).

### Matrícula escolar con TreeMap
En el primer ejemplo se presenta un gráfico jerárquico [TreeMap](https://en.wikipedia.org/wiki/Treemapping)

<div id="viz"></div>

<script>
  var visualization = d3plus.viz()
    .container("#viz")
    .data({{site.data.matricula | jsonify}})
    .type("tree_map")
    .id(["REGION","COMUNA"])
    .size("MATRICULA")
    .format("es_ES")
    .draw()
</script>


### Categorias de Desempeño con Diagrama de Sankey.

Los digagramas de Sankey...

<div id="viz2"></div>
<script>
var nodes = [
  {id: "alpha"},
  {id: "beta"},
  {id: "gamma"},
  {id: "epsilon"},
  {id: "zeta"},
  {id: "theta"}
];

var links = [
  {source: "alpha", target: "beta"},
  {source: "alpha", target: "gamma"},
  {source: "epsilon", target: "zeta"},
  {source: "epsilon", target: "theta"},
  {source: "theta", target: "alpha"}
];

new d3plus.Sankey()
  .links(links)
  .nodes(nodes)
  .render();

</script>
