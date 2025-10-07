---
{"dg-publish":true,"permalink":"/deteccion-de-anomalias/","dgPassFrontmatter":true}
---


# Que es
Es una técnica que se utiliza para identificar datos que se desvían significativamente del comportamiento normal o esperado de un conjunto de datos.
Como ejemplo, supongamos que tenemos estos datos sobre una aeronave que tiene buenas condiciones (motor).
- $X_1$= calor generado
- $X_2$= intensidad de vibración
![Pasted image 20250902125449.png](/img/user/attachments/Pasted%20image%2020250902125449.png)
**¿Entonces como detectamos la anomalia?**
Estableciendo fronteras de probabilidad y luego estableciendo que si esta probabilidad es menor a un numero llamado épsilon se detectara como anomalía y si esa probabilidad es mayor a ese épsilon entonces será normal.
En el grafico mostrado vemos que el epsilon puede ser la region morada el cual si nuestro dato esta fuero de esto entonces será anomalo, caso contrario sera normal.
![Pasted image 20250902125505.png](/img/user/attachments/Pasted%20image%2020250902125505.png)
# Distribucion gaussiana en deteccion de anomalias
Suponiendo que X es una variable, la probabilidad de X es determinado por un Gaussiano con media $\mu$ y varianza $\sigma^2$ . En donde $\mu$ nos indica la posicion del centro de la campana, y $\sigma$ nos indica que tan ancho es nuestra campana.
![Pasted image 20250902130326.png](/img/user/attachments/Pasted%20image%2020250902130326.png)
Si tuvieramos una sola caracteristica entonces tendriamos lo siguiente. en donde podemos definir que si la probabilidad es menor que epsilon entonces sera un dato anomalo
![Pasted image 20250902131129.png](/img/user/attachments/Pasted%20image%2020250902131129.png)
# Algoritmo deteccion de anomalias
Antes que nada debemos saber que al trabajar con anomalias, lo normal es que encontraremos varias características, y como nos interesa saber la probabilidad para definir fronteras entonces, la probabilidad en conjunto si es que los eventos son independientes es el siguiente:
$$P(x)=P_1*P_2*P_3*\cdots*P_n$$
Sabiendo esto el algoritmo seria de la siguiente forma:
1. Elegir n caracteristicas que puede indicar un ejemplo de anomalia.
2. Encajar los parametros de la media y varianza para cada caracteristicas $\mu_1, \ldots, \mu_n, \sigma_1^2, \ldots, \sigma_n^2$ 
		$$ \mu_j = \frac{1}{m} \sum_{i=1}^m x_j^{(i)} \qquad \sigma_j^2 = \frac{1}{m} \sum_{i=1}^m \left(x_j^{(i)} - \mu_j \right)^2$$
3. Hallar la probabilidad en conjunta $P(x)$. y definir que habra una anomalia si $p(x)<\epsilon$:
$$
p(x) = \prod_{j=1}^{n} p(x_j; \mu_j, \sigma_j^2) = \prod_{j=1}^{n} \frac{1}{\sqrt{2\pi} \sigma_j} \exp\left(-\frac{(x_j - \mu_j)^2}{2\sigma_j^2} \right)
$$
# Ejemplo de deteccion de anomalia
Siguiendo el ejemplo de las variables de $X_1$: calor generado, $X_2$: intensidad de vibración. Se tiene lo siguiente se visualiza como se comporta en conjunta las densidades de probabilidad.
![Pasted image 20250902132704.png](/img/user/attachments/Pasted%20image%2020250902132704.png)
# Sistema practico para detección de anomalias
## Evaluacion continua del algoritmo
- Se sugiere tener una forma de evaluar el algoritmo durante su desarrollo
- Te permite tomar decisiones informadas al cambiar parametros como epsilon o las features.
- Tener una metrica numerica facilita saber si el cambio mejoró o empeoró el desempeño
## Uso de ejemplos etiquetados
- Aunque el algoritmo aprende con datos no etiquetados, es util tener algunos ejemplos etiquetados de anomalias
- Dentro de las cuales se usa y=1, para datos anomalos, y=0 para datos normales
## Conjunto de entrenamiento, validacion y prueba
Si tuvieras 
- 10,000 motores normales (y=0)
- 20 motores defecutosos (y=1)
La distribucion sugerida
- Entrenamiento: 6000 normales
- CV: 2000 normales + 10 anomalias
- Test: 2000 normales + 10 anomalias
En caso tengas menos datos anomalos, entonces puedes optar por solamente el entrenamiento y testeo. Ademas de que es posible que puedas aumentar datos anomalos si entiendes bien el sistema
## Metricas
- Precision, Recall, F1-Score
# Eleccion de caracteristicas
En la deteccion de anomalias, es clave elegir bien las features, ya que no hay etiquetas que ayuden al algoritmo a ignorar o reescalar variables irrelevantes, segun Andrew se sugiere lo siguiente:}
1. Transformar variables para que sean mas gaussianas
2. Analizar errores: Revisar si hay ejemplos mal detectados, y preguntarse hay una nueva caracteristica que me ayudaria a diferenciarlos?
3. Iterar hasta mejorar la separacion entre normal y anomalo

[[Machine Learning\|Machine Learning]]