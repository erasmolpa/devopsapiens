---
title: "Introduccion a la IaC. Algunos Funamentos y Principios."
date: 2024-05-13
last_modified_at: 2024-05-13
cat:
  - IaC
---

# Introducción:

En tecnología es  Ya sabeis, esas conversaciones que pretender ser el origen de una toma de decisión para un problema que en realidad va mas allá de si una herramienta es mejor/preor que otra.

He vivido esa situación en innumerables ocasiones, muchas de ellas con resultados mejorables. Pero mi actitud optimista y el rodearte de personas con algo de pensamiento pragmático (y sobre todo crítico) te hace tener algo de fe 

Este post podría tener un enfoque de , porque Iac , beneficios bla bla..pero no me apetece escribir algo asi ..lo siento ...simplemente voy a dejar caer aquí algo de contexto y algunos principios básicos sobre el asunto 


## El Problema:

Independientemente de tu rol/experiencia en este mundo de la tecnología, es bastante probable que en algun punto de tu carrera y con más frecuencia de lo que te gustaría has tenido que lidiar con la frustrante labor de aprovisionar/configurar algo de "infra". 

Si eres Developer y por mucho que puedas decir eso de ..en mi local funciona!, seguro que no estas excento de alguna que otra batalla contra la máquina.

La infraestructura ha ido evolucionando  que ha llevado desde servidores físicos, pasando por virtualización, el paso a la nube (e incluso a los clusters de Kubernetes), ha hecho que la tarea de aprovisionar y configurar la infraestructura sea cada vez más desafiante.

Es decir, el problema a resolver radica en la complejidad creciente de gestionar la infraestructura a medida que ha ido mutando continuamente. 

## La solución:

_IaC "Enfoque que permite crear y configurar recursos de infraestructura de manera programática"_

Infrastructure as Code (IaC) ofrece una solución a estos desafíos. Es una metodología que permite definir, implementar y gestionar la infraestructura de TI utilizando código. En lugar de realizar cambios manualmente en la infraestructura en la nube, podemos escribir código que describa esos recursos y su configuración, y luego utilizar herramientas especializadas para implementar y mantener esa infraestructura de manera automatizada, consistente y, sobre todo, idempotente.

IaC nos permite tratar la infraestructura como código, aplicando los principios de desarrollo de software a la gestión de la infraestructura. Esto significa que podemos aprovechar las prácticas de desarrollo ágil, como la integración continua y la entrega continua, para iterar rápidamente en nuestra infraestructura y responder de manera eficiente a los cambios en los requisitos del negocio.



# Fundamentos: 

Puedes encontrar multitud de posts que te lo explicarán las características y beneficios. Me gustaría comentar las que considero mas relevantes a la hora de llevar IaC a cualquier proyecto: 


## Idempotencia:

Es la propiedad de una operación en la que su aplicación repetida no produce cambios adicionales más allá del primer efecto. En el contexto de IaC, la idempotencia implica que la ejecución repetida del código de infraestructura no cause efectos secundarios no deseados. Por ejemplo, si aplicamos un script de aprovisionamiento varias veces, solo se implementarán los cambios necesarios, evitando la duplicación de recursos o la alteración de configuraciones existentes.

Ejemplo: Supongamos que queremos asegurarnos de que un archivo de configuración esté presente en un servidor. Utilizaremos un comando bash para copiar este archivo desde una ubicación remota a nuestro servidor.

```bash
scp user@remote_host:/path/to/config_file.txt /path/to/local_directory/
```

Si ejecutamos este comando varias veces, el archivo se copiará solo una vez, y las ejecuciones posteriores no tendrán ningún efecto adicional, ya que el archivo ya estará presente en la ubicación especificada. No se crearán copias adicionales del archivo, lo que demuestra la propiedad idempotente del comando.

## Repetibilidad: 

Se refiere a la capacidad de repetir un proceso o una acción de manera consistente y predecible. En el contexto de IaC, la repeatabilidad implica que al desplegar la misma configuración varias veces, se obtendrán los mismos resultados en cada instancia. Esto asegura que los entornos y configuraciones sean reproducibles, lo que facilita la creación de entornos consistentes y la corrección de errores de manera eficiente

Ejemplo: Con el ejemplo anterior, siempre que ejecutemos ese comando, obtendremos el mismo resultado, es decir, el archivo de configuración se copiará desde la ubicación remota al directorio local especificado. Esto asegura que el proceso sea repetible, 

## Consistencia:

 Se refiere a la uniformidad y coherencia en la configuración y el comportamiento de los recursos de infraestructura. En el contexto de IaC, la consistencia implica que los entornos y configuraciones sean reproducibles y predecibles. Por ejemplo, si desplegamos la misma configuración varias veces, esperamos obtener los mismos resultados en cada instancia.

**Ejemplo:** verifique si el archivo de configuración ya existe en la ubicación local antes de intentar copiarlo nuevamente. Esto garantizará que la configuración en el servidor sea consistente y evitará la duplicación de archivos.

```bash
# Comprobar si el archivo de configuración ya existe en la ubicación local
if [ -f /path/to/local_directory/config_file.txt ]; then
    echo "El archivo de configuración ya existe en el servidor."
else
    # Copiar el archivo de configuración desde una ubicación remota al servidor
    scp user@remote_host:/path/to/config_file.txt /path/to/local_directory/
    echo "Se ha copiado el archivo de configuración al servidor."
fi
```

cada vez que ejecutamos el script, se verificará si el archivo de configuración ya está presente en el servidor local. Si ya existe, el script mostrará un mensaje indicando que el archivo ya está allí. Si no existe, se copiará el archivo desde la ubicación remota al servidor local. 


# Principios

- **Reusabilidad:** _Eso que acabas de hacer..Podrías repetirlo?_ 
  
  Escribir código reutilizable nos permite aprovechar soluciones existentes y evitar duplicar esfuerzos.

- **Consistencia:** 
  
  Mantener la consistencia entre los recursos de la infraestructura en la nube es fundamental para garantizar su confiabilidad y seguridad.

- **Transparencia:** 
  
  La transparencia en IaC implica tener visibilidad y comprensión del estado y la configuración de los recursos en la nube en todo momento.

- **Estabilidad:** _"no tengo miedo a cambiar"_ 
  
  La estabilidad en IaC no significa inmovilidad, sino la capacidad de implementar cambios de manera segura y controlada en tu infraestructura en la nube.

- **Efimera:** _"no te necesito"_ 
  
  Con IaC, podemos generar y recrear recursos en la infraestructura en la nube de manera automatizada, eliminando la necesidad de intervención manual en cada paso del proceso.


## En Práctica:

- **El código de infraestructura es fuego real:** Al igual que el fuego real, el código de infraestructura tiene un impacto significativo en la estabilidad y seguridad de la infraestructura en la nube.
- **Las pruebas son duras, y no negociables:** Las pruebas automatizadas son esenciales en IaC para garantizar la calidad y confiabilidad de la infraestructura en la nube.
- **Se pragmático:** Adoptar un enfoque pragmático al escribir código de infraestructura en la nube es fundamental para lograr los objetivos del proyecto de manera eficiente y efectiva.

- **Cada cosa en su sitio:** Entender la complejidad implícita y explícita de la infraestructura nos ayuda a organizar y estructurar el código de manera más efectiva.
- **No quiero sorpresas:** La consistencia y la predictibilidad son fundamentales en IaC.
- **Idempotencia:** La idempotencia es un principio fundamental en IaC que garantiza que la ejecución del código de infraestructura en la nube produzca el mismo resultado, independientemente del estado actual de la infraestructura.

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

## Conclusiones

* Si en tu proyecto/empresa se esta planteando/usando IaC, asegurate de entender al máximo la complejidad del problema y en base a eso Fundamentos. E
* Se pragmatico. Desarrollar IaC no es como desarrollar una API de negocio, pero , todas las buenas practicas y el pragmatismo es aplicable en este contexto. 
  

Espero que te halla gustado este post. En realidad pretendo convertirlo en una serie de post en la que iré tirando del hilo de todos los puntos tratados en esta intro , ya que como podras imaginar, hay mucha tela que cortar. 


¡Gracias por leer!

