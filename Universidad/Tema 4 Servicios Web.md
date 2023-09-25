# Conceptos Básicos
<u>Sistema distribuido</u>: Conjunto de agentes software que trabajan juntos para realizar alguna tarea.
<u>Servicio Web</u>: Sistema software diseñado para permitir la interacción máquina a máquina. Se suele usar un protocolo HTTP.

Ventajas de los servicios web:
- Es más sencillo de aprender
- Son independientes de la plataforma y lenguaje de implementación
- No hacen uso de puertos no estándar

### Arquitecturas de servicios Web
- En el plano conceptual
	-Un servicio es un componente software proporcionado a través de un endpoint
	-Tanto los consumidores como los proveedores de servicios usan mensajes para intercambiar peticiones y respuestas
	-Sin hacer suposiciones sobre las características tecnológicas del receptor
- En el plano técnico se puede implementar de dos formas:
	-Servicios SOAP
	-Servicios RESTful

#### Servicios SOAP
Simple Object Access Protocol
Sirve para el intercambio de información
Define una arquitectura de mensajes y sus formatos en XML
WSDL para describir la interfaz de los servidores (Web Service Description Language)

#### Servicios RESTful
Son vistos como recursos y pueden invocarse con una URI
Ofrecen operaciones que el cliente pueda invocar sobre ellos
Consideran HTTP no sólo como protocolo de transporte, sino también como un API
No existe una notación estándar

# Arquitectura REST
REpresentational State Transfer
- Es un estilo arquitectónico
- Para sistemas distribuidos basados en hipermedia, como la web
- Los recursos son la pieza fundamental de REST

### Principios
- Cliente-Servidor
- Sin estado: El contexto del cliente no se almacena en el servidor entre peticiones
- Cacheable: Cliente y servidor pueden almacenar respuestas
- Interfaz uniforme
- Sistema en capas
- Código bajo demanda

#### Protocolo HTTP
Es un protocolo sin estado
Peticiones:
- GET
- HEAD
- OPTIONS
- POST
- PUT
- PATCH
- DELETE