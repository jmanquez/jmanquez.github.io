---
layout: post
title: "Deserción Escolar"
author: "Jaime"
---
### Deserción Chile
La deserción es calculada según la metodología propuesta por el [MINEDUC en el documento publicado en el 2013](https://centroestudios.mineduc.cl/wp-content/uploads/sites/100/2017/06/A2N15_Desercion_escolar.pdf) se cambia la formula de cálculo dejando de utilizar la matrícula teórica.

Se cuantifica la deserción escolar en Chile y sus diferentes formas de visualizarlo. Esta cuantificación fue realizada bajo distintos enfoques que permitieran tener una visión general y en detalle. El código está disponible en [aquí](https://github.com/jmanquez/DESERCION). Las bases de datos utilizadas fueron de matrícula y rendimiento disponible en el portal de [Centro de Estudios del MINEDUC](http://datosabiertos.mineduc.cl/). Se cálculo la deserción para tres cohortes 2004, 2005 y 2006, con sus estudiantes graduados en el 2016, 2017 y 2018 respectivamente.

### La deserción del sistema regular como incidencia
La tasa de incidencia de la deserción busca medir la deserción escolar evaluando la transición entre un año y otro de los estudiantes. Así, se considerará desertor al niño o joven que no retorna al sistema escolar luego de haber estado matriculado en el periodo académico anterior, sin que durante este periodo se hayan graduado del sistema escolar. La deserción del sistema regular, considera a los estudiantes que se salieron del sistema escolar de niños y jóvenes, aun cuando hayan continuado sus estudios en el sistema de adultos.

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

Cómo se puede apreciar en el gráfico 1 existe una tendencia a la baja en términos deserción a nivel país, Chile tiene unas de las tasas más bajas a nivel de latinoamericano, sin embargo, para el año 2017 se registraron 85.901 estudiantes desertaron del sistema escolar.

<figure class="figure">
  <img src="/assets/img/desercion/des_agnos-1.png" class="figure-img img-fluid mx-auto" alt="Deserción por años">
    <figcaption class="figure-caption text-center"> Gráfico 1 - Deserción por año .</figcaption>
</figure>

<!--![Deserción años](/assets/img/desercion/unnamed-chunk-2-1.png)
-->
{% include_relative /desercion/tables/table1.html %}

### Deserción por grados o curso

La deserción en el año 2017 muestra una leve tendencia a la baja en comparación a los últimos tres años, ver gráfica 2. En enseñanza básica la deserción mantiene un patrón continuo estable hasta 5to básico con un leve aumento en 6º y 7º y con una pequeña baja en 8º, variando entre 1,5% y 2,5%. Sin embargo, en la transición de la enseñanza básica a media aumenta considerablemente la tasa, en el caso del año 2017 se pasa de una tasa de deserción de un 2,1% que representa a 5.243 desertores de 8º básico a un 7,6% que representa a 21.213 estudiantes desertores de 1 medio, este aumento puede deberse a diversas causas o factores.

En enseñanza media se tiene una tasa de un 7,6% en 1º medio, disminuye a un 4,5% en 2º, vuelve a aumenta en un 7,5% en 3º y disminuye nuevamente en 4º medio con 3,4% (la cantidad de desertores en cada grado y la matrícula correspondiente se puede ver en el a tabla 2)

<figure class="figure">
  <img src="/assets/img/desercion/des_agno_grado-1.png" class="figure-img img-fluid mx-auto" alt="Deserción por grado y años">
  <figcaption class="figure-caption text-center"> Gráfico 2 - Deserción por año y grado .</figcaption>
</figure>

{% include_relative /desercion/tables/table2.html %}

### Deserción a nivel regional

<figure class="figure">
  <img src="/assets/img/desercion/des_region-1.png" class="figure-img img-fluid mx-auto" alt="Deserción Regional">
    <figcaption class="figure-caption text-center"> Gráfico 3 - Deserción por Región .</figcaption>
</figure>

{% include_relative /desercion/tables/table3.html %}
