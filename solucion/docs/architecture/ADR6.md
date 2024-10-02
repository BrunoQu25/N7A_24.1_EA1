### Título 
ADR 006: Manage Work Requests para Consultas de Horarios de los ómnibus

### Participantes: 

228151 - Bruno Quadrelli

314064 - Ignacio Santalla

276280 - Santiago Alfonso

215542 - Juan Cano

270956 - Pablo Duran

### Estado
Propuesto

### Contexto
En el caso de uso de la consulta de horarios de buses, se espera un gran volumen de usuarios simultáneos (hasta 20,000 usuarios) con un requisito de tiempo de respuesta de 0.5 a 1 segundo. Para cumplir con este nivel de rendimiento bajo alta demanda, el sistema necesita gestionar correctamente las solicitudes de trabajo para evitar sobrecargas.

### Decisión:
Se implementará una táctica de Manage Work Requests (Gestionar Solicitudes de Trabajo) para reducir la cantidad de solicitudes procesadas simultáneamente, evitando la saturación del sistema. Se aplicará un SLA que limitará la cantidad de consultas permitidas por usuario o sistema en un período de tiempo determinado, asegurando que el rendimiento (tiempo de respuesta) se mantenga dentro del rango establecido de 0.5 a 1 segundo.

### Consecuencias
Positivas:
- Rendimiento mejorado: Limitar la cantidad de solicitudes permitirá mantener tiempos de respuesta rápidos bajo alta demanda, mejorando la experiencia del usuario.
- Confiabilidad: Al evitar sobrecargas, se garantiza que el sistema sea confiable, brindando tiempos de respuesta predecibles.

Negativas: 
- Posible limitación para usuarios: Los usuarios podrían encontrar restricciones en la cantidad de consultas que pueden realizar en un tiempo determinado, lo que podría afectar la experiencia en casos donde se necesiten actualizaciones frecuentes.