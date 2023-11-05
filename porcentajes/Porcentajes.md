# Caso de uso: Diferencia entre media de los porcentajes y porcentaje promedio en BI

## Teoría

Para demostrar que el promedio de los porcentajes es distinto de El promedio ponderado de los porcentajes, primero necesitamos entender qué significa cada uno.

### Promedio de los porcentajes

**El promedio de los porcentajes se calcula sumando todos los porcentajes y dividiendo por el número total de porcentajes**.  

Formalmente, si tenemos n cantidades $a_i$ con i en el rango [1, n], y cada cantidad tiene un porcentaje asociado $p_i$, entonces:

El **promedio de los porcentajes** es: $$\frac{1}{n} \sum_{i=1}^n​p_i​$$

Por ejemplo, supongamos que tenemos 3 cantidades: 100, 200 y 300. Y sus respectivos porcentajes son 10%, 20% y 30%.

El **promedio de los porcentajes** sería: $$\frac{30\%+20\%+30\%}{3}​=20\%$$

### Promedio ponderado de los porcentajes

**El promedio ponderado de los porcentajes se calcula sumando todas las cantidades (cada una multiplicada por su respectivo porcentaje) y dividiendo por la suma total de las cantidades, o equivalentemente, sumando los valores correspondientes a los porcentajes y dividiendo por la suma total de las cantidades**.

Formalmente, si tenemos n cantidades $a_i$ con i en el rango [1, n], y cada cantidad tiene un porcentaje asociado $p_i$, entonces:

El **promedio ponderado de los porcentajes** es: $$\frac{\sum_{i=1}^na_i·​p_i​}{\sum_{i=1}^na_i}​$$

Supongamos que tenemos el mismo ejemplo anterior, es decir, 3 cantidades: 100, 200 y 300. Y sus respectivos porcentajes son 10%, 20% y 30%.

El **promedio ponderado de los porcentajes** sería: $$\frac{100⋅10\%+200⋅20\%+300⋅30\%}{100+200+300}​=\frac{10+40+90}{600}=\frac{140}{600}=23.33\%$$

### Corolario sobre el promedio de los porcentajes y el promedio ponderado de los porcentajes

El promedio de los porcentajes (en nuestro ejemplo, un **20%**) es diferente al promedio ponderado de los porcentajes (en nuestro ejemplo, un **23.33%**).

**El promedio y el promedio ponderado de los porcentajes coinciden, si y solo si, los porcentajes se refieren a las mismas cantidades totales**.

Ejemplo:

$$\frac{30\%+20\%+30\%}{3}​=20\%$$

$$\frac{100⋅10\%+100⋅20\%+100⋅30\%}{100+100+100}​=\frac{10+20+30}{300}=\frac{60}{300}=20\%$$

**_Conclusión_**: **Como el promedio de los porcentajes cubre solo 1 caso, de $\infty$ posibles y el promedio ponderado de los porcentajes cubre todos los casos, entonces siempre se debe utilizar el promedio ponderado de los mismos**.

Imaginemos que tenemos que hacer una macedonia y solo nos dan los % de las frutas sin procesar, es decir, sin saber nada del peso, ni del volumen, ni de inguna otra magnitud utilizada.  

* 43% de una manzana  
* 82% de una pera  
* 63% de una sandía  
* 71% de un limón  
* 23% de un plátano  

y concluimos que hemos uilizado el:

$$\frac{43\%+82\%+63\%+71\%+23\%}{5}=\frac{282\%}{5}=56,4\%$$

es decir, pretenderíamos haber consumido el **56,4%** de las frutas, sin atender a las magnitudes originales, ya sea peso o volumen, o cualquier otra.

🍏🍐🍉🍋🍌

Obviamente, está mal calculado, ¿no?.😜

## Análisis

Imaginemos el siguiente ejemplo, para considerar el conjunto del problema:

Una empresa multinacional dedicada al dropshipping, quiere controlar los artículos más demandados mensualmente. Además, de forma muy dinámica, cada mes, crea y/o elimina referencias de su catálogo.

Esta empresa quiere saber cuál es el % de artículos más demandados, teniendo datos de enero a julio.

El año 2023 tiene los siguientes datos:

| Mes | nº artículos más demandados | nº artículos catálogo | indicador |
| :-: | --------------------------: | --------------------: | --------: |
| ene | 1.904                       | 11.204                | 16,99%    |
| feb | 1.434                       | 11.108                | 12,91%    |
| mar | 1.576                       | 12.226                | 12,89%    |
| abr | 1.350                       | 11.030                | 12,24%    |
| may | 1.540                       | 11.318                | 13,61%    |
| jun | 1.320                       | 11.770                | 11,21%    |
| jul | 1.098                       | 11.216                | 9,79%     |

% total acumulado calculado intuitívamente (promedio de los porcentajes), que utiliza la dirección (actualmente) es:

$$\frac{16,99\%+12,91\%+12,89\%+12,24\%+13,61\%+11,21\%+9,79\%}{7}=\frac{89,64}{7}=12,81\%$$ 

Hemos visto, en la teoría, que esto es un _error matemático_.

El _promedio ponderado de los porcentajes es correcto matemáticamente_:

$$\frac{1.904+1.434+1.576+1.350+1.540+1.320+1.098}{11.204+11.108+12.226+11.030+11.318+11.770+11.216}​=\frac{10.222}{79.872}=12,80\%$$

Pero es dicutible el valor de la información mostrada. Por otra parte, observamos que la dirección hace cálculos con los indicadores (%), olvidando las magnitudes de las que derivan, cuando lo que debiera hacer es obtener los indicadores para saber que les sucede (o puede suceder) a las magnitudes.

Imaginemos lo siguiente, para ver lo absurdo de operar con los indicadores y no con las magnitudes:

Producción (normal) de niños por mujer y mes: $$\frac{1}{9}=11,11\%$$

Entonces 9 mujeres pueden producir 1 niño al mes, porque $$9·(\frac{1}{9})=100\%$$

👶👶👶

Lo cual, es absurdo, ¿no?.😜

Además los valores se construyen con conjuntos restringidos. Es decir, si consideramos el período de enero a julio, no contaremos como uno de los _artículos más demandados_ más de una vez, es decir, si un artículo fue más demandado el mes de enero y el de abril, solo lo consideraremos una vez. Además un artículo que formó parte del catálogo en enero, pero no a partir de febrero, forma parte de catálogo total, de enero a julio, pero solo una vez.  

O sea, estas cantidades no se pueden obtener de ninguna operación matemática, a partir de las magnitudes expresadas anteriormente, sino por restricciones sobre la BD original.

Con lo cuál, la empresa nos proporciona los siguientes valores acumulados:

nº artículos más demandados = 6.368  
nº artículos catálogo       = 16.714  

y calculando el porcentaje: $$\frac{6.368}{16.714}=38,10\%$$  

¡¡¡Oh Diós mío, ¿¿¿qué es esto???!!!.😮😮😮 Pues, estimado/a lector/a, esto es la **_conjetura FG_** en acción:

> **_La vida es como una caja de bombones, nunca sabes lo que te va a tocar  
(Forrest Gump)_**

Lo que ha sucedido es que si se tuviesen en cuenta las restricciones (en el período seleccionado), en el cual que hemos considerado el cálculo, este sería el promedio ponderado de los porcentajes. Pero con las restricciones, que hemos contemplado, se ha complicado el cálculo.

La pregunta que nos hacemos es: ¿Este propedio ponderado de magnitudes acumuladas sirve para algo (a parte de para jugar con los números)?. Antes de responder pensemos en el negocio de nuestro cliente y lo que realmente quiere conseguir 🤔.

En este momento consideramos el primer precepto de la 4ª Revolución Industrial: **"El cliente en el centro"**.👈

Nuestro cliente quiere ver: _La evolución de las magnitudes (no de los indicadores, esto, como hemos visto, sería un error)_. 

Para ello, vamos a introducir el concepto de **variación en el crecimiento de las magnitudes**. 

Para hacer este cálculo, nos trasladamos al futuro e imaginamos los valores hasta el 31 de diciembre de 2024. Ahora estamos en noviembre de 2023.

Además, consideremos la siguiente fórmula para calcula la variación de la magnitid:

$$Variación=100+((\frac{V_2 - V_1}{V_1})·100)$$

- si Variación < 100, hemos decrecido
- si Variación = 100, nos hemos mantenido igual
- si Variación > 100, hemos crecido

**_Nº artículos más demandados_** 

- **_¿Cómo se ha comportado de enero a junio de 2.023?_**
- $V_1$=1.904
- $V_2$=1.320

$$Variación=100+((\frac{V_2 - V_1}{V_1})·100)=$$
$$100+((\frac{1.320 - 1.904}{1.904})·100)=$$
$$100+((\frac{-584}{1.904})·100)=$$
$$100+(-30,67)\%=$$
$$69,33\%$$ 

**_Resultado_**: el nº artículos más demandados **_se ha reducido en un 30,67%, al 69,33%_** 👈 **_de enero a junio de 2.023_**

- **_¿Cómo se ha comportado de enero a diciembre de 2.023?_**
- $V_1$=1.904
- $V_2$=1.549

$$Variación=100+((\frac{V_2 - V_1}{V_1})·100)=$$
$$100+((\frac{1.549 - 1.904}{1.904})·100)=$$
$$100+((\frac{-355}{1.904})·100)=$$
$$100+(-18,64)\%=$$
$$81,36\%$$ 

**_Resultado_**: el nº artículos más demandados **_se ha reducido en un 18,64%, al 81,36%_** 👈 de enero a diciembre de 2.023, es decir, **_el año 2.023_**

- **_¿Cómo se ha comportado de enero a junio de 2.024?_**
- $V_1$=1.704
- $V_2$=1.120

$$Variación=100+((\frac{V_2 - V_1}{V_1})·100)=$$
$$100+((\frac{1.120 - 1.704}{1.704})·100)=$$
$$100+((\frac{-584}{1.704})·100)=$$
$$100+(-34,27)\%=$$
$$65,73\%$$ 

**_Resultado_**: el nº artículos más demandados **_se a reducido en un 34,27%, al 65,73%_** 👈 **_de enero a junio de 2.024_**

- **_¿Cómo se ha comportado el 2.024?_**
- $V_1$=1.704
- $V_2$=1.349

$$Variación=100+((\frac{V_2 - V_1}{V_1})·100)=$$
$$100+((\frac{1.349 - 1.704}{1.704})·100)=$$
$$100+((\frac{-355}{1.704})·100)=$$
$$100+(-20,83)\%=$$
$$79,17\%$$ 

**_Resultado_**: el nº artículos más demandados **_se ha reducido en un 20,83%, al 79,17%_** 👈 de enero a diciembre de 2.024, es decir, **_el año 2.024_**

- **_¿Cómo se ha comportado del 2.023 al 2.024?_**
- $V_1$=1.904
- $V_2$=1.349

$$Variación=100+((\frac{V_2 - V_1}{V_1})·100)$$
$$=100+((\frac{1.349 - 1.904}{1.904})·100)$$
$$=100+((\frac{-555}{1.904})·100)$$
$$=100+(-29,15)\%$$
$$=70,85\%$$

**_Resultado_**: el nº artículos más demandados **_se ha reducido en un 29,15%, al 70,85%_** 👈 de enero de 2.023 a diciembre de 2.024, es decir, **_del año 2.023 al 2.024_** 

**_Nº artículos catálogo_**       

- **_¿Cómo se ha comportado de enero a junio de 2.023?_**
- $V_1$=11.204
- $V_2$=11.770

$$Variación=100+((\frac{V_2 - V_1}{V_1})·100)=$$
$$100+((\frac{11.770 - 11.204}{11.204})·100)=$$
$$100+((\frac{566}{11.204})·100)=$$
$$100+(5,05)\%=$$
$$105,05\%$$ 

**_Resultado_**: el nº artículos más demandados **_se ha incrementado en un 5,05%, al 105,05%_** 👈 **_de enero a junio de 2.023_**

- **_¿Cómo se ha comportado de enero a diciembre de 2.023?_**
- $V_1$=11.204
- $V_2$=12.301

$$Variación=100+((\frac{V_2 - V_1}{V_1})·100)=$$
$$100+((\frac{12.301 - 11.204}{11.204})·100)=$$
$$100+((\frac{1.097}{11.204})·100)=$$
$$100+(9,79)\%=$$
$$109,79\%$$ 

**_Resultado_**: el nº artículos más demandados **_se ha incrementado en un 9,79%, al 109,79%_** 👈 de enero a diciembre de 2.023, es decir, **_el año 2.023_**

- **_¿Cómo se ha comportado de enero a junio de 2.024?_**
- $V_1$=9.004
- $V_2$=6.570

$$Variación=100+((\frac{V_2 - V_1}{V_1})·100)=$$
$$100+((\frac{6.570 - 9.004}{9.004})·100)=$$
$$100+((\frac{-2.434}{9.004})·100)=$$
$$100+(-27,03)\%=$$
$$72,97\%$$ 

**_Resultado_**: el nº artículos más demandados **_se a reducido en un 27,03%, al 72,97%_** 👈 **_de enero a junio de 2.024_**

- **_¿Cómo se ha comportado el 2.024?_**
- $V_1$=9.004
- $V_2$=4.101

$$Variación=100+((\frac{V_2 - V_1}{V_1})·100)=$$
$$100+((\frac{4.101 - 9.004}{9.004})·100)=$$
$$100+((\frac{-4.903}{9.004})·100)=$$
$$100+(-54,45)\%=$$
$$45,55\%$$ 

**_Resultado_**: el nº artículos más demandados **_se ha reducido en un 54,45%, al 45,55%_** 👈 de enero a diciembre de 2.024, es decir, **_el año 2.024_**

- **_¿Cómo se ha comportado del 2.023 al 2.024?_**
- $V_1$=11.204
- $V_2$=4.101

$$Variación=100+((\frac{V_2 - V_1}{V_1})·100)$$
$$=100+((\frac{4.101 - 11.204}{11.204})·100)$$
$$=100+((\frac{-7.103}{11.204})·100)$$
$$=100+(-63,40)\%$$
$$=36,60\%$$

**_Resultado_**: el nº artículos más demandados **_se ha reducido en un 63,40%, al 36,60%_** 👈 de enero de 2.023 a diciembre de 2.024, es decir, **_del año 2.023 al 2.024_** 

**_Análisis de los resultados:_**

1. La deflación de 2024, ha reducido los pedidos, lo cual nos obliga a optimizar el stock de productos. Lo cual implica un catálogo menor (optimizado)
2. Nos interesa incrementar productos muy demandados en nuestro catálogo, de manera que la rotación de nuestro stock sea muy alta
3. Nos interesa eliminar de nuestro catálogo referencias con una demanda inferior y agregar artículos con muy alta rotación

| Período       | Artículos con alta demanda | Catálogo | Valoración |
| :-----------: | :------------------------: | :------: | :--------: |
| ene-jun 2.023 | -30,67%                    | +5,05%   | 👎        |
| 2.023         | -18,64%                    | +9,79%   | 👎        |
| ene-jun 2.024 | -34,27%                    | -27,03%  | 👍        |
| 2.024         | -20,83%                    | -54,45%  | 👌        |
| 2.023 - 2.024 | -29,15%                    | -63,40%  | 👍        |

El catálogo se ha incrementado en 2.023, aunque ha disminuido el número de artículos más demandados, o sea, lo hemos hecho muy mal (👎).

El primer semestre de 2.024, aunque se ha continuado reduciendo el nº de artículos más demandados, se ha disminuido mucho el catálogo, o sea, estamos reaccionando adecuadamente (👍).

El año 2.024, en su conjunto, hemos reducido a menos de la mitad nuestro catálogo y hemos reducido mucho el ritmo de decrecimiento el nº de artículos más demandados, o sea, estamos reaccionando perfectamente (👌).

En conjunto, gracias a las acciones correctivas que nos han permitido tomar estos indicadores, estamos reaccionando adecuadamente (👍).

Ahora recordemos el indicador que tenemos aparcado: el promedio ponderado de los valores acumulados. Recordemos que para el 2.023 teníamos:

- Nº artículos más demandados = 6.368  
- Nº artículos catálogo       = 16.714  

y calculando el porcentaje: $$\frac{6.368}{16.714}·100=38,10\%$$  

Para el 2.024 tenemos:

- Nº artículos más demandados = 5.840  
- Nº artículos catálogo       = 14.873  

y calculando el porcentaje: $$\frac{5.840}{14.873}·100=39,27\%$$ 

Lo cual nos indica que, tal como intuímos con el el indicador de la variación, estamos aumentado el peso de los artículos con más demanda en nuestro catálogo, al tiempo que disminuimos el catálogo (👍).

Pero, ¿cómo podemos presentar esta información de manera que sea inteligible? 😬

Primero, **cambiamos** el **sobrero de Matemático** por el **sombrero de Analista de Datos**.

**Diseño dimensional**:

- **_Dimensión de Tiempo_**: Fecha (granularidad de año y mes)  
- **_Dimensión de Referencias_**: No incluida en este ejemplo (nos la tenemos que creer). En esta tabla estarán todos los artículos, vivos o muertos, es decir, que formen o hayan formado parte del catálogo (en el período considerado).
- **_Hechos agregados_**: Fecha, nº artículos más demandados, nº artículos de catalogo.
- **_Hechos agregados anual_**: Fecha, nº artículos más demandados acumulado, nº artículos de catalogo acumulado.

**_¡Atención!_**: La granularidad de la dimensión relacionada, coincide con la granularidad de los hechos y no se relacionan dos tablas de hechos directamente (axiomas del diseño dimensional).

Mostraremos en forma de histograma lo siguiente:

| **_Año_**   | **_Mes_** | indicador |
| :---------: | :-------: | --------: |
| **_2.023_** | **_ene_** | 16,99%    |
| **_2.023_** | **_feb_** | 12,91%    |
| **_2.023_** | **_mar_** | 12,89%    |
| **_2.023_** | **_abr_** | 12,24%    |
| **_2.023_** | **_may_** | 13,61%    |
| **_2.023_** | **_jun_** | 11,21%    |
| **_2.023_** | **_jul_** | 9,79%     |
| ...         | ...       | ...       |

y lo siguiente (conmutadamente):

| **_Año_**   | **_Mes_** | nº artículos más demandados | nº artículos catálogo | 
| :---------: | :-------: | --------------------------: | --------------------: |
| **_2.023_** | **_ene_** | 1.904                       | 11.204                |
| **_2.023_** | **_feb_** | 1.434                       | 11.108                |
| **_2.023_** | **_mar_** | 1.576                       | 12.226                |
| **_2.023_** | **_abr_** | 1.350                       | 11.030                |
| **_2.023_** | **_may_** | 1.540                       | 11.318                |
| **_2.023_** | **_jun_** | 1.320                       | 11.770                |
| **_2.023_** | **_jul_** | 1.098                       | 11.216                |
| ...         | ...       | ...                         | ...                   |


De esta manera el usuario puede percibir (de manera muy intuitiva como evolucionan las magnitudes y el porcentaje ponderado relacionado)

En un lugar destacado mostraremos el promedio ponderado de las magnitudes (calculadas mensualmente) como un velocímetro:

**_Promedio ponderado del indicador=12,80\%_**  

**_Las propiedades de El promedio ponderado del indicador desaparecen en el año, es decir, sirven para comparar meses, pero no años._**. Esto no quiere decir que no se pueda analizar, por ejemplo, el último mes de 2.023 y el primero de 2.024, o el mes de marzo de 2.023 y el mismo mes de 2.024.

**_Nota muy importante_**: Para poder mostrar este valor debemos tener un paso ETL que nos genere una tabla con los valores agregados mensuales.

En un lugar destacado, pero en texto, y con algún tipo de texto explicativo mostramos:

- **_Promedio ponderado absoluto del período_**  
- **_Variación del nº artículos más demandados_**  
- **_Variación del nº artículos catálogo_**

## Proto BI

Para montar el prototipo utilizaremos los siguientes recursos:

1. Tabla de referencias: No necesario para el proto.
2. **_Tabla de hechos agregada_**: En formato CSV (recurso descargable desde el repositorio).
3. **_Tabla de hechos agregada anual_**: En formato CSV (recurso descargable desde el repositorio).
4. **_Power BI Desktop_**: Recurso descargable gratuitamente, desde la web de Microsoft.

La dimensión de tiempo la montaremos automáticamente en PBI Desktop.

![Modelo de datos del proto](https://i.imgur.com/u8HTWX3.png)
_Modelo de datos del proto_

La conmutación de los visuales y el popup informatico se hará de la manera estándard, con bookmarks.

![Indicadores](https://i.imgur.com/dAQEJM6.png)  
_Indicadores_

![Valores](https://i.imgur.com/8LGMwzb.png)  
_Valores_

Al promedio ponderado acumulado le llamaremos "Indicador acumulado", para simplificar.

A la variación del catálogo le llamaremos "Variación catálogo", para simplificar.

A la variación del nº artículos más demandados le llamaremos "Variación catálogo más demandado", para simplificar.

**Comprobación del modelo teórico con el resultado del proto**

**_Indicador acumulado calculado para el año 2.023_**:

$$\frac{6.368}{16.714}·100=38,10\% => perfecto$$

**_Indicador acumulado calculado para el año 2.024_**:

$$\frac{5.840}{14.873}·100=39,27\% => perfecto$$ 

**_Variaciones de las magnitudes_**

| Período       | Artículos con alta demanda | Catálogo | Comprobación |
| :-----------: | :------------------------: | :------: | :----------: |
| ene-jun 2.023 | -30,67%                    | +5,05%   | => perfecto  |
| 2.023         | -18,64%                    | +9,79%   | => perfecto  |
| ene-jun 2.024 | -34,27%                    | -27,03%  | => perfecto  |
| 2.024         | -20,83%                    | -54,45%  | => perfecto  |
| 2.023 - 2.024 | -29,15%                    | -63,40%  | => perfecto  |

URL del repositorio en GitHub: 

