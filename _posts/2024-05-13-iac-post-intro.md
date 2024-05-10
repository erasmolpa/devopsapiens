---
title: "Infraestructura como Código. Concetp fundamentos, principios e ideas locas "
date: 2024-05-13
last_modified_at: 2024-05-13
cat
  - IaC
  - series
  - foundations
---

# Porque este Post:

Veo demasiadas Tooling fights por ahi escritas, sobre Iac , donde en realidad se habla de que caracteristicas y que ventajas tiene la herramienta X sobre la Y. solo son herramientas y mi objetivo con este post es volcar algunas ideas, principios y conceptos basicos de la IaC. 

Intentaré ser neutral, pragmatico y desordenado :) ya que esto es mas bien un volcado de pensamientos. 

📓 Intenté generar este post con ChatGPT y Copilot  y fracasé ...Aunque  son herramientas que uso a diario y hacen que sea mas vago de lo que soy si cabe, el resultado no fue bueno asi que espero que al menos hagas un repost de esto porque he tenido que pensar y esforzarme. Dejo aqui evidencia de la imagen generada por Copilot para representar API layers vs Infra Layer de manera ilustrativa 

![OIG3](https://github.com/our-learning-path/learning-path-erasmo-2024/assets/1197538/9eed00f4-1228-49db-afe6-69555c4ad2cd)



# Breve introducción al problema:

Gestionar la infraestructura en la nube puede ser un desafío abrumador. Las organizaciones se enfrentan a una complejidad creciente, con infraestructuras distribuidas en múltiples proveedores de nube y entornos locales. La gestión manual de estos recursos es propensa a errores y no escalable. Además, la falta de consistencia entre los diferentes entornos, como desarrollo, pruebas y producción, puede provocar problemas de compatibilidad y seguridad.

En muchos proyectos actuales, nos encontramos con una serie de pasos manuales o semi-automatizados que son propensos a errores y no son idempotentes. Estos pasos a menudo incluyen configuraciones específicas del proveedor de la nube, instalaciones de software y ajustes de red. Además, en un fenómeno conocido como "Yak Shaving", nos encontramos realizando una serie de tareas aparentemente irrelevantes que consumen tiempo y recursos valiosos, como la configuración de herramientas de desarrollo o la resolución de dependencias de software.

---

# La solución:

Infrastructure as Code (IaC) ofrece una solución a estos desafíos. Es una metodología que permite definir, implementar y gestionar la infraestructura de TI utilizando código. En lugar de realizar cambios manualmente en la infraestructura en la nube, podemos escribir código que describa esos recursos y su configuración, y luego utilizar herramientas especializadas para implementar y mantener esa infraestructura de manera automatizada, consistente y, sobre todo, idempotente.

IaC nos permite tratar la infraestructura como código, aplicando los principios de desarrollo de software a la gestión de la infraestructura. Esto significa que podemos aprovechar las prácticas de desarrollo ágil, como la integración continua y la entrega continua, para iterar rápidamente en nuestra infraestructura y responder de manera eficiente a los cambios en los requisitos del negocio.

---

# Infraestructura:

## Principios:
- **No te necesito:** Con IaC, podemos generar y recrear recursos en la infraestructura en la nube de manera automatizada, eliminando la necesidad de intervención manual en cada paso del proceso.
- **Podrías repetirlo? Por supuesto!:** La capacidad de reproducir recursos en diferentes entornos de manera consistente es esencial en IaC.
- **Stability = Continuous Change:** La estabilidad en IaC no significa inmovilidad, sino la capacidad de implementar cambios de manera segura y controlada en tu infraestructura en la nube.

## Core Practices:
- **Reusabilidad:** Escribir código reutilizable nos permite aprovechar soluciones existentes y evitar duplicar esfuerzos.
- **Consistencia:** Mantener la consistencia entre los recursos de la infraestructura en la nube es fundamental para garantizar su confiabilidad y seguridad.
- **Transparencia:** La transparencia en IaC implica tener visibilidad y comprensión del estado y la configuración de los recursos en la nube en todo momento.

---

# Code:

## Principios:
- **El código de infraestructura es fuego real:** Al igual que el fuego real, el código de infraestructura tiene un impacto significativo en la estabilidad y seguridad de la infraestructura en la nube.
- **Las pruebas son duras, y no negociables:** Las pruebas automatizadas son esenciales en IaC para garantizar la calidad y confiabilidad de la infraestructura en la nube.
- **Se pragmático:** Adoptar un enfoque pragmático al escribir código de infraestructura en la nube es fundamental para lograr los objetivos del proyecto de manera eficiente y efectiva.

## Core Practices:
- **Cada cosa en su sitio:** Entender la complejidad implícita y explícita de la infraestructura nos ayuda a organizar y estructurar el código de manera más efectiva.
- **No quiero sorpresas:** La consistencia y la predictibilidad son fundamentales en IaC.
- **Idempotencia:** La idempotencia es un principio fundamental en IaC que garantiza que la ejecución del código de infraestructura en la nube produzca el mismo resultado, independientemente del estado actual de la infraestructura.

## Nos parecemos más de lo que te imaginas

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

## Consejos extraídos desde la observación

He visto infinidad de batallas entre herramientas y soluciones de IaC. Creo ,que hay mas material disponible en internet enfocado en comparar herramientas que post ...


1. Entiende los fundamentos. La herramienta es "lo de menos" 
2. Se pragmatico. 
3. IaC no es para todo el mundo. Empoderar o implantar Iac no es gratis 
## Conclusiones

Cloud Native representa un cambio fundamental en la forma en que se desarrollan, implementan y gestionan las aplicaciones en la era de la nube. Al adoptar los principios y prácticas de Cloud Native, las organizaciones pueden beneficiarse de una mayor agilidad, flexibilidad y eficiencia en el desarrollo de software.

Espero que esta introducción te haya proporcionado una comprensión básica de lo que implica ser Cloud Native y por qué es importante en el mundo actual del desarrollo de software.

¡Gracias por leer!

