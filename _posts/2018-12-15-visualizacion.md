---
layout: post
title: "Visualización de datos en Educación"
author: "Jaime"
---
Se presentan algunas visualizaciones utilizando datos abiertos del [MINEDUC](http://datosabiertos.mineduc.cl/) y de la [Agencia de Calidad de la Educación](http://informacionestadistica.agenciaeducacion.cl/#/bases). Para estas visualización se probaron las librerías JavaScript [D3](https://d3js.org/) y [D3plus](https://d3plus.org/).

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

Categorias de Desempeño y Diagramas Sankey...

<div id="viz2"></div>

<script>
  var nodes = [

    {"id": "2018"},
    {"id": "2017"},
    {"id": "2016"},

    {"id": "Alto"},
    {"id": "Medio"},
    {"id": "Medio-Bajo"},
    {"id": "Insuficiente"}
  ];
  var links = [

    {"value": 90,  "source": 0, "target": 3},
    {"value": 50,  "source": 0, "target": 4},
    {"value": 50,  "source": 0, "target": 5},
    {"value": 30,  "source": 0, "target": 6},

    {"value": 88,  "source": 1, "target": 3},
    {"value": 50,  "source": 1, "target": 4},
    {"value": 23,  "source": 1, "target": 5},
    {"value": 99,  "source": 1, "target": 6},


    {"value": 48,  "source": 2, "target": 3},
    {"value": 20,  "source": 2, "target": 4},
    {"value": 43,  "source": 2, "target": 5},
    {"value": 69,  "source": 2, "target": 6}
  ];
  var visualization = d3plus.viz()
    .container("#viz2")
    .edges({
      "strength": "strength",
      "value": links
    })
    .id("id")
    .nodes(nodes)
    .size(100)
    .type("sankey")
    .draw();
</script>
