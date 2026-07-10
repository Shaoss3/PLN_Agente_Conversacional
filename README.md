# Agente Conversacional para Admision y Nivelacion de la UG

**Procesamiento de Lenguaje Natural — Trabajo Parcial II**
**Carrera:** Ciencia de Datos e Inteligencia Artificial — Universidad de Guayaquil
**Integrantes:** Caicho Almeida Shanney · Cedeno Pinto Scarlett
**Docente:** Angel Cuenca Ortega

---

## Descripcion del proyecto

Agente conversacional basado en tecnicas clasicas de PLN que identifica la intencion del usuario y devuelve respuestas predefinidas sobre admision y nivelacion de la UG. Utiliza **TF-IDF + similitud coseno** para la deteccion de intenciones y un **corpus de informacion academica** para enriquecer las respuestas con datos reales sobre carreras y facultades. La interfaz de usuario se construye con **Gradio**.

No utiliza deep learning, transformers ni embeddings preentrenados.

---

## Estructura del repositorio

```
PLN_Agente_Conversacional/
│
├── data/
│   ├── intenciones.json          # 22 intenciones con utterances y respuestas predefinidas
│   └── corpus_nivelacion.json    # Corpus con informacion academica oficial de la UG
│
├── src/
│   └── agente_conversacional_ug.ipynb   # Notebook principal (Google Colab)
│
├── informe/
│   └── informe_pln.pdf           # Informe escrito (3-4 paginas)
│
└── README.md
```

---

## Requisitos

El proyecto se ejecuta en **Google Colab** o en cualquier entorno Python 3.8+.

Las bibliotecas necesarias se instalan automaticamente en la primera celda del notebook:

```
nltk
scikit-learn
pandas
gradio
```

---

## Instrucciones de ejecucion

### Opcion 1: Google Colab (recomendada)

1. Abrir el archivo `src/agente_conversacional_ug.ipynb` en Google Colab.
2. Ejecutar todas las celdas en orden: **Runtime → Run all** (o `Ctrl+F9`).
3. La interfaz Gradio se lanzara automaticamente al final del notebook con un enlace publico.

### Opcion 2: Entorno local

```bash
# Clonar el repositorio
git clone https://github.com/Shaoss3/PLN_Agente_Conversacional.git
cd PLN_Agente_Conversacional

# Instalar dependencias
pip install nltk scikit-learn pandas gradio

# Ejecutar el notebook
jupyter notebook src/agente_conversacional_ug.ipynb
```

---

## Funcionamiento del agente

1. El usuario escribe una consulta en la interfaz Gradio.
2. El texto se preprocesa: minusculas, eliminacion de tildes y puntuacion, stopwords y stemming Snowball.
3. Se vectoriza con TF-IDF y se calcula la similitud coseno con todos los utterances.
4. Si la similitud supera el umbral de confianza (0.25), se devuelve la respuesta de la intencion mas similar, enriquecida con informacion del corpus.
5. Si no supera el umbral, se activa la respuesta de fallback.

---

## Fuentes oficiales utilizadas

| Fuente | URL |
|---|---|
| Portal de Admision UG | https://admision.ug.edu.ec/admision/ |
| Pagina de Nivelacion UG | https://admision.ug.edu.ec/nivelacion/ |
| Registro Nacional | https://admision.educacion.gob.ec/ |
| SIUG | https://servicioenlinea.ug.edu.ec/SIUG/Account/Login.aspx |
| Campus Nivelacion | https://campusnivelacion.ug.edu.ec/login/index.php |
| Plataformas Virtuales | https://admision.ug.edu.ec/plataformas-virtuales/ |
| Directrices Nivelacion 2026 | https://admision.ug.edu.ec/Docs/Reg/Normativas/Directrices%20nivelaci%C3%B3n%202026%20CI.pdf |

---

## Metricas de evaluacion

| Metrica | Resultado |
|---|---|
| Accuracy | 100.00% |
| F1-macro | 100.00% |
| Consultas evaluadas | 30 |
| Intenciones definidas | 22 |

Evaluado sobre 30 consultas variadas incluyendo errores tipograficos, variaciones linguisticas y preguntas fuera del dominio.
