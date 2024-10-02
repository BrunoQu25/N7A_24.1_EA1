# Preguntas
1. Identifique los Atributos de calidad más relevantes indicando por qué los
seleccionan.

- Modificabilidad: 
    - Dado el requerimiento no funcional `Cualquier cambio en las API de los distintos DataProvider no debe tener impacto en el servicio TripLogic.` el servicio TripLogic al utilizar la API de DataProvider debe poder procesar las respuestas que esta le brinde a pesar de que se realicen cambios en esta.

- Performance:
    - Dado requerimiento no funcional `los ómnibus en tiempo real en la aplicación móvil debe ser lo más próximo al tiempo real posible` la aplicacion de movil debe ser altamente performante para cumplir con este requisito, ante la demanda en tiempo real.
    - A su vez el sistema tambien debe cumplir el siguiente requerimiento no funcional `se espera que el tiempo de respuesta se encuentre entre 0.5 y 1 seg.` al consultar los horarios de los buses, al ser un tiempo de respuesta breve para los datos que se deben procesar, debemos tener en cuenta que tiene que ser altamente performante.
    - Control Transito tambien realiza consultas periodicamente de datos masivos sobre recorridos de las distintas lineas para controlar la calidad del servicio con datos historicos de al menos 12 meses. NoSeComoIr debe trabajar con una carga importante de datos y no debe atrasarse en procesar y responder para no arruinar la experiencia de usuario y cumplir el requisito no funcional `la herramienta QueryTool no afecte los tiempos de respuesta de resto de los servicios del sistema`.

- Escalabilidad: 
    - Si la cantidad de usuarios aumenta mas allá del esperado o si todos consultan al mismo tiempo, el sistema debe poder escalar dinámicamente para adaptarse a picos inesperados.
    - En las horas pico se tienen 800 omnibus en simultaneo que se deben procesar sus datos de geolocalizacion, por lo tanto el sistema debe estar preparado para la recepcion de este.

- Interoperabilidad: 
    - Dada la dependencia y el bajo tiempo de respuesta que debe tener la aplicacion creemos que la interoperabilidad entre TripLogic y el DataProvider es esencial para el correcto funcionamiento del navegador de horarios de los buses.
    - Debe tener la capacidad de seguir estandares de comunicacion como HTTPS y RPC Sincronica.
     
- Disponibilidad: 
    - Para BusData, es necesario según la letra que `la autoridad de tránsito sea capaz de tener acceso a los datos históricos de al menos 12 meses`. Esto quiere decir que se debe garantizar un acceso a estos datos de forma ininterrumpida.
- Mantenibilidad:
    -  A la hora de actualizar el registro de datos de BusData, se debe poder gestionarlas y actualizarlas de manera sencilla sin interrumpir el acceso a la información. 

2. Propongan - basándose en la utilización de Patrones de diseño y tácticas de arquitectura - una solución que resuelva dichos requerimientos.

- Patron `Adapter`: Crea una capa intermedia entre el TripLogic y las APIs, entonces si alguna de las APIs cambia, solo es necesario modificar el adapter y no el TripLogic completo.

- Patron `Publisher/Susbscriber`: Existe una cola de eventos, con canales, donde cada bus tiene un canal para él mismo. Los usuarios interesados en un bus se suscriben a ese canal. Cada 30 segundos el bus envia su ubicacion a la cola y esta le envia la info a los suscriptores, y luego finalmente se envia a la BDD Bus Data. Esto evita todas las consultas a la BDD para ver la ubicacion de un omnibus en tiempo real, aumentando fuertemente la `performance`

- Patrón `CQRS`: Este patrón separa las operaciones de lectura de las operaciones de escritura. De esta manera, las consultas masivas de la autoridad de tránsito no van a interferir con las operaciones de agregado de datos. Esto fomenta la disponibilidad de datos.

- Táctica multiples copias de datos `Caché`: Se pueden almacenar en caché las consultas realizadas con más frecuencia por la autoridad de tránsito y de esta forma reducir el tiempo de respuesta para consultas repetidas.


3. Refleje su propuesta utilizando los diagramas que considere necesarios y documente las principales decisiones utilizando ADRs.
