# Clientes_Bicis_XLS

Análisis de perfiles y comportamiento de compra de clientes de una tienda de bicicletas.  
**Herramienta:** Microsoft Excel

---

## Objetivo

Identificar qué tipo de cliente compra una bicicleta en función de variables demográficas y socioeconómicas, y comunicar los hallazgos a través de un dashboard interactivo.

---

## Dataset

- **Fuente:** Dataset simulado de clientes de una tienda de bicicletas
- **Registros:** 1.026 clientes
- **Variables:** 13 columnas — demografía, ingresos, distancia al trabajo, región, número de coches y compra de bicicleta (Sí/No)

---

## Fases del proyecto

| Fase | Descripción |
|------|-------------|
| 1. Importación y exploración | Carga del CSV, creación del libro de trabajo, diccionario de datos |
| 2. Limpieza de datos | Eliminación de duplicados, renombrado de valores, segmentación por edad |
| 3. Análisis con tablas dinámicas | Cruces por género, edad, distancia, coches y región |
| 4. Dashboard | Visualización de insights con gráficos |

---

## Estructura del libro Excel

```
📊 Clientes_Bicis_XLS.xlsx
├── datos_crudos         → Dataset original sin modificar
├── hoja_trabajo         → Copia limpia sobre la que se trabaja
├── diccionario_datos    → Descripción de cada variable
├── tabla_género         → Pivot: compras por género
├── tabla_edad           → Pivot: compras por grupo de edad
├── tabla_millas         → Pivot: distancia al trabajo por edad
├── tabla_coches         → Pivot: número de coches
├── tabla_regiones       → Pivot: distribución geográfica
└── dashboard_insights   → Radiografía del cliente
```

---

## Principales hallazgos

- **Género:** El comportamiento de compra es equilibrado entre hombres y mujeres, sin diferencias significativas.
- **Edad:** El grupo **Adult Rider (36–50)** es el motor de ventas — más de 5 de cada 10 compran. Es el segmento prioritario para inversión en publicidad.
- **Young Rider (18–35):** Para este grupo la bici puede ser su único medio de transporte (necesidad). Acción recomendada: regalar el primer año de mantenimiento básico como palanca de cierre de venta.
- **Senior Rider (51+):** Los que viven muy cerca prefieren caminar; los que viven muy lejos no ven la bici como opción viable por el esfuerzo físico. Acción recomendada: promocionar bicicletas eléctricas, que eliminan el factor esfuerzo y amplían el radio de desplazamiento.
- **Región:** Pacific tiene menor volumen de clientes, pero una tasa de conversión más alta que Europe y North America: ¿Aumentar la inversión publicitaria en Pacific?

---

## Notas

Para más detalle sobre el proceso técnico paso a paso, consultar [`NOTAS_PROCESO.md`](./NOTAS_PROCESO.md).
