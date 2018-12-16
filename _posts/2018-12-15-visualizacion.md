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
    "COMUNA": "IQUIQUE",
    "MATRICULA": 34877,
    "REGION": "Región 1"
  },
  {
    "COMUNA": "ALTO HOSPICIO",
    "MATRICULA": 22336,
    "REGION": "Región 1"
  },
  {
    "COMUNA": "POZO ALMONTE",
    "MATRICULA": 2723,
    "REGION": "Región 1"
  },
  {
    "COMUNA": "CAMIÑA",
    "MATRICULA": 208,
    "REGION": "Región 1"
  },
  {
    "COMUNA": "COLCHANE",
    "MATRICULA": 121,
    "REGION": "Región 1"
  },
  {
    "COMUNA": "HUARA",
    "MATRICULA": 408,
    "REGION": "Región 1"
  },
  {
    "COMUNA": "PICA",
    "MATRICULA": 1059,
    "REGION": "Región 1"
  },
  {
    "COMUNA": "ANTOFAGASTA",
    "MATRICULA": 63857,
    "REGION": "Región 2"
  },
  {
    "COMUNA": "MEJILLONES",
    "MATRICULA": 2156,
    "REGION": "Región 2"
  },
  {
    "COMUNA": "SIERRA GORDA",
    "MATRICULA": 228,
    "REGION": "Región 2"
  },
  {
    "COMUNA": "TALTAL",
    "MATRICULA": 2266,
    "REGION": "Región 2"
  },
  {
    "COMUNA": "CALAMA",
    "MATRICULA": 31277,
    "REGION": "Región 2"
  },
  {
    "COMUNA": "OLLAGÜE",
    "MATRICULA": 38,
    "REGION": "Región 2"
  },
  {
    "COMUNA": "SAN PEDRO DE ATACAMA",
    "MATRICULA": 1463,
    "REGION": "Región 2"
  },
  {
    "COMUNA": "TOCOPILLA",
    "MATRICULA": 4838,
    "REGION": "Región 2"
  },
  {
    "COMUNA": "MARIA ELENA",
    "MATRICULA": 857,
    "REGION": "Región 2"
  },
  {
    "COMUNA": "COPIAPO",
    "MATRICULA": 29552,
    "REGION": "Región 3"
  },
  {
    "COMUNA": "CALDERA",
    "MATRICULA": 3236,
    "REGION": "Región 3"
  },
  {
    "COMUNA": "TIERRA AMARILLA",
    "MATRICULA": 2128,
    "REGION": "Región 3"
  },
  {
    "COMUNA": "CHAÑARAL",
    "MATRICULA": 2491,
    "REGION": "Región 3"
  },
  {
    "COMUNA": "DIEGO DE ALMAGRO",
    "MATRICULA": 2914,
    "REGION": "Región 3"
  },
  {
    "COMUNA": "VALLENAR",
    "MATRICULA": 9916,
    "REGION": "Región 3"
  },
  {
    "COMUNA": "ALTO DEL CARMEN",
    "MATRICULA": 776,
    "REGION": "Región 3"
  },
  {
    "COMUNA": "FREIRINA",
    "MATRICULA": 1034,
    "REGION": "Región 3"
  },
  {
    "COMUNA": "HUASCO",
    "MATRICULA": 1690,
    "REGION": "Región 3"
  },
  {
    "COMUNA": "LA SERENA",
    "MATRICULA": 45679,
    "REGION": "Región 4"
  },
  {
    "COMUNA": "COQUIMBO",
    "MATRICULA": 34655,
    "REGION": "Región 4"
  },
  {
    "COMUNA": "ANDACOLLO",
    "MATRICULA": 1805,
    "REGION": "Región 4"
  },
  {
    "COMUNA": "LA HIGUERA",
    "MATRICULA": 598,
    "REGION": "Región 4"
  },
  {
    "COMUNA": "PAIGUANO",
    "MATRICULA": 635,
    "REGION": "Región 4"
  },
  {
    "COMUNA": "VICUÑA",
    "MATRICULA": 4513,
    "REGION": "Región 4"
  },
  {
    "COMUNA": "ILLAPEL",
    "MATRICULA": 5740,
    "REGION": "Región 4"
  },
  {
    "COMUNA": "CANELA",
    "MATRICULA": 1294,
    "REGION": "Región 4"
  },
  {
    "COMUNA": "LOS VILOS",
    "MATRICULA": 3521,
    "REGION": "Región 4"
  },
  {
    "COMUNA": "SALAMANCA",
    "MATRICULA": 4701,
    "REGION": "Región 4"
  },
  {
    "COMUNA": "OVALLE",
    "MATRICULA": 20990,
    "REGION": "Región 4"
  },
  {
    "COMUNA": "COMBARBALA",
    "MATRICULA": 1883,
    "REGION": "Región 4"
  },
  {
    "COMUNA": "MONTE PATRIA",
    "MATRICULA": 4739,
    "REGION": "Región 4"
  },
  {
    "COMUNA": "PUNITAQUI",
    "MATRICULA": 1726,
    "REGION": "Región 4"
  },
  {
    "COMUNA": "RIO HURTADO",
    "MATRICULA": 584,
    "REGION": "Región 4"
  },
  {
    "COMUNA": "VALPARAISO",
    "MATRICULA": 43420,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "CASABLANCA",
    "MATRICULA": 4387,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "CONCON",
    "MATRICULA": 6942,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "JUAN FERNANDEZ",
    "MATRICULA": 137,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "PUCHUNCAVI",
    "MATRICULA": 2339,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "QUINTERO",
    "MATRICULA": 4805,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "VIÑA DEL MAR",
    "MATRICULA": 47125,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "ISLA DE PASCUA",
    "MATRICULA": 1254,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "LOS ANDES",
    "MATRICULA": 13847,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "CALLE LARGA",
    "MATRICULA": 2143,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "RINCONADA",
    "MATRICULA": 1157,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "SAN ESTEBAN",
    "MATRICULA": 1315,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "LA LIGUA",
    "MATRICULA": 5776,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "CABILDO",
    "MATRICULA": 3746,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "PAPUDO",
    "MATRICULA": 762,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "PETORCA",
    "MATRICULA": 1474,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "ZAPALLAR",
    "MATRICULA": 1275,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "QUILLOTA",
    "MATRICULA": 17287,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "CALERA",
    "MATRICULA": 9926,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "HIJUELAS",
    "MATRICULA": 2325,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "LA CRUZ",
    "MATRICULA": 1438,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "NOGALES",
    "MATRICULA": 3433,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "SAN ANTONIO",
    "MATRICULA": 15723,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "ALGARROBO",
    "MATRICULA": 2037,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "CARTAGENA",
    "MATRICULA": 3910,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "EL QUISCO",
    "MATRICULA": 1845,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "EL TABO",
    "MATRICULA": 920,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "SANTO DOMINGO",
    "MATRICULA": 2015,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "SAN FELIPE",
    "MATRICULA": 15563,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "CATEMU",
    "MATRICULA": 2117,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "LLAILLAY",
    "MATRICULA": 4326,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "PANQUEHUE",
    "MATRICULA": 1131,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "PUTAENDO",
    "MATRICULA": 1863,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "SANTA MARIA",
    "MATRICULA": 1949,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "QUILPUE",
    "MATRICULA": 27000,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "LIMACHE",
    "MATRICULA": 7108,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "OLMUE",
    "MATRICULA": 2096,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "VILLA ALEMANA",
    "MATRICULA": 18784,
    "REGION": "Región 5"
  },
  {
    "COMUNA": "RANCAGUA",
    "MATRICULA": 45672,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "CODEGUA",
    "MATRICULA": 1336,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "COINCO",
    "MATRICULA": 847,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "COLTAUCO",
    "MATRICULA": 2964,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "DOÑIHUE",
    "MATRICULA": 3312,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "GRANEROS",
    "MATRICULA": 7372,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "LAS CABRAS",
    "MATRICULA": 4168,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "MACHALI",
    "MATRICULA": 9877,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "MALLOA",
    "MATRICULA": 1300,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "MOSTAZAL",
    "MATRICULA": 3267,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "OLIVAR",
    "MATRICULA": 2075,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "PEUMO",
    "MATRICULA": 1895,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "PICHIDEGUA",
    "MATRICULA": 2094,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "QUINTA DE TILCOCO",
    "MATRICULA": 1988,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "RENGO",
    "MATRICULA": 10183,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "REQUINOA",
    "MATRICULA": 3496,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "SAN VICENTE",
    "MATRICULA": 9043,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "PICHILEMU",
    "MATRICULA": 2586,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "LA ESTRELLA",
    "MATRICULA": 223,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "LITUECHE",
    "MATRICULA": 905,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "MARCHIHUE",
    "MATRICULA": 749,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "NAVIDAD",
    "MATRICULA": 793,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "PAREDONES",
    "MATRICULA": 694,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "SAN FERNANDO",
    "MATRICULA": 15621,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "CHEPICA",
    "MATRICULA": 1643,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "CHIMBARONGO",
    "MATRICULA": 5566,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "LOLOL",
    "MATRICULA": 863,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "NANCAGUA",
    "MATRICULA": 2534,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "PALMILLA",
    "MATRICULA": 1070,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "PERALILLO",
    "MATRICULA": 1437,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "PLACILLA",
    "MATRICULA": 767,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "PUMANQUE",
    "MATRICULA": 251,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "SANTA CRUZ",
    "MATRICULA": 8892,
    "REGION": "Región 6"
  },
  {
    "COMUNA": "TALCA",
    "MATRICULA": 44483,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "CONSTITUCION",
    "MATRICULA": 8337,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "CUREPTO",
    "MATRICULA": 1115,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "EMPEDRADO",
    "MATRICULA": 681,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "MAULE",
    "MATRICULA": 4283,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "PELARCO",
    "MATRICULA": 927,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "PENCAHUE",
    "MATRICULA": 812,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "RIO CLARO",
    "MATRICULA": 1658,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "SAN CLEMENTE",
    "MATRICULA": 5541,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "SAN RAFAEL",
    "MATRICULA": 1148,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "CAUQUENES",
    "MATRICULA": 7021,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "CHANCO",
    "MATRICULA": 1126,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "PELLUHUE",
    "MATRICULA": 1230,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "CURICO",
    "MATRICULA": 29236,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "HUALAÑE",
    "MATRICULA": 1530,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "LICANTEN",
    "MATRICULA": 1053,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "MOLINA",
    "MATRICULA": 6963,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "RAUCO",
    "MATRICULA": 932,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "ROMERAL",
    "MATRICULA": 2015,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "SAGRADA FAMILIA",
    "MATRICULA": 2045,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "TENO",
    "MATRICULA": 4343,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "VICHUQUEN",
    "MATRICULA": 544,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "LINARES",
    "MATRICULA": 19318,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "COLBUN",
    "MATRICULA": 2937,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "LONGAVI",
    "MATRICULA": 3760,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "PARRAL",
    "MATRICULA": 7045,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "RETIRO",
    "MATRICULA": 3190,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "SAN JAVIER",
    "MATRICULA": 8730,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "VILLA ALEGRE",
    "MATRICULA": 1955,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "YERBAS BUENAS",
    "MATRICULA": 1696,
    "REGION": "Región 7"
  },
  {
    "COMUNA": "CONCEPCION",
    "MATRICULA": 40104,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "CORONEL",
    "MATRICULA": 20435,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "CHIGUAYANTE",
    "MATRICULA": 14000,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "FLORIDA",
    "MATRICULA": 1436,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "HUALQUI",
    "MATRICULA": 3308,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "LOTA",
    "MATRICULA": 7862,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "PENCO",
    "MATRICULA": 5720,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "SAN PEDRO DE LA PAZ",
    "MATRICULA": 20819,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "SANTA JUANA",
    "MATRICULA": 2278,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "TALCAHUANO",
    "MATRICULA": 21586,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "TOME",
    "MATRICULA": 8549,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "HUALPEN",
    "MATRICULA": 11375,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "LEBU",
    "MATRICULA": 4687,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "ARAUCO",
    "MATRICULA": 6332,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "CAÑETE",
    "MATRICULA": 7098,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "CONTULMO",
    "MATRICULA": 1099,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "CURANILAHUE",
    "MATRICULA": 5729,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "LOS ALAMOS",
    "MATRICULA": 3899,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "TIRUA",
    "MATRICULA": 1852,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "LOS ANGELES",
    "MATRICULA": 38514,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "ANTUCO",
    "MATRICULA": 634,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "CABRERO",
    "MATRICULA": 4819,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "LAJA",
    "MATRICULA": 4288,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "MULCHEN",
    "MATRICULA": 4994,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "NACIMIENTO",
    "MATRICULA": 5007,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "NEGRETE",
    "MATRICULA": 1424,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "QUILACO",
    "MATRICULA": 385,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "QUILLECO",
    "MATRICULA": 1249,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "SAN ROSENDO",
    "MATRICULA": 326,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "SANTA BARBARA",
    "MATRICULA": 2419,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "TUCAPEL",
    "MATRICULA": 2003,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "YUMBEL",
    "MATRICULA": 3242,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "ALTO BIOBIO",
    "MATRICULA": 1093,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "CHILLAN",
    "MATRICULA": 34536,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "BULNES",
    "MATRICULA": 3746,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "COBQUECURA",
    "MATRICULA": 566,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "COELEMU",
    "MATRICULA": 2727,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "COIHUECO",
    "MATRICULA": 3763,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "CHILLAN VIEJO",
    "MATRICULA": 3523,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "EL CARMEN",
    "MATRICULA": 2193,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "NINHUE",
    "MATRICULA": 723,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "ÑIQUEN",
    "MATRICULA": 1311,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "PEMUCO",
    "MATRICULA": 1086,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "PINTO",
    "MATRICULA": 1734,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "PORTEZUELO",
    "MATRICULA": 700,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "QUILLON",
    "MATRICULA": 2232,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "QUIRIHUE",
    "MATRICULA": 1792,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "RANQUIL",
    "MATRICULA": 829,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "SAN CARLOS",
    "MATRICULA": 8966,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "SAN FABIAN",
    "MATRICULA": 741,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "SAN IGNACIO",
    "MATRICULA": 2055,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "SAN NICOLAS",
    "MATRICULA": 2617,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "TREGUACO",
    "MATRICULA": 660,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "YUNGAY",
    "MATRICULA": 3120,
    "REGION": "Región 8"
  },
  {
    "COMUNA": "TEMUCO",
    "MATRICULA": 52601,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "CARAHUE",
    "MATRICULA": 4640,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "CUNCO",
    "MATRICULA": 2779,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "CURARREHUE",
    "MATRICULA": 1093,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "FREIRE",
    "MATRICULA": 3284,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "GALVARINO",
    "MATRICULA": 2161,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "GORBEA",
    "MATRICULA": 1668,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "LAUTARO",
    "MATRICULA": 6342,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "LONCOCHE",
    "MATRICULA": 3692,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "MELIPEUCO",
    "MATRICULA": 924,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "NUEVA IMPERIAL",
    "MATRICULA": 6329,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "PADRE LAS CASAS",
    "MATRICULA": 10180,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "PERQUENCO",
    "MATRICULA": 1229,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "PITRUFQUEN",
    "MATRICULA": 5517,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "PUCON",
    "MATRICULA": 4856,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "SAAVEDRA",
    "MATRICULA": 1837,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "TEODORO SCHMIDT",
    "MATRICULA": 1849,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "TOLTEN",
    "MATRICULA": 1678,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "VILCUN",
    "MATRICULA": 4822,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "VILLARRICA",
    "MATRICULA": 11858,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "CHOLCHOL",
    "MATRICULA": 2334,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "ANGOL",
    "MATRICULA": 10332,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "COLLIPULLI",
    "MATRICULA": 4649,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "CURACAUTIN",
    "MATRICULA": 2882,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "ERCILLA",
    "MATRICULA": 1178,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "LONQUIMAY",
    "MATRICULA": 1762,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "LOS SAUCES",
    "MATRICULA": 1084,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "LUMACO",
    "MATRICULA": 1317,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "PUREN",
    "MATRICULA": 1915,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "RENAICO",
    "MATRICULA": 1473,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "TRAIGUEN",
    "MATRICULA": 3380,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "VICTORIA",
    "MATRICULA": 6101,
    "REGION": "Región 9"
  },
  {
    "COMUNA": "PUERTO MONTT",
    "MATRICULA": 45681,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "CALBUCO",
    "MATRICULA": 5911,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "COCHAMO",
    "MATRICULA": 552,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "FRESIA",
    "MATRICULA": 1941,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "FRUTILLAR",
    "MATRICULA": 3513,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "LOS MUERMOS",
    "MATRICULA": 3262,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "LLANQUIHUE",
    "MATRICULA": 2289,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "MAULLIN",
    "MATRICULA": 1822,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "PUERTO VARAS",
    "MATRICULA": 8414,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "CASTRO",
    "MATRICULA": 9229,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "ANCUD",
    "MATRICULA": 7419,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "CHONCHI",
    "MATRICULA": 2705,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "CURACO DE VELEZ",
    "MATRICULA": 585,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "DALCAHUE",
    "MATRICULA": 2169,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "PUQUELDON",
    "MATRICULA": 405,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "QUEILEN",
    "MATRICULA": 814,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "QUELLON",
    "MATRICULA": 5293,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "QUEMCHI",
    "MATRICULA": 1138,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "QUINCHAO",
    "MATRICULA": 1841,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "OSORNO",
    "MATRICULA": 28997,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "PUERTO OCTAY",
    "MATRICULA": 1255,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "PURRANQUE",
    "MATRICULA": 3427,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "PUYEHUE",
    "MATRICULA": 1750,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "RIO NEGRO",
    "MATRICULA": 2110,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "SAN JUAN DE LA COSTA",
    "MATRICULA": 1073,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "SAN PABLO",
    "MATRICULA": 1406,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "CHAITEN",
    "MATRICULA": 674,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "FUTALEUFU",
    "MATRICULA": 402,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "HUALAIHUE",
    "MATRICULA": 1657,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "PALENA",
    "MATRICULA": 265,
    "REGION": "Región 10"
  },
  {
    "COMUNA": "COIHAIQUE",
    "MATRICULA": 11293,
    "REGION": "Región 11"
  },
  {
    "COMUNA": "LAGO VERDE",
    "MATRICULA": 90,
    "REGION": "Región 11"
  },
  {
    "COMUNA": "AISEN",
    "MATRICULA": 4596,
    "REGION": "Región 11"
  },
  {
    "COMUNA": "CISNES",
    "MATRICULA": 940,
    "REGION": "Región 11"
  },
  {
    "COMUNA": "GUAITECAS",
    "MATRICULA": 272,
    "REGION": "Región 11"
  },
  {
    "COMUNA": "COCHRANE",
    "MATRICULA": 624,
    "REGION": "Región 11"
  },
  {
    "COMUNA": "O'HIGGINS",
    "MATRICULA": 86,
    "REGION": "Región 11"
  },
  {
    "COMUNA": "TORTEL",
    "MATRICULA": 72,
    "REGION": "Región 11"
  },
  {
    "COMUNA": "CHILE CHICO",
    "MATRICULA": 809,
    "REGION": "Región 11"
  },
  {
    "COMUNA": "RIO IBAÑEZ",
    "MATRICULA": 305,
    "REGION": "Región 11"
  },
  {
    "COMUNA": "PUNTA ARENAS",
    "MATRICULA": 20852,
    "REGION": "Región 12"
  },
  {
    "COMUNA": "LAGUNA BLANCA",
    "MATRICULA": 31,
    "REGION": "Región 12"
  },
  {
    "COMUNA": "RIO VERDE",
    "MATRICULA": 7,
    "REGION": "Región 12"
  },
  {
    "COMUNA": "SAN GREGORIO",
    "MATRICULA": 40,
    "REGION": "Región 12"
  },
  {
    "COMUNA": "CABO DE HORNOS",
    "MATRICULA": 383,
    "REGION": "Región 12"
  },
  {
    "COMUNA": "ANTARTICA",
    "MATRICULA": 4,
    "REGION": "Región 12"
  },
  {
    "COMUNA": "PORVENIR",
    "MATRICULA": 994,
    "REGION": "Región 12"
  },
  {
    "COMUNA": "PRIMAVERA",
    "MATRICULA": 46,
    "REGION": "Región 12"
  },
  {
    "COMUNA": "TIMAUKEL",
    "MATRICULA": 21,
    "REGION": "Región 12"
  },
  {
    "COMUNA": "NATALES",
    "MATRICULA": 3634,
    "REGION": "Región 12"
  },
  {
    "COMUNA": "TORRES DEL PAINE",
    "MATRICULA": 33,
    "REGION": "Región 12"
  },
  {
    "COMUNA": "SANTIAGO",
    "MATRICULA": 71435,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "CERRILLOS",
    "MATRICULA": 10346,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "CERRO NAVIA",
    "MATRICULA": 13164,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "CONCHALI",
    "MATRICULA": 16434,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "EL BOSQUE",
    "MATRICULA": 29236,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "ESTACION CENTRAL",
    "MATRICULA": 20139,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "HUECHURABA",
    "MATRICULA": 11614,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "INDEPENDENCIA",
    "MATRICULA": 16615,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "LA CISTERNA",
    "MATRICULA": 23606,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "LA FLORIDA",
    "MATRICULA": 64377,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "LA GRANJA",
    "MATRICULA": 15053,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "LA PINTANA",
    "MATRICULA": 28203,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "LA REINA",
    "MATRICULA": 18709,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "LAS CONDES",
    "MATRICULA": 35256,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "LO BARNECHEA",
    "MATRICULA": 18136,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "LO ESPEJO",
    "MATRICULA": 9064,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "LO PRADO",
    "MATRICULA": 9345,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "MACUL",
    "MATRICULA": 12517,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "MAIPU",
    "MATRICULA": 82493,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "ÑUÑOA",
    "MATRICULA": 33700,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "PEDRO AGUIRRE CERDA",
    "MATRICULA": 12330,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "PEÑALOLEN",
    "MATRICULA": 30658,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "PROVIDENCIA",
    "MATRICULA": 27800,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "PUDAHUEL",
    "MATRICULA": 26966,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "QUILICURA",
    "MATRICULA": 36107,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "QUINTA NORMAL",
    "MATRICULA": 21498,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "RECOLETA",
    "MATRICULA": 26804,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "RENCA",
    "MATRICULA": 20897,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "SAN JOAQUIN",
    "MATRICULA": 8241,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "SAN MIGUEL",
    "MATRICULA": 22075,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "SAN RAMON",
    "MATRICULA": 11395,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "VITACURA",
    "MATRICULA": 17444,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "PUENTE ALTO",
    "MATRICULA": 86942,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "PIRQUE",
    "MATRICULA": 3182,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "SAN JOSE DE MAIPO",
    "MATRICULA": 2236,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "COLINA",
    "MATRICULA": 30003,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "LAMPA",
    "MATRICULA": 15313,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "TILTIL",
    "MATRICULA": 2788,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "SAN BERNARDO",
    "MATRICULA": 48778,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "BUIN",
    "MATRICULA": 16702,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "CALERA DE TANGO",
    "MATRICULA": 4392,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "PAINE",
    "MATRICULA": 13067,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "MELIPILLA",
    "MATRICULA": 22571,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "ALHUE",
    "MATRICULA": 953,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "CURACAVI",
    "MATRICULA": 5509,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "MARIA PINTO",
    "MATRICULA": 1643,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "SAN PEDRO",
    "MATRICULA": 1312,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "TALAGANTE",
    "MATRICULA": 17953,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "EL MONTE",
    "MATRICULA": 4349,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "ISLA DE MAIPO",
    "MATRICULA": 5425,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "PADRE HURTADO",
    "MATRICULA": 10559,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "PEÑAFLOR",
    "MATRICULA": 13647,
    "REGION": "Región 13"
  },
  {
    "COMUNA": "VALDIVIA",
    "MATRICULA": 26028,
    "REGION": "Región 14"
  },
  {
    "COMUNA": "CORRAL",
    "MATRICULA": 755,
    "REGION": "Región 14"
  },
  {
    "COMUNA": "LANCO",
    "MATRICULA": 2967,
    "REGION": "Región 14"
  },
  {
    "COMUNA": "LOS LAGOS",
    "MATRICULA": 3178,
    "REGION": "Región 14"
  },
  {
    "COMUNA": "MAFIL",
    "MATRICULA": 1167,
    "REGION": "Región 14"
  },
  {
    "COMUNA": "MARIQUINA",
    "MATRICULA": 4071,
    "REGION": "Región 14"
  },
  {
    "COMUNA": "PAILLACO",
    "MATRICULA": 3638,
    "REGION": "Región 14"
  },
  {
    "COMUNA": "PANGUIPULLI",
    "MATRICULA": 6689,
    "REGION": "Región 14"
  },
  {
    "COMUNA": "LA UNION",
    "MATRICULA": 7155,
    "REGION": "Región 14"
  },
  {
    "COMUNA": "FUTRONO",
    "MATRICULA": 2979,
    "REGION": "Región 14"
  },
  {
    "COMUNA": "LAGO RANCO",
    "MATRICULA": 1539,
    "REGION": "Región 14"
  },
  {
    "COMUNA": "RIO BUENO",
    "MATRICULA": 4798,
    "REGION": "Región 14"
  },
  {
    "COMUNA": "ARICA",
    "MATRICULA": 40792,
    "REGION": "Región 15"
  },
  {
    "COMUNA": "CAMARONES",
    "MATRICULA": 99,
    "REGION": "Región 15"
  },
  {
    "COMUNA": "PUTRE",
    "MATRICULA": 235,
    "REGION": "Región 15"
  },
  {
    "COMUNA": "GENERAL LAGOS",
    "MATRICULA": 50,
    "REGION": "Región 15"
  }
] 

  var visualization = d3plus.viz()
    .container("#viz")
    .data(sample_data)
    .type("tree_map")
    .id(["REGION","COMUNA"])
    .size("MATRICULA")
    .draw()
</script>


### Categorias de Desempeño con Diagrama de Sankey.

Los digagramas de Sankey...
