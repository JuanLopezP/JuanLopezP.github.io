---
title: "Sistema eléctrico y domótico del sótano"
layout: single
permalink: /sotano/
author_profile: true
header:
teaser: /assets/images/sotano/portada.jpg
---

## Objetivo

Diseñar e implementar una instalación eléctrica en un garaje de una casa unifamiliar.

## Alcance

- Iluminación en 3 sectores + parte automática con 2 sensores de presencia.
- Enchufes distribuidos + enchufes de fuerza para caldera y termo eléctrico de 2KW.
- Preparación para alimentar una bomba de achique sumergida.

## Arquitectura

La forma de distribuir los espacios es mediante 3 sectores de los cuales 1 será conmutado y 2 solo se podrán encender desde una llave única. La forma de distribuir los enchufes será a priori en dos zonas:
- Dos tomas de corriente al lado de los conmutadores.
- Dos tomas de corriente al lado del comutador para la tercera fila.
Los enchufes de fuerza irán montados sobre un cuadro dedicado con 4 magnetotérmicos de:
- 16 A para el termo (mayor demanda de corriente)
- Contactor para el termo.
- 10 A para la calefacción.
- 10 A para descalcificador.
- 10 A usos varios.

Hasta este cuadro bajará cable de 6 mm^2 desde el cuadro principal. Todo esto colgará de un magneto de 20 A en la subdivisión de garaje que queda protegida con un diferencial de 30 mA aislando problemas en el garaje del resto de la vivienda.

## Implementación

### Cuadro eléctrico de fuerza 

<div style="display: flex; flex-wrap: wrap; align-items: center; gap: 20px; margin: 20px 0;">

  <!-- Imagen -->
  <div style="flex: 1; min-width: 300px;">
    <img src="/assets/images/sotano/CuadroVacio.JPG" 
         style="width: 100%; border-radius: 16px;">
  </div>

  <!-- Texto -->
  <div style="flex: 1; min-width: 300px;">
    <p>
      Para realizar el cuadro eléctrico de fuerza se han tirado los cables directamente 
      y se ha colocado una caja con capacidad para 7 dispositivos y espacio suficiente 
      para meter relés inteligentes de domótica.
    </p>
  </div>

</div>
<p align="center">
  <img src="/assets/images/sotano/CuadroVacio.JPG" 
       alt="Cuadro eléctrico vacío"
       style="width: 500px; object-fit: cover; border-radius: 16px; margin: 10px;">
</p>
A continuación se procedio
### Iluminación
### Tomas de corriente

## Problemas encontrados

- limitación de espacio
- decisiones sobre protecciones
- ampliaciones futuras

## Mejoras futuras

- integración más profunda con Home Assistant
- monitorización energética
- control de cargas
