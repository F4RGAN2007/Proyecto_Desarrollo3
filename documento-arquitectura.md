

# Documento de Arquitectura del Sistema de Gestión de Órdenes y Entregas

## 1. Introducción  
Este documento describe la arquitectura inicial del sistema de gestión de órdenes y entregas, incluyendo requisitos funcionales, requisitos de calidad y restricciones que deben ser consideradas en el diseño del software.

**Equipo:** Los informantes
**Integrantes:** 

- Moises Uriel Medina Villa 2459709
- Santiago Avalo Monsalve 2359442
- Daniel Gómez Cano 2359396
- Edward Stivens Pinto 2359431

**Fecha:** 01/03/2026

---

## 2. Requisitos Funcionales  
Los requisitos funcionales se presentan en forma de **historias de usuario**, especificando los **criterios de aceptación**.

### **Historias de Usuario**
| **ID**    | **Historia de Usuario**         | **Criterios de Aceptación**         | INVEST                                      |
| --------- | ------------------------------- | ----------------------------------- | ------------------------------------------- |
| **US-01** | _[Agregar historia de usuario]_ | _[Agregar criterios de aceptación]_ | _[Agregar si cumple o no cumple y por que]_ |
| **US-02** | _[Agregar historia de usuario]_ | _[Agregar criterios de aceptación]_ |                                             |
| **US-03** | _[Agregar historia de usuario]_ | _[Agregar criterios de aceptación]_ |                                             |
|           |                                 |                                     |                                             |
|           |                                 |                                     |                                             |

>  **Instrucciones:**  
> - Completar al menos **6 historias de usuario**.  
> - Asegurar que cada historia tenga criterios de aceptación claros y verificables.  

---


## 3. Requisitos de Calidad  
Los requisitos de calidad se presentan en forma de **historias de calidad**, siguiendo la estructura de Len Bass.

### **Historias de Calidad**
| **ID**    | **Fuente**         | **Estímulo**         | **Artefactos**         | **Entorno**         | **Respuesta**         | **Medida de Respuesta**         |
| --------- | ------------------ | -------------------- | ---------------------- | ------------------- | --------------------- | ------------------------------- |
| **RQ-01 (Disponibilidad)** | Falla de infraestructura | Una instancia de un microservicio crítico se cae | Microservicios (Pedidos, Inventario, Entregas) | Operación normal o en hora pico | El gateway redirige automáticamente las solicitudes a instancias sanas y genera alerta | Redirección en ≤ 5 segundos. Disponibilidad ≥ 99.5% mensual. Alerta generada en ≤ 1 minuto|
| **RQ-02 (Rendimiento)** | Usuario (cliente/admin) | Realiza una solicitud (consulta catálogo o pedido) | API Gateway + Microservicios | Hora pico | El sistema procesa y responde la solicitud sin degradación perceptible | Tiempo de respuesta ≤ 300 ms en el 95% de las solicitudes |
| **RQ-03 (Escalabilidad)** | Incremento sostenido de usuarios | Aumento del 50% en la carga durante 10 minutos | Clúster en Kubernetes | Hora pico | El sistema levanta nuevas instancias automáticamente sin interrumpir usuarios | Nuevas instancias activas en ≤ 2 minutos. 0% de caída de servicio durante escalado|
| **RQ-04 (Seguridad - Autenticación)** | Usuario malintencionado | Múltiples intentos fallidos de autenticación | Servicio de autenticación (OAuth2 + JWT) | Operación normal | El sistema bloquea temporalmente la cuenta y registra evento sospechoso | Bloqueo tras 5 intentos fallidos en 5 minutos. Evento registrado en logs inmediatamente |
| **RQ-05 (Seguridad - Autorización)** | Usuario autenticado | Intenta acceder a recurso sin permisos | API Gateway / Control de roles | Operación normal | El sistema deniega acceso y registra intento | Respuesta HTTP 403 en ≤ 200 ms. Registro del evento en logs centralizados |
| **RQ-06 (Confiabilidad de Mensajería)** | Falla en procesamiento de mensaje | Un mensaje de actualización de stock no puede procesarse | Sistema de mensajería (Kafka/RabbitMQ) | Operación normal | El mensaje se reintenta automáticamente o pasa a cola de pendientes (DLQ) | 0% de pérdida de mensajes. Máximo 3 reintentos antes de enviarlo a DLQ |
| **RQ-07 (Consistencia de Inventario)** | Creación de pedido | Se descuenta stock de un producto | Servicio de Inventario | Alta concurrencia | El sistema evita stock negativo y mantiene consistencia | Stock nunca < 0. Actualización reflejada en ≤ 5 segundos |
| **RQ-08 (Observabilidad)** | Error repetitivo o tiempo alto de respuesta | Servicio supera umbral de latencia | Sistema completo (logs, métricas, monitoreo) | Hora pico | Se genera alerta automática y queda trazabilidad | Alerta en ≤ 1 minuto si latencia > 300 ms por 3 minutos consecutivos |
| **RQ-09 (Actualización casi en tiempo real)** | Repartidor actualiza estado | Cambio de estado a “En ruta” o actualización de ubicación | Servicio de Entregas | Pedido en proceso de entrega | El sistema refleja el cambio al cliente y operador | Actualización visible en ≤ 30 segundos |
| **RQ-10 (Recuperación ante fallos)** | Reinicio inesperado de servicio | Servicio vuelve a estar disponible | Microservicio afectado | Entorno degradado | El servicio se reintegra al clúster automáticamente | Reintegración en ≤ 2 minutos sin intervención manual |





>  **Instrucciones:**  
> - Completar al menos **6 historias de calidad**, alineadas con atributos clave como **rendimiento, escalabilidad y seguridad**.  
> - Definir cómo se medirá la respuesta esperada ante la situación planteada.  

---

## 4. Restricciones del Sistema  
Las restricciones establecen **limitaciones** en la arquitectura del sistema, ya sean tecnológicas, de negocio, regulatorias o de infraestructura.

### **Lista de Restricciones**
| **Tipo de Restricción** | **Descripción**                                                                                                                                                          |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| _[Agregar otro tipo]_   | _[Describir la restricción]_                                                                                                                                             |

>  **Tipos de restricciones:**  
> - **Tecnológicas:** Lenguajes, frameworks o herramientas que deben utilizarse.  
> - **De negocio:** Normativas o estándares de la empresa.  
> - **Regulatorias:** Cumplimiento de normativas legales o de seguridad.  
> - **De infraestructura:** Limitaciones en hardware, red o almacenamiento.  



