# EBE-CORE
API para facturación electronica.

Electronic Biller Engine Core es un API Stateless que abstrae la logica de comunicarse con el Ministerio de Hacienda de Costa Rica (MH), nace de la necesidad de centralizar la complejidad de la integración con el MH, además de centralizar los cambios versión con sus implicaciones de posibles cambios sobre estructuras, metodos y algoritmos requeridos para dicha integración con el MH.

EBE-CORE es un servicio que está en la nube para disposición y uso de cualquier desarrollador, esta la versión Stage que se mantendrá libre de uso para desarrollo y pruebas, y la versión Production que requiere un key de autenticación para su consumo.

Al ser un API Stateless el mismo actua como un proxy contra los servicios del MH, esto significa que no hay almacenamiento de datos de ningún tipo, ni en la recepción o respuesta de hacienda, el API es transparante y actual como “puente“ entre las integraciones y el MH.

El API se compone de servicios los cuales se clasifican en Operativos y Utilitarios.

## Ambientes
|Recurso | Descripción |
| ------------- | ------------- |
| https://gateway.dev.factura-e.cr/catalog/api/  | Desarrollo / Pruebas  |
| https://gateway.factura-e.cr/catalog/api/ | Producción  |

## Operativos
Los servicios operatvios abstraen toda la logica necesaria de enviar y consultar un documento fiscal desde/hacia el MH, encapsulan toda la logica en un simple llamado REST, dichos servicios son los siguientes:

-Enviar un documento hacia el MH
-Consultar el estado del documento por el consecutivo suministrado por el MH (/reception/{numeroComprobante}).

|Recurso | Verbo |Descripción|
| ------------- | ------------- |-------------|
| https://gateway.dev.factura-e.cr/dss/api/in-memory/sign-document | POST |Enviar documento |
| https://gateway.dev.factura-e.cr/invoice/api/reception/{consecutivo}| GET  |Obtener documento|

Además de poder consumir estos servicios operativos “completos”, se pueden consumir las partes que lo componen de forma individual, que son los siguientes servicios:

-Firmar un documento fiscal. (/in-memory/sign-document)
-Validacion de un documento fiscal (validación tanto en estructura como en calidad de los datos).
-Validar credenciales (/validate/credentials).
-Validar certicado (/pendiente).
-Obtener la informacion de un cetificado (/certificate-information).

|Recurso | Verbo |Descripción|
| ------------- | ------------- |-------------|
| https://gateway.dev.factura-e.cr/dss/api/in-memory/sign-document| POST |Firmar documento |
| https://gateway.dev.factura-e.cr/dss/api/certificate-information| POST  |Obtener información del certificado|
| https://gateway.dev.factura-e.cr/invoice/api/validate/credentials| POST  |Validar credenciales de hacienda|

## Utilitarios
Los servicios utilitarios permiten consumir una variedad de funcionalidades las cuales suelen ser muy útiles a la hora de trabajar con documentos fiscales con el MH; algunos de estos servicios son los siguientes:

-Tipo de cambio (obtenido diariamente desde el Banco Central de Costa Rica).
-Distribucion territorial de Costa Rica (Catalogo de Provincias, cantones y distritos).
-Consultas al patron electoral por cedula fisica nacional.
-Consultas a catalogos tipo “ENUMS“ definidos por el MH como:
-Tipo de identificación
-Actividades economicas
-Tipos de documentos fiscales

|Recurso | Verbo |Descripción|
| ------------- | ------------- |-------------|
| https://gateway.dev.factura-e.cr/catalog/api/exchange-request-current/318| GET |Obtener tipo de cambio |
| https://gateway.dev.factura-e.cr/catalog/api/identificationTypeList| GET  | Obtener catalogo de identificacion|

## Postman Collection
Aca esta la colección en Postman para su uso, https://www.getpostman.com/collections/2f073a796fa4fd68a9f5.
