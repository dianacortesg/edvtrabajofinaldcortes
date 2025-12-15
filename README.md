# edv_trabajofinal_dcortes
# 📊 Análisis de Ciberseguridad Global (2015–2024)

## 📑 TABLA DE CONTENIDOS
1. [🚀 Presentación del proyecto](#-presentación-del-proyecto)
2. [📂 Descripción del Dataset](#-descripción-del-dataset)
3. [🎯 Objetivos e Hipótesis](#-objetivos-e-hipótesis)
4. [📈 Plan de métricas KPI’s](#-plan-de-métricas-kpis)
5. [🔍 EDA: Análisis Exploratorio de Datos](#-eda-análisis-exploratorio-de-datos)
6. [🗂️ DER: Modelo Entidad Relación](#-der-modelo-entidad-relacion)
7. [📊 Conexión y desarrollo en PowerBI](#-conexión-y-desarrollo-en-powerbi)
8. [🧮 Medidas en DAX](#-medidas-en-dax)
9. [Analísis y discusión de resultados](#-analisis-y-discuisón-de-resultados)
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
- 📌 Primera: La mayoría de los ataques se concentran en pocos países.  
- 💸 Segunda:Los ataques más frecuentes generan mayores pérdidas económicas.  
- 👥 Tercera:Algunas industrias concentran mayor impacto social.  
- 🛡️ Cuarta: Mejores tiempos de respuesta reducen pérdidas económicas promedio.  

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
![Tabla Silver](images/cap6.png)

---

## 🗂️ Tablas Dimensionales

Se crearon **cinco tablas dimensionales en BigQuery** y con ellas la **tabla FACT**, todas con lenguaje SQL.  
A cada tabla se le asignó una columna adicional de **ID** que funcionó como *Primary Key* en la tabla FACT, esto por sugerencia del instructor y como forma de generar un análisis más limpio y preciso.  

- **DIM_DATE**
- 
- ![Carga Bronze](images/dimdate.jpg)

```sql
- CREATE OR REPLACE TABLE `bronzedianacortes.Cyberthreats_Silver.Dim_Date` AS
SELECT DISTINCT
    Year_ID
FROM `bronzedianacortes.Cyberthreats_Silver.Amenazas_Globales_Silver`
WHERE Anio IS NOT NULL;
```

- **DIM_PAIS**
- Con ella se buscó normalizar la información de países y asociar cada registro con un ID único.
  Se crearon atributos adicionales como Continente e ISO, para facilitar joins consistentes con la FACT.
- ![Carga Bronze](images/dimpais.jpg)

```sql
CREATE OR REPLACE TABLE `bronzedianacortes.Cyberthreats_Silver.DIM_Pais` AS
SELECT
    ROW_NUMBER() OVER (ORDER BY Pais) AS Pais_ID,
    Pais,
    Continente,
    ISO
FROM (
    SELECT DISTINCT
        Pais,
        Continente,
        ISO
    FROM `bronzedianacortes.Cyberthreats_Silver.Amenazas_Globales_Silver`
    WHERE Pais IS NOT NULL
      AND Continente IS NOT NULL
      AND ISO IS NOT NULL
);

```

- **DIM_ATTACK**  
  - Para ataques, se tomaron tres categorías originales (*Tipo de ataque, Fuente del ataque, Tipo de vulnerabilidad*) y se fusionaron, asignando un código único a cada combinación distinta.
  - Consolida información relacionada con el ataque en una sola tabla: Tipo, Fuente y Vulnerabilidad.
  - Cada ID representa la combinación única de los tres                                                                                        
El ID de ataque permitió vincular de mejor maanera cada incidente de la FACT con su descripción detallada sin repetir datos.
  - Esto también simplificó las dimensiones.
  - se llevó a cabo como experimento con el fin de agregar análisis mas profundo a los al modelo. Las tres características juntas describen completamente la naturaleza de cada incidente.
  - Al consolidarlas en un solo ID, se evita la duplicación de información en la FACT y se facilita el análisis multidimensional de los ataques, permitiendo identificar patrones, tendencias y relaciones entre distintos tipos de amenazas de manera consistente y eficiente.
  - ![Carga Bronze](images/dimataack.jpg)

 ```sql
CREATE OR REPLACE TABLE `bronzedianacortes.Cyberthreats_Silver.DIM_Ataque` AS
SELECT
    ROW_NUMBER() OVER (
        ORDER BY Tipo_Ataque, Fuente_Ataque, Vulnerabilidad
    ) AS Ataque_ID,
    Tipo_Ataque,
    Fuente_Ataque,
    Vulnerabilidad
FROM (
    SELECT DISTINCT
        Tipo_Ataque,
        Fuente_Ataque,
        Vulnerabilidad
    FROM `bronzedianacortes.Cyberthreats_Silver.Amenazas_Globales_Silver`
    WHERE Tipo_Ataque IS NOT NULL
      AND Fuente_Ataque IS NOT NULL
      AND Vulnerabilidad IS NOT NULL
);

```
  
- **DIM_DEFENSA**

  Enumera los mecanismos de defensa posibles y asigna un ID a cada uno.
Su sentido es permitir que la FACT pueda referenciar los mecanismos de defensa sin repetir nombres largos, manteniendo consistencia.
- ![Carga Bronze](images/dimdefensa.jpg)

```sql
CREATE OR REPLACE TABLE `bronzedianacortes.Cyberthreats_Silver.DIM_Defensa` AS
SELECT
    ROW_NUMBER() OVER (ORDER BY Mecanismo_Defensa) AS Defensa_ID,
    Mecanismo_Defensa
FROM (
    SELECT DISTINCT
        Mecanismo_Defensa
    FROM `bronzedianacortes.Cyberthreats_Silver.Amenazas_Globales_Silver`
    WHERE Mecanismo_Defensa IS NOT NULL
);
```
- **DIM_INDUSTRIA**

- Centraliza todas las industrias afectadas y asigna un ID único a cada una.
Esto ayuda a la FACT a referenciar la industria de manera consistente.
- ![Carga Bronze](images/dimindustria.jpg) 

```sql
CREATE OR REPLACE TABLE `bronzedianacortes.Cyberthreats_Silver.DIM_Industria` AS
SELECT
    ROW_NUMBER() OVER (ORDER BY Industria) AS Industria_ID,
    Industria
FROM (
    SELECT DISTINCT
        Industria
    FROM `bronzedianacortes.Cyberthreats_Silver.Amenazas_Globales_Silver`
    WHERE Industria IS NOT NULL
);
```
---

## ⭐ Tabla FACT (Hechos)

- La tabla `FACT_Cyberthreats` centraliza los datos y los relaciona con las diferentes tablas dimensionales por medio de las claves asignadas.  
- La construcción de esta tabla fue esencial para estructurar el **modelo estrella** de análisis de datos, ya que permitió crear un esquema sólido, relacional y para explorar tendencias, patrones de ataque y efectos económicos y sociales dentro del panorama de amenazas cibernéticas.  
- Se agregaron columnas con título **“raw”** para identificar cada uno de los nombres y categorías a las que se les había asignado un ID.  

![Tabla FACT](images/fact-tablafact.jpg)

```sql
CREATE OR REPLACE TABLE `bronzedianacortes.Cyberthreats_Silver.FACT_CYBERTHREATS` AS
SELECT
    -- Claves de dimensiones
    p.Pais_ID            AS country_id,
    s.Anio               AS Year_ID,
    a.Ataque_ID          AS attack_id,
    i.Industria_ID       AS industria_id,
    d.Defensa_ID         AS defensa_id,

    -- Métricas
    s.Perdida_Millones_USD,
    s.Usuarios_Afectados,
    s.Tiempo_Resolucion_Horas,

    -- Campos raw (tal cual se conservaron)
    s.Pais               AS country_name_raw,
    s.Anio               AS year_raw,
    s.Tipo_Ataque        AS attack_type_raw,
    s.Fuente_Ataque      AS source_raw,
    s.Vulnerabilidad     AS vulnerability_raw,
    s.Industria          AS industry_raw,
    s.Mecanismo_Defensa  AS defense_raw

FROM `bronzedianacortes.Cyberthreats_Silver.Amenazas_Globales_Silver` s

LEFT JOIN `bronzedianacortes.Cyberthreats_Silver.DIM_Pais` p
  ON s.Pais = p.Pais
 AND s.Continente = p.Continente
 AND s.ISO = p.ISO

LEFT JOIN `bronzedianacortes.Cyberthreats_Silver.DIM_Ataque` a
  ON s.Tipo_Ataque = a.Tipo_Ataque
 AND s.Fuente_Ataque = a.Fuente_Ataque
 AND s.Vulnerabilidad = a.Vulnerabilidad

LEFT JOIN `bronzedianacortes.Cyberthreats_Silver.DIM_Industria` i
  ON s.Industria = i.Industria

LEFT JOIN `bronzedianacortes.Cyberthreats_Silver.DIM_Defensa` d
  ON s.Mecanismo_Defensa = d.Mecanismo_Defensa;
```

# 6. 🗂️ Modelo Entidad Relación

- ![Carga Bronze](images/DER.png)

 # 7. 🗂️ Conexión y desarrollo en PowerBI

### 📥 Tablas importadas

Power BI se conectó directamente al proyecto de BigQuery e importó las siguientes tablas:

- 📊 **Tabla FACT**
  - `FACT_CYBERTHREATS`
- 📐 **Tablas de dimensiones**
  - `DIM_PAIS`
  - `DIM_DATE`
  - `DIM_ATTACK`
  - `DIM_INDUSTRIA`
  - `DIM_DEFENSA`
 
  - - - ![Carga Bronze](images/PB1.png)
- En la tabla de ataques se creó una columa adicional que asigna un nombre combinado a cada ID.
- Esto con el fin de que cada código también sea reconocido desde el atque, fuente y vulnerabilidad que representa, sin crear confusión y para facilitar su graficación
- ![Carga Bronze](images/PB4.png)

- la tabla de fecha, que e este caso represneta la DIM_DATE generó algunos problemas de formato por lo qe se le asignó valor de numro entero, esto, sin mebargo, no interfiri´mayormente en este modelo de análisis
- ![Carga Bronze](images/PB3.png)
---

### 🔗 Modelo entidad–relación

- La tabla `FACT_CYBERTHREATS` actúa como tabla central.
- Todas las dimensiones se conectan mediante claves sustitutas (`*_id`).
- Las relaciones son de tipo **uno a muchos (1:N)** desde las dimensiones hacia la tabla fact.
-  ![Carga Bronze](images/PB2.png)
- Se creó además una tabla adicional con las medidas, esta no va conectada al modelo
- - - ![Carga Bronze](images/PBMEDIDAS.png)
---

## 8. 🧮 Medidas DAX

Los cálculos se implementaron mediante **medidas DAX**, 

### 📈 Principales Métricas de Incidencia

**Total de ataques**
```DAX
Total Ataques = COUNTROWS(FACT_CYBERTHREATS)
```
**Ataques por año**
```DAX
Ataques por Año = COUNTROWS(FACT_CYBERTHREATS)
```
**YoY Crecimiento Ataques** 
```DAX
Crecimiento Ataques YoY =
DIVIDE(
    [Total Ataques] -
    CALCULATE([Total Ataques], SAMEPERIODLASTYEAR(DIM_DATE[Year_ID])),
    CALCULATE([Total Ataques], SAMEPERIODLASTYEAR(DIM_DATE[Year_ID]))
)
```

**Distribución: porcentaje de ataques por país** 
```DAX
% Ataques por País =
DIVIDE(
    [Total Ataques],
    CALCULATE([Total Ataques], ALL(DIM_PAIS))
)
```
### 👥 Métricas Sociales

**Total de usuarios afectados**
```DAX
Impacto Humano por Ataque =
SUM(FACT_CYBERTHREATS[Usuarios_Afectados])
```

ℹ️ El dataset no permite identificar usuarios únicos; las métricas representan el total de usuarios reportados como afectados.

### 🛡️ Métricas de Defensa

**Tiempo promedio de resolución**
``DAX
Tiempo Promedio Resolución =
AVERAGE(FACT_CYBERTHREATS[Tiempo_Resolucion_Horas])
```

**Tiempo de resolución por tipo de ataque**
```DAX
Tiempo Resolución por Ataque =
AVERAGE(FACT_CYBERTHREATS[Tiempo_Resolucion_Horas])
```

**Tiempo de resolución por industria**
```DAX
Tiempo Resolución por Industria =
AVERAGE(FACT_CYBERTHREATS[Tiempo_Resolucion_Horas])
```

### 📊 Diseño del Dashboard

El dashboard se organizó en páginas temáticas:

👥 Portada
- - ![Carga Bronze](images/PB5.png)

📈 Incidencia
- - ![Carga Bronze](images/PB6.png)
💰 Impacto económico y social

🛡️ Defensa

Se utilizaron gráficos de barras, gráfios de líneas,treemap, gráficos circulares y tarjetas KPI.

### Dashboard desde el enfoque gráfico y de diseño
- se eligió un fondo oscuro alusivo a ciberseguridad, originario de Freepik

- ### 📊 Análisis y discusión de resultados

## Comprobación de las hipótesis

- 💸 Segunda:Los ataques más frecuentes generan mayores pérdidas económicas.  
- 👥 Tercera:Algunas industrias concentran mayor impacto social.  
- 🛡️ Cuarta: Mejores tiempos de respuesta reducen pérdidas económicas promedio.  

-📌 Primera:Aunque el dataset es limitado y no permite afirmar diferencias abismales entre países, sí muestra que existen algunos países donde los ataques se concentran de manera notable. Los datos reflejan que, dentro del alcance del estudio, el fenómeno se distribuye de forma muy uniforme, pero es posible identificar los países más afectados (EEUU, Brasil e India) como focos principales del ciberataque. Esto, sin embargo, hay que analizarlo con cuidado, pues puede indicar que los datos podrían estar sesgados o incompletos, y que los patrones reales podrían diferir significativamente si se contaran incidentes no reportados o en regiones fuera del dataset.


- ### 📊 Conclusiones
- 
- Aunque el dataset es limitado y no permite extrapolar a nivel global con total certeza, los datos muestran que hay países que concentran un mayor número de incidentes. Esto permite identificar focos principales de ciberataques.
- 
- Se evidencia uniformidad relativa del fenómeno dentro del alcance de la muestra, lo que resepresenta un llamado a verificar que no se hayan presnetado sesgos en la recolección.

- 

