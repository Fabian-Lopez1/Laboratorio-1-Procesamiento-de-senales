# Laboratorio 1 Procesamiento  Digital de Señales: Análisis estadístico de la señal 
## Introducción
El propósito del presente laboratorio es profundizar las tecnicas estadisticas utilizadas en el análisis de señales biomédicas, aprendiendo a buscar señales biomedicas en repositorios como physionet con el fin de tener señales las cuales no solo pertenecen al campo de interes, sino que tambien permiten observar el antes y despues de realizar un procesamiento a la señal. En este caso se escogio una señal de un ECG hecho a pacientes con apnea, cada registro usado incluye una señal de ECG digitalizada continua, un conjunto de anotaciones de apnea (derivadas por expertos humanos sobre la base de la respiración registrada simultáneamente y señales relacionadas) y un conjunto de anotaciones QRS generadas por máquina; En resumen, señales de esfuerzo respiratorio torácico y abdominal obtenidas mediante pletismografía de inductancia.<br>
<br>
Para cumplir con todos los objetivos se utilizo el lenguaje de programacion Python, en el cual se realizo la importacion, muestra y tratamiento de los datos mencionados anteriormente(**para terceros se recomienda usar el software "Anaconda Navigator con su herramienta "Spider"**), al final de este repositorio se encontraran las instrucciones para poder usar el codigo de manera adecuada 

## Procesamiento de la señal
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
![Senal original](https://drive.google.com/uc?export=view&id=1Nq-gbisaOD_8Kpf-NBYKOK_pXGg7xiUb)

<br>

Una vez se confirmo que la señal se importo de manera correcta a python, se procedio con la primera parte del laboratorio la cual se basa en el estudio estadistico de la señal, en el cual se realizan diferentes medidas estadisticas tanto por formula como por comando de librerias de python; para esta parte es crucial importar las siguientes librerias: 

```python
import numpy as np
import math
from scipy.stats import variation
```
<br>

### Media estadistica
Como su nombre lo dicta es el valor promedio en el que se mantiene la señal, para la parte con formula se uso la siguiente formula y se implemento en el codigo de la siguiente manera:
<br>
![media](https://quicklatex.com/cache3/e9/ql_529238be61b9b711ea08fd55cd745ee9_l3.png)

```python
media = np.mean(valores)
print("La media de la señal es:", media)
```

En ambos casos se obtuvo un valor de **0.00102** aprocimadamente

### Desviacion estandar

La desviacion estandar, indica la dispersion la dispersion o variacion del conjunto de datos que se tiene, para encontrarla se utiliza la siguiente formula y se implemento por codigo asi: 
<br>
![Desviacion estandar](https://quicklatex.com/cache3/c9/ql_35e276e65637c4608038eba6cea6e8c9_l3.png)

```python
desviacion_estandar = np.std(valores)
print("La desviacion estandar de la señal es:", desviacion_estandar)
```
<br>

En ambos casos se obtuvo un valor de **0.4449** aproximadamente


