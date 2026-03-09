# TelecomX - Analisis de Evasion de Clientes

## Descripcion del Proyecto

Este proyecto forma parte del Challenge de Data Science de Alura Latam. El objetivo es analizar el comportamiento de los clientes de TelecomX para identificar los factores asociados a la evasion (churn), es decir, la decision de un cliente de cancelar sus servicios.

A traves de tecnicas de ETL, analisis exploratorio de datos (EDA) y visualizaciones estrategicas, se busca entregar informacion util que permita al equipo de Data Science desarrollar modelos predictivos y estrategias de retencion.

## Estructura del Proyecto

```
TelecomX/
├── TelecomX_LATAM.ipynb      # Notebook principal con todo el analisis
├── TelecomX_Data.json        # Dataset original (cargado desde API)
├── TelecomX_diccionario.md   # Diccionario de datos
└── README.md                 # Este archivo
```

## Tecnologias Utilizadas

- Python 3.x
- Pandas
- Matplotlib
- Seaborn
- Requests

## Instalacion y Requisitos

Para ejecutar este proyecto necesitas tener instalado Python 3.x. Luego instala las dependencias con:

```bash
pip install pandas matplotlib seaborn requests
```

## Como Ejecutar el Proyecto

1. Clona o descarga este repositorio
2. Abre el archivo `TelecomX_LATAM.ipynb` en Google Colab o Jupyter Notebook
3. Ejecuta las celdas en orden desde la seccion de Extraccion hasta el Informe Final

No es necesario descargar el dataset manualmente. Los datos se cargan directamente desde la siguiente URL:

```
https://raw.githubusercontent.com/ingridcristh/challenge2-data-science-LATAM/refs/heads/main/TelecomX_Data.json
```

## Etapas del Analisis

**1. Extraccion**
Carga de datos desde la API publica mediante la libreria requests. Conversion del JSON a un DataFrame de pandas para su manipulacion.

**2. Transformacion**
- Normalizacion de columnas anidadas con json_normalize()
- Exploracion de tipos de datos y estructura del dataset
- Deteccion y correccion de valores nulos, duplicados e inconsistencias
- Creacion de la columna Cobro_Diario a partir de la facturacion mensual
- Estandarizacion de variables binarias (Yes/No a 1/0)
- Traduccion de columnas al español para mayor claridad

**3. Carga y Analisis**
- Analisis descriptivo con estadisticas generales
- Visualizacion de la distribucion de evasion
- Analisis de evasion por variables categoricas (genero, tipo de contrato, metodo de pago)
- Analisis de evasion por variables numericas (meses de contrato, cobro mensual, cobro total)
- Matriz de correlacion entre variables (analisis extra)

**4. Informe Final**
Resumen ejecutivo con introduccion, hallazgos, conclusiones y recomendaciones estrategicas para reducir la tasa de evasion.

## Principales Hallazgos

- Los clientes con contrato mensual tienen una tasa de evasion significativamente mas alta que los de contratos anuales o bianuales
- Los clientes con menos meses de contrato son los mas propensos a abandonar el servicio
- El cobro mensual elevado esta correlacionado con mayor evasion, especialmente en clientes con servicio de fibra optica
- Los metodos de pago electronicos (cheque electronico) presentan mayor tasa de evasion
- Los clientes sin servicios adicionales (seguridad online, soporte tecnico) evaden mas frecuentemente

## Recomendaciones

- Incentivar contratos de largo plazo con beneficios o descuentos para nuevos clientes
- Revisar la estructura de precios del servicio de fibra optica
- Ofrecer paquetes de servicios adicionales a menor costo como estrategia de retencion
- Fortalecer la atencion en los primeros meses de vida del cliente

## Autor

Proyecto desarrollado como parte del Challenge 2 de Data Science - Alura Latam
