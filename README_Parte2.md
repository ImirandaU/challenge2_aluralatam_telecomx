# TelecomX - Parte 2: Prediccion de Evasion de Clientes

## Descripcion del Proyecto

Esta segunda parte del Challenge TelecomX de Alura Latam continua el trabajo realizado en la Parte 1.
Habiendo completado el analisis exploratorio, el rol ahora es de Analista Junior de Machine Learning.

El objetivo es construir modelos predictivos capaces de anticipar que clientes tienen mayor
probabilidad de cancelar sus servicios, entregando informacion accionable para que el equipo
de negocio implemente estrategias de retencion.

## Estructura del Proyecto

```
TelecomX/
├── TelecomX_LATAM.ipynb          # Notebook principal (Parte 1 + Parte 2)
├── TelecomX_Data.json            # Dataset original (cargado desde API)
├── datos_tratados.csv            # Dataset limpio exportado desde Parte 1
├── TelecomX_diccionario.md       # Diccionario de datos
└── README.md                     # Este archivo
```

## Tecnologias Utilizadas

- Python 3.x
- Pandas
- Scikit-learn
- Matplotlib
- Seaborn

## Instalacion y Requisitos

```bash
pip install pandas matplotlib seaborn scikit-learn
```

## Como Ejecutar el Proyecto

1. Clona o descarga este repositorio
2. Abre el archivo `TelecomX_LATAM.ipynb` en Google Colab o Jupyter Notebook
3. Ejecuta todas las celdas en orden desde el inicio
4. El archivo `datos_tratados.csv` se genera automaticamente al final de la Parte 1

## Etapas del Analisis — Parte 2

**1. Preparacion de Datos para Machine Learning**

- Carga del dataset tratado desde la Parte 1
- Eliminacion de columnas irrelevantes (ID_Cliente)
- One-Hot Encoding de variables categoricas con pd.get_dummies()
- Verificacion del balance de clases (73.5% no evadio / 26.5% evadio)
- Normalizacion de variables numericas continuas con StandardScaler
- Division en conjuntos de entrenamiento (80%) y prueba (20%) con stratify

**2. Correlacion y Seleccion de Variables**

- Matriz de correlacion entre variables numericas
- Analisis dirigido: Meses de contrato vs Evasion, Cobro Total vs Evasion
- Identificacion de variables con mayor relacion con el churn

**3. Modelado Predictivo**

Se entrenaron dos modelos de clasificacion:

| Modelo | Normalizacion | Accuracy | F1 Evadio | Recall Evadio |
|---|---|---|---|---|
| Regresion Logistica | Requerida | 79% | 0.57 | 52% |
| Random Forest | No requerida | 78% | 0.54 | 48% |

**4. Evaluacion de Modelos**

Metricas utilizadas: Accuracy, Precision, Recall, F1-score y Matriz de Confusion.

El modelo seleccionado es Regresion Logistica por su mayor Recall en la clase positiva (Evadio),
que es la metrica mas critica en problemas de churn.

**5. Interpretacion de Variables**

- Random Forest: importancia por reduccion de impureza en los arboles
- Regresion Logistica: analisis de coeficientes positivos y negativos

## Principales Hallazgos

El perfil de cliente con mayor riesgo de evasion presenta estas caracteristicas:

- Contrato de tipo mensual (Month-to-month)
- Servicio de Internet por Fibra Optica
- Pago mediante cheque electronico
- Pocos meses de antiguedad en la empresa
- Cobro mensual elevado sin servicios adicionales contratados

Los factores que mas reducen la probabilidad de evasion son la antiguedad del cliente
y los contratos de largo plazo (One year, Two year).

## Recomendaciones Estrategicas

1. Implementar un programa de fidelizacion durante los primeros 6 meses de contrato
2. Incentivar la migracion de contratos mensuales a anuales con descuentos o beneficios
3. Revisar la propuesta de valor del servicio de Fibra Optica
4. Crear campanas dirigidas al segmento que paga por cheque electronico
5. Desplegar el modelo como sistema de alerta temprana, con mejoras futuras via SMOTE

## Proximos Pasos Sugeridos

- Aplicar tecnicas de balanceo de clases como SMOTE para mejorar el Recall
- Realizar busqueda de hiperparametros con GridSearchCV
- Evaluar modelos adicionales como XGBoost o SVM
- Implementar validacion cruzada para resultados mas robustos

## Autor

Proyecto desarrollado como parte del Challenge 2 de Data Science - Alura Latam
