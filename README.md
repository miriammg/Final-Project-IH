## Final-Project

# Customer Analysis

Objetivo: dado un dataset con características sociodemográficas, tipo de póliza, y tipo de vehículo, vamos a predecir la cantidad total que puede llegar a reclamar un cliente. <br>

## 1. Análisis exploratorio de los datos. 

24 columnas:  <br>
- 16 object type  <br>
- 8 numeric type  <br>
9134 entidades <br>

### Categorical Variable: <br>

**Effective To Date** <br>
Cambiamos de tipo object a tipo dtime: <br>
Los datos están en los meses de Enero y Febrero <br>
Un 50% aproximadamente a cada mes. <br>

**Customer** <br>
 Tipo object: <br>
    Valores únicos para cada cliente. <br>

**State** <br>
 Our consumers are from 5 states in the western United States: <br>
    California    34.5%<br>
    Oregon        28.5%<br>
    Arizona       18.6%<br>
    Nevada         9.7%<br>
    Washington     8.7%<br>

**Response** <br>
Categorical variable with 2: <br>
    No     85.7% <br>
    Yes    14.3% <br>

**Coverage** <br>
'Coverage' is a categorical variable, with 3 categories, type of coverage in the policy. <br>
Basic 61% <br>
Extended 30% <br>
Premium 9% <br>

**Education**





### Numerical Variable: 

**Customer Life Time Value** <br>

