---
title: "Introduccion a la IaC. Fundamentos de Programacion"
date: 2024-05-27
last_modified_at: 2024-05-27
cat:
  - observability
  - post-series
---

# Introducción:


## El Problema:

## La solución:

## Fundamentos 

## Es la IaC una Práctica comparable al desarrollo de una API? 

0. **Desarrollo enfocado a reutilización de componentes:**
 
1. **Capas de la infraestructura como capas en una API:**

   - Al diseñar una API de producto, a menudo se divide en capas, como la capa de presentación, la capa de lógica de negocio y la capa de acceso a datos. De manera similar, al crear Infraestructura como Código, podemos pensar en diferentes capas de infraestructura, como la capa de red (VPC), la capa de almacenamiento (buckets de S3), la capa de computación (instancias EC2), entre otras. Cada una de estas capas cumple un propósito específico y se diseña para trabajar en conjunto para proporcionar un entorno de infraestructura completo.

2. **Externalización de la configuración:**

   - Al desarrollar una API de producto, a menudo es útil externalizar la configuración, como las URLs de conexión a bases de datos o las claves de API, para que puedan ser modificadas fácilmente sin necesidad de cambiar el código fuente. De manera similar, en IaC, podemos externalizar la configuración de la infraestructura utilizando prácticas como Configuration as Code (CaC). Esto nos permite definir la configuración de la infraestructura en archivos de código que pueden versionarse, revisarse y compartirse fácilmente, lo que facilita la gestión y el mantenimiento de la infraestructura a lo largo del tiempo.

3. **Versionado y control de cambios:**
   - En el desarrollo de una API, es común utilizar sistemas de control de versiones como Git para gestionar el código fuente y realizar un seguimiento de los cambios a lo largo del tiempo. De manera similar, en IaC, podemos utilizar herramientas de control de versiones para gestionar y versionar los archivos de configuración de la infraestructura, lo que nos permite realizar un seguimiento de los cambios, revertir a versiones anteriores y colaborar de manera efectiva en equipos distribuidos.

4. **Automatización de pruebas y validación:**
   - Al desarrollar una API, es fundamental realizar pruebas para garantizar que funcione como se espera y cumpla con los requisitos de negocio. Esto puede incluir pruebas unitarias, pruebas de integración y pruebas de aceptación. De manera similar, en IaC, podemos automatizar pruebas para validar nuestra infraestructura y asegurarnos de que se despliegue correctamente y cumpla con los criterios de calidad. Esto puede incluir pruebas de configuración, pruebas de seguridad y pruebas de rendimiento.

5. **Orquestación de recursos:**
   - Desarrollar una API de producto a menudo implica orquestar diferentes componentes y servicios para proporcionar una funcionalidad completa y coherente. Por ejemplo, podemos utilizar un patrón de diseño como el patrón de repositorio para separar la lógica de acceso a datos de la lógica de negocio. En IaC, también necesitamos orquestar diferentes recursos de infraestructura, como instancias de servidor, bases de datos y redes, para crear un entorno de infraestructura completo y funcional. Herramientas como Terraform y AWS CloudFormation nos permiten definir y gestionar estas relaciones de manera declarativa.

## Consejos:


¡Gracias por leer!

