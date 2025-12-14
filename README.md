# edv_trabajofinal_dcortes
# 📊 Análisis de Ciberseguridad Global (2015–2024)

## 📑 TABLA DE CONTENIDOS
1. [🚀 Presentación del proyecto](#-presentación-del-proyecto)
2. [📂 Descripción del Dataset](#-descripción-del-dataset)
3. [🎯 Objetivos e Hipótesis](#-objetivos-e-hipótesis)
4. [📈 Plan de métricas KPI’s](#-plan-de-métricas-kpis)
5. [🔍 EDA: Análisis Exploratorio de Datos](#-eda-análisis-exploratorio-de-datos)
6. [🗂️ DER: Modelo Entidad Relacionales](#-der-modelo-entidad-relacionales)
7. [🥈 Construcción capa Silver](#-construcción-capa-silver)
8. [📊 Conexión y desarrollo en PowerBI](#-conexión-y-desarrollo-en-powerbi)
9. [🧮 Medidas en DAX](#-medidas-en-dax)
10. [✅ Conclusiones](#-conclusiones)

---

# 1. 🚀 Presentación del proyecto
En un entorno digital cada vez más complejo, los ciberataques se han convertido en una amenaza constante para países, industrias y usuarios.  
Este proyecto utiliza análisis de datos para explorar patrones clave de ciberseguridad, identificar dónde y cómo ocurren los ataques, y comprender su impacto real.  

---

# 2. 📂 Descripción del Dataset
**Global Cybersecurity Threats (2015–2024)**  
Fuente: [Kaggle Dataset](https://www.kaggle.com/datasets/atharvasoundankar/global-cybersecurity-threats-2015-2024)

- Filas: ~3 000 incidentes  
- Columnas: 10 variables principales  
- Formato: CSV  
- Países: Alemania, Australia, Brasil, China, EEUU, Francia, Japón, India, Estados Unidos y Rusia  

👉 *Justificación política y social:* Los ciberataques son una amenaza directa para la estabilidad política, económica y social. Este análisis busca identificar patrones útiles para diseñar políticas de ciberdefensa y cooperación internacional.  

### Diccionario de datos
| Columna (Español)        | Columna (Inglés) | Descripción |
|---------------------------|------------------|-------------|
| País                      | Country          | País donde ocurrió el ataque |
| Año                       | Year             | Año del incidente |
| Tipo_Ataque               | Attack_Type      | Clasificación del ataque |
| Fuente_Ataque             | Attack_Source    | Origen del ataque |
| Vulnerabilidad            | Vulnerability    | Vulnerabilidad explotada |
| Industria                 | Industry         | Sector afectado |
| Mecanismo_Defensa         | Defense_Mechanism| Contramedida aplicada |
| Pérdida_Millones_USD      | Loss_Millions_USD| Pérdida económica |
| Usuarios_Afectados        | Users_Affected   | Personas impactadas |
| Tiempo_Resolución_Horas   | Incident_Resolution_Time_Hours | Tiempo de resolución |

---

# 3. 🎯 Objetivos e Hipótesis

### Objetivo general
Desarrollar un análisis de datos y un dashboard interactivo sobre ciberataques globales utilizando BigQuery y Power BI.

### Objetivos específicos
- Analizar patrones de ciberataques en los 10 países.  
- Diseñar métricas clave de desempeño y riesgo.  
- Crear un dashboard interactivo en Power BI.  

### Hipótesis
- 📌 La mayoría de los ataques se concentran en pocos países.  
- 💸 Los ataques más frecuentes generan mayores pérdidas económicas.  
- 👥 Algunas industrias concentran mayor impacto social.  
- 🛡️ Mejores tiempos de respuesta reducen pérdidas económicas promedio.  

---

# 4. 📈 Plan de métricas KPI’s

### Métricas de incidencia

| KPI                              | Descripción                                                       | Cálculo                                                        | Valor Analítico                                     |
|----------------------------------|-------------------------------------------------------------------|----------------------------------------------------------------|-----------------------------------------------------|
| Distribución de ataques por país | Muestra cuántos ataques recibió cada país y qué porcentaje representan del total. | Contar ataques por país y dividir entre el total de ataques. | Permite comparar países y entender la concentración geográfica del riesgo. |
| Total de ataques por año         | Total de incidentes registrados cada año.                         | Sumar todos los ataques reportados en un año.                 | Facilita evaluar tendencias temporales y detectar años críticos. |
| Crecimiento interanual de ataques| Mide la variación porcentual de ataques año contra año.            | (Ataques año actual – año anterior) / año anterior.            | Indica velocidad de incremento o reducción de ciberataques. |
| Distribución de ataques por industria | Ranking de industrias según su nivel de exposición.             | Ataques por industria / total de ataques.                      | Identifica sectores más vulnerables y prioritarios. |

---

### 💸 Métricas económicas

| KPI                                      | Descripción                                        | Cálculo                                   | Valor Analítico                                       |
|------------------------------------------|----------------------------------------------------|-------------------------------------------|-----------------------------------------------------|
| Costo económico por tipo de ataque en cada país | Suma de pérdidas económicas agrupadas por país y por tipo de ataque. | Sumar pérdidas donde coincidan país + tipo de ataque. | Permite identificar amenazas con mayor impacto financiero para cada país. |
| Pérdida promedio por ataque              | Promedio de pérdidas generadas por un incidente.   | Total de pérdidas / número total de ataques. | Evalúa la severidad económica general del ecosistema. |
| Crecimiento interanual de pérdidas       | Variación económica año a año.                     | (Pérdidas año actual – año anterior) / año anterior. | Ayuda a anticipar aumentos futuros y ajustar presupuestos de defensa. |

---

### 👥 Métricas sociales

| KPI                                                              | Descripción                                                         | Cálculo                                         | Valor Analítico                                 |
|------------------------------------------------------------------|---------------------------------------------------------------------|-------------------------------------------------|-----------------------------------------------|
| Total de personas afectadas por país                             | Cantidad total de usuarios impactados en cada país.                 | Sumar usuarios afectados para cada país.        | Mide impacto humano y exposición de datos.     |
| Industria más afectada (impacto × recurrencia)                   | Industria con más ataques considerando personas afectadas y frecuencia. | Multiplicar número de personas afectadas × frecuencia de ataques. | Refleja el nivel de impacto de los ataques en la industria. |

---

### 🛡️ Métricas de defensa

| KPI                                          | Descripción                                              | Cálculo                                                 | Valor Analítico                                        |
|----------------------------------------------|----------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------|
| Defensa más efectiva por tipo de ataque       | Identifica el mecanismo de defensa que mejor reduce el impacto. | Comparar pérdidas o usuarios afectados entre mecanismos para el mismo tipo de ataque. | Optimiza estrategias de ciberseguridad basadas en evidencia. |
| Tiempo promedio de respuesta según tipo de ataque | Evalúa la eficiencia de resolución por tipo de amenaza.   | Promediar horas de resolución agrupadas por tipo de ataque. | Permite identificar ataques que tardan más en resolverse. |
| Tiempo promedio de resolución por industria   | Tiempo medio que tardan en resolverse ataques según industria. | Promediar horas de resolución por industria.             | Identifica sectores con procesos defensivos más lentos o ineficientes. |

---

# 5. 🔍 EDA: Análisis Exploratorio de Datos

### a. SOFTWARE, AI Y LENGUAJES UTILIZADOS
![Software utilizado](images/herram.png)

### b. ARQUITECTURA DE DATOS
![Arquitectura Medallón](images/medall.png)  

## 🥉 C. CAPA BRONZE

Se creó un proyecto en **BigQuery** con el nombre de `bronzedianacortes`, y en él se crearon dos conjuntos de datos:  
- Uno para la **capa Bronze**  
- Otro para las **tablas de la capa Silver**  

No se crearon dos proyectos diferentes ya que de esta forma fue más práctico y no se registraron impedimentos por orígenes y vinculaciones, como sí ocurrió al intentar hacerlo en proyectos distintos. Esto fue comentado con uno de los instructores en una de las clases, quien refirió que no habría problema alguno.  

La carga de datos se realizó a partir de un archivo **CSV**.  
Previo a su ingesta en BigQuery, se ajustaron los nombres de dos columnas directamente en Excel, ya que contenían caracteres especiales no reconocidos por el motor de BigQuery, lo cual impedía la correcta carga del archivo.  

![Carga Bronze](images/1capqbigq.png)

👉 **Resultado:** El archivo cargó en su totalidad.  
![Carga Bronze](images/2capbigq.png)

---

## 🥈 D. CAPA SILVER

**Limpieza de datos:**  
A lo largo del proyecto se realizó un proceso de limpieza y preparación del *Global Cybersecurity Threats Dataset (2015–2024)* para asegurar su consistencia y usabilidad en BigQuery y Power BI.  

### 🔧 Principales etapas
- **Revisión y estandarización de columnas**  
  - Se aplicaron funciones de estandarización (`LOWER`, `TRIM`, `REGEXP_REPLACE`) en BigQuery para identificar categorías con variaciones de escritura.
  - El análisis mostró que los tipos de ataque ya se encontraban homogéneos.
  - ![Carga Bronze](images/cap4.jpg) 
  - Se verificaron los nombres de las columnas y se renombraron para mantener un formato estándar.
 ![Carga Bronze](images/3capbigq.png)

- **Tratamiento de valores faltantes**  
  - No se identificaron campos con valores nulos.
   - ![Carga Bronze](images/cap5.png) 
     
  - Los nombres de países ya estaban estandarizados.  
  - Se verificó que el modelo de datos se conectara correctamente con BigQuery.  
  - Se revisaron las relaciones entre tablas y se ajustaron cardinalidades.  
  - Se creó la tabla **Silver** con datos limpios y nombres estándar.
  - - ![Carga Bronze](images/cap6.png)  
  - No fue necesario realizar conversiones de fechas, ya que el dataset solo incluía la variable **AÑO**.
    
```sql
CREATE OR REPLACE TABLE `bronzedianacortes.Cyberthreats_Silver.Amenazas_Globales_Silver` AS
SELECT
    Pais,
    Anio,
    Tipo_Ataque,
    Fuente_Ataque,
    Vulnerabilidad,
    Industria,
    Mecanismo_Defensa,
    CAST(Perdida_Millones_USD AS FLOAT64) AS Perdida_Millones_USD,
    CAST(Usuarios_Afectados AS INT64) AS Usuarios_Afectados,
    CAST(Tiempo_Resolucion_Horas AS FLOAT64) AS Tiempo_Resolucion_Horas
FROM `bronzedianacortes.Cyberthreats_Bronze.Amenazas_Globales`;
```



### 📊 Tabla Silver Original
La tabla `Amenazas_Globales_Silver` se creó para asegurar datos limpios, consistentes y listos para análisis, actuando como la base sólida necesaria para construir un modelo confiable y un Dashboard analítico de ciberseguridad.  
Los nombres de las columnas se tradujeron a Español.  

👉 **Nota:** Todas las columnas fueron útiles para el análisis, por lo que se consideraron en su totalidad.  
![Tabla Silver](images/capa-silver.png)

---

## 🗂️ Tablas Dimensionales

Se crearon **cinco tablas dimensionales en BigQuery** y con ellas la **tabla FACT**, todas con lenguaje SQL.  
A cada tabla se le asignó una columna adicional de **ID** que funcionó como *Primary Key* en la tabla FACT, esto por sugerencia del instructor y como forma de generar un análisis más limpio y preciso.  

- **DIM_DATE**  
- **DIM_PAIS**  
- **DIM_ATTACK**  
  - Para ataques, se tomaron tres categorías originales (*Tipo de ataque, Fuente del ataque, Tipo de vulnerabilidad*) y se fusionaron, asignando un código único a cada combinación distinta.  
  - Esto simplificó las dimensiones.  
- **DIM_DEFENSA**  
- **DIM_INDUSTRIA**  

---

## ⭐ Tabla FACT (Hechos)

- La tabla `FACT_Cyberthreats` centraliza los datos y los relaciona con las diferentes tablas dimensionales por medio de las claves asignadas.  
- La construcción de esta tabla fue esencial para estructurar el **modelo estrella** de análisis de datos, ya que permitió transformar un dataset disperso y heterogéneo en un esquema sólido, relacional y listo para explorar tendencias, patrones de ataque y efectos económicos y sociales dentro del panorama de amenazas cibernéticas.  
- Se agregaron columnas con título **“raw”** para identificar cada uno de los nombres y categorías a las que se les había asignado un ID.  

![Tabla FACT](images/fact-cyberthreats.png)
