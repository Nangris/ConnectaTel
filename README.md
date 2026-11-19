# ConnectaTel: análisis del uso de llamadas y mensajes

Proyecto del Sprint 6 del bootcamp de Análisis de Datos de TripleTen.

## Objetivo

ConnectaTel es una empresa de telecomunicaciones con operaciones en México y Colombia. Este análisis busca entender cómo usan los clientes las llamadas y los mensajes, detectar comportamientos atípicos e identificar segmentos de clientes, para mejorar la oferta de planes.

## Preguntas de negocio

- ¿Qué segmentos de clientes usan más o menos las llamadas y los mensajes?
- ¿Qué usuarios presentan valores atípicos que puedan indicar comportamientos inusuales o errores de registro?
- ¿Cómo varía el uso según la edad y el tipo de plan?
- ¿Qué patrones pueden ayudar a diseñar mejores planes?

## Datasets

Los archivos fueron proporcionados por TripleTen como parte del proyecto.

| Archivo | Registros | Contenido |
|---|---|---|
| `plans.csv` | 2 planes | Basico y Premium: precio mensual, mensajes, minutos y GB incluidos, y costo por consumo extra |
| `users_latam.csv` | 4,000 usuarios | Edad, ciudad, fecha de registro, plan y fecha de baja |
| `usage.csv` | 40,000 eventos | Llamadas (duración en minutos) y mensajes (longitud en caracteres) del 1 de enero al 30 de junio de 2024 |

## Etapas del análisis

1. **Carga y exploración** de los tres datasets.
2. **Calidad de datos:** nulos, sentinels y fechas fuera de rango.
3. **Limpieza:** reemplazo de sentinels, conversión de fechas y verificación de nulos MAR.
4. **Resumen estadístico** del uso por usuario.
5. **Distribuciones y outliers:** histogramas, boxplots y método IQR.
6. **Segmentación** por nivel de uso y por edad.
7. **Insight ejecutivo** con conclusiones y recomendaciones.

## Principales hallazgos

- **Calidad de datos:** se corrigieron 55 edades registradas como -999, 96 ciudades registradas con un signo de interrogación (`"?"`) en lugar del nombre, 40 fechas de registro en 2026 y 60 registros de uso con valores imposibles (120 minutos y 1490 caracteres). `churn_date` viene en notación científica y no se pudo usar.
- **Uso bajo y homogéneo:** en promedio, cada usuario envía menos de 1 mensaje y habla menos de 4 minutos al mes, sin diferencias por edad, plan ni país.
- **Segmentos:** 73.6% de los usuarios es de uso medio, 19.5% de uso bajo y 7.0% de uso alto. Por edad, 50.4% son adultos, 30.6% adultos mayores y 19.0% jóvenes.
- **Planes:** los clientes Premium pagan más del doble que los Basico, pero no hacen más llamadas ni envían más mensajes. Ningún usuario se acerca a lo que incluye el plan Basico.
- **Recomendación principal:** diferenciar los planes por beneficios que sí se usen, por ejemplo datos móviles, y crear un plan ligero para los clientes de bajo uso.

## Cómo ejecutar el notebook

El notebook lee los datos desde la carpeta `/datasets/`.

### En Google Colab

1. Abre el notebook en Colab: **File → Open notebook → GitHub**, y pega la URL de este repositorio.
2. En el panel de archivos de la izquierda, sube `plans.csv`, `users_latam.csv` y `usage.csv`.
3. Crea una celda al inicio del notebook y ejecuta:
   ```
   !mkdir -p /datasets
   !cp plans.csv users_latam.csv usage.csv /datasets/
   ```
4. Ejecuta todo con **Runtime → Run all**.

### En Jupyter (local)

1. Instala las librerías:
   ```
   pip install pandas numpy seaborn matplotlib jupyter
   ```
2. Copia los tres CSV a una carpeta `/datasets/`, o cambia las rutas `/datasets/...` del notebook por la ubicación de tus archivos.
3. Abre el notebook con `jupyter notebook` y ejecuta todas las celdas.

## Estructura del repositorio

```
├── README.md
└── ConnectaTel_analisis.ipynb
```

## Herramientas

Python · pandas · NumPy · seaborn · matplotlib · Jupyter Notebook

---

Proyecto realizado por Nancy como parte del bootcamp de Análisis de Datos de TripleTen.
