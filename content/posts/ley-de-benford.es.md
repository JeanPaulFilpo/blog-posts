---
title: "Benford, ayúdame ahí."
date: 2026-08-30
draft: false
tags: ["fraude", "benford", "logaritmo"]
categories: ["fraude"]
description: "¿Cómo las empresas saben cuando alguien está haciendo fraude?"
---
El otro día abrí Youtube para perder un poco de tiempo, y me detuve a ver las recomendaciones de mi algoritmo: encripción de llave pública, pimienta negra recién molida (el que sabe sabe), documentales de la naturaleza, lo típico. Sin embargo, hubo una recomendación que llamó mucho mi atención: All Time Trending Baby Pink Glamour 2025; inmediatamente entendí que mi esposa había estando usando mi cuenta. 

De manera similar, muchas empresas ya tienen un perfil (quizá demasiado detallado) sobre quiénes somos: qué compramos, a qué hora lo compramos, por qué plataforma, cuánto costó, y así por el estilo, de modo que cualquier comportamiento fuera de lo común levanta la bandera de fraude. Así que si vives en Santo Domingo y de repente llenas el tanque en un viaje al interior en una estación de combustible de un paraje remoto en Montecristi, puedes esperar una cálida llamada del departamento de fraude de tu banco favorito (o no tanto).

### ¿Entonces no me puedo ir nunca de viaje?

Tranquilo, solo tienes que notificarlo. Pues si, aunque la idea de utilizar el comportamiento del consumidor como un detector de actividad fraudulenta no deja de ser interesante, tiene varias oportunidades que estoy seguro ustedes son lo suficientemente inteligentes para inferir. El propósito de este blog es hablar sobre un método particular de detección de fraude que me parece sumamente interesante, y cuyo origen resulta ser bastante anecdótico.

### ¿Qué es la Ley de Benford?

Antes de que las calculadoras de bolsillo empezaran a comercializarse en la década de los 70, todo aquel que necesitara el valor de alguna función trascendental (léase: seno, coseno, exponencial, etc.) debía usar una tabla impresa donde podía encontrar muchos de los valores ya calculados (si sabes de qué estoy hablando, probablemente te duele la espalda mientras lees esto).

Una de estas personas fue el astrónomo canadiense Simon Newcomb, quien en 1881 encontró que las primeras páginas de las tablas de logaritmos (las que empiezan con 1) estaban bastante más maltratadas que las páginas posteriores. Este fenómeno fue luego observado por el físico Frank Benford en 1938, quien probó estas observaciones en datasets de más de 20 dominios diferentes (economía, geografía, demografía, etc.) Para ser más precisos:

La **Ley de Benford** (también conocida como la Ley del Primer Dígito) sugiere que en muchos conjuntos de datos numéricos, el dígito inicial tiende a ser pequeño. Matemáticamente, un conjunto de números dice satisfacer la Ley de Benford si el dígito inicial \(d \in \{1,2,3,...9\} \) ocurre con probabilidad \[P(d) = log_{10} \left( 1 + \frac {1}{d}\right)\]

Haciendo algunos cálculos, podemos ver que la probabilidad esperada del primer dígito se ve algo como:

| \(d\) | \(P(d)\) |
|:-----:|---------:|
| 1     | 30.1%    |
| 2     | 17.6%    |
| 3     | 12.5%    |
| 4     | 9.7%     |
| 5     | 7.9%     |
| 6     | 6.7%     |
| 7     | 5.8%     |
| 8     | 5.1%     |
| 9     | 4.6%     |

### Profe, hágase un ejemplito ahí

Me gustó el ejemplo de Wikipedia, entonces vamos a traerlo aquí. Si buscamos la lista de las 58 estructuras más altas del mundo por categoría, y anotamos las alturas correspondientes (sorprendentemente, da igual si las anotamos en metros o en pies), nos encontramos con lo siguiente:

| Dígito inicial | m (Conteo) | m (%) | ft (Conteo) | ft (%) | Según Benford|
|:---:|---:|---:|---:|---:|---:|
| 1 | 23 | 39.7% | 15 | 25.9% | 30.1% |
| 2 | 12 | 20.7% | 8  | 13.8% | 17.6% |
| 3 | 6  | 10.3% | 5  | 8.6%  | 12.5% |
| 4 | 5  | 8.6%  | 7  | 12.1% | 9.7%  |
| 5 | 2  | 3.4%  | 9  | 15.5% | 7.9%  |
| 6 | 5  | 8.6%  | 4  | 6.9%  | 6.7%  |
| 7 | 1  | 1.7%  | 3  | 5.2%  | 5.8%  |
| 8 | 4  | 6.9%  | 6  | 10.3% | 5.1%  |
| 9 | 0  | 0%    | 1  | 1.7%  | 4.6%  |

Como vemos, la distribución real guarda cierta relación con la propuesta por la Ley de Benford, independientemente de la unidad de medida.

### ¿Y esto funciona para TODOS los conjuntos de datos?

Buena pregunta. Realmente la Ley de Benford tiende a ser más precisa en conjuntos de datos que comprendan varios órdenes de magnitud (recordemos que la expresión de probabilidad es logarítmica). Es decir, si aplicamos la ley para ver la distribución de salarios a nivel nacional, es muy posible que veamos la ley en acción. Sin embargo, si repetimos el mismo ejercicio para los salarios entry-level, y definimos entry-level como personas que perciben sueldos menores a RD$25,000, pues la ley no aplicaría.

### Okay, creo que entendí. ¿Qué tiene que ver la ley con el fraude?

En muchos casos se utiliza como casuística. Si una persona que está cometiendo una actividad fraudulenta se está inventando los registros, el sentido común probablemente le diga que sería más engañoso si los números están bien dispersos entre sí. Dicho de otro modo, intentaría repartir los números de la forma más equitativa posible, para evitar muchas repeticiones sospechosas; matemáticamente, la distribución de los primeros dígitos sería más o menos uniforme, y cada dígito ocurriría con una probabilidad de aproximada 11%. 

### ¿Y esto se usa en la vida real?

A diferencia del trinomio cuadrado perfecto, existen numerosos casos reportados de uso de la Ley de Benford para detección de fraude, como en las elecciones de la gobernación de California en el 2003, las elecciones de Irán en el 2009 y los reportes macroeconómicos que Grecia entregó a la Unión Europea para su ingreso en la Eurozona en el 2001.

Sin embargo, es importante destacar que también se han dado casos de la aplicación incorrecta de la Ley, como en el análisis de votos de varios recintos estadounidenses durante las elecciones del 2020. De hecho, existen argumentos interesantes a favor y en contra de la aplicación de la Ley de Benford en análisis de fraude electoral. No te preocupes, te dejaré varios enlaces en las fuentes para que no vayas a aplicar la Ley de Benford a este post.

### Profe...¿usted se imagina si aplican eso aquí en RD?

Bueno, ya que insisten. Sin embargo, considero necesario hacer 2 disclaimers importantes:

1. Desde el punto de vista técnico, existen algunas mejoras a la Ley de Benford (como analizar la distribución de los primeros 2 dígitos, combinar con pruebas de chi-cuadrado, etc.), pero no hemos abundado en estas sofisticaciones para no hacer el post muy técnico. 

2. La información que vamos a comentar aquí está públicamente disponible en el portal de la DGCP (Dirección General de Contrataciones Públicas), y el objetivo de estos comentarios es 100% didáctico.

Okay. Tomemos como referencia el archivo de todos los contratos adjudicados en el primer semestre de 2026 para la ETED (Empresa de Transmisión Eléctrica Dominicana). ¿Qué encontramos aquí?

Aunque la mediana de los montos adjudicados ronda los RD$150,000, el promedio ronda los RD$47,000,000; este es un primer indicador de que probablemente existen valores atípicos en este dataset. _Profe, ¿¿y esa licitación de RD$44 mil millones de pesos en servicios de estandarización de especificaciones??_ Dejen eso así.

Como podemos ver, los montos adjudicados cubren varios órdenes de magnitud, por cuanto una aplicación de la Ley de Benford sería interesante. De hecho, la distribución de los primeros dígitos de los montos adjudicados se ve algo así:

| Dígito | Observado | Benford esperado | Diferencia (pp) | Contribución al χ² |
|---|---|---|---|---|
| 1 | 37.85% | 30.10% | +7.74 | 19.4 |
| 2 | 31.08% | 17.61% | +13.47 | **100.4** |
| 3 | 6.87% | 12.49% | −5.62 | 24.7 |
| 4 | 5.23% | 9.69% | −4.46 | 20.0 |
| 5 | 5.23% | 7.92% | −2.69 | 8.9 |
| 6 | 3.49% | 6.69% | −3.21 | 15.0 |
| 7 | 2.77% | 5.80% | −3.03 | 15.4 |
| 8 | 4.72% | 5.12% | −0.40 | 0.3 |
| 9 | 2.77% | 4.58% | −1.81 | 7.0 |

Podemos ver que el estadístico \(\chi ^2\) viene sumamente apoyado por la desviación del 2 como primer dígito, y de hecho, vemos que el 69% de los procesos adjudicados tienen montos que inician con 1 o con 2. 

Esto probablemente puede explicarse porque, en la data estudiada, el 82% de los artículos descritos tienen precios entre RD$10,000 y RD$999,999, mientras que el 34.5% de los montos son múltiplos de 100. En resumen, pareciera que no hay mucho de qué preocuparse (les dije que dejen eso así).

### Profe, dígase un último mensaje.

La Ley de Benford no deja de ser una casuística sumamente interesante para la detección de fraude, y nos muestra que los datos siempre hablan, aunque no siempre en el mismo idioma que nosotros. *Profe, entonces ese monto...* **Dejen eso así.**

### Fuentes

- [Benford in Election Forensics](http://www-personal.umich.edu/~wmebane/pm06.pdf)
- [Benford in Election Forensics 2](https://www.cambridge.org/core/journals/political-analysis/article/benfords-law-and-the-detection-of-election-fraud/3B1D64E822371C461AF3C61CE91AAF6D)
- [Benford in Election Forensics 3](https://www.cambridge.org/core/journals/political-analysis/article/comment-on-benfords-law-and-the-detection-of-election-fraud/BC29680D8B5469A54C7C9D865029FE7C)
-  [Benford in Election Forensics 4](https://www.reuters.com/article/uk-factcheck-benford/fact-check-deviation-from-benfords-law-does-not-prove-election-fraud-idUSKBN27Q3AI)
-  [Iranian Elections](https://www.newscientist.com/article/mg20227144.000-statistics-hint-at-fraud-in-iranian-election.html)
-  [Portal Datos Abiertos DGCP](https://datosabiertos.dgcp.gob.do/datos-abiertos/tablas)



