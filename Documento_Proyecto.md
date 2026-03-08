

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
| **US-01** | Como organizador de eventos quiero publicar un evento con su información y número de boletas disponibles para vender entradas a los asistentes. | - El organizador puede crear un evento.<br> - Debe poder definir fecha, lugar y cupo máximo. <br> - El evento queda visible para los usuarios. <br> - No se pueden vender más boletas que el cupo definido. | I: Es independiente a las demas historias. <br> N: Negociable <br> V: Es valiosa, crea la base del programa <br> E: Estimable <br> S: Pequeña <br> T: Comprobable |
| **US-02** | Como organizador quiero definir diferentes tipos de boletas (general, VIP) para ofrecer distintas opciones de compra a los usuarios. | - El organizador puede crear múltiples tipos de boleta. <br> - Cada tipo tiene precio y cantidad. <br> - El sistema controla el inventario por tipo de boleta. | I: Es independiente a las demas historias. <br> N: Negociable <br> V: Es valiosa <br> E: Estimable <br> S: Pequeña <br> T: Comprobable|
| **US-03** | Como usuario quiero buscar eventos disponibles para comprar entradas al evento de mi interés. | - El sistema muestra eventos disponibles. <br> - Los usuarios pueden ver información del evento. | I: Es independiente a las demas historias. <br> N: Negociable <br> V: Es valiosa <br> E: Estimable <br> S: Pequeña <br> T: Comprobable |
| **US-04** | Como usuario quiero comprar una boleta para un evento de manera segura, para evitar que me roben. | - El usuario puede seleccionar el tipo de boleta. <br> - El sistema genera una orden de compra. <br> - El estado del pago puede ser pendiente, fallido o confirmado. <br> - La compra se hace mediante una pasarela de pagos. | I: Es independiente a las demas historias. <br> N: Negociable, nos pueden pedir metodos de pago especificos <br> V: Es valiosa <br> E: Estimable (por daniel) <br> S: Pequeña <br> T: Comprobable|
| **US-05** | Como usuario quiero recibir una boleta digital con código QR después del pago confirmado para poder ingresar al evento. | - Se genera una boleta digital única  con un QR integrado. <br> - La boleta se envía por correo o notificación. <br> - Solo se genera cuando el pago está confirmado. | I: Parcialmente independiente <br> N: Negociable, presetación de la boleta <br> V: Es valiosa <br> E: Estimable (por daniel) <br> S: Pequeña <br> T: Comprobable|
| **US-06** | Como personal de logística quiero escanear el QR de una boleta para verificar si es válida y permitir el ingreso al evento. | - El sistema verifica si la boleta existe. <br> - El sistema verifica si ya fue usada. <br> - Si es válida, se marca como utilizada. <br> - Si ya fue usada, se rechaza el acceso. | I: Dependiente <br> N: Negociable <br> V: Es valiosa <br> E: Estimable  <br> S: Pequeña <br> T: Parcialmente comprobable |
| **US-07** | Como organizador quiero modificar precios, cupos o códigos promocionales para gestionar la venta de boletas según la estrategia del evento. | - El organizador puede actualizar precios. <br> - Puede activar o desactivar códigos promocionales. <br> - El sistema registra quién realizó el cambio y cuándo. | I: Dependiente <br> N: Negociable <br> V: Es valiosa <br> E: Estimable <br> S: Pequeña <br> T: Parcialmente comprobable |
| **US-08** | Como organizador quiero cancelar un evento publicado para notificar a los asistentes y gestionar las devoluciones correspondientes | - El organizador puede cancelar el evento. <br> - El sistema debe permitir devoluciones a través una pasarela de pagos <br> - El sistema debe notificar a los usuarios de la cancelación del evento | I: Dependiente <br> N: Negociable <br> V: Es valiosa <br> E: No es estimable <br> S: ? <br> T: Parcialmente comprobable |


>  **Instrucciones:**  
> - Completar al menos **6 historias de usuario**.  
> - Asegurar que cada historia tenga criterios de aceptación claros y verificables.  

---

## 3. Requisitos de Calidad  
Los requisitos de calidad se presentan en forma de **historias de calidad**, siguiendo la estructura de Len Bass.

### **Historias de Calidad**
| **ID**    | **Fuente**         | **Estímulo**         | **Artefactos**         | **Entorno**         | **Respuesta**         | **Medida de Respuesta**         |
| --------- | ------------------ | -------------------- | ---------------------- | ------------------- | --------------------- | ------------------------------- |
| **RQ-01** | _[Agregar fuente]_ | _[Agregar estímulo]_ | _[Agregar artefactos]_ | _[Agregar entorno]_ | _[Agregar respuesta]_ | _[Agregar medida de respuesta]_ |
| **RQ-02** | _[Agregar fuente]_ | _[Agregar estímulo]_ | _[Agregar artefactos]_ | _[Agregar entorno]_ | _[Agregar respuesta]_ | _[Agregar medida de respuesta]_ |
| **RQ-03** | _[Agregar fuente]_ | _[Agregar estímulo]_ | _[Agregar artefactos]_ | _[Agregar entorno]_ | _[Agregar respuesta]_ | _[Agregar medida de respuesta]_ |

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

