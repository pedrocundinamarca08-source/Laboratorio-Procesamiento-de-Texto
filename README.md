# Laboratorio-Procesamiento-de-Texto
# Laboratorio de Procesamiento de Texto con Python

**Asignatura:** Procesamiento del Lenguaje Natural  
**Estudiante:** Pedro Pascual Murcia Vargas  
**Fecha:** 27/09/2026  
**Notebook principal:** `Untitled0.ipynb`

---

## 1. Descripción del proyecto

Este repositorio contiene el desarrollo de un laboratorio práctico de **Procesamiento de Lenguaje Natural (NLP)** utilizando Python y Google Colab.

El objetivo del trabajo es implementar y analizar diferentes técnicas de procesamiento de texto, desde procedimientos básicos de limpieza y transformación hasta tareas avanzadas mediante modelos basados en Transformers.

El notebook incluye ejemplos ejecutables, resultados y análisis para cada uno de los temas solicitados.

---

## 2. Objetivo general

Implementar diferentes técnicas de procesamiento de lenguaje natural mediante Python para comprender cómo se puede limpiar, analizar, representar, clasificar, interpretar y generar texto utilizando métodos tradicionales y modelos modernos de inteligencia artificial.

### Objetivos específicos

- Normalizar y preparar textos antes de su análisis.
- Aplicar stemming, lematización y eliminación de stopwords.
- Calcular frecuencia de términos e importancia de palabras mediante TF e IDF.
- Identificar categorías gramaticales y relaciones sintácticas.
- Reconocer entidades presentes en un texto.
- Utilizar modelos de lenguaje para generación de texto.
- Implementar sistemas de Question Answering y Summarization.
- Calcular similitud semántica entre oraciones.
- Clasificar textos mediante análisis de sentimiento.
- Traducir automáticamente textos entre idiomas.
- Aplicar técnicas básicas de minería de texto.

---

## 3. Tecnologías y librerías utilizadas

El proyecto fue desarrollado en **Google Colab** utilizando Python.

Principales librerías:

- `NLTK`
- `spaCy`
- `pandas`
- `NumPy`
- `scikit-learn`
- `matplotlib`
- `transformers`
- `sentence-transformers`
- `PyTorch`

También se utilizó el modelo de idioma español:

```text
es_core_news_sm
```

de spaCy.

---

## 4. Instalación

En Google Colab se instalaron las principales dependencias mediante:

```python
!pip -q install nltk spacy scikit-learn pandas matplotlib transformers sentence-transformers
!python -m spacy download es_core_news_sm -q
```

Posteriormente se descargaron recursos de NLTK para tokenización y stopwords.

---

# 5. Desarrollo

## 5.1 Normalización de texto

La normalización permite transformar un texto a un formato uniforme antes de realizar otros análisis.

En el laboratorio se aplicaron las siguientes operaciones:

- Conversión a minúsculas.
- Eliminación de números.
- Eliminación de signos de puntuación y caracteres especiales.
- Eliminación de espacios innecesarios.

### Ejemplo

Texto original:

> La Inteligencia Artificial está CAMBIANDO el mundo!!! En 2026, muchas empresas utilizan IA para analizar información, automatizar procesos y mejorar la toma de decisiones.

Después de la normalización:

> la inteligencia artificial está cambiando el mundo en muchas empresas utilizan ia para analizar información automatizar procesos y mejorar la toma de decisiones

### Análisis

La normalización redujo variaciones innecesarias en el texto y dejó la información en una forma más adecuada para las siguientes etapas del procesamiento.

---

## 5.2 Stemming

El stemming busca reducir diferentes palabras a una raíz común.

Algunos resultados obtenidos fueron:

| Palabra | Stem |
|---|---|
| estudiar | estudi |
| estudiando | estudi |
| estudiante | estudi |
| estudios | estudi |
| computación | comput |
| computadores | comput |
| inteligencia | inteligent |

### Análisis

Se observó que varias palabras relacionadas fueron reducidas a raíces similares. El stemming facilita la agrupación de términos, aunque la raíz resultante no siempre corresponde a una palabra válida del idioma.

---

## 5.3 Eliminación de Stopwords

Las stopwords son palabras muy frecuentes que normalmente aportan poca información al análisis.

El conjunto utilizado contenía **313 stopwords en español**.

Para el texto de prueba, después de eliminar las stopwords se conservaron términos como:

```text
inteligencia
artificial
tecnología
permite
computadoras
realizar
tareas
relacionadas
aprendizaje
análisis
información
```

### Análisis

La eliminación de stopwords redujo palabras frecuentes como artículos, preposiciones y conectores, conservando principalmente términos relacionados con el contenido principal.

---

## 5.4 Term Frequency (TF)

Term Frequency permite determinar con qué frecuencia aparece una palabra dentro de un documento.

La expresión utilizada es:

```text
TF = frecuencia del término / número total de términos
```

Resultados principales:

| Palabra | Frecuencia | TF |
|---|---:|---:|
| inteligencia | 3 | 0.214286 |
| artificial | 3 | 0.214286 |
| permite | 2 | 0.142857 |
| datos | 2 | 0.142857 |
| analizar | 1 | 0.071429 |
| automatizar | 1 | 0.071429 |

### Análisis

Las palabras **inteligencia** y **artificial** presentaron los valores TF más altos, mostrando que son los términos con mayor presencia dentro del documento utilizado.

---

## 5.5 Inverse Document Frequency (IDF)

IDF permite determinar qué tan informativa es una palabra dentro de una colección de documentos.

Los términos presentes en menos documentos reciben un valor mayor, mientras que los términos frecuentes en varios documentos reciben un valor menor.

Algunos valores obtenidos fueron:

| Término | IDF |
|---|---:|
| analizar | 1.693147 |
| aprendizaje | 1.693147 |
| automatizar | 1.693147 |
| cantidades | 1.693147 |
| automático | 1.693147 |
| datos | 1.287682 |
| artificial | 1.287682 |
| inteligencia | 1.287682 |
| permite | 1.287682 |

### Análisis

Los términos que aparecieron solamente en algunos documentos tuvieron un IDF superior. En cambio, palabras compartidas por varios documentos recibieron una ponderación menor.

---

## 5.6 Part-of-Speech Tagging

El etiquetado gramatical permite determinar la función que cumple cada palabra dentro de una oración.

Ejemplo obtenido:

| Palabra | POS | Descripción |
|---|---|---|
| Los | DET | determiner |
| estudiantes | NOUN | noun |
| desarrollan | VERB | verb |
| proyectos | NOUN | noun |
| innovadores | ADJ | adjective |
| utilizando | VERB | verb |
| inteligencia | NOUN | noun |
| artificial | ADJ | adjective |

### Análisis

El modelo identificó correctamente diferentes categorías gramaticales, permitiendo conocer la función de cada término dentro de la oración.

---

## 5.7 Lematización

La lematización transforma las palabras a su forma base teniendo en cuenta información lingüística.

Resultados obtenidos:

| Palabra original | Lema |
|---|---|
| estudiantes | estudiante |
| estaban | estar |
| estudiando | estudiar |
| diferentes | diferente |
| técnicas | técnica |
| desarrollaron | desarrollar |
| proyectos | proyecto |
| tecnológicos | tecnológico |

### Análisis

A diferencia del stemming, la lematización generó formas base lingüísticamente válidas, lo que permite conservar mejor el significado de las palabras.

---

## 5.8 Parsing o análisis sintáctico

El parsing permite identificar las relaciones sintácticas presentes en una oración.

Se analizó:

> El estudiante desarrolla un proyecto de inteligencia artificial.

El modelo identificó **desarrolla** como la raíz (`ROOT`) de la oración.

También se reconocieron relaciones como:

- `estudiante` → sujeto nominal (`nsubj`)
- `proyecto` → objeto (`obj`)
- `inteligencia` → modificador nominal (`nmod`)
- `artificial` → modificador adjetival (`amod`)

### Análisis

Este procedimiento permite entender cómo se relacionan las palabras y cómo se organiza gramaticalmente una oración.

---

## 5.9 Named Entity Recognition (NER)

NER permite identificar automáticamente entidades relevantes dentro de un texto.

En el ejemplo se obtuvieron las siguientes entidades:

| Entidad | Tipo detectado |
|---|---|
| Google | ORG |
| Madrid | LOC |
| La empresa | MISC |
| Colombia | LOC |
| Estados Unidos | LOC |

### Análisis

El modelo reconoció correctamente organizaciones y lugares presentes en el texto. También clasificó la expresión **"La empresa"** como `MISC`, mostrando que los modelos de reconocimiento de entidades pueden presentar resultados imperfectos dependiendo del contexto y del modelo utilizado.

---

## 5.10 Generación de texto usando un LLM

Se utilizó el modelo:

```text
Qwen/Qwen2.5-0.5B-Instruct
```

La instrucción solicitó explicar brevemente qué es la inteligencia artificial y mencionar una aplicación industrial.

El modelo generó una respuesta en la que describió la IA como un campo relacionado con sistemas capaces de aprender, procesar información y tomar decisiones, además de mencionar aplicaciones de automatización en la industria.

### Análisis

El resultado demuestra que un modelo de lenguaje puede interpretar una instrucción escrita en lenguaje natural y producir nuevo contenido relacionado con el contexto solicitado.

---

## 5.11 Question Answering

Para esta tarea se utilizó un modelo BERT entrenado para responder preguntas en español:

```text
mrm8488/bert-base-spanish-wwm-cased-finetuned-spa-squad2-es
```

Pregunta utilizada:

> ¿Cuáles son algunas aplicaciones de la inteligencia artificial?

El modelo extrajo del contexto una respuesta relacionada con:

> reconocimiento de imágenes, procesamiento de lenguaje natural y vehículos autónomos.

### Análisis

El modelo identificó dentro del texto la sección que contenía la respuesta más relacionada con la pregunta. Esta técnica puede utilizarse para consultar documentos de manera automática.

---

## 5.12 Summarization

Para generar resúmenes se utilizó:

```text
facebook/bart-large-cnn
```

El texto original describía diferentes aplicaciones de la inteligencia artificial.

Resumen generado:

> Companies are using AI systems to analyze large amounts of data and improve decision-making. Machine learning algorithms can identify patterns that would be difficult to detect manually.

### Análisis

El modelo logró reducir el texto y conservar ideas principales relacionadas con análisis de datos, toma de decisiones y aprendizaje automático.

---

## 5.13 Sentence Similarity

Se utilizó el modelo multilingüe:

```text
paraphrase-multilingual-MiniLM-L12-v2
```

Se compararon tres oraciones.

Resultados:

| Comparación | Similitud |
|---|---:|
| IA analiza datos vs. IA procesa información | 0.7912 |
| IA analiza datos vs. estudiantes juegan fútbol | 0.0031 |

### Análisis

Las dos primeras oraciones presentaron una similitud alta porque expresaban ideas relacionadas, aunque no utilizaban exactamente las mismas palabras.

La tercera oración presentó una similitud prácticamente nula debido a que trataba un tema diferente.

Esto demuestra que los embeddings permiten comparar el significado semántico y no solamente palabras idénticas.

---

## 5.14 Text Classification

Se realizó una clasificación de sentimiento utilizando:

```text
nlptown/bert-base-multilingual-uncased-sentiment
```

Resultados:

| Texto | Clasificación | Confianza |
|---|---|---:|
| Proyecto funcionando perfectamente | 5 stars | 0.617861 |
| Sistema con muchos errores | 1 star | 0.732770 |
| Producto funcionando de manera normal | 2 stars | 0.372354 |

### Análisis

El modelo diferenció correctamente una opinión claramente positiva de otra claramente negativa. El tercer caso presentó menor confianza, demostrando que las expresiones menos marcadas pueden resultar más difíciles de clasificar.

---

## 5.15 Translation

Se utilizó el modelo:

```text
Helsinki-NLP/opus-mt-es-en
```

Texto original:

> La inteligencia artificial está transformando los procesos industriales.

Resultado:

> Artificial intelligence is transforming industrial processes.

### Análisis

El modelo produjo una traducción coherente del español al inglés conservando el significado general de la oración.

---

## 5.16 Text Generation

Para generación automática de texto se utilizó el modelo:

```text
gpt2
```

Texto inicial:

> Artificial intelligence will transform the future because

El modelo generó automáticamente una continuación de la secuencia.

### Análisis

La generación de texto demuestra cómo un modelo puede utilizar una secuencia inicial como contexto y predecir nuevos tokens para construir contenido adicional.

Debido al carácter probabilístico del modelo, los resultados pueden variar entre ejecuciones.

---

## 5.17 Text Mining

En la sección de minería de texto se combinaron técnicas de normalización, tokenización, eliminación de stopwords y análisis de frecuencias.

Los términos más frecuentes encontrados fueron:

| Palabra | Frecuencia |
|---|---:|
| inteligencia | 2 |
| artificial | 2 |
| automatizar | 2 |
| procesos | 2 |
| analizar | 2 |
| datos | 2 |
| permite | 1 |
| grandes | 1 |
| cantidades | 1 |
| aprendizaje | 1 |

### Análisis

Los términos con mayor frecuencia están directamente relacionados con el tema principal de los documentos: inteligencia artificial, automatización, análisis y datos.

Esto permite observar cómo la minería de texto puede ayudar a identificar rápidamente los conceptos predominantes dentro de una colección documental.

---

# 6. Análisis general de resultados

El laboratorio permitió observar diferentes niveles de procesamiento de lenguaje natural.

Las técnicas de **normalización, stopwords, stemming y lematización** permitieron preparar el texto y reducir variaciones antes del análisis.

Los métodos **TF e IDF** facilitaron la identificación de términos relevantes mediante criterios de frecuencia e importancia documental.

Con **POS Tagging, Parsing y NER** fue posible analizar características lingüísticas más avanzadas, incluyendo categorías gramaticales, relaciones sintácticas y entidades nombradas.

Finalmente, los modelos basados en **Transformers** hicieron posible realizar tareas de mayor complejidad, como:

- Generación de texto.
- Respuesta automática de preguntas.
- Resumen de documentos.
- Similitud semántica.
- Clasificación de sentimiento.
- Traducción automática.

Los resultados obtenidos muestran que el procesamiento de lenguaje natural combina técnicas estadísticas, lingüísticas y modelos de aprendizaje profundo para trabajar con información expresada en lenguaje humano.

---

# 7. Conclusiones

1. El procesamiento de lenguaje natural permite transformar texto no estructurado en información que puede analizarse automáticamente.

2. El preprocesamiento es una etapa fundamental, ya que técnicas como normalización, eliminación de stopwords, stemming y lematización facilitan los análisis posteriores.

3. TF e IDF permiten estudiar la relevancia de las palabras desde perspectivas diferentes: frecuencia dentro de un documento e importancia dentro de una colección.

4. spaCy permitió realizar análisis lingüísticos como POS Tagging, lematización, parsing y reconocimiento de entidades.

5. Los modelos basados en Transformers permitieron resolver tareas avanzadas que requieren una mayor comprensión semántica del texto.

6. La similitud semántica mostró una diferencia clara entre oraciones relacionadas (`0.7912`) y oraciones de temas distintos (`0.0031`).

7. Los resultados también muestran que los modelos no son perfectos. Por ejemplo, algunas entidades o sentimientos pueden ser clasificados de manera inesperada, por lo que los resultados automáticos deben ser interpretados y revisados.

8. En conjunto, las técnicas desarrolladas permiten construir una base para aplicaciones como buscadores inteligentes, análisis de documentos, asistentes virtuales, clasificación de opiniones y sistemas automáticos de consulta.

---

# 8. Modelos utilizados

| Tarea | Modelo |
|---|---|
| Procesamiento lingüístico en español | `es_core_news_sm` |
| Generación con LLM | `Qwen/Qwen2.5-0.5B-Instruct` |
| Question Answering | `mrm8488/bert-base-spanish-wwm-cased-finetuned-spa-squad2-es` |
| Summarization | `facebook/bart-large-cnn` |
| Sentence Similarity | `paraphrase-multilingual-MiniLM-L12-v2` |
| Text Classification | `nlptown/bert-base-multilingual-uncased-sentiment` |
| Translation | `Helsinki-NLP/opus-mt-es-en` |
| Text Generation | `gpt2` |

---




## Autor

**Pedro Pascual Murcia Vargas**

Laboratorio académico de Procesamiento del Lenguaje Natural.
