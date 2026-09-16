---
title: "Servidor doméstico: domótica y nube local"
layout: single
permalink: /servidor-domestico/
author_profile: false
toc: true
toc_label: "En esta página"
toc_sticky: true
---

Servidor doméstico construido a partir de un portátil reutilizado para centralizar la domótica de la vivienda, alojar una nube familiar de fotografías y reducir la dependencia de servicios externos. El sistema funciona sobre Ubuntu Server y organiza sus servicios mediante contenedores Docker.

<div class="notice--info">
<strong>Estado actual:</strong> Home Assistant e Immich están funcionando de forma estable. El almacenamiento NAS, las copias automatizadas y la experimentación con IA local forman parte de las siguientes fases.
</div>

## Problema

Me encontraba cansado de acumular aplicaciones independientes para controlar dispositivos de distintos fabricantes. Esto obligaba a mantener varias cuentas y hacía que algunas automatizaciones dependieran de los atajos de un teléfono concreto.

Por esta razón el objetivo era trasladar esas tareas a un sistema local y permanente que pudiera utilizar toda la familia. Además de simplificar el control diario, la plataforma debía permitir combinar datos de consumo energético, producción solar y condiciones ambientales para tomar decisiones más eficientes.

## Solución

Se reutilizó un portátil Lenovo IdeaPad que llevaba varios años sin uso. Sobre él se instaló Ubuntu Server directamente. El equipo funciona sin pantalla ni periféricos y se administra mediante SSH.

Los servicios se ejecutan en contenedores independientes. Cada uno mantiene su propio archivo Docker Compose, configuración y volúmenes, lo que permite actualizarlo o reiniciarlo sin afectar al resto del sistema.

<!-- IMAGEN 1: fotografía del portátil o del lugar donde está instalado -->

## Hardware

| Componente | Configuración |
|---|---|
| Equipo | Portátil Lenovo IdeaPad reutilizado |
| Procesador | Intel Core i3 |
| Memoria | 8 GB de RAM |
| Almacenamiento principal | SSD de 512 GB |
| Gráficos | Integrados en el procesador |
| Alimentación | Cargador original, batería interna y SAI |
| Red actual | Wi-Fi con dirección IP fija |
| Sistema operativo | Ubuntu Server 24.04.5 LTS |

La carga de trabajo actual es baja, por lo que el portátil trabaja con poco ruido y sin problemas apreciables de temperatura. Su batería interna añade un pequeño margen ante cortes, mientras que el SAI proporciona una protección adicional.

La conexión se realiza actualmente por Wi-Fi sobre una red mesh propia. Como mejora futura se contempla añadir Ethernet mediante un adaptador para obtener una conexión cableada más estable.

## Arquitectura de servicios

| Servicio | Función | Estado |
|---|---|---|
| Home Assistant | Centralización y automatización de la vivienda | Operativo |
| Immich | Nube familiar y organización de fotografías | Operativo |
| Tailscale | Acceso remoto privado | Operativo |
| NAS doméstico | Almacenamiento local de archivos y copias | Pendiente |
| IA local | Gestión y toma de decisiones a partir de sensores | Exploración futura |

Los contenedores están configurados para iniciarse automáticamente después de un reinicio. Las actualizaciones se ejecutan durante la noche y el estado del equipo se revisa periódicamente.

## Home Assistant

Home Assistant se ejecuta como contenedor y actúa como punto común para los dispositivos de la vivienda. Actualmente integra enchufes, relés, sensores magnéticos, medidores de consumo y el inversor solar. La comunicación se realiza principalmente mediante Wi-Fi, aunque algunos dispositivos admiten también otros protocolos.

Entre las automatizaciones implementadas se encuentran:

- Encendido automático por horario y presencia de luces.
- Gestión de la bomba de achique.
- Control de calefacción y termo según la producción solar.
- Control del aire acondicionado en verano según el consumo energético y la producción solar.
- Integración con Alexa para facilitar el uso cotidiano (Pendiente).

Al trasladar las automatizaciones al servidor, dejan de depender de atajos ejecutados desde los teléfonos. Esto evita procesos nocturnos que consumían batería y permite que las reglas funcionen incluso cuando el propietario no está en casa.

<figure class="project-figure">
  <img src="/assets/images/servidor-domestico/home-assistant.png" alt="Panel principal de Home Assistant con iluminación, bomba de achique, climatización y producción solar">
  <figcaption>Panel central de la vivienda: iluminación, bomba de achique, climatización, previsión meteorológica y seguimiento de la producción solar.</figcaption>
</figure>

## Immich

Immich proporciona una nube local de fotografías para tres usuarios. El servicio se ejecuta en Docker y mantiene las imágenes dentro de la infraestructura doméstica, sin depender de Google Photos, iCloud u otra nube comercial.

Actualmente se están sincronizando algunos álbumes y ya se utilizan funciones como el reconocimiento facial, los mapas y la búsqueda. Las fotografías cuentan con copias adicionales en discos duros, aunque el sistema de almacenamiento y respaldo todavía se encuentra en una fase bastante prematura.

<figure class="project-figure">
  <img src="/assets/images/servidor-domestico/immich.png" alt="Interfaz web de Immich ejecutándose en el servidor doméstico">
  <figcaption>Interfaz web de Immich, utilizada como nube familiar de fotografías dentro de la infraestructura doméstica.</figcaption>
</figure>

## Acceso remoto y seguridad

El servidor puede administrarse de forma remota mediante Tailscale. El acceso administrativo está limitado para una mayor seguridad en las conexiones y tratar de mantener el server alejado de posibles ataques.

La combinación de acceso privado, servicios locales y administración mediante SSH permite trabajar con el servidor sin exponer directamente sus aplicaciones a Internet.

## Decisiones de diseño

### Reutilizar un portátil

El portátil ofrece suficiente capacidad para la carga actual y evita comprar hardware nuevo. También integra pantalla, teclado y batería para tareas de diagnóstico, aunque normalmente funciona completamente desatendido.

### Utilizar Ubuntu Server

Ubuntu Server proporciona un sistema ligero y estable que puede administrarse íntegramente por SSH. Al instalarlo directamente sobre el hardware se reserva la mayor parte de los recursos para los servicios.

### Separar los servicios en contenedores

Docker permite alojar Home Assistant, Immich y futuras aplicaciones en el mismo equipo sin convertir el servidor en un sistema dedicado a una única función. Cada servicio puede mantenerse y actualizarse de forma independiente.

## Resultado

El servidor lleva aproximadamente un mes funcionando de manera estable. Home Assistant centraliza el control de la vivienda y ejecuta las automatizaciones de forma local, mientras que Immich ofrece una nube familiar sobre la que se conserva el control de los datos.

El proyecto también ha creado una base para analizar conjuntamente consumo, producción solar y condiciones ambientales. Su valor principal no está únicamente en alojar aplicaciones, sino en disponer de una infraestructura propia que puede evolucionar con las necesidades de la vivienda.

## Mejoras futuras

- Conectar el servidor mediante Ethernet.
- Completar la subida automática de fotografías.
- Automatizar las copias de seguridad de Home Assistant y de los demás servicios.
- Incorporar almacenamiento NAS con discos dedicados.
- Mejorar la estrategia de recuperación ante el fallo del SSD principal.
- Añadir monitorización continua de recursos y temperatura.
- Explorar una IA local capaz de tomar decisiones a partir de sensores, consumo y condiciones ambientales.
