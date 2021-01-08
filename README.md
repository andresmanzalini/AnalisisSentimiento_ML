# NLP y Machine Learning


### Analisis de sentimiento a partir de reseñas de peliculas.
 
Utilizando reseñas de peliculas, aplica un analisis subjetivo del sentimiento generado por determinada pelicula, en forma de critica. 
La critica puede ser etiquetada como positiva o negativa, y representa el sentimiento generado por la pelicula.
Ese sentimiento/sensacion, representado en una lista de strings, se tokeniza en palabras y se vectoriza, para homogeneizar la representacion computacional de ese sentimiento.

Luego se entrenan distintos modelos de machine learning, capaces de predecir la polaridad del sentimiento dentro de las sentencias de palabras.




### Especificaciones


Partimos del dataset publico de Kaggle, txt_sentoken 

Se crea un preprocesador, que limpia la data de caracteres raros o nulos, stop words, etc. 
Asi reduce la cantidad de palabras que representan el sentimiento hacia esa pelicula. 
Al aplicar el preprocesamiento, quedan las palabras mas represetantivas de la reseña.


Una vez definido el preprocesador, se hace el procesamiento de la informacion.

Para esto se crea un Pipe, con los siguientes parametros:
	
	. Vectorizador, para tokenizar las palabras y limpiarlas con el preprocesador personalizado. Asi reducimos la dimensionalidad. 

	. Transformador TfidfTransformer(),  para transformar los tokens a una estructura en forma de diccionario, con la palabra y su frecuencia de aparicion.

	. Clasificador con los parametros adecuados
	

El clasificador, ahora con forma de Pipe, recibe como entrada un conjunto de datos X_train de entrenamiento, de la forma lista de strings. Cada fila es una reseña de la pelicula, en formato string; y tambien recibe Y_train, con el tipo de sentimiento asociado a la reseña: positivo o negativo


Ejecuta el entrenamiento, con clasificador.fit(x_train, y_train, params)


Hace la prueba, con clasificador.predict(X_test) y comparando el resultado con Y_test


Se hace una validacion cruzada para comparar resultados.



A partir del analisis de sentimiento de reseñas de pelicuas, se extrapola al analisis de sentimiento a casos generales. Es decir, experiencias de viajes, compras, de alquileres, de ventas, etc.
De esta manera es posible aplicarlo a casos de uso reales, analizando el sentimiento de opiniones de distinto tipo.



## Resultados

      
 			
         precision media |  grid search	  |  seg   | validacion cruzada  

*Maquinas de Soporte de Vectores SVM*

SGDClassifier ->      		0.85  	| 	0.835     |   214s    |  0.84 +- 0.03

SVMClasifier -> 	    	0.845	|	0.82	  |   421s    |  0.83 +- 0.02



*Naive Bayes*

Binomial -> 		        0.8375	|   	0.77	    |   214s  |  0.79 +- 0.03

Multinomial -> 		        0.809 	| 	  0.801	    |   212s  |  0.82 +- 0.06


RandomForest ->         	0.8525  |     0.825     |   1346s |  0.82 +- 0.02




### Fuente

https://arxiv.org/abs/cs/0409058



