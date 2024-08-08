# Laboratorio 1 Procesamiento  Digital de Señales: Análisis estadístico de la señal 
## Introducción
El propósito del presente laboratorio es profundizar las tecnicas estadisticas utilizadas en el análisis de señales biomédicas, aprendiendo a buscar señales biomedicas en repositorios como physionet con el fin de tener señales las cuales no solo pertenecen al campo de interes, sino que tambien permiten observar el antes y despues de realizar un procesamiento a la señal. En este caso se escogio una señal de un ECG hecho a pacientes con apnea, cada registro usado incluye una señal de ECG digitalizada continua, un conjunto de anotaciones de apnea (derivadas por expertos humanos sobre la base de la respiración registrada simultáneamente y señales relacionadas) y un conjunto de anotaciones QRS generadas por máquina; En resumen, señales de esfuerzo respiratorio torácico y abdominal obtenidas mediante pletismografía de inductancia.<br>
<br>
Para cumplir con todos los objetivos se utilizo el lenguaje de programacion Python, en el cual se realizo la importacion, muestra y tratamiento de los datos mencionados anteriormente(**para terceros se recomienda usar el software "Anaconda Navigator con su herramienta "Spider"**), al final de este repositorio se encontraran las instrucciones para poder usar el codigo de manera adecuada 

## Procesamiento de la señal
## Analisis estadistico
Una vez se decidio la señal que seria usada("a03"), se descargo de [Physionet](https://physionet.org/content/apnea-ecg/1.0.0/) teniendo en cuenta que se tienen que descargar 2 archivos que se llamen igual pero que tengan las estenciones .hea y .dat, una vez con estos archivos se hizo uso de la libreria llamada "Waveform Database" o por sus siglas wfdb para poder importar los datos de la señal a python y poder obtener sus valores y el longitud del arreglo, de la siguiente manera: 

```python
import wfdb
signal = wfdb.rdrecord('a03')
valores = signal.p_signal
tamaño = signal.sig_len
```
<br>
Una vez obtenida la señal era momento de mostrarla para poder observar lo que se denomino "señal original", esto se hizo usando la libreria "matplotlib" obteniendo la siguiente señal: 
<br>
<br>

![Senal original](https://drive.google.com/uc?export=view&id=1Nq-gbisaOD_8Kpf-NBYKOK_pXGg7xiUb)

Una vez se confirmo que la señal se importo de manera correcta a python, se procedio con la primera parte del laboratorio la cual se basa en el estudio estadistico de la señal, en el cual se realizan diferentes medidas estadisticas tanto por formula como por comando de librerias de python; para esta parte es crucial importar las siguientes librerias: matplotlib, numpy, math y scipy


### Media estadistica
Como su nombre lo dicta es el valor promedio en el que se mantiene la señal(en este caso en unidades de la escala de Voltios), para la parte con formula se uso la siguiente formula y se implemento en el codigo de la siguiente manera:
<br>
<br>
![media](https://quicklatex.com/cache3/e9/ql_529238be61b9b711ea08fd55cd745ee9_l3.png)

```python
media = np.mean(valores)
print("La media de la señal es:", media)
```

En ambos casos se obtuvo un valor de **0.00102** aproximadamente

### Desviacion estandar

La desviacion estandar, indica la dispersion la dispersion o variacion del conjunto de datos que se tiene, para encontrarla se utiliza la siguiente formula y se implemento por codigo asi: 
<br>
<br>
![Desviacion estandar](https://quicklatex.com/cache3/c9/ql_35e276e65637c4608038eba6cea6e8c9_l3.png)

```python
desviacion_estandar = np.std(valores)
print("La desviacion estandar de la señal es:", desviacion_estandar)
```
<br>

En ambos casos se obtuvo un valor de **0.4449** aproximadamente

### Coeficiente de variacion 
El coeficiente de variacion indica que tanto cambia una variable en funcion de la otra, en este caso que tanto cambia la amplitud respecto al tiempo, para la parte con formula se uso la siguiente formula y se implemento en el codigo de la siguiente manera:
<br>
<br>
![Coeficiente de variacion](https://quicklatex.com/cache3/94/ql_1e34d0d4e0591516687ef56b0dd03694_l3.png)

```python
C_variacion = variation(valores)
print("El coeficiente de variacion de la señal es:", C_variacion)
```
<br>

En ambos casos se obtuvo un valor de **435.4675** aproximadamente
<br>
### Histograma y Funcion de probabilidad
El histograma y la funcion de probabilidad estan interconectados, por eso se decidio unir los resultados en una sola parte. Estos se realizaron por formula, sin embargo es mas simple para el usuario mostrar los resultados obtenidos, ya que en el codigo se encuentra indicado en que parte se hacen las modificaciones a los mismos: 
<br>
<br>
![Histograma](https://drive.google.com/uc?export=view&id=1gH-x2WzdD5oh5uOKuq1KVC9wJTtaKf6D) ![Funcion de probabilidad](https://drive.google.com/uc?export=view&id=1m2sgsltka0-iiEm1dLqA9y7J9f3RD_0r)

## Relacion señal ruido (SNR)
La Relacion señal ruido  es la relación entre la potencia de una señal útil y la potencia del ruido de fondo. Se utiliza para medir la calidad de la señal; un SNR más alto indica una señal más clara y menos afectada por el ruido; se utiliza la siguiente formula:
<br>
<br>
![SNR](https://quicklatex.com/cache3/2f/ql_51d12e518023d4d41be035e9f8e68f2f_l3.png)

### Ruido gaussiano 
El ruido gaussiano es un tipo de ruido que tiene una distribución de probabilidad normal (gaussiana), caracterizada por su media y desviación estándar; debido a esto dependiendo de ciertop valor que sera mencionado despues, los valores de SNR cambian dependiendo de cuanta desviacion estandar se le coloque a la ecuacion(En este casi **0.5**), los resultados obtenidos fueron: 
<br>
<br>
![Gaussiano](https://drive.google.com/uc?export=view&id=1dRuoYXGvYfdgrtF0axQyYVFrbrICOPhz)

### Ruido tipo impulso
El ruido tipo impulso es un tipo de ruido que se manifiesta como picos repentinos y breves en la señal, debido a eventos esporádicos o fallos en el sistema; para este caso se tuvo que implementar el nivel del ruido y la probabilidad de que ocurriera un impulos, ambos son valores que se pueden manipular para afectar no solo la señal sino tambien el nivel del SNR, en este caso con un nivel de ruido de **0.8** y una probabilidad de impulso del **0.05** se obtuvo la siguiente grafica: 
<br>
<br>
![impulso](https://drive.google.com/uc?export=view&id=1zL0GFKqSwFlB2ru0pAaJDoY7_orEz9uj)

### Ruido tipo artefacto 
El ruido tipo artefacto es un ruido no deseado en una señal que se origina por defectos o interferencias en el sistema de medición o procesamiento, como fallos en el hardware o errores en la adquisición de datos; este tipo de ruido es aleatorio, por lo que se usa una funcion que genere una onda aleatoria, la cual tambien usa una desviacion estandar de **0.5**, obteniendo asi la siguiente grafica: 
<br>
<br>
![impulso](https://drive.google.com/uc?export=view&id=1CTO9oftJyyHk6YvR-k4NEci5NUXMdHsO)

# Instrucciones para el usuario 
Para evitar problemas se le recomienda al usuario usar la version 3.10 de python y no modificar nada de lo que no se mensione en los siguientes pasos, ya que el codigo generara las demas cosas de manera automatica. ademas se recomienda usar datos de una dimension o un vector (si no se tienen de esa forma convertirlos a un solo vector)

1. importar las siguientes librerias luego de instalarlas previamente
   
```python
import wfdb 
import matplotlib.pyplot as plt
import numpy as np
import math
from scipy.stats import variation
```
2. descargar los archivos .hea y . dat de una señal de la pagina web [Physionet](https://physionet.org/about/database/)
3. cargar los datos descargados anteriormente de la siguiente forma (linea 21 de codigo)
```python
signal = wfdb.rdrecord('nombre_de_sus_archivos')
```
4. una vez teniendo esto se obtienen automaticamente las siguientes cosas: los valores de la señal, la longitud(o tamaño) del arreglo, se muestra la grafica de sus datos, La media, la desviacion estandar y el coeficiente de variacion.
5. para el histograma y la funcion de probabilidad se usa algo llamado "bins", que se podria decir que son los intervalos en los que se agrupan los datos, a menor numero de bins menor numero de barrras y visceversa, estos se modifican en la linea 84, 104 y 138; donde se muestra(**_del usuario depende cuantos bins colocar en cada uno de estos, ya que dependera de la señal utilizada_**):
```python
#histograma por formula(linea 84)
num_bins = "numero deseado de bins sin comillas"

#histograma por codigo(linea 104)
plt.hist(valores, bins="numero deseado de bins sin comillas")

#funcion de probabilidad por codigo(linea 138)
count, bins = np.histogram(valores, bins="numero deseado de bins sin comillas", density=True)
```
6. Para la parte de los ruidos, el valor de SNR depende de la variacion estandar que se le quiera permitir a la señal del ruido, ya que esta se normaliza o estandariZa de forma automatica
<br>
   a. Para el ruido gaussiano (linea 162)
   
 ```python
noise_level = np.std(valores)*"valor de desviacion estandar que se desea sin comillas"
```
   b. para el ruido impulso se debe poner el nivel del ruido que se desea y la probabilidad que ocurra un impulso(linea 235 y linea 249/251)
```python
#linea 235
def add_impulse_noise(signal, noise_level="nivel de ruido deseado sin comillas", impulse_probability="probabilidad de que un impulso ocurra sin comillas"):
#lineas 249 y 251
noise_level = "nivel de ruido deseado sin comillas"

impulse_probability = "probabilidad de que un impulso ocurra sin comillas"
```
   c. para ruido artefacto tambien se modifica la desviacion estandar, que es com un tipo de tolerancia que tiene la onda para producir el ruido (linea 313)
```python
ruido = np.random.normal(0, "valor de desviacion estandar que se desea sin comillas", tamaño)  
```
### Uso 
Por favor, cite este artículo:
<br>
Goldberger, A., Amaral, L., Glass, L., Hausdorff, J., Ivanov, P. C., Mark, R., ... & Stanley, H. E. (2000). PhysioBank, PhysioToolkit, and PhysioNet: Components of a new research resource for complex physiologic signals. Circulation [Online]. 101 (23), pp. e215–e220
### Informacion de contacto
est.fabiana.lopez@unimilitar.edu.co
<br>
est.tania.sandoval@unimilitar.edu.co
   








