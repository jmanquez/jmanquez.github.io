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
  {
    "NOM_COM_RBD": "IQUIQUE",
    "COUNT(MRUN)": 34877,
    "COD_REG_RBD": "Región 1"
  },
  {
    "NOM_COM_RBD": "ALTO HOSPICIO",
    "COUNT(MRUN)": 22336,
    "COD_REG_RBD": "Región 1"
  },
  {
    "NOM_COM_RBD": "POZO ALMONTE",
    "COUNT(MRUN)": 2723,
    "COD_REG_RBD": "Región 1"
  },
  {
    "NOM_COM_RBD": "CAMIÑA",
    "COUNT(MRUN)": 208,
    "COD_REG_RBD": "Región 1"
  },
  {
    "NOM_COM_RBD": "COLCHANE",
    "COUNT(MRUN)": 121,
    "COD_REG_RBD": "Región 1"
  },
  {
    "NOM_COM_RBD": "HUARA",
    "COUNT(MRUN)": 408,
    "COD_REG_RBD": "Región 1"
  },
  {
    "NOM_COM_RBD": "PICA",
    "COUNT(MRUN)": 1059,
    "COD_REG_RBD": "Región 1"
  },
  {
    "NOM_COM_RBD": "ANTOFAGASTA",
    "COUNT(MRUN)": 63857,
    "COD_REG_RBD": "Región 2"
  },
  {
    "NOM_COM_RBD": "MEJILLONES",
    "COUNT(MRUN)": 2156,
    "COD_REG_RBD": "Región 2"
  },
  {
    "NOM_COM_RBD": "SIERRA GORDA",
    "COUNT(MRUN)": 228,
    "COD_REG_RBD": "Región 2"
  },
  {
    "NOM_COM_RBD": "TALTAL",
    "COUNT(MRUN)": 2266,
    "COD_REG_RBD": "Región 2"
  },
  {
    "NOM_COM_RBD": "CALAMA",
    "COUNT(MRUN)": 31277,
    "COD_REG_RBD": "Región 2"
  },
  {
    "NOM_COM_RBD": "OLLAGÜE",
    "COUNT(MRUN)": 38,
    "COD_REG_RBD": "Región 2"
  },
  {
    "NOM_COM_RBD": "SAN PEDRO DE ATACAMA",
    "COUNT(MRUN)": 1463,
    "COD_REG_RBD": "Región 2"
  },
  {
    "NOM_COM_RBD": "TOCOPILLA",
    "COUNT(MRUN)": 4838,
    "COD_REG_RBD": "Región 2"
  },
  {
    "NOM_COM_RBD": "MARIA ELENA",
    "COUNT(MRUN)": 857,
    "COD_REG_RBD": "Región 2"
  },
  {
    "NOM_COM_RBD": "COPIAPO",
    "COUNT(MRUN)": 29552,
    "COD_REG_RBD": "Región 3"
  },
  {
    "NOM_COM_RBD": "CALDERA",
    "COUNT(MRUN)": 3236,
    "COD_REG_RBD": "Región 3"
  },
  {
    "NOM_COM_RBD": "TIERRA AMARILLA",
    "COUNT(MRUN)": 2128,
    "COD_REG_RBD": "Región 3"
  },
  {
    "NOM_COM_RBD": "CHAÑARAL",
    "COUNT(MRUN)": 2491,
    "COD_REG_RBD": "Región 3"
  },
  {
    "NOM_COM_RBD": "DIEGO DE ALMAGRO",
    "COUNT(MRUN)": 2914,
    "COD_REG_RBD": "Región 3"
  },
  {
    "NOM_COM_RBD": "VALLENAR",
    "COUNT(MRUN)": 9916,
    "COD_REG_RBD": "Región 3"
  },
  {
    "NOM_COM_RBD": "ALTO DEL CARMEN",
    "COUNT(MRUN)": 776,
    "COD_REG_RBD": "Región 3"
  },
  {
    "NOM_COM_RBD": "FREIRINA",
    "COUNT(MRUN)": 1034,
    "COD_REG_RBD": "Región 3"
  },
  {
    "NOM_COM_RBD": "HUASCO",
    "COUNT(MRUN)": 1690,
    "COD_REG_RBD": "Región 3"
  },
  {
    "NOM_COM_RBD": "LA SERENA",
    "COUNT(MRUN)": 45679,
    "COD_REG_RBD": "Región 4"
  },
  {
    "NOM_COM_RBD": "COQUIMBO",
    "COUNT(MRUN)": 34655,
    "COD_REG_RBD": "Región 4"
  },
  {
    "NOM_COM_RBD": "ANDACOLLO",
    "COUNT(MRUN)": 1805,
    "COD_REG_RBD": "Región 4"
  },
  {
    "NOM_COM_RBD": "LA HIGUERA",
    "COUNT(MRUN)": 598,
    "COD_REG_RBD": "Región 4"
  },
  {
    "NOM_COM_RBD": "PAIGUANO",
    "COUNT(MRUN)": 635,
    "COD_REG_RBD": "Región 4"
  },
  {
    "NOM_COM_RBD": "VICUÑA",
    "COUNT(MRUN)": 4513,
    "COD_REG_RBD": "Región 4"
  },
  {
    "NOM_COM_RBD": "ILLAPEL",
    "COUNT(MRUN)": 5740,
    "COD_REG_RBD": "Región 4"
  },
  {
    "NOM_COM_RBD": "CANELA",
    "COUNT(MRUN)": 1294,
    "COD_REG_RBD": "Región 4"
  },
  {
    "NOM_COM_RBD": "LOS VILOS",
    "COUNT(MRUN)": 3521,
    "COD_REG_RBD": "Región 4"
  },
  {
    "NOM_COM_RBD": "SALAMANCA",
    "COUNT(MRUN)": 4701,
    "COD_REG_RBD": "Región 4"
  },
  {
    "NOM_COM_RBD": "OVALLE",
    "COUNT(MRUN)": 20990,
    "COD_REG_RBD": "Región 4"
  },
  {
    "NOM_COM_RBD": "COMBARBALA",
    "COUNT(MRUN)": 1883,
    "COD_REG_RBD": "Región 4"
  },
  {
    "NOM_COM_RBD": "MONTE PATRIA",
    "COUNT(MRUN)": 4739,
    "COD_REG_RBD": "Región 4"
  },
  {
    "NOM_COM_RBD": "PUNITAQUI",
    "COUNT(MRUN)": 1726,
    "COD_REG_RBD": "Región 4"
  },
  {
    "NOM_COM_RBD": "RIO HURTADO",
    "COUNT(MRUN)": 584,
    "COD_REG_RBD": "Región 4"
  },
  {
    "NOM_COM_RBD": "VALPARAISO",
    "COUNT(MRUN)": 43420,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "CASABLANCA",
    "COUNT(MRUN)": 4387,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "CONCON",
    "COUNT(MRUN)": 6942,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "JUAN FERNANDEZ",
    "COUNT(MRUN)": 137,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "PUCHUNCAVI",
    "COUNT(MRUN)": 2339,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "QUINTERO",
    "COUNT(MRUN)": 4805,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "VIÑA DEL MAR",
    "COUNT(MRUN)": 47125,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "ISLA DE PASCUA",
    "COUNT(MRUN)": 1254,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "LOS ANDES",
    "COUNT(MRUN)": 13847,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "CALLE LARGA",
    "COUNT(MRUN)": 2143,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "RINCONADA",
    "COUNT(MRUN)": 1157,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "SAN ESTEBAN",
    "COUNT(MRUN)": 1315,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "LA LIGUA",
    "COUNT(MRUN)": 5776,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "CABILDO",
    "COUNT(MRUN)": 3746,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "PAPUDO",
    "COUNT(MRUN)": 762,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "PETORCA",
    "COUNT(MRUN)": 1474,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "ZAPALLAR",
    "COUNT(MRUN)": 1275,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "QUILLOTA",
    "COUNT(MRUN)": 17287,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "CALERA",
    "COUNT(MRUN)": 9926,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "HIJUELAS",
    "COUNT(MRUN)": 2325,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "LA CRUZ",
    "COUNT(MRUN)": 1438,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "NOGALES",
    "COUNT(MRUN)": 3433,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "SAN ANTONIO",
    "COUNT(MRUN)": 15723,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "ALGARROBO",
    "COUNT(MRUN)": 2037,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "CARTAGENA",
    "COUNT(MRUN)": 3910,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "EL QUISCO",
    "COUNT(MRUN)": 1845,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "EL TABO",
    "COUNT(MRUN)": 920,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "SANTO DOMINGO",
    "COUNT(MRUN)": 2015,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "SAN FELIPE",
    "COUNT(MRUN)": 15563,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "CATEMU",
    "COUNT(MRUN)": 2117,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "LLAILLAY",
    "COUNT(MRUN)": 4326,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "PANQUEHUE",
    "COUNT(MRUN)": 1131,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "PUTAENDO",
    "COUNT(MRUN)": 1863,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "SANTA MARIA",
    "COUNT(MRUN)": 1949,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "QUILPUE",
    "COUNT(MRUN)": 27000,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "LIMACHE",
    "COUNT(MRUN)": 7108,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "OLMUE",
    "COUNT(MRUN)": 2096,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "VILLA ALEMANA",
    "COUNT(MRUN)": 18784,
    "COD_REG_RBD": "Región 5"
  },
  {
    "NOM_COM_RBD": "RANCAGUA",
    "COUNT(MRUN)": 45672,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "CODEGUA",
    "COUNT(MRUN)": 1336,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "COINCO",
    "COUNT(MRUN)": 847,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "COLTAUCO",
    "COUNT(MRUN)": 2964,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "DOÑIHUE",
    "COUNT(MRUN)": 3312,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "GRANEROS",
    "COUNT(MRUN)": 7372,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "LAS CABRAS",
    "COUNT(MRUN)": 4168,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "MACHALI",
    "COUNT(MRUN)": 9877,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "MALLOA",
    "COUNT(MRUN)": 1300,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "MOSTAZAL",
    "COUNT(MRUN)": 3267,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "OLIVAR",
    "COUNT(MRUN)": 2075,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "PEUMO",
    "COUNT(MRUN)": 1895,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "PICHIDEGUA",
    "COUNT(MRUN)": 2094,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "QUINTA DE TILCOCO",
    "COUNT(MRUN)": 1988,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "RENGO",
    "COUNT(MRUN)": 10183,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "REQUINOA",
    "COUNT(MRUN)": 3496,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "SAN VICENTE",
    "COUNT(MRUN)": 9043,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "PICHILEMU",
    "COUNT(MRUN)": 2586,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "LA ESTRELLA",
    "COUNT(MRUN)": 223,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "LITUECHE",
    "COUNT(MRUN)": 905,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "MARCHIHUE",
    "COUNT(MRUN)": 749,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "NAVIDAD",
    "COUNT(MRUN)": 793,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "PAREDONES",
    "COUNT(MRUN)": 694,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "SAN FERNANDO",
    "COUNT(MRUN)": 15621,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "CHEPICA",
    "COUNT(MRUN)": 1643,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "CHIMBARONGO",
    "COUNT(MRUN)": 5566,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "LOLOL",
    "COUNT(MRUN)": 863,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "NANCAGUA",
    "COUNT(MRUN)": 2534,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "PALMILLA",
    "COUNT(MRUN)": 1070,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "PERALILLO",
    "COUNT(MRUN)": 1437,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "PLACILLA",
    "COUNT(MRUN)": 767,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "PUMANQUE",
    "COUNT(MRUN)": 251,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "SANTA CRUZ",
    "COUNT(MRUN)": 8892,
    "COD_REG_RBD": "Región 6"
  },
  {
    "NOM_COM_RBD": "TALCA",
    "COUNT(MRUN)": 44483,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "CONSTITUCION",
    "COUNT(MRUN)": 8337,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "CUREPTO",
    "COUNT(MRUN)": 1115,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "EMPEDRADO",
    "COUNT(MRUN)": 681,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "MAULE",
    "COUNT(MRUN)": 4283,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "PELARCO",
    "COUNT(MRUN)": 927,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "PENCAHUE",
    "COUNT(MRUN)": 812,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "RIO CLARO",
    "COUNT(MRUN)": 1658,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "SAN CLEMENTE",
    "COUNT(MRUN)": 5541,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "SAN RAFAEL",
    "COUNT(MRUN)": 1148,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "CAUQUENES",
    "COUNT(MRUN)": 7021,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "CHANCO",
    "COUNT(MRUN)": 1126,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "PELLUHUE",
    "COUNT(MRUN)": 1230,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "CURICO",
    "COUNT(MRUN)": 29236,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "HUALAÑE",
    "COUNT(MRUN)": 1530,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "LICANTEN",
    "COUNT(MRUN)": 1053,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "MOLINA",
    "COUNT(MRUN)": 6963,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "RAUCO",
    "COUNT(MRUN)": 932,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "ROMERAL",
    "COUNT(MRUN)": 2015,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "SAGRADA FAMILIA",
    "COUNT(MRUN)": 2045,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "TENO",
    "COUNT(MRUN)": 4343,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "VICHUQUEN",
    "COUNT(MRUN)": 544,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "LINARES",
    "COUNT(MRUN)": 19318,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "COLBUN",
    "COUNT(MRUN)": 2937,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "LONGAVI",
    "COUNT(MRUN)": 3760,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "PARRAL",
    "COUNT(MRUN)": 7045,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "RETIRO",
    "COUNT(MRUN)": 3190,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "SAN JAVIER",
    "COUNT(MRUN)": 8730,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "VILLA ALEGRE",
    "COUNT(MRUN)": 1955,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "YERBAS BUENAS",
    "COUNT(MRUN)": 1696,
    "COD_REG_RBD": "Región 7"
  },
  {
    "NOM_COM_RBD": "CONCEPCION",
    "COUNT(MRUN)": 40104,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "CORONEL",
    "COUNT(MRUN)": 20435,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "CHIGUAYANTE",
    "COUNT(MRUN)": 14000,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "FLORIDA",
    "COUNT(MRUN)": 1436,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "HUALQUI",
    "COUNT(MRUN)": 3308,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "LOTA",
    "COUNT(MRUN)": 7862,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "PENCO",
    "COUNT(MRUN)": 5720,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "SAN PEDRO DE LA PAZ",
    "COUNT(MRUN)": 20819,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "SANTA JUANA",
    "COUNT(MRUN)": 2278,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "TALCAHUANO",
    "COUNT(MRUN)": 21586,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "TOME",
    "COUNT(MRUN)": 8549,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "HUALPEN",
    "COUNT(MRUN)": 11375,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "LEBU",
    "COUNT(MRUN)": 4687,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "ARAUCO",
    "COUNT(MRUN)": 6332,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "CAÑETE",
    "COUNT(MRUN)": 7098,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "CONTULMO",
    "COUNT(MRUN)": 1099,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "CURANILAHUE",
    "COUNT(MRUN)": 5729,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "LOS ALAMOS",
    "COUNT(MRUN)": 3899,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "TIRUA",
    "COUNT(MRUN)": 1852,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "LOS ANGELES",
    "COUNT(MRUN)": 38514,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "ANTUCO",
    "COUNT(MRUN)": 634,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "CABRERO",
    "COUNT(MRUN)": 4819,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "LAJA",
    "COUNT(MRUN)": 4288,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "MULCHEN",
    "COUNT(MRUN)": 4994,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "NACIMIENTO",
    "COUNT(MRUN)": 5007,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "NEGRETE",
    "COUNT(MRUN)": 1424,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "QUILACO",
    "COUNT(MRUN)": 385,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "QUILLECO",
    "COUNT(MRUN)": 1249,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "SAN ROSENDO",
    "COUNT(MRUN)": 326,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "SANTA BARBARA",
    "COUNT(MRUN)": 2419,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "TUCAPEL",
    "COUNT(MRUN)": 2003,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "YUMBEL",
    "COUNT(MRUN)": 3242,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "ALTO BIOBIO",
    "COUNT(MRUN)": 1093,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "CHILLAN",
    "COUNT(MRUN)": 34536,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "BULNES",
    "COUNT(MRUN)": 3746,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "COBQUECURA",
    "COUNT(MRUN)": 566,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "COELEMU",
    "COUNT(MRUN)": 2727,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "COIHUECO",
    "COUNT(MRUN)": 3763,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "CHILLAN VIEJO",
    "COUNT(MRUN)": 3523,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "EL CARMEN",
    "COUNT(MRUN)": 2193,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "NINHUE",
    "COUNT(MRUN)": 723,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "ÑIQUEN",
    "COUNT(MRUN)": 1311,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "PEMUCO",
    "COUNT(MRUN)": 1086,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "PINTO",
    "COUNT(MRUN)": 1734,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "PORTEZUELO",
    "COUNT(MRUN)": 700,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "QUILLON",
    "COUNT(MRUN)": 2232,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "QUIRIHUE",
    "COUNT(MRUN)": 1792,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "RANQUIL",
    "COUNT(MRUN)": 829,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "SAN CARLOS",
    "COUNT(MRUN)": 8966,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "SAN FABIAN",
    "COUNT(MRUN)": 741,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "SAN IGNACIO",
    "COUNT(MRUN)": 2055,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "SAN NICOLAS",
    "COUNT(MRUN)": 2617,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "TREGUACO",
    "COUNT(MRUN)": 660,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "YUNGAY",
    "COUNT(MRUN)": 3120,
    "COD_REG_RBD": "Región 8"
  },
  {
    "NOM_COM_RBD": "TEMUCO",
    "COUNT(MRUN)": 52601,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "CARAHUE",
    "COUNT(MRUN)": 4640,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "CUNCO",
    "COUNT(MRUN)": 2779,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "CURARREHUE",
    "COUNT(MRUN)": 1093,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "FREIRE",
    "COUNT(MRUN)": 3284,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "GALVARINO",
    "COUNT(MRUN)": 2161,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "GORBEA",
    "COUNT(MRUN)": 1668,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "LAUTARO",
    "COUNT(MRUN)": 6342,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "LONCOCHE",
    "COUNT(MRUN)": 3692,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "MELIPEUCO",
    "COUNT(MRUN)": 924,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "NUEVA IMPERIAL",
    "COUNT(MRUN)": 6329,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "PADRE LAS CASAS",
    "COUNT(MRUN)": 10180,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "PERQUENCO",
    "COUNT(MRUN)": 1229,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "PITRUFQUEN",
    "COUNT(MRUN)": 5517,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "PUCON",
    "COUNT(MRUN)": 4856,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "SAAVEDRA",
    "COUNT(MRUN)": 1837,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "TEODORO SCHMIDT",
    "COUNT(MRUN)": 1849,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "TOLTEN",
    "COUNT(MRUN)": 1678,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "VILCUN",
    "COUNT(MRUN)": 4822,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "VILLARRICA",
    "COUNT(MRUN)": 11858,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "CHOLCHOL",
    "COUNT(MRUN)": 2334,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "ANGOL",
    "COUNT(MRUN)": 10332,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "COLLIPULLI",
    "COUNT(MRUN)": 4649,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "CURACAUTIN",
    "COUNT(MRUN)": 2882,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "ERCILLA",
    "COUNT(MRUN)": 1178,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "LONQUIMAY",
    "COUNT(MRUN)": 1762,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "LOS SAUCES",
    "COUNT(MRUN)": 1084,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "LUMACO",
    "COUNT(MRUN)": 1317,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "PUREN",
    "COUNT(MRUN)": 1915,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "RENAICO",
    "COUNT(MRUN)": 1473,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "TRAIGUEN",
    "COUNT(MRUN)": 3380,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "VICTORIA",
    "COUNT(MRUN)": 6101,
    "COD_REG_RBD": "Región 9"
  },
  {
    "NOM_COM_RBD": "PUERTO MONTT",
    "COUNT(MRUN)": 45681,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "CALBUCO",
    "COUNT(MRUN)": 5911,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "COCHAMO",
    "COUNT(MRUN)": 552,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "FRESIA",
    "COUNT(MRUN)": 1941,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "FRUTILLAR",
    "COUNT(MRUN)": 3513,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "LOS MUERMOS",
    "COUNT(MRUN)": 3262,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "LLANQUIHUE",
    "COUNT(MRUN)": 2289,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "MAULLIN",
    "COUNT(MRUN)": 1822,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "PUERTO VARAS",
    "COUNT(MRUN)": 8414,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "CASTRO",
    "COUNT(MRUN)": 9229,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "ANCUD",
    "COUNT(MRUN)": 7419,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "CHONCHI",
    "COUNT(MRUN)": 2705,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "CURACO DE VELEZ",
    "COUNT(MRUN)": 585,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "DALCAHUE",
    "COUNT(MRUN)": 2169,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "PUQUELDON",
    "COUNT(MRUN)": 405,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "QUEILEN",
    "COUNT(MRUN)": 814,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "QUELLON",
    "COUNT(MRUN)": 5293,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "QUEMCHI",
    "COUNT(MRUN)": 1138,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "QUINCHAO",
    "COUNT(MRUN)": 1841,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "OSORNO",
    "COUNT(MRUN)": 28997,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "PUERTO OCTAY",
    "COUNT(MRUN)": 1255,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "PURRANQUE",
    "COUNT(MRUN)": 3427,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "PUYEHUE",
    "COUNT(MRUN)": 1750,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "RIO NEGRO",
    "COUNT(MRUN)": 2110,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "SAN JUAN DE LA COSTA",
    "COUNT(MRUN)": 1073,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "SAN PABLO",
    "COUNT(MRUN)": 1406,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "CHAITEN",
    "COUNT(MRUN)": 674,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "FUTALEUFU",
    "COUNT(MRUN)": 402,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "HUALAIHUE",
    "COUNT(MRUN)": 1657,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "PALENA",
    "COUNT(MRUN)": 265,
    "COD_REG_RBD": "Región 10"
  },
  {
    "NOM_COM_RBD": "COIHAIQUE",
    "COUNT(MRUN)": 11293,
    "COD_REG_RBD": "Región 11"
  },
  {
    "NOM_COM_RBD": "LAGO VERDE",
    "COUNT(MRUN)": 90,
    "COD_REG_RBD": "Región 11"
  },
  {
    "NOM_COM_RBD": "AISEN",
    "COUNT(MRUN)": 4596,
    "COD_REG_RBD": "Región 11"
  },
  {
    "NOM_COM_RBD": "CISNES",
    "COUNT(MRUN)": 940,
    "COD_REG_RBD": "Región 11"
  },
  {
    "NOM_COM_RBD": "GUAITECAS",
    "COUNT(MRUN)": 272,
    "COD_REG_RBD": "Región 11"
  },
  {
    "NOM_COM_RBD": "COCHRANE",
    "COUNT(MRUN)": 624,
    "COD_REG_RBD": "Región 11"
  },
  {
    "NOM_COM_RBD": "O'HIGGINS",
    "COUNT(MRUN)": 86,
    "COD_REG_RBD": "Región 11"
  },
  {
    "NOM_COM_RBD": "TORTEL",
    "COUNT(MRUN)": 72,
    "COD_REG_RBD": "Región 11"
  },
  {
    "NOM_COM_RBD": "CHILE CHICO",
    "COUNT(MRUN)": 809,
    "COD_REG_RBD": "Región 11"
  },
  {
    "NOM_COM_RBD": "RIO IBAÑEZ",
    "COUNT(MRUN)": 305,
    "COD_REG_RBD": "Región 11"
  },
  {
    "NOM_COM_RBD": "PUNTA ARENAS",
    "COUNT(MRUN)": 20852,
    "COD_REG_RBD": "Región 12"
  },
  {
    "NOM_COM_RBD": "LAGUNA BLANCA",
    "COUNT(MRUN)": 31,
    "COD_REG_RBD": "Región 12"
  },
  {
    "NOM_COM_RBD": "RIO VERDE",
    "COUNT(MRUN)": 7,
    "COD_REG_RBD": "Región 12"
  },
  {
    "NOM_COM_RBD": "SAN GREGORIO",
    "COUNT(MRUN)": 40,
    "COD_REG_RBD": "Región 12"
  },
  {
    "NOM_COM_RBD": "CABO DE HORNOS",
    "COUNT(MRUN)": 383,
    "COD_REG_RBD": "Región 12"
  },
  {
    "NOM_COM_RBD": "ANTARTICA",
    "COUNT(MRUN)": 4,
    "COD_REG_RBD": "Región 12"
  },
  {
    "NOM_COM_RBD": "PORVENIR",
    "COUNT(MRUN)": 994,
    "COD_REG_RBD": "Región 12"
  },
  {
    "NOM_COM_RBD": "PRIMAVERA",
    "COUNT(MRUN)": 46,
    "COD_REG_RBD": "Región 12"
  },
  {
    "NOM_COM_RBD": "TIMAUKEL",
    "COUNT(MRUN)": 21,
    "COD_REG_RBD": "Región 12"
  },
  {
    "NOM_COM_RBD": "NATALES",
    "COUNT(MRUN)": 3634,
    "COD_REG_RBD": "Región 12"
  },
  {
    "NOM_COM_RBD": "TORRES DEL PAINE",
    "COUNT(MRUN)": 33,
    "COD_REG_RBD": "Región 12"
  },
  {
    "NOM_COM_RBD": "SANTIAGO",
    "COUNT(MRUN)": 71435,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "CERRILLOS",
    "COUNT(MRUN)": 10346,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "CERRO NAVIA",
    "COUNT(MRUN)": 13164,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "CONCHALI",
    "COUNT(MRUN)": 16434,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "EL BOSQUE",
    "COUNT(MRUN)": 29236,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "ESTACION CENTRAL",
    "COUNT(MRUN)": 20139,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "HUECHURABA",
    "COUNT(MRUN)": 11614,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "INDEPENDENCIA",
    "COUNT(MRUN)": 16615,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "LA CISTERNA",
    "COUNT(MRUN)": 23606,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "LA FLORIDA",
    "COUNT(MRUN)": 64377,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "LA GRANJA",
    "COUNT(MRUN)": 15053,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "LA PINTANA",
    "COUNT(MRUN)": 28203,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "LA REINA",
    "COUNT(MRUN)": 18709,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "LAS CONDES",
    "COUNT(MRUN)": 35256,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "LO BARNECHEA",
    "COUNT(MRUN)": 18136,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "LO ESPEJO",
    "COUNT(MRUN)": 9064,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "LO PRADO",
    "COUNT(MRUN)": 9345,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "MACUL",
    "COUNT(MRUN)": 12517,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "MAIPU",
    "COUNT(MRUN)": 82493,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "ÑUÑOA",
    "COUNT(MRUN)": 33700,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "PEDRO AGUIRRE CERDA",
    "COUNT(MRUN)": 12330,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "PEÑALOLEN",
    "COUNT(MRUN)": 30658,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "PROVIDENCIA",
    "COUNT(MRUN)": 27800,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "PUDAHUEL",
    "COUNT(MRUN)": 26966,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "QUILICURA",
    "COUNT(MRUN)": 36107,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "QUINTA NORMAL",
    "COUNT(MRUN)": 21498,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "RECOLETA",
    "COUNT(MRUN)": 26804,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "RENCA",
    "COUNT(MRUN)": 20897,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "SAN JOAQUIN",
    "COUNT(MRUN)": 8241,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "SAN MIGUEL",
    "COUNT(MRUN)": 22075,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "SAN RAMON",
    "COUNT(MRUN)": 11395,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "VITACURA",
    "COUNT(MRUN)": 17444,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "PUENTE ALTO",
    "COUNT(MRUN)": 86942,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "PIRQUE",
    "COUNT(MRUN)": 3182,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "SAN JOSE DE MAIPO",
    "COUNT(MRUN)": 2236,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "COLINA",
    "COUNT(MRUN)": 30003,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "LAMPA",
    "COUNT(MRUN)": 15313,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "TILTIL",
    "COUNT(MRUN)": 2788,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "SAN BERNARDO",
    "COUNT(MRUN)": 48778,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "BUIN",
    "COUNT(MRUN)": 16702,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "CALERA DE TANGO",
    "COUNT(MRUN)": 4392,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "PAINE",
    "COUNT(MRUN)": 13067,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "MELIPILLA",
    "COUNT(MRUN)": 22571,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "ALHUE",
    "COUNT(MRUN)": 953,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "CURACAVI",
    "COUNT(MRUN)": 5509,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "MARIA PINTO",
    "COUNT(MRUN)": 1643,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "SAN PEDRO",
    "COUNT(MRUN)": 1312,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "TALAGANTE",
    "COUNT(MRUN)": 17953,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "EL MONTE",
    "COUNT(MRUN)": 4349,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "ISLA DE MAIPO",
    "COUNT(MRUN)": 5425,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "PADRE HURTADO",
    "COUNT(MRUN)": 10559,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "PEÑAFLOR",
    "COUNT(MRUN)": 13647,
    "COD_REG_RBD": "Región 13"
  },
  {
    "NOM_COM_RBD": "VALDIVIA",
    "COUNT(MRUN)": 26028,
    "COD_REG_RBD": "Región 14"
  },
  {
    "NOM_COM_RBD": "CORRAL",
    "COUNT(MRUN)": 755,
    "COD_REG_RBD": "Región 14"
  },
  {
    "NOM_COM_RBD": "LANCO",
    "COUNT(MRUN)": 2967,
    "COD_REG_RBD": "Región 14"
  },
  {
    "NOM_COM_RBD": "LOS LAGOS",
    "COUNT(MRUN)": 3178,
    "COD_REG_RBD": "Región 14"
  },
  {
    "NOM_COM_RBD": "MAFIL",
    "COUNT(MRUN)": 1167,
    "COD_REG_RBD": "Región 14"
  },
  {
    "NOM_COM_RBD": "MARIQUINA",
    "COUNT(MRUN)": 4071,
    "COD_REG_RBD": "Región 14"
  },
  {
    "NOM_COM_RBD": "PAILLACO",
    "COUNT(MRUN)": 3638,
    "COD_REG_RBD": "Región 14"
  },
  {
    "NOM_COM_RBD": "PANGUIPULLI",
    "COUNT(MRUN)": 6689,
    "COD_REG_RBD": "Región 14"
  },
  {
    "NOM_COM_RBD": "LA UNION",
    "COUNT(MRUN)": 7155,
    "COD_REG_RBD": "Región 14"
  },
  {
    "NOM_COM_RBD": "FUTRONO",
    "COUNT(MRUN)": 2979,
    "COD_REG_RBD": "Región 14"
  },
  {
    "NOM_COM_RBD": "LAGO RANCO",
    "COUNT(MRUN)": 1539,
    "COD_REG_RBD": "Región 14"
  },
  {
    "NOM_COM_RBD": "RIO BUENO",
    "COUNT(MRUN)": 4798,
    "COD_REG_RBD": "Región 14"
  },
  {
    "NOM_COM_RBD": "ARICA",
    "COUNT(MRUN)": 40792,
    "COD_REG_RBD": "Región 15"
  },
  {
    "NOM_COM_RBD": "CAMARONES",
    "COUNT(MRUN)": 99,
    "COD_REG_RBD": "Región 15"
  },
  {
    "NOM_COM_RBD": "PUTRE",
    "COUNT(MRUN)": 235,
    "COD_REG_RBD": "Región 15"
  },
  {
    "NOM_COM_RBD": "GENERAL LAGOS",
    "COUNT(MRUN)": 50,
    "COD_REG_RBD": "Región 15"
  }
]

  var visualization = d3plus.viz()
    .container("#viz")
    .data(sample_data)
    .type("tree_map")
    .id(["COD_REG_RBD","NOM_COM_RBD"])
    .size("COUNT(MRUN)")
    .draw()
</script>


### Categorias de Desempeño con Diagrama de Sankey.

Los digagramas de Sankey...
