# ande-plugin-qgis-arquitecture
Documentación técnica, patrón MVC y Changelog del "ANDE Plugin" (PyQGIS) desarrollado para Tierra-Ayni Ltda.

# 🔌 ANDE Plugin v3.4 "Legado" (Sentinel Edition) - Arquitectura y Documentación Técnica

**Desarrolladores:** Sergio Hernández / Mario Mieres  
**Organización:** Tierra-Ayni Ltda.  
**Plataforma:** QGIS (PyQGIS) 3.44+  

## 📌 Descripción General
El **ANDE Plugin** es una herramienta de grado corporativo diseñada para la generación automática, corrección topológica y auditoría de redes eléctricas de Baja Tensión (BT) y Media Tensión (MT) a partir de datos de relevamiento LiDAR. 

Este repositorio contiene la **documentación de arquitectura de software, el registro de versiones (Changelog) y la estructura de directorios** desarrollada durante la Práctica Profesional en Ingeniería en Informática (Duoc UC).
En su versión cumbre (v3.4 "Legado"), el sistema logra la unificación total de la red principal con sus derivaciones (Acometidas y Alumbrado Público) en un solo grafo espacial continuo, garantizando 0% de superposiciones geométricas ("efecto rebote") y una continuidad matemática perfecta de sus identificadores (`rwo_id`).

> ⚠️ **Nota de Confidencialidad:** Por políticas de la empresa (NDA), este repositorio solo contiene la documentación de diseño y arquitectura (Archivos `.txt` y Markdown). El código fuente comercial (`.py`) es propiedad exclusiva de Tierra-Ayni Ltda.

## 🏗️ Arquitectura de Software (Patrón MVC)
El complemento está estructurado utilizando el patrón de diseño **Modelo-Vista-Controlador (MVC)**, garantizando un código desacoplado y tolerante a fallos:
- **Modelo (Core):** Lógica matemática espacial, algoritmos de Teoría de Grafos (*Union-Find*) e Índices Espaciales (`QgsSpatialIndex`).
- **Vista (UI):** Interfaz gráfica asíncrona desarrollada en PyQt5 con hojas de estilo (QSS) corporativas y personalización dinámica.
- **Controlador:** Orquestación de hilos, prevención de *crashes* mediante *Bulk Delete* y manejo de eventos.
- **Módulo QA (El Centinela):** Escáner topológico implacable con Filtro Anti-FME. Clasifica nodos flotantes, detecta micro-tramos y exporta reportes gerenciales en formato `.csv` para discriminar falsos positivos (excepciones legales) de errores reales.

## 📂 Archivos en este Repositorio
Te invitamos a explorar los siguientes documentos de ingeniería incluidos en este repositorio:
1. `patron-arquitectura-mvc.txt`: Explicación detallada de las responsabilidades del sistema.
2. `estructura-directorios.txt`: Mapa del software y módulos complementarios (Toolbox).
3. `changelog-versiones.txt`: Evolución histórica desde la v1.0 hasta la **v3.4 (Legado / Sentinel Edition)**.
4. `proyecto-general.txt`: Resumen de capacidades y flujos de trabajo en producción.
