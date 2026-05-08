---
title: "Instalación wifi mesh en vivienda"
layout: single
permalink: /wifi-mesh/
author_profile: true
toc: true
toc_label: "Contenido"
toc_icon: "bolt"
header:
  overlay_color: "#0d1117"
  overlay_filter: 0.6
  overlay_image: /assets/images/wifi-mesh/portada.jpg
---

<!-- ============================================================
  IMÁGENES: sube las fotos a  assets/images/wifi-mesh/
  y reemplaza los src de los bloques de abajo.
  Formato recomendado: nodo1.jpg, plano-cobertura.jpg, portada.jpg...
  ============================================================ -->

Descripción breve del proyecto en una o dos frases.

---

## Objetivo

<!-- ¿Qué problema de cobertura había? ¿Plantas sin señal, velocidad insuficiente en zonas concretas? -->

## Alcance

<!-- ¿Cuántos nodos? ¿Qué superficie cubre? ¿Qué mejoras se consiguieron? -->

- Instalación de 3 nodos tribanda en puntos estratégicos
- Cableado de backhaul entre nodos (o wireless)
- Configuración y segmentación de red
- 

## Arquitectura del sistema

<!-- Describe la topología: dónde va cada nodo, cómo se interconectan, si hay backhaul por cable -->

### Equipamiento

| Componente | Modelo / Descripción |
|------------|---------------------|
| Sistema mesh | |
| Número de nodos | |
| Backhaul | Cableado / Wireless |
| Router principal | |

## Implementación

### Ubicación de los nodos

<div class="project-img-text">
  <div class="project-img-text__img">
    <img src="/assets/images/wifi-mesh/nodo-principal.jpg" alt="Nodo principal instalado">
  </div>
  <div class="project-img-text__text">
    <p><!-- Dónde se instaló el nodo principal, cómo se conecta al router o módem de la operadora --></p>
  </div>
</div>

<div class="project-img-text project-img-text--reversed">
  <div class="project-img-text__img">
    <img src="/assets/images/wifi-mesh/nodo-secundario.jpg" alt="Nodo secundario instalado">
  </div>
  <div class="project-img-text__text">
    <p><!-- Criterios para elegir la ubicación de los nodos secundarios --></p>
  </div>
</div>

### Resultados de cobertura

<figure class="project-figure">
  <img src="/assets/images/wifi-mesh/cobertura.jpg" alt="Comparativa de cobertura antes y después">
  <figcaption><!-- Mapa de calor o comparativa de señal antes/después de la instalación --></figcaption>
</figure>

---

## Problemas encontrados

<!-- Interferencias, posicionamiento de nodos, configuración del ISP... -->

## Mejoras futuras

- VLAN para separar red de dispositivos IoT de la red principal
- Monitorización del tráfico por dispositivo
- 
