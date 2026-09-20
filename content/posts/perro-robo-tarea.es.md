---
title: "El perro se robó mi tarea."
date: 2026-09-13
draft: false
tags: ["copyright", "openai", "demostracion"]
categories: ["copyright"]
description: "Profe, ¿cómo así que un millón de dólares por un problema de matemática?"
---
Dependiendo de lo que Lord Algoritmo haya decidido para ti en estas últimas semanas, es posible que hayas visto un anuncio sobre la resolución de uno de los Problemas del Milenio: las ecuaciones de Navier-Stokes. 

Vayamos como una vaca vestida de uniforme (tú puedes).

### ¿Qué son los Problemas del Milenio?

En el año 2000, el Instituto Clay de Matemática publicó una lista de 7 problemas matemáticos cuya resolución produciría avances monumentales en sus respectivas áreas. El primero en resolverse fue la conjectura de Poincaré en el año 2003 por el matemático ruso Grigori Perelman, y hasta la fecha ninguno de los otros cuenta con una solución oficial y verificada por la comunidad matemática. Sin entrar en muchos detalles técnicos, y para que no me acusen de misterioso, describamos brevemente los problemas:

- **P vs NP**: pregunta si todo problema cuya solución puede verificarse rápidamente puede a su vez resolverse rápidamente.
- **La hipótesis de Riemann**: probablemente el más famoso, que busca entender dónde se ubican todas las soluciones de una famosa expresión matemática.
- **La conjetura de Hodge**: que pregunta cuándo ciertas formas geométricas complejas pueden expresarse en piezas algebraicas más simples. 
- **La conjetura de Poincaré**: que plantea que la esfera es la única forma tridimensional cerrada y sin agujeros.
- **Yang-Mills y salto de masa**: problema de física matemática que pide determinar bases matemáticas rigurosas para ciertas teorías cuánticas y probar que existe una brecha de masa en las partículas fundamentales que describen.
- **La conjetura de Birch y Swinnerton-Dyer**: busca relacionar la aritmética de las curvas elípticas con el comportamiento de ciertas funciones asociadas.
- **Las ecuaciones de Navier-Stokes**: pregunta si las ecuaciones que describen el movimiento de los fluidos siempre tienen soluciones bien comportadas en 3 dimensiones, o si pueden desarrollar singularidades. 

### Profe...se pasó.

Yo te dije. La idea básica es la siguiente: lo que hacen las ecuaciones de Navier-Stokes es dotarnos de un librito que nos explica sobre cómo interactúan los fluidos: la aerodinámica de un carro de F1, el agua que corre por una tubería, el desplazamiento de las corrientes de aire sobre las alas de un avión, esencialmente cualquier fenómeno que involucre fluidos.

### Okay...¿y cuál es el problema?

Que no sabemos si el librito está completo. No sabemos si realmente, cada vez que yo vea un fenómeno que involucra fluidos, puedo encontrar su explicación en el librito. O peor, si el librito me da una explicación, no sabemos si esta explicación va a ser cierta siempre. 

### ¿Y qué fue lo que pasó?

Los matemáticos Tristan Buckmaster de NYU y Levent Alpöge de Anthropic (la empresa de Claude) publicaron resultados que indicaban que había muchas posibilidades de que el librito estuviese incompleto. Estuvieron trabajando en ello en silencio apoyándose de varias herramientas de IA, entre ellas Codex, de Open AI.

La controversia viene porque varios días después, OpenAI publica un artículo diciendo que hizo uso de un modelo interno que han desarrollado, que orquestó más de 10,000 trabajando en paralelo durante 88 horas, consumiendo 4.9 millones de mensajes y produciendo más de 300 billones tokens de salida para ofrecer una solución completa al problema.

### ¿Qué sostienen ambas partes?

Buckmaster ha dicho de que OpenAI se le acercó para ofrecerle autoría en el paper final, pero que debía dejar de lado las contribuciones de Alpöge (que trabajaba para la competencia). Además, ambos sostienen que como estaba alojando su trabajo en Codex, entendían que OpenAI habría utilizado sus avances como material de base para ejecutar su propia solución: una acusación gravísima de privacidad y seguridad de la información.

Por su parte, OpenAI en principio negó que esto haya sido así, y su respuesta fue que "no pueden descartar que sus modelos hayan hecho uso de data interna de clientes no identificable para producir ciertos outputs". 

Más adelante, su propio release post el 8 de septiembre aborda esta situación, y establecen categóricamente que no solo no utilizaron data que no estuviera públicamente disponible, sino que es imposible que los prompts que Buckmaster sometió a Codex hayan influenciado de manera alguna los resultados de su sistema.

### ¿Y qué dicen los matemáticos, profe?

Qué te digo. Parece que la prueba es totalmente correcta, porque incluso publicaron una versión de Lean (un lenguaje de programación diseñado específicamente para determinar la correctitud de pruebas matemáticas), pero este proceso de prueba ha dejado un mal sabor entre los investigadores, donde muchos opinan que es contrario al espíritu matemático de entendimiento profundo y de descubrimiento paulatino.

Incluso, hay una implicación económica detrás de todo esto: si hacemos un pequeño cálculo de costo detrás del escenario que presenta OpenAI, veremos que la "solución" de su sistema debió costar unos US$30,000,000. 

¿Quiere decir esto que el futuro de la investigación será quemar dinero hasta que una IA resuelva el problema? Admito que esta mentalidad es un poco pesimista, pero vale la pena pensar en las implicaciones, ¿pues qué impide que otras grandes empresas de IA recopilen los últimos avances de cualquier rama del conocimiento y realicen pruebas similares?

### Profe pero...¿esto es malo? ¿No fue para esto que se creó la IA?

¿Te soy sincero? No lo creo. Creo que la razón de ser fundamental de la IA es potencializar el ser humano y mejorar nuestras capacidades de razonamiento, no sustituirlas. 

Leí por ahí que el mayor peligro que corre el hombre de delegar el pensamiento a las máquinas, son los hombres que controlan esas máquinas.

¿Y últimamente? Estoy empezando a pensar que tienen razón.

