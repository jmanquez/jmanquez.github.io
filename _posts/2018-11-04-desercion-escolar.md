---
layout: post
title: "Deserción Escolar"
author: "Jaime"
---
La educación en Chile ha sufrido una serie de reformas con el fin de asegurar una educación de calidad. Una de estas reformas tiene relación con el derecho de todos los individuos de completar la enseñanza media, decretándose obligatoria y gratuita en el año 2013, esto implica que el estado debe asegurar una educación inclusiva y de calidad, promoviendo que se den las condiciones necesarias para el acceso y permanencia en el sistema educativo.

Sin embargo, aún se tiene una gran cantidad de estudiantes desertando del sistema escolar, según cifras del MINEDUC en el año 2011 se registraron 91.968 desertores equivalente a un 3% del sistema regular (niños, niñas y jóvenes)[1].

### El indicador de deserción

El MINEDUC utiliza dos medidas para calcular la deserción, la tasa de incidencia y de prevalencia, estas dos medidas consideran dos indicadores cada una, la deserción regular (niños y jóvenes) y otra que mide la deserción global (incluye la educación para adultos). Para al cálculo del indicador se escogió la tasa de incidencia de sistema regular [@MINEDUC2013].

**La tasa de incidencia**: Mide la deserción evaluando la transición de un año a otro, es decir, si presenta matrícula en el año 2016 y no aparece en los registros de matrícula el 2017 (y que no se graduó) se considera desertor.

Formula:

\\[Des_{y}^{j} = Ap_{t-1}^{j-1} +  Rep_{t-1}^j + Ret_{t-1}^j\\]

Donde:

\\(Des_{y}^{j}\\), corresponde al número de estudiantes que desertaron en el sistema escolar en el grado \\(j\\) y periodo \\(t\\).

\\(Ap_{t-1}^{j-1}\\), corresponde a quienes, habiendo aprobado el grado \\(j-1\\) en el periodo \\(t-1\\), no presentan matrícula en el periodo \\(t\\), sin que durante ese periodo hayan finalizado la educación escolar.

\\(Rep_{t-1}^j\\), corresponde a quienes habiendo reprobado el grado \\(j\\) en el periodo \\(t-1\\) no presenta matrícula en el periodo \\(t\\).

\\(Ret_{t-1}^j\\), corresponde a quienes se retiraron durante el periodo \\(t-1\\), en el grado \\(j\\), y no presentan matrícula en el periodo \\(t\\).

La tasa de deserción medida como incidencia queda expresada:

\\[TDI_{t}^{j} = \frac{Des_{t}^{j}}{M_{t}^j + Des_{t}^j}\\]

Donde:

\\(M_{j}^j\\), corresponde a la matrícula efectiva en el periodo \\(t\\) y grado \\(j\\).

\\(TDI_{t}^j\\), corresponde a la tasa de deserción medida como incidencia del periodo \\(t\\) y grado \\(j\\).

### Deserción nivel país

Cómo se puede apreciar en el gráfico XX existe una tendencia a la baja en términos deserción a nivel país, Chile tiene unas de las tasas más bajas a nivel de Latinoamérica, sin embargo, para el año 2017 se registraron 85.901 estudiantes desertaron del sistema escolar. Dado el impacto y las consecuencias que generan la no continuidad de los estudios a nivel escolar es importante poner el énfasis en esta problemática.

<figure class="figure">
  <img src="/assets/img/desercion/des_agnos-1.png" class="figure-img img-fluid mx-auto" alt="Deserción por años">
</figure>

<!--![Deserción años](/assets/img/desercion/unnamed-chunk-2-1.png)
-->
{% include_relative /desercion/tables/table1.html %}

### Deserción por grados o curso

La deserción en el año 2017 muestra una leve tendencia a la baja, según se puede ver en la gráfica 1. En enseñanza básica la deserción mantiene un patrón lineal hasta 5to básico con un leve aumento en 6to y 7mo y con una pequeña baja en 8vo, variando entre 1,5% y 2,5%. Sin embargo, en la transición de la enseñanza básica a media se genera un aumento considerable, en el caso del año 2017 se pasa de una tasa de deserción de un 2,1% que representa a 5.243 desertores de 8vo básico a un 7,6% que representa a 21.213 estudiantes desertores de 1 medio. Esto aumento puede deberse a diversos motivos (cambio de colegio por no contar enseñase media), nuevos profesores y compañeros, trabajo etc.. desarrollar ideas y apoyar con referencias bibliográficas. Sin embargo, es parte de este estudio poder identificar los factores que inciden en este aumento de la deserción y poder utilizarlos como características a considerar en un modelo predictivos de deserción.

En enseñanza media se tiene una tasa de un 7,6% en 1 medio, disminuye a un 4,5% en 2do, vuelve a aumenta en un 7,5% en 3ro y disminuye nuevamente en 4 medio con 3,4% (la cantidad de desertores en cada grado y la matrícula correspondiente se puede ver en el a tabla xx)

<figure class="figure">
  <img src="/assets/img/desercion/des_agno_grado-1.png" class="figure-img img-fluid mx-auto" alt="Deserción por grado y años">
  <figcaption class="figure-caption text-center"> Gráfico 1 .</figcaption>

</figure>

{% include_relative /desercion/tables/table2.html %}

### Deserción a nivel regional

<figure class="figure">
  <img src="/assets/img/desercion/des_region-1.png" class="figure-img img-fluid mx-auto" alt="Deserción Regional">
</figure>

{% include_relative /desercion/tables/table3.html %}
