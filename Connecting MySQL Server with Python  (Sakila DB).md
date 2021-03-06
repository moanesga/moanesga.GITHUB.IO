## Connecting MySQL Server with Python  (Sakila DB)

**Project description:** Description of two methods to connect MySQL databases to Python. With the first method it is possible easy access to the information converting tables in dictionary to have a first overview of the content. In the second method using sqlalchemy, the options are expanded to use pandas and plotly express. Here the MySQL Sakila database (Movies) was taken as an example to transfer information in DataFrames and interactive charts with views of Customer by country including geolocation by continent.

### 1. Reading the film_list View into a pandas DataFrame

```python
film = pd.read_sql('SELECT * FROM film_list', engine)
film.head(5)
```

<img src="images/003_Connecting MySQL_with_Python_DataFrame_001.PNG?raw=true"/>


### 2. Using plotly express to create an interactive Bar Chart
Rating meaning: 
PG(Parental guidance suggested)
G(General audiences – All ages admitted) 
NC-17 (No One 17 or Under Admitted)
PG-13 (Rated PG-13: Parents Strongly Cautioned – Some material may be inappropriate for children under 13.)
R:Restricted – Under 17 requires accompanying parent or adult guardian.

```python
import plotly.express as px
fig = px.bar(film, x='category', y='FID',  hover_data=['rating'], color='rating')
fig.show()
```

<img src="images/003_Connecting MySQL_with_Python_DataFrame_002.PNG?raw=true"/>


### 3. Plotting a scatter graph of customers by country

```python
fig = px.scatter(customer, x= "country", y="count(1)", color="country",
                     hover_name= "country", size="count(1)")
fig.show()
```

<img src="images/003_Connecting MySQL_with_Python_DataFrame_003.PNG?raw=true"/>


### 4. Plotting a scatter geo graph of customer_list_by_continent View 


```python
fig_3 = px.scatter_geo(customer_by_continent, locations="Code", color="Continent",
                     hover_name="country", size="count(1)",
                     projection="natural earth")
fig_3.show()
```

<img src="images/003_Connecting MySQL_with_Python_DataFrame_004.PNG?raw=true"/>



For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
