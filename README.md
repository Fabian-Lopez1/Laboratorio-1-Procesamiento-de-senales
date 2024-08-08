# Laboratorio 1 Procesamiento  Digital de Señales: Análisis estadístico de la señal 
## Introducción
El propósito del presente laboratorio es profundizar las tecnicas estadisticas utilizadas en el análisis de señales biomédicas, aprendiendo a buscar señales biomedicas en repositorios como physionet con el fin de tener señales las cuales no solo pertenecen al campo de interes, sino que tambien permiten observar el antes y despues de realizar un procesamiento a la señal. En este caso se escogio una señal de un ECG hecho a pacientes con apnea, cada registro usado incluye una señal de ECG digitalizada continua, un conjunto de anotaciones de apnea (derivadas por expertos humanos sobre la base de la respiración registrada simultáneamente y señales relacionadas) y un conjunto de anotaciones QRS generadas por máquina; En resumen, señales de esfuerzo respiratorio torácico y abdominal obtenidas mediante pletismografía de inductancia.<br>
<br>
Para cumplir con todos los objetivos se utilizo el lenguaje de programacion Python, en el cual se realizo la importacion, muestra y tratamiento de los datos mencionados anteriormente(**para terceros se recomienda usar el software "Anaconda Navigator con su herramienta "Spider"**), al final de este repositorio se encontraran las instrucciones para poder usar el codigo de manera adecuada 

##Procesamiento de la señal
Una vez se decidio la señal que seria usada("a03"), se descargo de [Physionet](https://physionet.org/content/apnea-ecg/1.0.0/) teniendo en cuenta que se tienen que descargar 2 archivos que se llamen igual pero que tengan las estenciones .hea y .dat, una vez con estos archivos se hizo uso de la libreria llamada "Waveform Database" o por sus siglas wfdb para poder importar los datos de la señal a python y poder obtener sus valores y el longitud del arreglo, de la siguiente manera: 

```python
import wfdb
signal = wfdb.rdrecord('a03')
valores = signal.p_signal
tamaño = signal.sig_len
```
<br>
Una vez obtenida la señal era momento de mostrarla para poder observar lo que se denomino "señal original", esto se hizo usando la libreria "matplotlib" de esta manera y obteniendo la siguiente señal: 

```python
import matplotlib.pyplot as plt
plt.plot(valores,label='Señal de ECG-APNEA')
plt.title('Señal de ECG-APNEA obtenida de physionet')
plt.xlabel('Muestras (t en s)')
plt.ylabel('Amplitud (mV)')
plt.legend()
```
!(https://drive.google.com/file/d/1Nq-gbisaOD_8Kpf-NBYKOK_pXGg7xiUb/view?usp=sharing)
