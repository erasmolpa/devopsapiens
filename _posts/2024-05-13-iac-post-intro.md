---
title: "Infraestructura como Código. Breve introducción caótica."
date: 2024-05-13
last_modified_at: 2024-05-13
cat:
  - IaC
---

# Por qué este Post?:

Una de las sensaciones que menos me gustan como perfil técnico , es esa que se tiene cuando se habla todo el tiempo en el contexto de la solución. Me explico, son esas conversacines que pretender ser el origen de una toma de decisión para un problema que en realidad va mas allá de si una herramienta es mejor/preor que otra.

He vivido esa situación en innumerables ocasiones, muchas de ellas con resultados mejorables. Pero mi actitud optimista y el rodearte de personas con algo de pensamiento pragmático (y sobre todo crítico) te hace tener algo de fe 

Este post podría tener un enfoque de , porque Iac , beneficios bla bla..pero no me apetece escribir algo asi ..lo siento ...simplemente voy a dejar caer aquí algo de contexto y algunos principios básicos sobre el asunto 


# Breve introducción al problema:

Da igual el tipo de rol que tengas en tu compañía/proyecto; Backend , Frontend , Sys Admin/"DevOps"/SRE/Platform Engineer/X/Y/Z , que seguro que en algun punto de tu carrera y con más frecuencia de lo que te gustaría ,  has tenido que lidiar con manejar frustación al instalar/configurar algo que tenga que ver con "infra". 

Si eres Developer, "estas de suerte" has pasado de tener que invertir multitud de horas en instalar y configurar un servidor local a poder decir, en mi local funciona! incluso probablemente hay muchisima gente preocupada ahora mismo por porporcionarte una buena Dev Experience (Ironía de la buena )

Lo sé amigo, se que la vida del Dev no es tan bonita :D ..pero que pasa con la gente al otro lado del muro? esos que conocemos como , "la parte Ops" . Pues dejame decirte que esta gente va avanzando a pasos agiganados, ya escriben la infraestructura como código y son capaces de crearte un entorno de produccion en 


Lidiar con el concepto de Yak Shaving puede ser muy frustrante tambien creeme . Lo he 


Gestionar la infraestructura en la nube puede ser un desafío abrumador. Las organizaciones se enfrentan a una complejidad creciente, con infraestructuras distribuidas en múltiples proveedores de nube y entornos locales. La gestión manual de estos recursos es propensa a errores y no escalable. Además, la falta de consistencia entre los diferentes entornos, como desarrollo, pruebas y producción, puede provocar problemas de compatibilidad y seguridad.


# La solución:

Infrastructure as Code (IaC) ofrece una solución a estos desafíos. Es una metodología que permite definir, implementar y gestionar la infraestructura de TI utilizando código. En lugar de realizar cambios manualmente en la infraestructura en la nube, podemos escribir código que describa esos recursos y su configuración, y luego utilizar herramientas especializadas para implementar y mantener esa infraestructura de manera automatizada, consistente y, sobre todo, idempotente.

IaC nos permite tratar la infraestructura como código, aplicando los principios de desarrollo de software a la gestión de la infraestructura. Esto significa que podemos aprovechar las prácticas de desarrollo ágil, como la integración continua y la entrega continua, para iterar rápidamente en nuestra infraestructura y responder de manera eficiente a los cambios en los requisitos del negocio.

# Definición: 

"Es un enfoque que permite provisionar y configurar recursos de infraestructura de manera programática"

Para una definición más completa , [wikipedia IaC](https://en.wikipedia.org/wiki/Infrastructure_as_code)

Dame motives 
Increased consistency and repeatability: 

# Beneficios: 

Podría enumerarte infinidad de beneficios. Puedes encontrar multitud de posts que te lo explicarán mejor que yo , asi que me voy a centrar en solamente dos de ellos que para mi son los más interesantes (en realidad es que no me apetece hablar aqui de seguridad, costes, colaboracion jaja :D )

## Consistencia:

 Se refiere a la uniformidad y coherencia en la configuración y el comportamiento de los recursos de infraestructura. En el contexto de IaC, la consistencia implica que los entornos y configuraciones sean reproducibles y predecibles. Por ejemplo, si desplegamos la misma configuración varias veces, esperamos obtener los mismos resultados en cada instancia.

**Ejemplo:** Utilizando el gestor de paquetes `apt` en sistemas basados en Debian, el siguiente comando siempre instalará la misma versión de Apache:

```bash
sudo apt update && sudo apt install apache2

Cada vez que ejecutamos este comando, obtenemos la misma versión de Apache instalada, asegurando consistencia en la configuración del servidor web en múltiples ejecuciones.

## Idempotencia:

Es la propiedad de una operación en la que su aplicación repetida no produce cambios adicionales más allá del primer efecto. En el contexto de IaC, la idempotencia implica que la ejecución repetida del código de infraestructura no cause efectos secundarios no deseados. Por ejemplo, si aplicamos un script de aprovisionamiento varias veces, solo se implementarán los cambios necesarios, evitando la duplicación de recursos o la alteración de configuraciones existentes.

Ejemplo: Supongamos que queremos agregar una regla de firewall para permitir el tráfico SSH en nuestro servidor. El siguiente comando de iptables añade esta regla, pero si lo ejecutamos múltiples veces, no se crearán reglas duplicadas: 

```bash
iptables -A INPUT -p tcp --dport 22 -j ACCEPT

Al ejecutar este comando varias veces, solo se agregará una única regla para permitir el tráfico SSH, evitando la duplicación de reglas y garantizando la idempotencia en la configuración del firewall.


# Infraestructura:

## Principios:
- **No te necesito:** Con IaC, podemos generar y recrear recursos en la infraestructura en la nube de manera automatizada, eliminando la necesidad de intervención manual en cada paso del proceso.
- **Podrías repetirlo? Por supuesto!:** La capacidad de reproducir recursos en diferentes entornos de manera consistente es esencial en IaC.
- **Stability = Continuous Change:** La estabilidad en IaC no significa inmovilidad, sino la capacidad de implementar cambios de manera segura y controlada en tu infraestructura en la nube.

## Core Practices:
- **Reusabilidad:** Escribir código reutilizable nos permite aprovechar soluciones existentes y evitar duplicar esfuerzos.
- **Consistencia:** Mantener la consistencia entre los recursos de la infraestructura en la nube es fundamental para garantizar su confiabilidad y seguridad.
- **Transparencia:** La transparencia en IaC implica tener visibilidad y comprensión del estado y la configuración de los recursos en la nube en todo momento.


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
4. 
## Conclusiones


¡Gracias por leer!

