---
layout: post
title: "Visualización de datos en Educación"
author: "Jaime"
---
Test Visualizaciones de datos abiertos del [MINEDUC](http://datosabiertos.mineduc.cl/) y de la [Agencia de Calidad de la Educación](http://informacionestadistica.agenciaeducacion.cl/#/bases).

Se utilizaron las librerías JavaScript [D3](https://d3js.org/) y [D3plus](https://d3plus.org/).

### Matrícula escolar con Tree Map
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


### Categorías de Desempeño con Diagrama de Sankey.

Categorías de Desempeño y Diagramas [Sankey](https://es.wikipedia.org/wiki/Diagrama_de_Sankey)

* [Ejemplo 1](https://jmanquez.github.io/vis/vis_cd.html)
* [Ejemplo 2](https://jmanquez.github.io/vis/vis_cd2.html)
* [Ejemplo 3](https://jmanquez.github.io/vis/vis_cd3.html)
