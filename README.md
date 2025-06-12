# TFM
Este repositorio es para el TFM del Máster en Bioinformática.

## Resumen
La criotomografía electrónica es la técnica más utilizada para la visualización *in situ* de estructuras celulares, ya que mediante la inclinación de la rejilla del microscopio electrónico permite obtener diferentes imágenes de la misma muestra, que luego se alinean para dar lugar a un tomograma 3D.

No obstante, presenta dificultades a la hora de interpretar los tomogramas obtenidos debido al bajo ratio señal-ruido y a la alta densidad molecular, lo que dificulta la detección de partículas. La estrategia más empleada para ello, *template matching*, basada en la búsqueda de una plantilla en el tomograma, tiene un alto coste computacional y no permite alcanzar una caracterización completa.

Por este motivo, se está evolucionando hacia estrategias basadas en redes neuronales convolucionales, más concretamente en la arquitectura *U-Net*, diseñada para la segmentación de imágenes biomédicas. El reto más relevante de este enfoque es la necesidad de tomogramas anotados para entrenar la red, lo que ha dado lugar al desarrollo de *software* diseñado para generar y anotar tomogramas sintéticos, como es el caso de **PolNet**. PolNet es un paquete de Python que se enfoca en la simulación de estructuras celulares de bajo nivel, como membranas, proteínas y filamentos, a partir de modelos matemáticos.

En este trabajo, se utilizó PolNet para la generación de un dataset de tomogramas sintéticos de vesículas sinápticas aisladas de cerebro de ratón, basándonos en el estudio de *Wang et al.* (2024). Tras la generación de los tomogramas, se emplearon para entrenar un modelo de **nnUNet**, una variante de *U-Net* que ajusta automáticamente sus hiperparámetros en función de las características de los datos de entrada.

El objetivo del modelo generado fue la segmentación de membranas y proteínas de membrana tanto en los tomogramas sintéticos como en los reales del artículo de referencia, por lo que se evaluó con ambos tipos. El modelo mostró un buen rendimiento en los tomogramas sintéticos. Sin embargo, debido a las diferencias significativas con respecto a los tomogramas reales, su desempeño en estos últimos fue notablemente inferior.

Los resultados sugieren la necesidad de mejorar este tipo de herramientas de generación de tomogramas sintéticos para adaptarlos todavía más a las características de los tomogramas reales. De esta forma, se logrará que los modelos de segmentación entrenados con datos sintéticos puedan generalizar y analizar de manera efectiva datos experimentales, superando las limitaciones actuales y acelerando la caracterización de estructuras celulares *in situ*.

## Referencias
Wang,C.,Jiang, W., Leitz, J., et al. (2024). Structure and topography of the synaptic V-ATPase-synaptophysin complex. Nature, 631, 899-904. [https://doi.org/10.1038/s41586-02407610-x](https://doi.org/10.1038/s41586-024-07610-x)
