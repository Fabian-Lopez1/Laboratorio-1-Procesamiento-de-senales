# Laboratorio 1 Procesamiento  Digital de Señales: Análisis estadístico de la señal 
## Introducción
El propósito del presente laboratorio es profundizar las tecnicas estadisticas utilizadas en el análisis de señales biomédicas, aprendiendo a buscar señales biomedicas en repositorios como physionet con el fin de tener señales las cuales no solo pertenecen al campo de interes, sino que tambien permiten observar el antes y despues de realizar un procesamiento a la señal. En este caso se escogio una señal de un ECG hecho a pacientes con apnea, cada registro usado incluye una señal de ECG digitalizada continua, un conjunto de anotaciones de apnea (derivadas por expertos humanos sobre la base de la respiración registrada simultáneamente y señales relacionadas) y un conjunto de anotaciones QRS generadas por máquina; En resumen, señales de esfuerzo respiratorio torácico y abdominal obtenidas mediante pletismografía de inductancia.<br>
<br>
Para cumplir con todos los objetivos se utilizo el lenguaje de programacion Python, en el cual se realizo la importacion, muestra y tratamiento de los datos mencionados anteriormente(**para terceros se recomienda usar el software "Anaconda Navigator con su herramienta "Spider"**), al final de este repositorio se encontraran las instrucciones para poder usar el codigo de manera adecuada 

##Procesamiento de la señal
Una vez se decidio la señal que seria usada("a03"), se descargo de [Physionet](https://physionet.org/content/apnea-ecg/1.0.0/)
