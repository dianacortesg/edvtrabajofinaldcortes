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

### c. CAPA BRONZE
![Carga CSV en BigQuery](images/1capbigq.png)

### d. CAPA SILVER
![Tabla Silver](images/2capbigq.png)

---

# 6. 🗂️ DER: Modelo Entidad Relacionales
![DER](images/der.png)

---

# 7. 🥈 Construcción capa Silver
Proceso de limpieza, estandarización y creación de dimensiones clave.  
- Revisión de duplicados semánticos  
- Verificación de nombres de columnas  
- Ajuste de cardinalidades  
- Creación de tabla **Amenazas_Globales_Silver**  

---

# 8. 📊 Conexión y desarrollo en PowerBI
![Dashboard Power BI](images/dashboard-powerbi.png)

---

# 9. 🧮 Medidas en DAX
*(Aquí puedes añadir tus fórmulas DAX si lo deseas)*  

---

# 10. ✅ Conclusiones
- Patrones claros de concentración geográfica y sectores vulnerables.  
- Impactos económicos y sociales medibles para priorizar políticas.  
- Análisis de defensas orienta mejoras operativas.  
- BigQuery + Power BI soportan dashboards confiables y accionables.  
