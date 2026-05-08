---
title: "Sistema eléctrico y domótico del sótano"
layout: single
permalink: /sotano/
author_profile: true
toc: true
toc_label: "Contenido"
toc_icon: "bolt"
header:
  overlay_image: /assets/images/sotano/hero.jpg
  overlay_filter: 0.6
  overlay_color: "#0d1117"
---

Instalación eléctrica completa de un garaje en vivienda unifamiliar: desde el diseño del cuadro de distribución hasta la integración con domótica mediante un relé inteligente Shelly con soporte Matter y Zigbee.

---

## Objetivo

Diseñar e implementar una instalación eléctrica segura, escalable y preparada para la integración domótica en el sótano-garaje de una vivienda unifamiliar. El objetivo no era solo resolver las necesidades inmediatas —iluminación, enchufes y cargas de fuerza— sino sentar las bases para una gestión inteligente de la energía, con capacidad de monitorización y automatización sin tener que rehacerlo todo más adelante.

## Alcance

- **Iluminación**: 3 sectores independientes + 2 zonas con detección automática de presencia mediante sensores PIR.
- **Tomas de corriente**: enchufes distribuidos en zonas de trabajo + enchufes de fuerza para termo eléctrico (2 kW) y caldera.
- **Cuadro de fuerza**: subcuadro dedicado con protecciones independientes para cada carga, alimentado con cable de 6 mm² desde el cuadro general.
- **Domótica**: relé inteligente Shelly 1PM Gen 4 con soporte Matter/Zigbee para control y monitorización del termo.
- **Preparación para bomba de achique**: línea dedicada con toma estanca IP44 y protección propia.

## Arquitectura del sistema

La instalación parte del cuadro principal de la vivienda, desde el que desciende una línea de **6 mm²** protegida por un magnetotérmico de **20 A** y un diferencial de **30 mA**. Este diferencial aísla eléctricamente el garaje del resto de la vivienda, de modo que cualquier fallo en el sótano no afecta al suministro de las demás plantas.

### Distribución de iluminación

| Sector | Zona | Tipo de control |
|--------|------|----------------|
| 1 — Zona principal | Área central del garaje | Conmutado (dos puntos de encendido) |
| 2 — Zona de trabajo | Banco de herramientas | Interruptor único + 2 focos orientables |
| 3 — Acceso y pasillo | Escalera y puerta de entrada | Sensor de presencia PIR |

Adicionalmente, se instaló un segundo sensor PIR junto a la puerta interior que comunica con la vivienda, para que la iluminación se active automáticamente al bajar.

### Cuadro de fuerza

| Protección | Calibre | Carga protegida |
|------------|---------|----------------|
| Magnetotérmico curva C | 16 A | Termo eléctrico |
| Contactor auxiliar | — | Corte de carga del termo vía Shelly |
| Magnetotérmico | 10 A | Sistema de calefacción |
| Magnetotérmico | 10 A | Descalcificador |
| Magnetotérmico | 10 A | Usos varios / bomba de achique |

## Implementación

### Cuadro eléctrico de fuerza

<div class="project-img-text">
  <div class="project-img-text__img">
    <img src="/assets/images/sotano/CuadroVacio.JPG" alt="Caja del cuadro vacía antes de instalar">
  </div>
  <div class="project-img-text__text">
    <p>El punto de partida fue una caja de 7 elementos, elegida con margen deliberado respecto a las necesidades inmediatas. La razón: desde el diseño inicial se contempló la posibilidad de incorporar relés inteligentes sin reemplazar la caja. Esta previsión resultó clave al añadir el Shelly 1PM.</p>
    <p>Los cables de 6 mm² llegaron directamente desde el cuadro principal. Antes de montar ningún componente, se planificó el recorrido interior para evitar cruces y facilitar intervenciones futuras.</p>
  </div>
</div>

<div class="project-img-text project-img-text--reversed">
  <div class="project-img-text__img">
    <img src="/assets/images/sotano/CuadroSuperiorEnProceso.JPG" alt="Parte superior del cuadro durante el montaje">
  </div>
  <div class="project-img-text__text">
    <p>Para el cableado interior se utilizaron <strong>punteras ferrules crimpadas</strong>, una técnica habitual en instalaciones industriales que garantiza un contacto limpio y duradero en los bornes de los magnetotérmicos. Ya las había usado en el cableado de robots del equipo de robótica, así que el proceso fue cómodo.</p>
    <p>Los puentes superiores se montaron primero para distribuir la tensión de la línea de 6 mm² de forma equitativa entre todos los dispositivos del cuadro.</p>
  </div>
</div>

<div class="project-img-text">
  <div class="project-img-text__img">
    <img src="/assets/images/sotano/Crimpado.JPG" alt="Detalle del crimpado de punteras">
  </div>
  <div class="project-img-text__text">
    <p>Detalle del crimpado de punteras en los cables de salida. Cada conductor queda perfectamente terminado e identificado, lo que facilita cualquier intervención posterior. Una instalación ordenada desde el principio se amplía o repara sin sorpresas.</p>
  </div>
</div>

<div class="project-img-text project-img-text--reversed">
  <div class="project-img-text__img">
    <img src="/assets/images/sotano/CuadroSuperiorTerminado.JPG" alt="Parte superior del cuadro terminada">
  </div>
  <div class="project-img-text__text">
    <p>Con la parte superior terminada, cada magnetotérmico queda conectado a su carga correspondiente. Se puede ver el <strong>contactor</strong> en uno de los laterales: su función es interponer un elemento de corte robusto entre el relé inteligente y la carga del termo, prolongando la vida del Shelly aunque esté dimensionado para aguantar la corriente directamente.</p>
  </div>
</div>

<figure class="project-figure">
  <img src="/assets/images/sotano/CuadroFuerzaTerminado.JPG" alt="Cuadro de fuerza completamente terminado">
  <figcaption>Cuadro de fuerza terminado y etiquetado, listo para su instalación definitiva.</figcaption>
</figure>

---

### Integración domótica: Shelly 1PM Gen 4

<div class="notice--info">
<strong>¿Por qué el Shelly 1PM Gen 4?</strong> Es uno de los pocos relés de su rango que soporta de forma nativa <strong>Zigbee, Matter y Wi-Fi</strong> simultáneamente, lo que lo hace compatible con prácticamente cualquier ecosistema domótico sin depender de un hub específico.
</div>

El **Shelly 1PM Gen 4** es un relé inteligente con monitorización de potencia en tiempo real. En esta instalación controla el encendido del **termo eléctrico** a través del contactor, con las siguientes capacidades activas:

**Monitorización en tiempo real:**
- Potencia instantánea, tensión y corriente.
- Detección del estado del termo: calentamiento activo frente a mantenimiento.
- Historial de consumo exportable para análisis energético.

**Automatizaciones implementadas:**
1. **Programación horaria**: activación en las horas de menor coste eléctrico (tarifa con discriminación horaria).
2. **Integración con Home Assistant**: control desde el panel de energía unificado de la vivienda via Matter.
3. **Base para futuras optimizaciones**: cruce de datos de consumo con previsiones meteorológicas o con la API de precios de Red Eléctrica para determinar el momento óptimo de calentamiento.

El dispositivo opera en **modo local** sin dependencia de servidores en la nube, lo que garantiza el funcionamiento aunque la conexión a internet falle.

---

### Iluminación

La iluminación se divide en tres sectores independientes, diseñados para cubrir las distintas zonas sin necesidad de iluminar todo el espacio a la vez.

**Sector 1 — Zona principal (conmutado):** La zona de mayor superficie se cablea con un circuito conmutado, permitiendo el control desde dos puntos del garaje. Se instalaron luminarias LED de superficie de 20 W para obtener una iluminación uniforme sin puntos ciegos. El cableado de retorno entre conmutadores usa conductor de 1,5 mm².

**Sector 2 — Zona de trabajo:** Interruptor único con dos focos LED orientables de 30 W. La orientabilidad permite dirigir la luz hacia la zona de trabajo activa en cada momento, ya sea el banco de herramientas o una tarea en el suelo.

**Sector 3 + automatización por presencia:** Las zonas del pasillo de acceso y la entrada desde la vivienda se controlan mediante **sensores PIR con temporización regulable**. La luz se activa al detectar movimiento y se apaga automáticamente tras el tiempo configurado (entre 1 y 10 minutos), eliminando olvidos y reduciendo el consumo.

Todo el cableado de iluminación discurre por canaleta corrugada con conductores de **1,5 mm²**.

---

### Tomas de corriente y bomba de achique

<div class="project-img-text">
  <div class="project-img-text__img">
    <img src="/assets/images/sotano/InterruptorEnchufeYbomba.JPG" alt="Enchufe, interruptor y conexión de la bomba">
  </div>
  <div class="project-img-text__text">
    <p>Los enchufes de uso general se instalaron próximos a cada punto de control de iluminación, para tener siempre una toma accesible cerca de donde se trabaja. Todos los circuitos de enchufes usan conductor de <strong>2,5 mm²</strong>.</p>
    <p>Para la <strong>bomba de achique</strong> se instaló una línea dedicada protegida con un magnetotérmico de 10 A, terminada en una toma estanca <strong>IP44</strong> para conexión directa de la bomba. La línea queda preparada también para un sensor de nivel flotador que active la bomba automáticamente ante una inundación.</p>
  </div>
</div>

<div class="project-img-text project-img-text--reversed">
  <div class="project-img-text__img">
    <img src="/assets/images/sotano/BombaGaraje.JPG" alt="Bomba de achique en su posición definitiva">
  </div>
  <div class="project-img-text__text">
    <p>La bomba de achique sumergida se ubica en el punto más bajo del sótano. La línea incluye un interruptor de corte manual accesible sin necesidad de ir al cuadro principal, lo que facilita el mantenimiento y los trabajos cerca de la bomba.</p>
  </div>
</div>

---

## Problemas encontrados

### Espacio en el cuadro

La caja de 7 módulos quedó muy ajustada al añadir el contactor, que ocupa el equivalente a dos módulos DIN. Para resolverlo se reasignaron posiciones dentro del cuadro y se sustituyeron algunos puentes de cable por puenteadoras de carril para ganar espacio. La solución fue efectiva, pero refuerza una lección importante: **dimensionar siempre el cuadro con al menos un 30 % de espacio libre** para futuras ampliaciones.

### Neutro para el relé inteligente

El Shelly 1PM Gen 4 requiere **línea de neutro** para su alimentación interna, algo que no siempre está disponible en los puntos de control domésticos. Al tratarse de una instalación nueva el neutro sí llegaba al cuadro, pero fue necesario planificar su distribución para que el Shelly quedara correctamente alimentado sin comprometer la sección de los conductores adyacentes.

### Elección de la protección del termo

Determinar el calibre correcto para el termo requirió revisar la ficha técnica del equipo. Un termo de 2 kW consume en torno a **9 A** a 230 V, pero los transitorios de arranque pueden superarlo. Se optó por un **magnetotérmico de 16 A curva C**, que tolera esos picos sin disparar innecesariamente, con un margen de seguridad adecuado.

### Tendido del cable de 6 mm² desde el cuadro principal

El recorrido desde el cuadro principal hasta el sótano obligó a abrir rozas en varios tramos y coordinar el paso por canalizaciones existentes sin interferir con otras líneas. El tramo más complicado fue la escalera, donde el espacio disponible era reducido y fue necesario usar tubo corrugado flexible para adaptarse al recorrido.

---

## Mejoras futuras

- **Integración completa con Home Assistant**: añadir el Shelly al panel de energía de HA para visualizar el consumo del sótano junto con el resto de la vivienda en tiempo real.
- **Automatización de la bomba de achique**: instalar un sensor de nivel flotador conectado a un segundo Shelly para activar la bomba automáticamente y enviar una notificación push ante una inundación.
- **Monitorización energética global**: añadir un contador de energía en el cuadro principal para tener visibilidad del consumo total de la vivienda y, en el futuro, cruzarlo con la generación de una instalación fotovoltaica.
- **Ampliación del cuadro de fuerza**: sustituir la caja actual por una de 12–16 módulos para albergar relés inteligentes en las demás cargas y, si procede, un carril de baja tensión (24 V DC) para sensores.
