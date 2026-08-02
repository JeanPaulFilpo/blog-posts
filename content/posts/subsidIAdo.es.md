---
title: "¿SubsidIAdos?"
date: 2026-08-01
draft: false
tags: ["ia", "infraestructura", "modelos-abiertos"]
categories: ["ia"]
description: "¿Cuánto nos costaría correr modelos como Claude o GPT-5.6 en infraestructura propia?"
---
Creo que el término «open-weights» en lo que concierne a  IA y grandes modelos del lenguaje sigue siendo relativamente desconocido, más allá del dominio de quiénes seguimos esta tecnología desde una perspectiva académica y profesional.

A grandes rasgos, una LLM de pesos abiertos es un modelo de lenguaje donde la empresa/desarrollador que lo entrenó publica los parámetros ya entrenados (léase, los pesos del modelo) para que cualquiera los pueda descargar y consumir libremente, sin necesidad de pagar un acceso a través de una API. Empresas como Meta y DeepSeek han lanzado modelos abiertos, y los benchmarks muestran que su rendimiento es bastante aceptable en comparación con frontier models como Claude Opus 5 y GPT-5.6.

### Espera...¿hay modelos de IA que son gratis?

Nada es gratis. Sin embargo, lo que sí es cierto es que si puedes descargar estos modelos y correrlos en tu propia computadora, podrías interactuar con los mismos sin pagar costos de inferencia. Es decir, hablarle al modelo y recibir respuestas del modelo no tendría costo (aunque probablemente extrañes la interfaz estética y funcional de Claude Code o ChatGPT).

Si esto es así, entonces:

### ¿Puede tu computadora alojar y correr un modelo como Claude?

Hahaha. No. 

Para entender porqué, quiero contarte brevemente sobre Kimi K3.

K3 es un modelo de la empresa china Moonshot AI, quienes lo lanzaron el 16 de julio de 2026 y publicaron los pesos el 27 de julio de 2026. Aunque en las fuentes te dejo el detalle técnico de Kimi, te adelanto que es un modelo de 2.8 mil millones de parámetros con una arquitectura Mixture-of-Experts (MoE), y es hasta el momento el modelo más grande (esencialmente, más inteligente) que se ha lanzado de manera abierta.

Según diferentes benchmarks (que encontrarás en las fuentes) Kimi compite directamente con frontier models como GPT-5.6 Sol y Claude Fable 5 y eso lo hace (al día que escribimos este post) el mejor comparativo que tenemos para determinar qué implicaría correr estos modelos por cuenta propia. De acuerdo a algunas especificaciones consultadas, requeriríamos solamente:

- **594 GB** de espacio en disco para los pesos del modelo.
- Mínimo **8x GPUs H100 de 80GB**.

### Okay. ¿Y qué cuestan esos GPUs?

Como podrán imaginar dado el boom actual de la IA, la demanda de estas tecnologías está por las nubes y el precio de un solo GPU H100 oscila **entre los US$25,000 y US$40,000**, si es que los encuentras. Siendo conservadores, podrías sustituirlos por GPUs A100 con precios **entre los US$10,000 y US$20,000**. Si necesitamos 8, le dejo el resto de la ecuación a usted, estimado lector.

### ¿Y quién habló de comprar? Yo trabajo en la nube.

No hay problema. El costo en nube por estos GPUs ronda entre **US$1.50 - US$4.50 por hora**. Para no arruinar la sorpresa, asume un promedio de US$3/h, 8 horas de uso diarias, 25 días de uso al mes, por 8 GPUs, y luego cuéntame si te hace sentido. 

### Pero yo pago US$20 por mi suscripción. ¿Cómo esto es rentable para estas empresas?

No lo es. Actualmente la mayoría de las grandes empresas de desarrollo de LLM están operando bajo un modelo de cash-burn que busca generar demanda y acaparar mercado, bajo la esperanza de liquidez mediante valuaciones astronómicas (y probablemente poco realistas). De hecho, según proyecciones de Bloomberg, OpenAI tiene planes de quemar **hasta US$218 billones** para el 2029; para tener alguna referencia de lo absurdo del número, el ejemplo moderno y más famoso de cash-burn es probablemente Uber, con unos pírricos **US$18.2 billones** entre 2016 y 2022.

### ¿Quién sale ganando entonces? ¿Y a quiénes les convienen los modelos de pesos abiertos?

Nosotros, al menos por ahora. De hecho, justo en esta semana OpenAI tuvo agresivos recortes en los precios por token de varios de sus modelos y cada vez más se añaden nuevas funcionalidades a las interfaces web, mientras a su vez los fabricantes chinos lanzan modelos abiertos de  bajo costo y alto rendimiento que buscan insertarse en el mercado e influir en los precios actuales.

Así mismo, estos modelos propician la competitividad y a su vez dan acceso a comunidades de investigadores y desarrolladores que hacen que cada día los modelos sean más inteligentes, pero sobre todo más eficientes. 

Y por supuesto, a los fabricantes de GPUs (te veo, Nvidia) y proveedores de nube que actualmente están viendo retornos millonarios sobre sus inversiones.

### Y de las empresas que desarrollan LLMs, ¿a cuáles ves ganándole la carrera al subsidio?

Bueno, si me obligas a hacer una lista de todas las empresas que, a mi criterio, vencerán en la carrera del subsidio, se vería algo así:

1. Google.

¿Por qué? Pues hay varias razones, pero principalmente porque Gemini no es la razón de ser de Google. Los grandes motores de revenue de Google son su negocio de ads (tanto en Google Search como en Youtube) y su negocio cloud. Esta fuente de ingresos constante es más que suficiente para justificar inversiones cuantiosas en el desarrollo de IA.

Si consideras además su (ya existente y funcional) infraestructura tecnológica como el ecosistema de productos y servicios dentro de los cuáles pueden insertar a Gemini, la pregunta no es porqué Google, sino: ¿quién puede competir con eso?

Pues probablemente Apple, pero muchos de ustedes no están listos para esa conversación y aparentemente Apple tampoco.

### Profe, dígase un último mensaje.

Disfrutemos mientras podamos. 

Estamos viviendo un momento privilegiado en el desarrollo de la IA, donde sigue vigente la máxima de que la IA que estamos usando hoy, es la peor que vamos a usar. Sin embargo, se están acercando los días donde también la IA que uses hoy será la más barata.

¿Te acuerdas cuando decíamos que un teléfono nunca podría llegar a costar US$1,000? Qué tiempos.

---

### Fuentes

- [Kimi K3 Tech Blog](https://www.kimi.com/blog/kimi-k3)
- [Kimi K3: Moonshot's 2.8T Open-Weight Model Explained](https://felloai.com/kimi-k3/)
- [Kimi K3 Open Weights: 2.8T Params, Day-0 Hosting](https://www.explainx.ai/blog/kimi-k3-open-weights-2-8-trillion-parameters-july-2026)
-  [Run Kimi K3 Locally: Confirmed Hardware + vLLM](https://explainx.ai/blog/kimi-k3-run-locally-open-weights-desktop-july-2026)
-  [Kimi K3 — API Pricing & Benchmarks](https://openrouter.ai/moonshotai/kimi-k3)
- [OpenAI Says Spending To Rise to $115B Through 2029](https://www.bloomberg.com/news/articles/2025-09-06/openai-says-spending-to-rise-to-115b-through-2029-information)