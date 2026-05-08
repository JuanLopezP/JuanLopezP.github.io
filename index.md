---
layout: splash
title: "Juan López"
header:
  overlay_color: "#000000"
  overlay_filter: 0.5
  overlay_image: /assets/images/hero.JPG
  actions:
    - label: "Ver proyectos"
      url: /projects/
    - label: "GitHub"
      url: "https://github.com/JuanLopezP"

excerpt: "Construyo instalaciones eléctricas, sistemas domóticos y robots. Estudiante de Ingeniería en Málaga."
feature_row:
  - image_path: /assets/images/portada.JPG
    alt: "Proyecto sótano"
    title: "Instalación eléctrica y domótica del sótano"
    excerpt: "Diseño eléctrico, distribución de cargas y automatización con Shelly 1PM Gen 4."
    url: /sotano/
    btn_label: "Ver proyecto"
    btn_class: "btn--primary"

  - image_path: /assets/images/sotano/achique.JPG
    alt: "Automatización bomba de achique"
    title: "Automatización bomba de achique"
    excerpt: "Análisis meteorológico para energización automática de bomba de achique."
    url: /bomba-achique/
    btn_label: "Ver proyecto"
    btn_class: "btn--primary"

  - image_path: /assets/images/dron/dron.jpg
    alt: "Vigilancia aérea con UAV"
    title: "Vigilancia aérea de regadíos"
    excerpt: "Análisis mediante UAV de la efectividad de sistemas de riego en fincas privadas."
    url: /dron-riego/
    btn_label: "Ver proyecto"
    btn_class: "btn--primary"

  - image_path: /assets/images/wifi-mesh/portada.jpg
    alt: "Wifi mesh"
    title: "Instalación wifi mesh en vivienda"
    excerpt: "Mejora de cobertura con red mesh tribanda de 3 nodos en vivienda unifamiliar."
    url: /wifi-mesh/
    btn_label: "Ver proyecto"
    btn_class: "btn--primary"

  - image_path: /assets/images/domotica/portada.jpg
    alt: "Domotización hogar"
    title: "Domotización de vivienda unifamiliar"
    excerpt: "Unificación de dispositivos IoT bajo Home Assistant con automatizaciones personalizadas."
    url: /domotica/
    btn_label: "Ver proyecto"
    btn_class: "btn--primary"

  - image_path: /assets/images/bateria/portada.jpg
    alt: "Batería LiFePo4"
    title: "Batería 5S8P para equipo de robótica"
    excerpt: "Montaje y soldadura de celdas LiFePo4 18650 con BMS Daly para equipo de competición."
    url: /bateria/
    btn_label: "Ver proyecto"
    btn_class: "btn--primary"
---

## Sobre mí

<div class="about-section">

  <div class="about-text">
    <p>Soy estudiante de la <strong>Universidad de Málaga</strong> cursando el grado en Ingeniería Electrónica, Robótica y Mecatrónica. También formo parte del equipo <a href="https://github.com/RoboRescueUMA" target="_blank">Roborescue UMA</a>.</p>
    <p>Me apasiona el diseño y la impresión 3D, el mundo de los drones y la domótica. Colaboro en proyectos que combinan hardware, software y sistemas reales.</p>
    <p>Desde pequeño aprendí mecánica trabajando con maquinaria agrícola. Esa mezcla entre lo manual y lo digital es lo que me llevó a la ingeniería y lo que guía cada proyecto que construyo.</p>
  </div>

  <div class="about-image-slider">
    <img src="/assets/images/Yo1.jpeg" alt="Juan López 1">
    <img src="/assets/images/Yo2.jpg" alt="Juan López 2">
    <img src="/assets/images/Yo3.jpg" alt="Juan López 3">
  </div>

</div>

## Tecnologías y herramientas

<div class="tech-chips">
  <span>Home Assistant</span>
  <span>KiCad</span>
  <span>Arduino / ESP32</span>
  <span>Zigbee · Matter</span>
  <span>Impresión 3D</span>
  <span>FreeCAD</span>
  <span>UAV / Drones</span>
  <span>Instalaciones eléctricas</span>
  <span>ROS</span>
</div>

## Proyectos destacados

{% include feature_row %}
