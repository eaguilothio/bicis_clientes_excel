# 🚲 Análisis de Clientes — Tienda de Bicicletas
**Herramienta:** Microsoft Excel | **Dataset:** 1.000 registros | **Variables:** 7 columnas

---

## 🧩 Contexto

Proyecto de análisis de perfiles de compra para una tienda de bicicletas. La pregunta de negocio: **¿qué tipo de cliente compra una bicicleta?** El objetivo era identificar qué grupos de clientes tienen mayor tasa de conversión (porcentaje de personas que acaban comprando) y trasladarlo en recomendaciones concretas.

---

## 📊 Datos

Dataset simulado con 1.000 clientes y 7 variables. Variables utilizadas en el análisis:

| Variable | Tipo | Descripción |
|---|---|---|
| Gender | Categórico | Male (hombre) / Female (mujer) |
| Age | Numérico | Edad del cliente en años |
| Cars | Numérico | Número de coches en el hogar |
| Commute Distance | Categórico | Distancia al trabajo (0-1, 1-2, 2-5, 5-10, 10+ Miles) |
| Region | Categórico | Región geográfica (Europe, North America, Pacific) |
| Purchased Bike | Objetivo | Yes = compró bici / No = no compró — Variable a predecir |

---

## ⚙️ Proceso

### Fase 1 — Importación y exploración

1. **Importar el CSV** con Unicode 65001 para evitar errores con tildes y caracteres especiales

2. **Estructurar el libro** en dos hojas diferenciadas:
   - `datos_crudos` — datos originales, nunca se modifican
   - `hoja_trabajo` — copia sobre la que se opera siempre

3. **Añadir una leyenda de variables** es una buena práctica, te ayuda a entender las variables que son seleccionadas para el análisis. 

---

### Fase 2 — Limpieza

4. **Eliminar duplicados:** `Datos → Quitar duplicados`

5. **Renombrar valores abreviados:** `Inicio → Buscar y seleccionar → Reemplazar`
   - `M → Male` / `F → Female`

6. **Crear columna `Age Brackets`** con SI anidado:

```
=SI(G2<18;"Junior";SI(G2<36;"Young Rider";SI(G2<51;"Adult Rider";"Senior Rider")))
```

   Los rangos tienen lógica de negocio, no son arbitrarios. El dataset no contiene clientes menores de 18 años, por lo que los segmentos activos son:

   | Segmento | Edad |
   |---|---|
   | Young Rider | < 36 |
   | Adult Rider | 36–50 |
   | Senior Rider | 51+ |


---

### Fase 3 — Tablas dinámicas

7. **5 tablas dinámicas** cruzando la variable de compra con:
   - Género
   - Grupo de edad
   - Distancia al trabajo
   - Número de coches
   - Región

   > 💡 **Decisión técnica:** los valores se configuraron como **% por fila** (no % del total). La diferencia es clave: el % del total te dice qué tan grande es cada grupo; el % por fila te dice cuántos de ese grupo acaban comprando. Para analizar comportamiento de compra siempre se usa % por fila. Sin ese ajuste, Pacific parecía irrelevante (solo el 11% del total). Con % por fila se descubre que es la región donde más gente compra (58,85%).

---

### Fase 4 — Dashboard

8. **Hoja `dashboard_insights`** con todos los gráficos centralizados

---

## 📁 Estructura del libro

```
📊 Clientes_Bicis_XLS.xlsx
├── datos_crudos         → Dataset original sin modificar
├── hoja_trabajo         → Copia limpia sobre la que se trabaja
├── leyenda_variables    → Descripción de cada variable
├── tabla_género         → Tabla dinámica: compras por género
├── tabla_edad           → Tabla dinámica: compras por grupo de edad
├── tabla_millas         → Tabla dinámica: distancia al trabajo por edad
├── tabla_coches         → Tabla dinámica: número de coches
├── tabla_regiones       → Tabla dinámica: distribución geográfica
└── dashboard_insights   → Radiografía del cliente
```

---

## 📈 Resultados

- **Young Rider (< 36):** para muchos la bici es su único medio de transporte. Hay una necesidad, enfocar la publicidad, también, para este grupo. Ofrecer el primer año de mantenimiento gratuito para cerrar venta.
- **Adult Rider (36–50):** motor de ventas — de cada 10 clientes, más de 5 compran. Segmento prioritario para publicidad.
- **Senior Rider (51+):** los que viven cerca prefieren caminar; los que viven lejos ven el esfuerzo físico como barrera. Recomendación: promocionar bicis eléctricas.
- **Región Pacific:** aunque hay menos gente viviendo en Pacific, la probabilidad de que compren una bici es mayor que en Europe o North America. Oportunidad: aumentar inversión publicitaria en esa región.
- **Género:** comportamiento de compra equilibrado entre hombres y mujeres — el género no es un factor determinante. La oferta es atractiva para ambos perfiles.

---

## 💡 Reflexión

- Tres segmentos de edad donde invertir: Adult Rider es el motor de ventas — más de 5 de cada 10 compran. Young Rider tiene una necesidad real de transporte. Senior Rider es el grupo con mayor rechazo, pero tiene solución: la bici eléctrica elimina el esfuerzo físico y amplía el radio de desplazamiento. Y una región a tener en cuenta: Pacific es el mercado más pequeño, pero donde más gente acaba comprando.

## ⚠️ Limitaciones

- El dataset es simulado, lo que limita la validez de las conclusiones. Un dataset real podría tener más problemas con los datos que un simulado no refleja. También, con datos reales de una empresa, lo primero sería entender el problema de negocio antes de tocar los datos. El análisis cambia completamente según lo que la empresa necesite resolver.
- El grupo Senior Rider tiene la tasa de rechazo más alta (60%). La hipótesis es — viven muy cerca y prefieren caminar, o viven muy lejos y el esfuerzo físico es una barrera — pero no hay datos suficientes para confirmarlo. Sería interesante analizar las reseñas de este grupo para saber si existe o no alguna problemática.
