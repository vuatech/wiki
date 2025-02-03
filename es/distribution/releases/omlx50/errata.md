---
title: OpenMandriva Lx 5.0 Errata
description: 
published: true
date: 2023-11-15T14:41:16.127Z
tags: 5.0
editor: markdown
dateCreated: 2022-12-26T17:59:33.144Z
---

# OpenMandriva Lx 5.0 Errata - Problemas Conocidos

> Como con cualquier lanzamiento, aún existen problemas y errores que pueden no haber sido resueltos. Esta página documenta aquellos que pueden causar inconvenientes y, cuando es posible, detalla cómo solucionarlos. 
{.is-info}

Como con cualquier lanzamiento, aún existen problemas y errores que pueden no haber sido resueltos.
Esta página documenta aquellos que pueden causar inconvenientes y, cuando es posible,
detalla cómo solucionarlos.
<br />

## Problemas conocidos y soluciones
<br />

### Tarjetas gráficas NVIDIA

Esta versión incluye el controlador *nouveau* desarrollado a partir de ingeniería inversa,
el cual proporciona un soporte moderadamente bueno para la mayoría de las tarjetas NVIDIA.
Para algunos entornos de doble pantalla, en realidad es mejor que el controlador binario de NVIDIA, 
ya que permite la rotación de pantalla en un segundo monitor, lo cual es útil para monitores con pantallas giratorias.
Los usuarios pueden utilizar los controladores del sitio web de NVIDIA, 
pero estos no son compatibles con OpenMandriva.
Por diversas razones, OpenMandriva no puede brindar soporte para estos controladores. 
La instalación y el mantenimiento de cualquier controlador propietario de NVIDIA es decisión y 
responsabilidad exclusiva del usuario.
Existen controladores de NVIDIA con soporte comunitario disponibles en el repositorio *non-free*.
<br />
### NVME SSDs

Hay un problema conocido con algunos dispositivos NVME SSD (especialmente los más nuevos) y dispositivos PCIE, 
donde el SSD puede no ser reconocido. 
Este problema es conocido y está siendo trabajado por los desarrolladores de OpenMandriva y los desarrolladores upstream.

![header-tr-50.svg](/assets/header-tr-50.svg){.align-abstopright}
