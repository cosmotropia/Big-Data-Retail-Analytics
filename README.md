# Big-Data-Retail-Analytics

**Retail Analytics Pipeline** — repositorio del proyecto de evaluación del **Módulo 9: Fundamentos de Big Data**, en el marco del curso de Data Science. La consigna plantea un escenario de **RetailMax** (analítica y machine learning sobre operaciones de e‑commerce): construir un flujo escalable con **Apache Spark** que integre ingesta, transformaciones masivas, **Spark SQL**, y **MLlib**, demostrando competencias en RDDs, DataFrames, consultas SQL y modelado distribuido.

Este repositorio implementa ese pipeline sobre datos públicos de comercio electrónico (**dataset Olist**), alineado a los requerimientos del módulo.

---

## Índice

1. [Introducción](#introducción)
2. [Dataset](#dataset)
3. [Estructura del proyecto](#estructura-del-proyecto)
4. [Requisitos previos](#requisitos-previos)
5. [Instalación](#instalación)
6. [Ejecución](#ejecución)
7. [Contenido por lecciones](#contenido-por-lecciones)
8. [Resultados y entregables](#resultados-y-entregables)
9. [Git y publicación en GitHub (cuenta personal)](#git-y-publicación-en-github-cuenta-personal)
10. [Referencias](#referencias)

---

## Introducción

El trabajo cubre, de forma progresiva:

- Fundamentos y motivación de Big Data en retail.
- Configuración de **SparkSession** / **SparkContext** y lectura inicial en **RDD**.
- Manipulación de **RDD** y **Pair RDD** (transformaciones y acciones).
- **DataFrames**, esquemas explícitos, **Spark SQL**, métricas de negocio y persistencia en **Parquet**.
- **MLlib**: *features* (p. ej. `VectorAssembler`, `StringIndexer`), **Regresión Logística** y **K-Means**, evaluación y lectura para marketing.

El notebook principal documenta el linaje de operaciones y el uso del motor Spark en modo local (`local[*]`).

---

## Dataset

Se utiliza el **Brazilian E-Commerce (Olist)**: archivos CSV con órdenes, ítems por orden y reseñas, ubicados en la carpeta `data/`:

| Archivo | Rol |
|--------|-----|
| `olist_orders_dataset.csv` | Pedidos (estado, fechas, etc.) |
| `olist_order_items_dataset.csv` | Líneas de pedido (precio, flete, etc.) |
| `olist_order_reviews_dataset.csv` | Reseñas vinculadas a órdenes |

Los CSV deben mantenerse en `data/` respecto a la raíz del proyecto para que las rutas del notebook funcionen sin cambios.

---

## Estructura del proyecto

Tras clonar, la **raíz del repositorio** (carpeta `Big-Data-Retail-Analytics` por defecto) contiene:

```
Big-Data-Retail-Analytics/    # raíz = root directory del repo
├── README.md
├── requirements.txt
├── main.ipynb                # Notebook único: lecciones 1–5
└── data/                     # CSV Olist + salida Parquet al ejecutar
    ├── olist_orders_dataset.csv
    ├── olist_order_items_dataset.csv
    ├── olist_order_reviews_dataset.csv
    └── orders_final.parquet  # generado al ejecutar la lección 4
```

---

## Requisitos previos

- **Python** 3.10+ (el proyecto se ha usado con 3.12).
- **JDK** instalado y coherente con la versión de Spark/PySpark que instales (Apache Spark requiere JVM).
- Herramienta para abrir **Jupyter** / notebooks (VS Code, Cursor, JupyterLab, etc.).

---

## Instalación

Desde la **raíz del repositorio** (donde está `requirements.txt`):

```bash
git clone git@github.com:cosmotropia/Big-Data-Retail-Analytics.git
cd Big-Data-Retail-Analytics

python3 -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

Si usas el host SSH `github-personal` (cuenta personal frente a la del trabajo), usa el mismo `clone` pero con `git@github-personal:cosmotropia/Big-Data-Retail-Analytics.git` una vez configurado `~/.ssh/config` (ver sección [Git](#git-y-publicación-en-github-cuenta-personal)).

Opcional: si ejecutas el notebook fuera del IDE, instala un kernel Jupyter:

```bash
pip install ipykernel
```

---

## Ejecución

1. Activar el entorno virtual.
2. Abrir `main.ipynb` y ejecutar las celdas **en orden** desde el inicio (sesión Spark, carga de datos, RDD, SQL, ML).

La primera celda crea la `SparkSession` con `master("local[*]")`. Ajusta memoria o `master` solo si tu entorno lo requiere.

---

## Contenido por lecciones

| Lección | Tema principal |
|--------|----------------|
| 1 | Marco Big Data, fuentes retail, arquitectura conceptual |
| 2 | Spark: sesión, RDD, `count` / `take`, validación de datos |
| 3 | RDD / Pair RDD: `map`, `filter`, `flatMap`, `distinct`, `sortBy`, agregaciones |
| 4 | DataFrames, SQL, métricas, exportación **Parquet** |
| 5 | MLlib: pipeline, clasificación, clustering, evaluación |

---

## Resultados y entregables

- **Código**: `main.ipynb` funcional.
- **Datos procesados**: salida Parquet (p. ej. `data/orders_final.parquet`) tras la etapa SQL.
- **Análisis**: consultas agregadas (ventas, distribuciones, *top* órdenes, etc.) y métricas de modelos ML según las celdas finales del notebook.
- **Documentación de entrega**: además de este README, el curso suele pedir **informe en PDF** y material según la rúbrica del módulo 9.

---

## Git y publicación en GitHub (cuenta personal)

Repositorio remoto: **https://github.com/cosmotropia/Big-Data-Retail-Analytics**

Para no mezclar la cuenta de **trabajo** con la **personal**, conviene un host SSH dedicado en `~/.ssh/config`:

```text
Host github-personal
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_personal   # ajusta a tu clave personal
```

Luego el remoto usa `git@github-personal:cosmotropia/Big-Data-Retail-Analytics.git` en lugar de `git@github.com:...`.

**Subir el proyecto por primera vez** (desde la raíz del repo, con `.venv` en `.gitignore`):

```bash
cd Big-Data-Retail-Analytics   # o la ruta local donde tengas el proyecto
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin git@github-personal:cosmotropia/Big-Data-Retail-Analytics.git
git push -u origin main
```

Si ya creaste el repo vacío en GitHub y solo falta enlazar:

```bash
git remote add origin git@github-personal:cosmotropia/Big-Data-Retail-Analytics.git
git push -u origin main
```

*(Si no usas el alias `github-personal`, sustituye por `git@github.com:cosmotropia/Big-Data-Retail-Analytics.git`.)*

---

## Referencias

- [Apache Spark — documentación](https://spark.apache.org/docs/latest/)
- Dataset **Olist**: conjunto público ampliamente usado en competencias y docencia (comercio electrónico Brasil).

---

*Evaluación — Módulo 9: Fundamentos de Big Data · Retail Analytics Pipeline*
