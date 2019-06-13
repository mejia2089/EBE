# EBE-CORE
API para facturación electronica.

Electronic Biller Engine Core es un API Stateless que abstrae la logica de comunicarse con el Ministerio de Hacienda de Costa Rica (MH), nace de la necesidad de centralizar la complejidad de la integración con el MH, además de centralizar los cambios versión con sus implicaciones de posibles cambios sobre estructuras, metodos y algoritmos requeridos para dicha integración con el MH.

EBE-CORE es un servicio que está en la nube para disposición y uso de cualquier desarrollador, esta la versión Stage que se mantendrá libre de uso para desarrollo y pruebas, y la versión Production que requiere un key de autenticación para su consumo.

Al ser un API Stateless el mismo actua como un proxy contra los servicios del MH, esto significa que no hay almacenamiento de datos de ningún tipo, ni en la recepción o respuesta de hacienda, el API es transparante y actual como “puente“ entre las integraciones y el MH.

El API se compone de servicios los cuales se clasifican en Operativos y Utilitarios.

 Markup : * Bullet list
              * Nested bullet
                  * Sub-nested bullet etc
          * Bullet list item 2
