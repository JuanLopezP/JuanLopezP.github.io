---
title: "Batería 5S8P LiFePo4 para equipo de robótica"
layout: single
permalink: /bateria/
author_profile: true
toc: true
toc_label: "Contenido"
toc_icon: "bolt"
header:
  overlay_color: "#0d1117"
  overlay_filter: 0.6
  overlay_image: /assets/images/bateria/portada.jpg
---

<!-- ============================================================
  IMÁGENES: sube las fotos a  assets/images/bateria/
  y reemplaza los src de los bloques de abajo.
  Formato recomendado: celdas.jpg, soldadura.jpg, bms.jpg, portada.jpg...
  ============================================================ -->

Descripción breve del proyecto en una o dos frases.

---

## Objetivo

<!-- ¿Para qué robot o equipo se construyó? ¿Qué requisitos de voltaje y capacidad había? -->

## Especificaciones

| Parámetro | Valor |
|-----------|-------|
| Configuración | 5S8P |
| Química | LiFePo4 18650 |
| Tensión nominal | ~16 V |
| Capacidad | |
| BMS | Daly |
| Corriente máxima de descarga | |

## Diseño de la batería

<!-- Explica por qué se eligió la configuración 5S8P: requisitos de tensión del robot,
     autonomía necesaria, limitaciones de peso o espacio -->

## Implementación

### Selección y verificación de celdas

<div class="project-img-text">
  <div class="project-img-text__img">
    <img src="/assets/images/bateria/celdas.jpg" alt="Celdas LiFePo4 18650">
  </div>
  <div class="project-img-text__text">
    <p><!-- Proveedor, proceso de selección/matching de celdas por capacidad interna, herramientas usadas --></p>
  </div>
</div>

### Soldadura y montaje

<div class="project-img-text project-img-text--reversed">
  <div class="project-img-text__img">
    <img src="/assets/images/bateria/soldadura.jpg" alt="Proceso de soldadura de celdas">
  </div>
  <div class="project-img-text__text">
    <p><!-- Técnica de soldadura (punto, estaño...), útiles usados, orden de montaje de grupos paralelos y serie --></p>
  </div>
</div>

### BMS Daly y cableado final

<div class="project-img-text">
  <div class="project-img-text__img">
    <img src="/assets/images/bateria/bms.jpg" alt="BMS Daly instalado">
  </div>
  <div class="project-img-text__text">
    <p><!-- Configuración del BMS: corriente de corte, balanceo, conectores de carga y descarga --></p>
  </div>
</div>

<figure class="project-figure">
  <img src="/assets/images/bateria/terminada.jpg" alt="Batería terminada">
  <figcaption><!-- Batería finalizada, encapsulada y lista para montar en el robot --></figcaption>
</figure>

---

## Problemas encontrados

<!-- Dificultades en la soldadura, celdas con capacidad distinta, configuración del BMS... -->

## Mejoras futuras

- Añadir conector de balance para carga por cargador convencional
- Medir la curva de descarga real y comparar con especificaciones
- 
