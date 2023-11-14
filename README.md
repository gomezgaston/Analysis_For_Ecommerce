
![Imagen](images/herramientas-de-analitica-web.jpg)

# Introduccion:
En este proyecto de Python, llevamos a cabo un análisis detallado de un conjunto de datos que abarca diversas columnas de valores financieros. El conjunto de datos comprende información relacionada con los movimientos de compras de un E-Commerce. Nuestro objetivo principal consiste en extraer ideas clave sobre las tendencias y patrones presentes en estos registros financieros. A través de la visualización y resumen de los datos, buscamos comprender la evolución del comportamiento de los ingresos a lo largo del tiempo y analizar la distribución de estos . Este análisis nos proporcionará información valiosa acerca de las tendencias financieras, lo cual resultará fundamental para la toma de decisiones basada en datos.


# Datos

Los datos fueron extraidos de Kaggle.com. Si gusta, puede revisar el conjunto de datos original en el siguiente [link](https://www.kaggle.com/datasets/rishikumarrajvansh/marketing-insights-for-e-commerce-company/data)


El dataset consta de siguientes 4 archivos:


**Online_Sales.csv:** This file contains actual orders data (point of Sales data) at transaction level with
below variables.

- *CustomerID:* Customer unique ID
- *Transaction_ID:* Transaction Unique ID
- *Transaction_Date:* Date of Transaction
- *Product_SKU:* SKU ID – Unique Id for product
- *Product_Description:* Product Description
- *Product_Cateogry:* Product Category
- *Quantity:* Number of items ordered
- *Avg_Price:* Price per one quantity
- *Delivery_Charges:* Charges for delivery
- *Coupon_Status:* Any discount coupon applied

**Customers_Data.csv:** This file contains customer’s demographics.

- *CustomerID:* Customer Unique ID
- *Gender:* Gender of customer
- *Location:* Location of Customer
- *Tenure_Months:* Tenure in Months


**Discount_Coupon.csv**: Discount coupons have been given for different categories in different months

- *Month*: Discount coupon applied in that month
- *Product_Category*: Product category
- *Coupon_Code:* Coupon Code for given Category and given month
- *Discount_pct:* Discount Percentage for given coupon

**Marketing_Spend.csv:** Marketing spend on both offline & online channels on day wise.

- *Date*: Date
- *Offline_Spend:* Marketing spend on offline channels like TV, Radio, NewsPapers, Hordings etc…
- *Online_Spend:* Marketing spend on online channels like Google keywords, facebook etc..

**Tax_Amount.csv**: GST Details for given category

- *Product_Category:* Product Category
- *GST:* Percentage of GST


# Objetivos:

Los objetivos que se buscarán son los mismos que plantea el proyecto original, a saber:

># Business Objective:
>La compañia de E-Commerce espera cumplir con los siguientes requisitos
>
> ## Calculate Invoice amount or sale_amount or revenue for each transaction and item level
> - Invoice Value =(( QuantityAvg_price)(1-Dicount_pct)*(1+GST))+Delivery_Charges
>
> ## Perform Detailed exploratory analysis
> - Understanding how many customers acquired every month
>- Understand the retention of customers on month on month basis
>- How the revenues from existing/new customers on month on month basis
>- How the discounts playing role in the revenues?
>- Understand the trends/seasonality of sales by category, location, month etc…
>- How number order varies and sales with different days?
>- How marketing spend is impacting on revenue?
>- Which product was appeared in the transactions?
>- Which product was purchased mostly based on the quantity?
>
>## Performing Customer Segmentation
>- Heuristic (Value based, RFM) – Divide the customers into Premium, Gold, Silver, Standard customers and define strategy on the same.
>- Scientific (Using K-Means) & Understand the profiles. Define strategy for each segment.
>
>## Predicting Customer Lifetime Value (Low Value/Medium Value/High Value)
>- Define a dependent variable with categories low value, medium value, high value using customer revenue Then perform a Classification model.
----

# Contenido. 

Este proyecto consta de los siguientes archivos:

**EDA.ipynb**: Analisis exploratorio, donde se corroboró la integridad de los datasets, y luego donde se cumplio los objetivos

**Report.md**: Reporte detallado donde se cumplen con los objetivos propuestos referente a la exploracion de datos

**Sementation_and_LTV.ipynb**: Notebook donde se realizo la segmentacion de clientes y el modelo de ML para agrupar nuevos clientes.

**sql_database.ipynb**: *proximamente*


# EDA Preliminar:

### CustomerData

![Imagen_1](images/output.png)


En este gráfico, se presenta la distribución general de nuestros clientes según su género y localidad. Además, se destaca una agrupación de clientes en función de su antigüedad (tenure).

Este análisis proporciona una visión integral de la diversidad de la base de clientes, revelando patrones relacionados con la distribución geográfica y la lealtad de los clientes a lo largo del tiempo. La agrupación por antigüedad puede ofrecer insights valiosos sobre la retención de clientes y su relación con factores geográficos o demográficos. Esta información es esencial para adaptar estrategias de marketing, servicio al cliente y desarrollo de productos según las características específicas de cada segmento, contribuyendo así a una comprensión más profunda de la dinámica del mercado y a una toma de decisiones más informada.

### Marketing_Spends

![Imagen_2](images/output2.png)

El primer gráfico muestra los gastos diarios realizados en marketing, abarcando tanto el ámbito offline como el digital.

En el segundo gráfico, estos gastos se encuentran agrupados mensualmente, incorporando además una tercera línea que representa el total de gastos.

Esta representación visual ofrece una perspectiva detallada de la distribución diaria de los gastos de marketing, permitiendo identificar posibles patrones o variaciones a lo largo del mes. Al consolidar los gastos mensualmente y agregar la línea que representa el total, se obtiene una visión más global y permite evaluar la magnitud de la inversión en marketing en un periodo más amplio. Este análisis facilita la toma de decisiones estratégicas, como la asignación de presupuesto y la evaluación del rendimiento general de la estrategia de marketing.
### Online_Sales

![Imagen_3](images/output3.png)

En estos gráficos, se pueden identificar los usuarios que realizaron el mayor número de transacciones, tanto en términos de cantidad de compras como de montos invertidos. Además, se presenta una distribución general que refleja las tendencias por temporada y destaca los productos más comercializados, así como aquellos que generan mayores ganancias.

Esta visualización permite destacar a los usuarios más activos, proporcionando información clave sobre el comportamiento de compra y su contribución al volumen total de transacciones. Asimismo, la representación de tendencias estacionales y productos destacados es fundamental para la planificación estratégica, como la gestión de inventario y la promoción de productos específicos en momentos clave. Analizar la relación entre los usuarios destacados y los productos más rentables puede llevar a estrategias más efectivas para maximizar el valor de cada transacción.


# Segmentacion.

Para realizar la segmentacion de los usuarios se utilizaron dos tecnicas. 

## Basada en euristica, haciendo con reglas definidas utilizando como paramentro el RFM:

**Recency (R - Recencia):** Evalúa cuándo fue la última vez que un cliente realizó una compra. Este aspecto se centra en la temporalidad y mide la "frescura" de la interacción más reciente del cliente con el negocio.

**Frequency (F - Frecuencia):** Indica con qué frecuencia un cliente realiza compras o interactúa con el negocio en un período de tiempo específico. Mide la repetición de las transacciones y cuántas veces un cliente ha comprado o participado en cierto período.

**Monetary Value (M - Valor Monetario)**: Refleja cuánto dinero ha gastado un cliente en total durante un período determinado. Este aspecto se centra en el valor económico de las transacciones realizadas por el cliente.

Se dividio la basde de clientes en 4 estratos: Standar, Silver, Gold y Premium


## Basada en Machine Learning:

Aplicando el modelo de clustering KNN

![Imagen_4](images/segmentation.png)


# Prediciendo Lifetime Value.

Para esto se realizo una distincion entre clientes basadas en reglas predefinidas. 

Luego se realizo un modelo de Machine Learnign de clasificacion (DecisionTreeClassifier) para categorizar los nuevos clientes


---
---




# TODO

Creacion de base de datos en SQL SERVER y normalizacion

Dashboard