---
title: "Automatización de una bomba de achique"
layout: single
permalink: /bomba-achique/
author_profile: false
toc: true
toc_label: "En esta página"
toc_sticky: true
---

Automatización desarrollada en Home Assistant para preparar una bomba de achique antes de episodios de lluvia. El sistema consulta periódicamente la previsión meteorológica, energiza la bomba mediante un relé inteligente Selly 1PM cuando se supera el umbral configurado y la desconecta automáticamente al finalizar un temporizador.

<div class="notice--info">
<strong>Idea principal:</strong> anticiparse a la lluvia y mantener disponible la bomba durante el periodo de riesgo, sin dejarla energizada permanentemente.
</div>

## Problema

La bomba se encuentra en el punto bajo del sótano y dispone de una boya que determina cuándo debe comenzar a extraer agua. Sin embargo, para que esa protección funcione, el circuito debe estar previamente energizado.

Mantener la alimentación activa de forma permanente no era necesario. La solución debía anticiparse a los episodios de lluvia, preparar la bomba únicamente durante el periodo relevante y devolver después el sistema a su estado habitual.

## Solución

Home Assistant ejecuta una comprobación cada treinta minutos. En cada ciclo solicita el pronóstico horario de la vivienda y almacena la respuesta en una variable temporal.

A continuación, una plantilla analiza las seis primeras horas del pronóstico y suma la precipitación prevista:

```jinja
{% raw %}
{% set horas = prevision['weather.forecast_casa']['forecast'][:6] %}
{% set lluvia = horas
  | map(attribute='precipitation')
  | map('float', 0)
  | sum %}
{{ lluvia >= 2 }}
{% endraw %}
```

Cuando el valor acumulado es igual o superior al umbral configurado, Home Assistant:

1. Enciende el relé que alimenta la bomba.
2. Inicia el temporizador asociado al episodio de lluvia.
3. Mantiene el circuito preparado para que la boya pueda activar la bomba si sube el nivel de agua.

Al finalizar el temporizador, una segunda automatización apaga el relé y corta la alimentación.

<figure class="project-figure">
  <img src="/assets/images/bomba-achique/automatizacion-general.png" alt="Vista general de la automatización de la bomba de achique en Home Assistant">
  <figcaption>Automatización principal: consulta del pronóstico, evaluación de la condición y activación del relé y del temporizador.</figcaption>
</figure>

## Flujo de funcionamiento

| Etapa | Acción |
|---|---|
| Comprobación | La automatización se ejecuta cada 30 minutos |
| Consulta | Home Assistant obtiene el pronóstico meteorológico por horas |
| Evaluación | Se suma la precipitación prevista durante las próximas 6 horas |
| Activación | Si el valor alcanza el umbral, se energiza el circuito |
| Protección | La boya conserva el control directo de la activación hidráulica |
| Temporización | Se inicia el temporizador de lluvia |
| Desconexión | Al terminar el temporizador, Home Assistant apaga el relé |
| Supervisión | Cada cambio de estado genera una notificación móvil |

## Condición meteorológica

La decisión no depende únicamente de si aparece lluvia en el pronóstico. La plantilla suma la precipitación prevista durante una ventana de seis horas, evitando energizar el circuito por previsiones aisladas de poca relevancia.

El umbral puede ajustarse desde Home Assistant según el comportamiento real del sótano, la capacidad de drenaje y la precisión de la fuente meteorológica.

<figure class="project-figure">
  <img src="/assets/images/bomba-achique/condicion-lluvia.png" alt="Plantilla de Home Assistant que suma la precipitación prevista durante seis horas">
  <figcaption>Plantilla utilizada para sumar la precipitación prevista durante las siguientes seis horas y compararla con el umbral.</figcaption>
</figure>

## Notificaciones

Una automatización independiente detecta los cambios del relé entre encendido y apagado. Cada transición envía una notificación al teléfono, permitiendo comprobar cuándo se ha preparado la bomba y cuándo ha vuelto a desconectarse.

Esta supervisión facilita detectar activaciones inesperadas y confirmar que el ciclo automático se ha completado.

## Componentes

- Bomba de achique con boya de nivel.
- Línea eléctrica dedicada.
- Relé inteligente controlable Selly 1PM.
- Home Assistant Container.
- Integración meteorológica con pronóstico horario.
- Temporizador y notificaciones de la aplicación móvil.

## Resultado

La bomba queda preparada antes de los episodios de lluvia sin permanecer energizada continuamente. Home Assistant se ocupa de la anticipación meteorológica, la temporización y las notificaciones, mientras que la boya mantiene el control físico de la bomba en función del nivel de agua.

La solución combina una protección local sencilla con información meteorológica y automatización, sin eliminar el mecanismo de seguridad propio de la bomba.

## Mejoras futuras

- Ajustar el umbral a partir del histórico de precipitaciones y activaciones.
- Registrar el tiempo real de funcionamiento y el consumo eléctrico.
- Añadir una alerta si la bomba permanece activa más tiempo del esperado.
- Incorporar un sensor de nivel adicional para supervisar el estado del pozo.
