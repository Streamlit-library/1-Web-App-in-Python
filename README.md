# Web App in Python

1. [Crear env en conda y activarlo ](#schema1)
2. [Instalar Streamlit](#schema2)
3. [Instalar YFinance](#schema3)
4. [Texto en la aplicación](#schema4)
5. [Obtención de los datos](#schema5)
6. [Mostramos las gráficas](#schema6)
7. [Ejecutar aplicación](#schema7)
8. [Documentación](#schema8)


<hr>

<a name="schema1"></a>

# 1. Crear env en conda y activarlo

~~~bash
conda create --name streamlit python=3.7.0
conda activate streamlit 
~~~
<hr>

<a name="schema2"></a>

# 2. Instalar Streamlit
~~~
pip install streamlit
~~~
<hr>

<a name="schema3"></a>

# 3. Instalar YFinance

YFinance se creó para ayudar a los programas y usuarios que confiaban en la API de Yahoo Finance. Resuelve el problema al permitir a los usuarios descargar datos usando Python y también tiene algunas características excelentes que lo hacen favorable para su uso para el análisis de datos de existencias. YFinance no solo descarga los datos del Precio de las Acciones sino que también nos permite descargar todos los datos financieros de una Compañía desde su cotización en el mercado de valores. Es fácil de usar y increíblemente rápido. Esta biblioteca es bastante famosa por el análisis de datos financieros.

~~~
pip install yfinance
~~~


Los argumentos clave aquí son:
- período: la frecuencia con la que se recopilan los datos,- las opciones comunes incluirían "1d" (diario), "1 mes" (mensual), "1 año" (anual)
- inicio: la fecha para comenzar a recopilar los datos. Por ejemplo, "2010–1–1"
- fin: la fecha para finalizar la recopilación de datos. Por ejemplo, "2020–1–25"


El resultado debe ser un marco de datos de Pandas que contenga datos históricos diarios sobre el precio de las acciones de la empresa elegida. Los campos clave incluyen:
- Open: el precio de la acción al comienzo de ese día / mes / año
- Close: el precio de las acciones al final de ese día / mes / año
- High:: el precio más alto que alcanzó la acción ese día / mes / año
- Low: el precio más bajo que alcanzó la acción ese día / mes / año
- Volume: cuántas acciones se negociaron ese día / mes / año

<hr>

<a name="schema4"></a>


# 4. Texto en la aplicación
El título o cualquier cosa que se quiera poner de texto den la aplicación de `streamlit`se usa `st.streamlit`
~~~python
st.write("""
# Simple Stock Price App
Shown are the stock closing price and volume of Google!
""")
~~~
<hr>

<a name="schema5"></a>

# 5. Obtención de los datos

Definimos la empresa
~~~python
tickerSymbol = 'GOOGL'
~~~
Obtenemos los datos
~~~python 

tickerData = yf.Ticker(tickerSymbol)
~~~
Obtenemos el historial de precios
~~~python

tickerDf = tickerData.history(period='1d', start='2010-5-31', end='2020-5-31')

~~~

<hr>

<a name="schema6"></a>

# 6. Mostramos las gráficas
~~~python
st.line_chart(tickerDf.Close)

st.line_chart(tickerDf.Volume)
~~~

<hr>

<a name="schema7"></a>

# 7. Ejecutar aplicación
~~~python
streamlit run first_app.py

~~~

<hr>

<a name="schema8"></a>



# 8. Documentación
https://towardsdatascience.com/how-to-get-stock-data-using-python-c0de1df17e75

https://www.youtube.com/channel/UCV8e2g4IWQqK71bbzGDEI4Q