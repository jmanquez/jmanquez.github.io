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

Categorias de Desempeño y Diagramas Sankey...

<div id="viz2"></div>

<script>
  var nodes = [
    /*grupos*/
    {"id": "Grupos"},
    {"id": "Grupo 1"},
    {"id": "Grupo 2"},
    {"id": "Grupo 3"},
    {"id": "Grupo 4"},
    {"id": "Grupo 5"},
    /*conceptos*/
    {"id": "Cambio/Reforma Constitucional"},
    {"id": "Protección de los Derechos"},
    {"id": "Estado Laico"},
    {"id": "Igualdad"},
    {"id": "Defensor del Ciudadano"},
    {"id": "Dignidad"},
    {"id": "Sindicalizarse y Negociación Colectiva"},
    {"id": "Cambio/Reforma Constitucional"},
    {"id": "Salud"},
    {"id": "Educación"},
    {"id": "Asamblea Constituyente"},
    {"id": "Estado Laico"},
    {"id": "Sindicalizarse y Negociación Colectiva"},
    {"id": "Régimen de Gobierno"},
    {"id": "Seguridad Social"},
    {"id": "Banco Central"},
    {"id": "Propiedad"},
    {"id": "Familia"},
    {"id": "Libre Empresa"},
    {"id": "Tribunal Constitucional"},
    {"id": "Voto Obligatorio"},
    {"id": "Democracia Participativa"},
    {"id": "Asamblea Constituyente"},
    {"id": "Estado Laico"},
    {"id": "Equidad"},
    /*comunas*/
    {"id": "Cerrillos"},
    {"id": "Cerro Navia"},
    {"id": "El Bosque"},
    {"id": "Quilicura"},
    {"id": "Estación Central"},
    {"id": "Huechuraba"},
    {"id": "La Cisterna"},
    {"id": "La Florida"},
    {"id": "Macul"},
    {"id": "Maipú"},
    {"id": "Peñalolén"},
    {"id": "Recoleta"},
    {"id": "San Joaquín"},
    {"id": "San Miguel"},
    {"id": "La Reina"},
    {"id": "Las Condes"},
    {"id": "Lo Barnechea"},
    {"id": "Ñuñoa"},
    {"id": "Providencia"},
    {"id": "Santiago"},
    {"id": "Vitacura"},
    {"id": "Conchalí"},
    {"id": "Independencia"},
    {"id": "La Pintana"},
    {"id": "Lo Espejo"},
    {"id": "Pedro Aguirre Cerda"},
    {"id": "Renca"},
    {"id": "San Ramón"},
    {"id": "La Granja"},
    {"id": "Lo Prado"},
    {"id": "Pudahuel"},
    {"id": "Quinta Normal"}
  ];
  var edges = [
    /*grupos*/
    {"strenght": 1,  "source": 0, "target": 1},
    {"strenght": 1,  "source": 0, "target": 2},
    {"strenght": 1,  "source": 0, "target": 3},
    {"strenght": 1,  "source": 0, "target": 4},
    {"strenght": 1,  "source": 0, "target": 5},
    /*conceptos*/
    {"strenght": 1,  "source": 6, "target": 1},
    {"strenght": 1,  "source": 7, "target": 1},
    {"strenght": 1,  "source": 8, "target": 1},
    {"strenght": 1,  "source": 9, "target": 1},
    {"strenght": 1,  "source": 10, "target": 1},
    {"strenght": 1,  "source": 11, "target": 2},
    {"strenght": 1,  "source": 12, "target": 2},
    {"strenght": 1,  "source": 13, "target": 2},
    {"strenght": 1,  "source": 14, "target": 2},
    {"strenght": 1,  "source": 15, "target": 2},
    {"strenght": 1,  "source": 16, "target": 3},
    {"strenght": 1,  "source": 17, "target": 3},
    {"strenght": 1,  "source": 18, "target": 3},
    {"strenght": 1,  "source": 19, "target": 3},
    {"strenght": 1,  "source": 20, "target": 3},
    {"strenght": 1,  "source": 21, "target": 4},
    {"strenght": 1,  "source": 22, "target": 4},
    {"strenght": 1,  "source": 23, "target": 4},
    {"strenght": 1,  "source": 24, "target": 4},
    {"strenght": 1,  "source": 25, "target": 4},
    {"strenght": 1,  "source": 26, "target": 5},
    {"strenght": 1,  "source": 27, "target": 5},
    {"strenght": 1,  "source": 28, "target": 5},
    {"strenght": 1,  "source": 29, "target": 5},
    {"strenght": 1,  "source": 30, "target": 5},
    /*comunas*/
    {"strenght": 1,  "source": 5, "target": 31},
    {"strenght": 1,  "source": 5, "target": 32},
    {"strenght": 1,  "source": 5, "target": 33},
    {"strenght": 1,  "source": 5, "target": 34},
    {"strenght": 1,  "source": 4, "target": 35},
    {"strenght": 1,  "source": 4, "target": 36},
    {"strenght": 1,  "source": 4, "target": 37},
    {"strenght": 1,  "source": 4, "target": 38},
    {"strenght": 1,  "source": 4, "target": 39},
    {"strenght": 1,  "source": 4, "target": 40},
    {"strenght": 1,  "source": 4, "target": 41},
    {"strenght": 1,  "source": 4, "target": 42},
    {"strenght": 1,  "source": 4, "target": 43},
    {"strenght": 1,  "source": 4, "target": 44},
    {"strenght": 1,  "source": 3, "target": 45},
    {"strenght": 1,  "source": 3, "target": 46},
    {"strenght": 1,  "source": 3, "target": 47},
    {"strenght": 1,  "source": 3, "target": 48},
    {"strenght": 1,  "source": 3, "target": 49},
    {"strenght": 1,  "source": 3, "target": 50},
    {"strenght": 1,  "source": 3, "target": 51},
    {"strenght": 1,  "source": 2, "target": 52},
    {"strenght": 1,  "source": 2, "target": 53},
    {"strenght": 1,  "source": 2, "target": 54},
    {"strenght": 1,  "source": 2, "target": 55},
    {"strenght": 1,  "source": 2, "target": 56},
    {"strenght": 1,  "source": 2, "target": 57},
    {"strenght": 1,  "source": 2, "target": 58},
    {"strenght": 1,  "source": 1, "target": 59},
    {"strenght": 1,  "source": 1, "target": 60},
    {"strenght": 1,  "source": 1, "target": 61},
    {"strenght": 1,  "source": 1, "target": 62}
  ];
  var visualization = d3plus.viz()
    .container("#viz2")
    .edges({
      "strength": "strength",
      "value": edges
    })
    .focus({
      "tooltip": false,
      "value": "Grupos"
    })
    .id("id")
    .nodes(nodes)
    .size(100)
    .type("sankey")
    .draw();
</script>
