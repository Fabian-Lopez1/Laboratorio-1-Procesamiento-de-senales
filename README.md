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

![Senal original](https://drive.google.com/uc?export=view&id=1Nq-gbisaOD_8Kpf-NBYKOK_pXGg7xiUb)

<br>

Una vez se confirmo que la señal se importo de manera correcta a python, se procedio con la primera parte del laboratorio la cual se basa en el estudio estadistico de la señal, en el cual se realizan diferentes medidas estadisticas tanto por formula como por comando de librerias de python; para esta parte es crucial importar las siguientes librerias: matplotlib, numpy, math y scipy

<br>

### Media estadistica
Como su nombre lo dicta es el valor promedio en el que se mantiene la señal(en este caso en unidades de la escala de Voltios), para la parte con formula se uso la siguiente formula y se implemento en el codigo de la siguiente manera:
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
![Histograma](https://drive.google.com/uc?export=view&id=1gH-x2WzdD5oh5uOKuq1KVC9wJTtaKf6D) ![Funcion de probabilidad](https://drive.google.com/uc?export=view&id=1m2sgsltka0-iiEm1dLqA9y7J9f3RD_0r)

## Relacion señal ruido (SNR)
La Relacion señal ruido  es la relación entre la potencia de una señal útil y la potencia del ruido de fondo. Se utiliza para medir la calidad de la señal; un SNR más alto indica una señal más clara y menos afectada por el ruido; se utiliza la siguiente formula:
<br>
![SNR](https://quicklatex.com/cache3/2f/ql_51d12e518023d4d41be035e9f8e68f2f_l3.png)

### Ruido gaussiano 
El ruido gaussiano es un tipo de ruido que tiene una distribución de probabilidad normal (gaussiana), caracterizada por su media y desviación estándar; debido a esto dependiendo de ciertop valor que sera mencionado despues, los valores de SNR cambian dependiendo de cuanta desviacion estandar se le coloque a la ecuacion, los resultados obtenidos fueron: 
<br>
![Gaussiano](https://drive.google.com/uc?export=view&id=1dRuoYXGvYfdgrtF0axQyYVFrbrICOPhz)







