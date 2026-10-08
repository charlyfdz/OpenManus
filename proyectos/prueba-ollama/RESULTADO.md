# Resultado de la prueba local

**Fecha:** 2026-09-15  
**Modelo:** `llama3.2:1b`  
**Proveedor:** Ollama local (`http://localhost:11434/v1`)  
**APIs de nube:** no utilizadas

## Prueba del cliente LLM

**Resultado: aprobado.** El cliente interno `app.llm.LLM` pudo conectarse al
modelo local y generar una respuesta coherente en español:

> Un servidor propio en casa puede ofrecer una mayor privacidad y seguridad,
> ya que no está conectado a Internet y, por lo tanto, no está expuesto a
> ataques cibernéticos.

## Prueba del agente Manus

**Resultado: parcial, no apto todavía para evaluar tareas con herramientas.**

El agente inició correctamente y se conectó a Ollama, pero el modelo de 1B:

- generó llamadas de herramientas con argumentos mal formados;
- repitió la misma llamada varias veces;
- intentó usar rutas Linux como `/home/user/Documents` en Windows;
- no terminó la tarea aunque se le pidió expresamente no usar herramientas.

La ejecución se detuvo de forma manual para evitar consumo innecesario de
recursos. No se usó navegador, Daytona ni ningún servicio externo.

## Cambios locales de esta prueba

- Se creó `config/config.toml` para Ollama.
- Se creó la carpeta de este proyecto de prueba.
- Se añadió un contador de tokens aproximado y offline para modelos locales que
  `tiktoken` no reconoce.

## Conclusión provisional

OpenManus funciona como cliente de un modelo Ollama pequeño, pero `llama3.2:1b`
no tiene capacidad suficiente para orquestar de forma confiable las
herramientas de Manus. Para evaluar el valor real del agente necesitaremos
posteriormente un modelo local más capaz o una prueba limitada a generación de
texto.
