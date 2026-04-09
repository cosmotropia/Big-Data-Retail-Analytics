# Big-Data-Retail-Analytics

**Retail Analytics Pipeline** — proyecto de evaluación del **Módulo 9: Fundamentos de Big Data** (Data Science). Consigna **RetailMax**: pipeline escalable con **Apache Spark** (ingesta, transformaciones, **Spark SQL**, **MLlib**), cubriendo RDDs, DataFrames, SQL y modelado distribuido.

Los datos son el dataset público **Olist** (e‑commerce Brasil), alineado a los requerimientos del módulo.

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
9. [Git (clonar y remoto)](#git-clonar-y-remoto)
10. [Referencias](#referencias)

---

## Introducción

- Marco Big Data aplicado a retail.
- **SparkSession** / **SparkContext**, lectura en **RDD**.
- **RDD** y **Pair RDD** (transformaciones y acciones).
- **DataFrames**, esquemas, **Spark SQL**, métricas y **Parquet**.
- **MLlib** (`VectorAssembler`, `StringIndexer`, regresión logística, K-Means).

El notebook documenta el flujo en modo local (`local[*]`).

---

## Dataset

**Brazilian E-Commerce (Olist)** — CSV en `data/`:

| Archivo | Rol |
|--------|-----|
| `olist_orders_dataset.csv` | Pedidos |
| `olist_order_items_dataset.csv` | Líneas de pedido |
| `olist_order_reviews_dataset.csv` | Reseñas |

Mantén los archivos bajo `data/` respecto a la raíz del repo para que las rutas del notebook coincidan.

---

## Estructura del proyecto

```
Big-Data-Retail-Analytics/
├── README.md
├── requirements.txt
├── main.ipynb
└── data/
    ├── olist_orders_dataset.csv
    ├── olist_order_items_dataset.csv
    ├── olist_order_reviews_dataset.csv
    └── orders_final.parquet   # generado al ejecutar la lección 4
```

---

## Requisitos previos

- Python 3.10+ (probado con 3.12).
- JDK compatible con tu versión de PySpark.
- Editor o entorno con soporte Jupyter (VS Code, Cursor, JupyterLab, etc.).

---

## Instalación

```bash
git clone https://github.com/<tu-usuario>/Big-Data-Retail-Analytics.git
cd Big-Data-Retail-Analytics

python3 -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

Opcional: `pip install ipykernel` si usas kernel Jupyter fuera del IDE.

---

## Ejecución

1. Activar el entorno virtual.
2. Abrir `main.ipynb` y ejecutar las celdas **en orden** (Spark → datos → RDD → SQL → ML).

La sesión usa `master("local[*]")` por defecto.

---

## Contenido por lecciones

| Lección | Tema |
|--------|------|
| 1 | Big Data, fuentes retail, arquitectura |
| 2 | Spark: sesión, RDD, `count` / `take` |
| 3 | RDD / Pair RDD: `map`, `filter`, `flatMap`, `distinct`, `sortBy` |
| 4 | DataFrames, SQL, Parquet |
| 5 | MLlib: pipeline, clasificación, clustering |

---

## Resultados y entregables

- Código: `main.ipynb`.
- Parquet intermedio/final bajo `data/` según el notebook.
- Entrega académica: suele incluir informe PDF según rúbrica del módulo.

---

## Git (clonar y remoto)

- **HTTPS:** `https://github.com/<tu-usuario>/Big-Data-Retail-Analytics.git`
- **SSH (recomendado si usas llave):** `git@github.com:<tu-usuario>/Big-Data-Retail-Analytics.git`

Si tienes **varias cuentas** en GitHub, define en `~/.ssh/config` un `Host` propio (p. ej. `github.com-work`) con `HostName github.com`, `User git` y `IdentityFile` apuntando a la clave correcta; luego usa ese host en la URL del remoto.

Primer push típico:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin git@github.com:<tu-usuario>/Big-Data-Retail-Analytics.git
git push -u origin main
```

---

## Referencias

- [Apache Spark](https://spark.apache.org/docs/latest/)
- Dataset [Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) (Kaggle / repositorio público)

---

*Módulo 9 — Fundamentos de Big Data · Retail Analytics Pipeline*
