# Representación y Clustering de Documentos

Este repositorio contiene la implementación de un sistema completo para la representación vectorial de documentos textuales y su posterior agrupamiento mediante técnicas de clustering no supervisado. El proyecto fue desarrollado como parte de las Tareas 3 y 4 del Máster en Investigación en Inteligencia Artificial de la UNED.

## Descripción

El sistema procesa un subconjunto de la colección 20_newsgroup que contiene comentarios sobre noticias de diversos temas organizados en siete categorías. Desarrollamos cuatro tipos de representaciones vectoriales y evaluamos su rendimiento con dos algoritmos de clustering diferentes, analizando cuál ofrece la mejor capacidad para recuperar la estructura temática original.

## Características principales

- **Preprocesamiento avanzado de documentos**:
  - Eliminación de cabeceras y firmas mediante patrones estructurales
  - Tokenización, eliminación de palabras vacías y stemming con algoritmo de Porter
  - Filtrado adicional de caracteres especiales y normalización

- **Representaciones implementadas**:
  - **TF**: Modelo del espacio vectorial con pesos basados en frecuencia absoluta de términos
  - **TF-IDF**: Modelo del espacio vectorial con ponderación por frecuencia inversa del documento
  - **Aditiva**: Suma de vectores GloVe pre-entrenados de 50 dimensiones
  - **Media**: Promedio de vectores GloVe pre-entrenados de 50 dimensiones

- **Algoritmos de clustering**:
  - **K-means**: Como método de partición (k=7)
  - **Clustering Jerárquico Aglomerativo**: Con enlace Ward para minimizar la varianza intra-cluster

- **Evaluación exhaustiva**:
  - Medidas BCubed (Precision, Recall, F-score)
  - Índice Rand Ajustado (ARI)
  - Matrices de confusión para análisis de grupos problemáticos
  - Cálculo de dispersión de categorías entre clusters

## Estructura del repositorio

- `representation.ipynb`: Notebook para la generación de las representaciones (Tarea 3)
- `clustering_kmedias.ipynb`: Notebook para la aplicación de algoritmos de clustering (Tarea 4)
- `resultados/`: Directorio con las representaciones generadas y resultados del clustering
  - `representacion_tf.txt`: Representación TF de los documentos
  - `representacion_tfidf.txt`: Representación TF-IDF de los documentos
  - `representacion_aditiva.txt`: Representación aditiva basada en word embeddings
  - `representacion_media.txt`: Representación media basada en word embeddings
  - `resultados_clustering/`: Resultados de los algoritmos de clustering y evaluaciones
- `graficas/`: Visualizaciones generadas durante el análisis
- `Corpus-representacion/`: Conjunto de datos (subconjunto de 20_newsgroup)

## Resultados principales

- La combinación TF-IDF con Clustering Jerárquico alcanzó el mejor desempeño con un BCubed F-score de 0,397
- El algoritmo Jerárquico superó consistentemente a K-means en todas las representaciones, con una mejora promedio del 14,8%
- Las categorías 'comp.sys.ibm.pc.hardware' y 'talk.politics.guns' resultaron las más difíciles de caracterizar, con dispersión de 0,47 y 0,44 respectivamente
- Identificamos un claro trade-off entre precisión y exhaustividad en las diferentes combinaciones

## Requisitos

- Python 3.8+
- NumPy, Pandas, Matplotlib, Seaborn
- scikit-learn
- NLTK
- gensim

## Instalación

```bash
git clone https://github.com/oddissea/document-clustering.git
cd document-clustering
pip install -r requirements.txt
```

## Uso

1. Para generar las representaciones:
```bash
jupyter notebook representation.ipynb
```

2. Para ejecutar los algoritmos de clustering:
```bash
jupyter notebook clustering_kmedias.ipynb
```

## Licencia

MIT

## Autor

Fernando H. Nasser-Eddine López - fnassered1@alumno.uned.es
