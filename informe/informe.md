# Taller 4 – Mapa de Infraestructura y Diagnóstico Técnico

**Arquitectura Empresarial**

## Plataforma Analizada

**RedExpress – Plataforma de logística y rastreo de envíos**

---

# 1. Introducción

RedExpress es una plataforma logística que permite gestionar envíos y realizar rastreo de paquetes en tiempo real mediante una aplicación móvil y una plataforma web. La infraestructura tecnológica integra servicios en la nube, servidores regionales y dispositivos móviles utilizados por los mensajeros.

El objetivo de este trabajo es modelar un mapa de infraestructura del sistema e identificar posibles debilidades técnicas, cuellos de botella y oportunidades de mejora que puedan afectar el rendimiento, la disponibilidad y la escalabilidad de la plataforma.

---

# 2. Descripción general de la infraestructura

La arquitectura de RedExpress se compone de varios componentes tecnológicos que permiten la interacción entre usuarios, mensajeros y centros logísticos.

Los principales elementos de la infraestructura incluyen:

* Aplicación móvil y plataforma web utilizadas por clientes y mensajeros.
* API Gateway encargado de centralizar las solicitudes del sistema.
* Balanceadores de carga para distribuir el tráfico entre servicios.
* Servicios de aplicación que gestionan el rastreo de paquetes, los envíos y el procesamiento de rutas.
* Servidores regionales para optimizar el procesamiento de información logística en diferentes zonas geográficas.
* Base de datos distribuida que almacena información de clientes, paquetes y estados de envío.
* Sistemas de monitoreo y alertas para supervisar el funcionamiento de la plataforma.

Esta infraestructura permite conectar los centros de distribución físicos con la plataforma digital y con los dispositivos móviles utilizados por los mensajeros.

---

# 3. Identificación de cuellos de botella

## Latencia en el rastreo de paquetes

El rastreo en tiempo real requiere consultas constantes a la base de datos para obtener el estado actualizado de cada paquete. En momentos de alta demanda, como promociones o temporadas festivas, estas consultas pueden generar un aumento significativo en la latencia del sistema.

Una posible solución es implementar un sistema de **cache distribuido** que almacene temporalmente los estados más recientes de los paquetes, reduciendo la carga sobre la base de datos principal.

---

## Sobrecarga en el procesamiento de rutas

El cálculo de rutas para los envíos puede requerir un alto consumo de recursos computacionales, especialmente cuando se procesan múltiples entregas simultáneamente.

Para mejorar el rendimiento, es recomendable distribuir el procesamiento de rutas entre **servidores regionales**, permitiendo reducir los tiempos de respuesta y optimizar el uso de recursos.

---

# 4. Riesgos de disponibilidad

## Puntos únicos de falla

Algunos componentes críticos de la infraestructura pueden representar puntos únicos de falla si no cuentan con redundancia. Entre ellos se encuentran el balanceador de carga o algunos servicios centrales.

Para evitar interrupciones en el servicio, se recomienda implementar mecanismos de **redundancia y failover automático**, lo que permitiría mantener el sistema operativo incluso si uno de los componentes falla.

---

# 5. Escalabilidad del sistema

La plataforma RedExpress debe ser capaz de escalar para soportar aumentos en la demanda, especialmente en temporadas de alto volumen logístico.

Una arquitectura basada en **microservicios desplegados en la nube** permite escalar horizontalmente los servicios más utilizados, agregando nuevas instancias cuando el tráfico aumenta. Esto permite mantener tiempos de respuesta adecuados y mejorar la experiencia del usuario.

---

# 6. Monitoreo y observabilidad

El monitoreo continuo del sistema es fundamental para detectar problemas antes de que afecten a los usuarios.

Se recomienda utilizar herramientas de monitoreo que permitan analizar métricas como:

* uso de CPU y memoria
* tiempos de respuesta de los servicios
* número de solicitudes concurrentes
* estado de los servidores regionales

El uso de sistemas de alertas permite notificar automáticamente al equipo técnico cuando se detectan anomalías en el sistema.

---

# 7. Conclusión

El diagnóstico técnico de la infraestructura de RedExpress permite identificar áreas críticas relacionadas con la latencia del rastreo de paquetes, la escalabilidad del procesamiento de rutas y la disponibilidad de los servicios.

La implementación de mecanismos como **cache distribuido, redundancia de componentes críticos y escalabilidad basada en cloud** permitirá mejorar la resiliencia del sistema, optimizar su rendimiento y garantizar una experiencia confiable para los usuarios.

---

# Referencias

* Newman, S. (2021). *Building Microservices*. O’Reilly Media.
* Bass, L., Clements, P., & Kazman, R. (2022). *Software Architecture in Practice*. Addison-Wesley.
* Amazon Web Services. (2023). *AWS Well-Architected Framework*.
