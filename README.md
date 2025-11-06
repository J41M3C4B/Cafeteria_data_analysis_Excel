# Proyecto: Análisis de Ventas de Cafetería (Coffee Shop Sales)

## 📊 Resumen del Proyecto

Este proyecto consiste en un análisis de datos de ventas de una cafetería, realizado íntegramente en **Microsoft Excel**. El objetivo es limpiar y transformar un conjunto de datos transaccionales crudos para, finalmente, construir un **dashboard interactivo** que permita identificar patrones de ventas, rendimiento de productos y tendencias de consumo.

El proyecto demuestra el ciclo completo de análisis de datos: desde la limpieza y transformación (ETL) hasta el análisis (EDA) y la visualización interactiva.

## ❓ Preguntas de Negocio Resueltas

El dashboard interactivo fue diseñado para responder preguntas clave del negocio:
* ¿Cuáles son las horas pico de ventas y los días de mayor afluencia?
* ¿Qué tienda (ubicación) genera más ingresos?
* ¿Qué categorías de productos son las más rentables y cuáles las más populares?
* ¿Cuál es el ticket promedio por cliente (Average Order Value)?
* ¿Qué tamaños de productos prefieren los clientes?

## 🛠️ Herramientas y Habilidades Demostradas

* **Microsoft Excel:**
    * Limpieza y formato de datos.
    * **Ingeniería de Características (Feature Engineering):** Creación de nuevas columnas (`total_sale`, `hour`, `day_of_week`, `product_size`, `order_id`).
    * **Tablas Dinámicas (Pivot Tables):** Agregación y resumen de datos.
    * **Gráficos Dinámicos (Pivot Charts):** Visualización de datos.
    * **Segmentadores de Datos (Slicers):** Creación de un dashboard interactivo.
* **Power Pivot (Modelo de Datos):**
    * Uso del Modelo de Datos de Excel para permitir cálculos avanzados.
* **DAX (Data Analysis Expressions):**
    * Creación de medidas DAX personalizadas, como **`Ticket Promedio`** (`DIVIDE(SUM(Ventas), DISTINCTCOUNT(Pedidos))`).

## 🚀 Metodología del Proyecto

El proyecto se estructuró en 4 hojas de cálculo principales:

### 1. DS ORIGINAL (Datos Crudos)
Se partió de un conjunto de datos transaccionales sin procesar que incluía `transaction_id`, `transaction_date`, `transaction_time`, `store_id`, `product_detail`, etc.

### 2. TIDY DATA (Limpieza y Transformación)
Esta fue la etapa más crítica. Los datos crudos se limpiaron y se enriquecieron mediante la creación de nuevas columnas (Ingeniería de Características) para permitir un análisis más profundo:

* **`total_sale`**: Se calculó multiplicando `transaction_qty * unit_price`.
* **`hour` y `day_of_week`**: Se extrajeron de las columnas de fecha y hora para analizar tendencias temporales.
* **`product_size`**: Se extrajo mediante fórmulas de texto (ej. "Lg", "Rg", "Sm") a partir de la columna `product_detail`.
* **`order_id`**: **Esta fue la característica más importante**. Se generó un ID de pedido único agrupando transacciones que compartían la misma fecha y hora exactas (`transaction_date` + `transaction_time`). Esto fue crucial para diferenciar *artículos vendidos* de *pedidos únicos*.

### 3. ANALISIS (Tablas Dinámicas)
En esta hoja se centralizaron todas las tablas dinámicas utilizadas para impulsar el dashboard. Se calcularon métricas clave como:
* Ingresos totales por tienda, categoría y hora.
* Conteo de pedidos únicos (usando **`RECUENTO DISTINTO`** sobre `order_id`) por hora y día.
* Conteo de productos por tamaño.
* Estadísticas descriptivas (Min, Max, Promedio) de precios y cantidades.

### 4. DASHBOARD (Visualización)
Se creó un dashboard ejecutivo que consolida todos los hallazgos en una sola vista. El dashboard es **totalmente interactivo** y utiliza **Segmentadores de Datos (Slicers)** para filtrar los datos por:
* Tienda (`store_location`)
* Categoría de Producto (`product_category`)
* Día de la Semana (`day_of_week`)

<img width="966" height="657" alt="image" src="https://github.com/user-attachments/assets/7590f4c3-187b-4275-bf92-2ea48176682b" />
<img width="970" height="270" alt="image" src="https://github.com/user-attachments/assets/643d794b-3168-4465-b803-d93e3a80e901" />



## 💡 Hallazgos Clave (Insights)

* **Horas Pico:** La mayor afluencia de clientes y volumen de ventas ocurre entre las **8 a.m. y las 10 a.m.**
* **Rendimiento de Tiendas:** Las tres tiendas (Astoria, Hell's Kitchen, Lower Manhattan) tienen un rendimiento de ingresos notablemente similar, lo que indica un buen equilibrio operativo.
* **Ticket Promedio (AOV):** Se calculó el gasto promedio por pedido único, una métrica clave que no estaba disponible en los datos crudos (creada con DAX).
* **Categorías Populares:** El café (`Coffee`) es la categoría de mayor ingreso, seguida de cerca por el té (`Tea`) y los productos de panadería (`Bakery`).

## 📥 Cómo Usar este Proyecto

1.  Descarga el archivo `.xlsx`.
2.  Ábrelo en Microsoft Excel (se recomienda una versión que soporte Power Pivot y Modelo de Datos, como Excel 2016 o posterior).
3.  Navega a la hoja **"DASHBOARD"**.
4.  Utiliza los segmentadores de datos (filtros) en la parte superior para explorar los datos.
