### Título 
ADR 005: Gestionar la tasa de muestreo

### Participantes: 

228151 - Bruno Quadrelli

314064 - Ignacio Santalla

276280 - Santiago Alfonso

215542 - Juan Cano

270956 - Pablo Duran

### Estado
Propuesto

### Contexto
El sistema actualmente actualiza las ubicaciones de los ómnibus y usuarios en intervalos cortos, lo que genera una alta carga de procesamiento. Esto puede generar una sobrecarga en horas donde se generan picos de consultas o de actualizaciones, dando como resultado una mala performance y una mala experiencia para el usuario.

### Decisión:
Se reducirá la frecuencia de las actualizaciones de ubicación, por ejemplo, pasando de actualizaciones cada 30 segundos a cada 40 segundos o incluso más. Esta reducción en la tasa de muestreo disminuirá la carga de procesamiento, sin afectar gravemente la experiencia del usuario.

### Consecuencias
Positivas:
- Menor carga de procesamiento: Reducir la tasa de muestreo disminuirá significativamente la cantidad de datos procesados, mejorando la eficiencia del sistema
- Rendimiento optimizado: Al reducir la cantidad de eventos procesados por segundo, se mejorará el rendimiento global sin una pérdida significativa en la precisión de los datos.

Negativas:
- Datos menos actualizados: La reducción en la tasa de actualización podría causar que algunos usuarios perciban retrasos en la información sobre la ubicación de los buses.