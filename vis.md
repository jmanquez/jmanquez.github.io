---
layout: post
title: "Vis"
author: "Jaime"
permalink: /vis/
---
<html lang="en">

<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">


<title>

  Vis &middot; Jaime M.

</title>
<script src="//d3js.org/d3.v3.min.js"></script>
    <script src="//cdn.rawgit.com/newrelic-forks/d3-plugins-sankey/master/sankey.js"></script>
    <script src="//cdn.rawgit.com/misoproject/d3.chart/master/d3.chart.min.js"></script>
    <script src="//cdn.rawgit.com/q-m/d3.chart.sankey/master/d3.chart.sankey.min.js"></script>
    <style>
      body {
        padding: 10px;
        min-width: 600px;
        max-width: 1200px;
        margin: auto;
      }
      #chart {
        height: 500px;
        font: 13px sans-serif;
      }
      .node rect {
        fill-opacity: .9;
        shape-rendering: crispEdges;
        stroke-width: 0;
      }
      .node text {
        text-shadow: 0 1px 0 #fff;
      }
      .link {
        fill: none;
        stroke: #000;
        stroke-opacity: .2;
      }
    </style>
<!-- Boostrap :) -->
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css" integrity="sha384-MCw98/SFnGE8fJT3GXwEOngsV7Zt27NXFoaoApmYm81iuXoPkFOJwJ8ERdknLPMO" crossorigin="anonymous">

<!-- CSS -->
<link rel="stylesheet" href="/assets/main.css">
<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Libre+Baskerville:400,400i,700">

<!-- Favicon -->
<link rel="icon" type="image/png" sizes="32x32" href="/assets/favicon.png">
<!--
<link rel="icon" type="image/png" sizes="32x32" href="/assets/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="/assets/favicon-16x16.png">
<link rel="apple-touch-icon" sizes="180x180" href="/assets/apple-touch-icon.png">
-->
<!-- RSS -->
<link type="application/atom+xml" rel="alternate" href="http://localhost:4000/feed.xml" title="Jaime M." />
<!-- Google Analytics -->

<!-- Librerias para insertar formulas en LATEX -->
<!-- Just one possible MathJax CDN below. You may use others. -->
<!--<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>-->
<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-AMS-MML_HTMLorMML' async></script>
<!-- Asegurnado sitio responsive en todos los dispositivos-->
<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
</head>


<body>
  <nav class="nav">
    <div class="nav-container">
      <a href="/">
        <h2 class="nav-title">Jaime M.</h2>
      </a>
       <ul>
      <li><a href="/about">About</a></li>
      <li><a href="/">Posts</a></li>
      <li><a href="/vis">Vis</a></li>

    </ul>
  </div>
</nav>

<main>
<div id="chart"></div>

    <script>
      var colors = {
            'environment':         '#edbd00',
            'social':              '#367d85',
            'animals':             '#97ba4c',
            'health':              '#f5662b',
            'research_ingredient': '#3f3e47',
            'fallback':            '#9f9fa3'
          };
      d3.json("//cdn.rawgit.com/q-m/d3.chart.sankey/master/example/data/product.json", function(error, json) {
        var chart = d3.select("#chart").append("svg").chart("Sankey.Path");
        chart
          .name(label)
          .colorNodes(function(name, node) {
            return color(node, 1) || colors.fallback;
          })
          .colorLinks(function(link) {
            return color(link.source, 4) || color(link.target, 1) || colors.fallback;
          })
          .nodeWidth(15)
          .nodePadding(10)
          .spread(true)
          .iterations(0)
          .draw(json);
        function label(node) {
          return node.name.replace(/\s*\(.*?\)$/, '');
        }
        function color(node, depth) {
          var id = node.id.replace(/(_score)?(_\d+)?$/, '');
          if (colors[id]) {
            return colors[id];
          } else if (depth > 0 && node.targetLinks && node.targetLinks.length == 1) {
            return color(node.targetLinks[0].source, depth-1);
          } else {
            return null;
          }
        }
      });
    </script>
</main>

<footer>
  <span>
    <time datetime="2018-11-08 23:50:27 -0300">2018</time> Hecho con Jekyll y el tema <a href="https://github.com/chesterhow/tale/">Tale</a>.
  </span>
</footer>
<!-- Boostrap librerias -->
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.3/umd/popper.min.js" integrity="sha384-ZMP7rVo3mIykV+2+9J3UJ46jBk0WLaUAdn689aCwoqbBJiSnjAK/l8WvCWPIPm49" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/js/bootstrap.min.js" integrity="sha384-ChfqqxuZUCnJSK3+MXmPNIyE6ZbWh2IMqE241rYiqJxyMiZ6OW/JmZQ5stwEULTy" crossorigin="anonymous"></script>
</body>
</html>
