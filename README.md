# Pandas Data Analysis Practice

```python
import pandas as pd
```

```python
from urllib.request import urlretrieve

urlretrieve('https://hub.jovian.ml/wp-content/uploads/2020/09/countries.csv', 
            'countries.csv')
```
    ('countries.csv', <http.client.HTTPMessage at 0x19f75cea370>)

```python
countries_df = pd.read_csv('countries.csv')
```

```python
countries_df
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>location</th>
      <th>continent</th>
      <th>population</th>
      <th>life_expectancy</th>
      <th>hospital_beds_per_thousand</th>
      <th>gdp_per_capita</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>38928341.0</td>
      <td>64.83</td>
      <td>0.50</td>
      <td>1803.987</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Albania</td>
      <td>Europe</td>
      <td>2877800.0</td>
      <td>78.57</td>
      <td>2.89</td>
      <td>11803.431</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Algeria</td>
      <td>Africa</td>
      <td>43851043.0</td>
      <td>76.88</td>
      <td>1.90</td>
      <td>13913.839</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Andorra</td>
      <td>Europe</td>
      <td>77265.0</td>
      <td>83.73</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Angola</td>
      <td>Africa</td>
      <td>32866268.0</td>
      <td>61.15</td>
      <td>NaN</td>
      <td>5819.495</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>205</th>
      <td>Vietnam</td>
      <td>Asia</td>
      <td>97338583.0</td>
      <td>75.40</td>
      <td>2.60</td>
      <td>6171.884</td>
    </tr>
    <tr>
      <th>206</th>
      <td>Western Sahara</td>
      <td>Africa</td>
      <td>597330.0</td>
      <td>70.26</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>207</th>
      <td>Yemen</td>
      <td>Asia</td>
      <td>29825968.0</td>
      <td>66.12</td>
      <td>0.70</td>
      <td>1479.147</td>
    </tr>
    <tr>
      <th>208</th>
      <td>Zambia</td>
      <td>Africa</td>
      <td>18383956.0</td>
      <td>63.89</td>
      <td>2.00</td>
      <td>3689.251</td>
    </tr>
    <tr>
      <th>209</th>
      <td>Zimbabwe</td>
      <td>Africa</td>
      <td>14862927.0</td>
      <td>61.49</td>
      <td>1.70</td>
      <td>1899.775</td>
    </tr>
  </tbody>
</table>
<p>210 rows × 6 columns</p>
</div>


Q: How many countries does the dataframe contain?

Hint: Use the .shape attribute

```python
num_countries = countries_df.shape[0]
```

```python
print('There are {} countries in the dataset'.format(num_countries))
```
    There are 210 countries in the dataset
    

Q: Retrieve a list of continents from the dataframe?

Hint: Use the .unique method of a series

```python
continents = countries_df['continent'].unique()
```

```python
continents
```
    array(['Asia', 'Europe', 'Africa', 'North America', 'South America',
           'Oceania'], dtype=object)


Q: What is the total population of all the countries listed in this dataset?

```python
total_population = countries_df.population.sum()
```

```python
print('The total population is {}.'.format(int(total_population)))
```
    The total population is 7757980095.


Q: (Optional) What is the overall life expectancy across in the world?

Hint: You'll need to take a weighted average of life expectancy using populations as weights.

```python
weights = countries_df.population
```

```python
lf = countries_df.life_expectancy
```

```python
x = weights * lf
```

```python
overall_le = x.sum() / total_population
overall_le
```
    72.72165193409664

```python
print('The overall life expectancy is {}.'.format(int(overall_le)))
```
    The overall life expectancy is 72.
    

Q: Create a dataframe containing 10 countries with the highest population.

Hint: Chain the sort_values and head methods.

```python
most_populous_df = countries_df.sort_values('population', ascending=False).head(10)
```

```python
most_populous_df
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>location</th>
      <th>continent</th>
      <th>population</th>
      <th>life_expectancy</th>
      <th>hospital_beds_per_thousand</th>
      <th>gdp_per_capita</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>41</th>
      <td>China</td>
      <td>Asia</td>
      <td>1.439324e+09</td>
      <td>76.91</td>
      <td>4.34</td>
      <td>15308.712</td>
    </tr>
    <tr>
      <th>90</th>
      <td>India</td>
      <td>Asia</td>
      <td>1.380004e+09</td>
      <td>69.66</td>
      <td>0.53</td>
      <td>6426.674</td>
    </tr>
    <tr>
      <th>199</th>
      <td>United States</td>
      <td>North America</td>
      <td>3.310026e+08</td>
      <td>78.86</td>
      <td>2.77</td>
      <td>54225.446</td>
    </tr>
    <tr>
      <th>91</th>
      <td>Indonesia</td>
      <td>Asia</td>
      <td>2.735236e+08</td>
      <td>71.72</td>
      <td>1.04</td>
      <td>11188.744</td>
    </tr>
    <tr>
      <th>145</th>
      <td>Pakistan</td>
      <td>Asia</td>
      <td>2.208923e+08</td>
      <td>67.27</td>
      <td>0.60</td>
      <td>5034.708</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Brazil</td>
      <td>South America</td>
      <td>2.125594e+08</td>
      <td>75.88</td>
      <td>2.20</td>
      <td>14103.452</td>
    </tr>
    <tr>
      <th>141</th>
      <td>Nigeria</td>
      <td>Africa</td>
      <td>2.061396e+08</td>
      <td>54.69</td>
      <td>NaN</td>
      <td>5338.454</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Bangladesh</td>
      <td>Asia</td>
      <td>1.646894e+08</td>
      <td>72.59</td>
      <td>0.80</td>
      <td>3523.984</td>
    </tr>
    <tr>
      <th>157</th>
      <td>Russia</td>
      <td>Europe</td>
      <td>1.459345e+08</td>
      <td>72.58</td>
      <td>8.05</td>
      <td>24765.954</td>
    </tr>
    <tr>
      <th>125</th>
      <td>Mexico</td>
      <td>North America</td>
      <td>1.289328e+08</td>
      <td>75.05</td>
      <td>1.38</td>
      <td>17336.469</td>
    </tr>
  </tbody>
</table>
</div>

Q: Add a new column in countries_df to record the overall GDP per country (product of population & per capita GDP).

```python
countries_df['gdp'] = countries_df.population * countries_df.gdp_per_capita
```

```python
countries_df
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>location</th>
      <th>continent</th>
      <th>population</th>
      <th>life_expectancy</th>
      <th>hospital_beds_per_thousand</th>
      <th>gdp_per_capita</th>
      <th>gdp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>38928341.0</td>
      <td>64.83</td>
      <td>0.50</td>
      <td>1803.987</td>
      <td>7.022622e+10</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Albania</td>
      <td>Europe</td>
      <td>2877800.0</td>
      <td>78.57</td>
      <td>2.89</td>
      <td>11803.431</td>
      <td>3.396791e+10</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Algeria</td>
      <td>Africa</td>
      <td>43851043.0</td>
      <td>76.88</td>
      <td>1.90</td>
      <td>13913.839</td>
      <td>6.101364e+11</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Andorra</td>
      <td>Europe</td>
      <td>77265.0</td>
      <td>83.73</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Angola</td>
      <td>Africa</td>
      <td>32866268.0</td>
      <td>61.15</td>
      <td>NaN</td>
      <td>5819.495</td>
      <td>1.912651e+11</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>205</th>
      <td>Vietnam</td>
      <td>Asia</td>
      <td>97338583.0</td>
      <td>75.40</td>
      <td>2.60</td>
      <td>6171.884</td>
      <td>6.007624e+11</td>
    </tr>
    <tr>
      <th>206</th>
      <td>Western Sahara</td>
      <td>Africa</td>
      <td>597330.0</td>
      <td>70.26</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>207</th>
      <td>Yemen</td>
      <td>Asia</td>
      <td>29825968.0</td>
      <td>66.12</td>
      <td>0.70</td>
      <td>1479.147</td>
      <td>4.411699e+10</td>
    </tr>
    <tr>
      <th>208</th>
      <td>Zambia</td>
      <td>Africa</td>
      <td>18383956.0</td>
      <td>63.89</td>
      <td>2.00</td>
      <td>3689.251</td>
      <td>6.782303e+10</td>
    </tr>
    <tr>
      <th>209</th>
      <td>Zimbabwe</td>
      <td>Africa</td>
      <td>14862927.0</td>
      <td>61.49</td>
      <td>1.70</td>
      <td>1899.775</td>
      <td>2.823622e+10</td>
    </tr>
  </tbody>
</table>
<p>210 rows × 7 columns</p>
</div>

Q: (Optional) Create a dataframe containing 10 countries with the lowest GDP per capita, among the counties with population greater than 100 million.

```python
least_gdp_df = countries_df[countries_df.population > 100000000].sort_values('gdp', ascending=True).head(10)
```

```python
least_gdp_df
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>location</th>
      <th>continent</th>
      <th>population</th>
      <th>life_expectancy</th>
      <th>hospital_beds_per_thousand</th>
      <th>gdp_per_capita</th>
      <th>gdp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>63</th>
      <td>Ethiopia</td>
      <td>Africa</td>
      <td>114963583.0</td>
      <td>66.60</td>
      <td>0.30</td>
      <td>1729.927</td>
      <td>1.988786e+11</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Bangladesh</td>
      <td>Asia</td>
      <td>164689383.0</td>
      <td>72.59</td>
      <td>0.80</td>
      <td>3523.984</td>
      <td>5.803628e+11</td>
    </tr>
    <tr>
      <th>151</th>
      <td>Philippines</td>
      <td>Asia</td>
      <td>109581085.0</td>
      <td>71.23</td>
      <td>1.00</td>
      <td>7599.188</td>
      <td>8.327273e+11</td>
    </tr>
    <tr>
      <th>58</th>
      <td>Egypt</td>
      <td>Africa</td>
      <td>102334403.0</td>
      <td>71.99</td>
      <td>1.60</td>
      <td>10550.206</td>
      <td>1.079649e+12</td>
    </tr>
    <tr>
      <th>141</th>
      <td>Nigeria</td>
      <td>Africa</td>
      <td>206139587.0</td>
      <td>54.69</td>
      <td>NaN</td>
      <td>5338.454</td>
      <td>1.100467e+12</td>
    </tr>
    <tr>
      <th>145</th>
      <td>Pakistan</td>
      <td>Asia</td>
      <td>220892331.0</td>
      <td>67.27</td>
      <td>0.60</td>
      <td>5034.708</td>
      <td>1.112128e+12</td>
    </tr>
    <tr>
      <th>125</th>
      <td>Mexico</td>
      <td>North America</td>
      <td>128932753.0</td>
      <td>75.05</td>
      <td>1.38</td>
      <td>17336.469</td>
      <td>2.235239e+12</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Brazil</td>
      <td>South America</td>
      <td>212559409.0</td>
      <td>75.88</td>
      <td>2.20</td>
      <td>14103.452</td>
      <td>2.997821e+12</td>
    </tr>
    <tr>
      <th>91</th>
      <td>Indonesia</td>
      <td>Asia</td>
      <td>273523621.0</td>
      <td>71.72</td>
      <td>1.04</td>
      <td>11188.744</td>
      <td>3.060386e+12</td>
    </tr>
    <tr>
      <th>157</th>
      <td>Russia</td>
      <td>Europe</td>
      <td>145934460.0</td>
      <td>72.58</td>
      <td>8.05</td>
      <td>24765.954</td>
      <td>3.614206e+12</td>
    </tr>
  </tbody>
</table>
</div>

Q: Create a data frame that counts the number countries in each continent?

Hint: Use groupby, select the location column and aggregate using count.

```python
country_counts_df = countries_df.groupby('continent')['location'].count()
```

```python
country_counts_df
```

    continent
    Africa           55
    Asia             47
    Europe           51
    North America    36
    Oceania           8
    South America    13
    Name: location, dtype: int64

Q: Create a data frame showing the total population of each continent.

Hint: Use groupby, select the population column and aggregate using sum.

```python
continent_populations_df = countries_df.groupby('continent')['population'].sum()
```

```python
continent_populations_df
```

    continent
    Africa           1.339424e+09
    Asia             4.607388e+09
    Europe           7.485062e+08
    North America    5.912425e+08
    Oceania          4.095832e+07
    South America    4.304611e+08
    Name: population, dtype: float64

Let's download another CSV file containing overall Covid-19 stats for various countires, and read the data into another Pandas data frame.


```python
urlretrieve('https://hub.jovian.ml/wp-content/uploads/2020/09/covid-countries-data.csv', 
            'covid-countries-data.csv')
```

    ('covid-countries-data.csv', <http.client.HTTPMessage at 0x19f75ddd550>)

```python
covid_data_df = pd.read_csv('covid-countries-data.csv')
```

```python
covid_data_df
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>location</th>
      <th>total_cases</th>
      <th>total_deaths</th>
      <th>total_tests</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>38243.0</td>
      <td>1409.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Albania</td>
      <td>9728.0</td>
      <td>296.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Algeria</td>
      <td>45158.0</td>
      <td>1525.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Andorra</td>
      <td>1199.0</td>
      <td>53.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Angola</td>
      <td>2729.0</td>
      <td>109.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>207</th>
      <td>Western Sahara</td>
      <td>766.0</td>
      <td>1.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>208</th>
      <td>World</td>
      <td>26059065.0</td>
      <td>863535.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>209</th>
      <td>Yemen</td>
      <td>1976.0</td>
      <td>571.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>210</th>
      <td>Zambia</td>
      <td>12415.0</td>
      <td>292.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>211</th>
      <td>Zimbabwe</td>
      <td>6638.0</td>
      <td>206.0</td>
      <td>97272.0</td>
    </tr>
  </tbody>
</table>
<p>212 rows × 4 columns</p>
</div>


Q: Count the number of countries for which the total_tests data is missing.

Hint: Use the .isna method.

```python
total_tests_missing = covid_data_df.total_tests.isna().sum()
```

```python
print("The data for total tests is missing for {} countries.".format(int(total_tests_missing)))
```

    The data for total tests is missing for 122 countries.
    

Let's merge the two data frames, and compute some more metrics.

Q: Merge countries_df with covid_data_df on the location column.

*Hint: Use the .merge method on countries_df.

```python
combined_df = countries_df.merge(covid_data_df, on='location')
```

```python
combined_df
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>location</th>
      <th>continent</th>
      <th>population</th>
      <th>life_expectancy</th>
      <th>hospital_beds_per_thousand</th>
      <th>gdp_per_capita</th>
      <th>gdp</th>
      <th>total_cases</th>
      <th>total_deaths</th>
      <th>total_tests</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>38928341.0</td>
      <td>64.83</td>
      <td>0.50</td>
      <td>1803.987</td>
      <td>7.022622e+10</td>
      <td>38243.0</td>
      <td>1409.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Albania</td>
      <td>Europe</td>
      <td>2877800.0</td>
      <td>78.57</td>
      <td>2.89</td>
      <td>11803.431</td>
      <td>3.396791e+10</td>
      <td>9728.0</td>
      <td>296.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Algeria</td>
      <td>Africa</td>
      <td>43851043.0</td>
      <td>76.88</td>
      <td>1.90</td>
      <td>13913.839</td>
      <td>6.101364e+11</td>
      <td>45158.0</td>
      <td>1525.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Andorra</td>
      <td>Europe</td>
      <td>77265.0</td>
      <td>83.73</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1199.0</td>
      <td>53.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Angola</td>
      <td>Africa</td>
      <td>32866268.0</td>
      <td>61.15</td>
      <td>NaN</td>
      <td>5819.495</td>
      <td>1.912651e+11</td>
      <td>2729.0</td>
      <td>109.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>205</th>
      <td>Vietnam</td>
      <td>Asia</td>
      <td>97338583.0</td>
      <td>75.40</td>
      <td>2.60</td>
      <td>6171.884</td>
      <td>6.007624e+11</td>
      <td>1046.0</td>
      <td>35.0</td>
      <td>261004.0</td>
    </tr>
    <tr>
      <th>206</th>
      <td>Western Sahara</td>
      <td>Africa</td>
      <td>597330.0</td>
      <td>70.26</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>766.0</td>
      <td>1.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>207</th>
      <td>Yemen</td>
      <td>Asia</td>
      <td>29825968.0</td>
      <td>66.12</td>
      <td>0.70</td>
      <td>1479.147</td>
      <td>4.411699e+10</td>
      <td>1976.0</td>
      <td>571.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>208</th>
      <td>Zambia</td>
      <td>Africa</td>
      <td>18383956.0</td>
      <td>63.89</td>
      <td>2.00</td>
      <td>3689.251</td>
      <td>6.782303e+10</td>
      <td>12415.0</td>
      <td>292.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>209</th>
      <td>Zimbabwe</td>
      <td>Africa</td>
      <td>14862927.0</td>
      <td>61.49</td>
      <td>1.70</td>
      <td>1899.775</td>
      <td>2.823622e+10</td>
      <td>6638.0</td>
      <td>206.0</td>
      <td>97272.0</td>
    </tr>
  </tbody>
</table>
<p>210 rows × 10 columns</p>
</div>

Q: Add columns tests_per_million, cases_per_million and deaths_per_million into combined_df.


```python
combined_df['tests_per_million'] = combined_df['total_tests'] * 1e6 / combined_df['population']
```

```python
combined_df['cases_per_million'] = combined_df['total_cases'] * 1e6 / combined_df['population']
```

```python
combined_df['deaths_per_million'] = combined_df['total_deaths'] * 1e6 / combined_df['population']
```

```python
combined_df
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>location</th>
      <th>continent</th>
      <th>population</th>
      <th>life_expectancy</th>
      <th>hospital_beds_per_thousand</th>
      <th>gdp_per_capita</th>
      <th>gdp</th>
      <th>total_cases</th>
      <th>total_deaths</th>
      <th>total_tests</th>
      <th>tests_per_million</th>
      <th>cases_per_million</th>
      <th>deaths_per_million</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>38928341.0</td>
      <td>64.83</td>
      <td>0.50</td>
      <td>1803.987</td>
      <td>7.022622e+10</td>
      <td>38243.0</td>
      <td>1409.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>982.394806</td>
      <td>36.194710</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Albania</td>
      <td>Europe</td>
      <td>2877800.0</td>
      <td>78.57</td>
      <td>2.89</td>
      <td>11803.431</td>
      <td>3.396791e+10</td>
      <td>9728.0</td>
      <td>296.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3380.359997</td>
      <td>102.856349</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Algeria</td>
      <td>Africa</td>
      <td>43851043.0</td>
      <td>76.88</td>
      <td>1.90</td>
      <td>13913.839</td>
      <td>6.101364e+11</td>
      <td>45158.0</td>
      <td>1525.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1029.804468</td>
      <td>34.776824</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Andorra</td>
      <td>Europe</td>
      <td>77265.0</td>
      <td>83.73</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1199.0</td>
      <td>53.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>15518.022390</td>
      <td>685.950948</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Angola</td>
      <td>Africa</td>
      <td>32866268.0</td>
      <td>61.15</td>
      <td>NaN</td>
      <td>5819.495</td>
      <td>1.912651e+11</td>
      <td>2729.0</td>
      <td>109.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>83.033462</td>
      <td>3.316470</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>205</th>
      <td>Vietnam</td>
      <td>Asia</td>
      <td>97338583.0</td>
      <td>75.40</td>
      <td>2.60</td>
      <td>6171.884</td>
      <td>6.007624e+11</td>
      <td>1046.0</td>
      <td>35.0</td>
      <td>261004.0</td>
      <td>2681.403324</td>
      <td>10.745996</td>
      <td>0.359570</td>
    </tr>
    <tr>
      <th>206</th>
      <td>Western Sahara</td>
      <td>Africa</td>
      <td>597330.0</td>
      <td>70.26</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>766.0</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1282.373228</td>
      <td>1.674116</td>
    </tr>
    <tr>
      <th>207</th>
      <td>Yemen</td>
      <td>Asia</td>
      <td>29825968.0</td>
      <td>66.12</td>
      <td>0.70</td>
      <td>1479.147</td>
      <td>4.411699e+10</td>
      <td>1976.0</td>
      <td>571.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>66.250993</td>
      <td>19.144391</td>
    </tr>
    <tr>
      <th>208</th>
      <td>Zambia</td>
      <td>Africa</td>
      <td>18383956.0</td>
      <td>63.89</td>
      <td>2.00</td>
      <td>3689.251</td>
      <td>6.782303e+10</td>
      <td>12415.0</td>
      <td>292.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>675.317108</td>
      <td>15.883415</td>
    </tr>
    <tr>
      <th>209</th>
      <td>Zimbabwe</td>
      <td>Africa</td>
      <td>14862927.0</td>
      <td>61.49</td>
      <td>1.70</td>
      <td>1899.775</td>
      <td>2.823622e+10</td>
      <td>6638.0</td>
      <td>206.0</td>
      <td>97272.0</td>
      <td>6544.605918</td>
      <td>446.614587</td>
      <td>13.859989</td>
    </tr>
  </tbody>
</table>
<p>210 rows × 13 columns</p>
</div>


Q: Create a dataframe with 10 countires that have highest number of tests per million people.

```python
highest_tests_df = combined_df.sort_values('tests_per_million', ascending=False).head(10)
```

```python
highest_tests_df
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>location</th>
      <th>continent</th>
      <th>population</th>
      <th>life_expectancy</th>
      <th>hospital_beds_per_thousand</th>
      <th>gdp_per_capita</th>
      <th>gdp</th>
      <th>total_cases</th>
      <th>total_deaths</th>
      <th>total_tests</th>
      <th>tests_per_million</th>
      <th>cases_per_million</th>
      <th>deaths_per_million</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>197</th>
      <td>United Arab Emirates</td>
      <td>Asia</td>
      <td>9890400.0</td>
      <td>77.97</td>
      <td>1.200</td>
      <td>67293.483</td>
      <td>6.655595e+11</td>
      <td>71540.0</td>
      <td>387.0</td>
      <td>7177430.0</td>
      <td>725696.635121</td>
      <td>7233.276713</td>
      <td>39.128852</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Bahrain</td>
      <td>Asia</td>
      <td>1701583.0</td>
      <td>77.29</td>
      <td>2.000</td>
      <td>43290.705</td>
      <td>7.366273e+10</td>
      <td>52440.0</td>
      <td>190.0</td>
      <td>1118837.0</td>
      <td>657527.137965</td>
      <td>30818.361490</td>
      <td>111.660730</td>
    </tr>
    <tr>
      <th>115</th>
      <td>Luxembourg</td>
      <td>Europe</td>
      <td>625976.0</td>
      <td>82.25</td>
      <td>4.510</td>
      <td>94277.965</td>
      <td>5.901574e+10</td>
      <td>7928.0</td>
      <td>124.0</td>
      <td>385820.0</td>
      <td>616349.508607</td>
      <td>12665.022301</td>
      <td>198.090662</td>
    </tr>
    <tr>
      <th>122</th>
      <td>Malta</td>
      <td>Europe</td>
      <td>441539.0</td>
      <td>82.53</td>
      <td>4.485</td>
      <td>36513.323</td>
      <td>1.612206e+10</td>
      <td>1931.0</td>
      <td>13.0</td>
      <td>188539.0</td>
      <td>427004.183096</td>
      <td>4373.339614</td>
      <td>29.442473</td>
    </tr>
    <tr>
      <th>53</th>
      <td>Denmark</td>
      <td>Europe</td>
      <td>5792203.0</td>
      <td>80.90</td>
      <td>2.500</td>
      <td>46682.515</td>
      <td>2.703946e+11</td>
      <td>17195.0</td>
      <td>626.0</td>
      <td>2447911.0</td>
      <td>422621.755488</td>
      <td>2968.645954</td>
      <td>108.076323</td>
    </tr>
    <tr>
      <th>96</th>
      <td>Israel</td>
      <td>Asia</td>
      <td>8655541.0</td>
      <td>82.97</td>
      <td>2.990</td>
      <td>33132.320</td>
      <td>2.867782e+11</td>
      <td>122539.0</td>
      <td>969.0</td>
      <td>2353984.0</td>
      <td>271962.665303</td>
      <td>14157.289533</td>
      <td>111.951408</td>
    </tr>
    <tr>
      <th>89</th>
      <td>Iceland</td>
      <td>Europe</td>
      <td>341250.0</td>
      <td>82.99</td>
      <td>2.910</td>
      <td>46482.958</td>
      <td>1.586231e+10</td>
      <td>2121.0</td>
      <td>10.0</td>
      <td>88829.0</td>
      <td>260304.761905</td>
      <td>6215.384615</td>
      <td>29.304029</td>
    </tr>
    <tr>
      <th>157</th>
      <td>Russia</td>
      <td>Europe</td>
      <td>145934460.0</td>
      <td>72.58</td>
      <td>8.050</td>
      <td>24765.954</td>
      <td>3.614206e+12</td>
      <td>1005000.0</td>
      <td>17414.0</td>
      <td>37176827.0</td>
      <td>254750.159763</td>
      <td>6886.653091</td>
      <td>119.327539</td>
    </tr>
    <tr>
      <th>199</th>
      <td>United States</td>
      <td>North America</td>
      <td>331002647.0</td>
      <td>78.86</td>
      <td>2.770</td>
      <td>54225.446</td>
      <td>1.794877e+13</td>
      <td>6114406.0</td>
      <td>185744.0</td>
      <td>83898416.0</td>
      <td>253467.507769</td>
      <td>18472.377957</td>
      <td>561.155633</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Australia</td>
      <td>Oceania</td>
      <td>25499881.0</td>
      <td>83.44</td>
      <td>3.840</td>
      <td>44648.710</td>
      <td>1.138537e+12</td>
      <td>25923.0</td>
      <td>663.0</td>
      <td>6255797.0</td>
      <td>245326.517406</td>
      <td>1016.592979</td>
      <td>26.000121</td>
    </tr>
  </tbody>
</table>
</div>

Q: Create a dataframe with 10 countires that have highest number of positive cases per million people.

```python
highest_cases_df = combined_df.sort_values('cases_per_million', ascending=False).head(10)
```

```python
highest_cases_df
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>location</th>
      <th>continent</th>
      <th>population</th>
      <th>life_expectancy</th>
      <th>hospital_beds_per_thousand</th>
      <th>gdp_per_capita</th>
      <th>gdp</th>
      <th>total_cases</th>
      <th>total_deaths</th>
      <th>total_tests</th>
      <th>tests_per_million</th>
      <th>cases_per_million</th>
      <th>deaths_per_million</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>155</th>
      <td>Qatar</td>
      <td>Asia</td>
      <td>2881060.0</td>
      <td>80.23</td>
      <td>1.20</td>
      <td>116935.600</td>
      <td>3.368985e+11</td>
      <td>119206.0</td>
      <td>199.0</td>
      <td>634745.0</td>
      <td>220316.480740</td>
      <td>41375.743650</td>
      <td>69.071800</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Bahrain</td>
      <td>Asia</td>
      <td>1701583.0</td>
      <td>77.29</td>
      <td>2.00</td>
      <td>43290.705</td>
      <td>7.366273e+10</td>
      <td>52440.0</td>
      <td>190.0</td>
      <td>1118837.0</td>
      <td>657527.137965</td>
      <td>30818.361490</td>
      <td>111.660730</td>
    </tr>
    <tr>
      <th>147</th>
      <td>Panama</td>
      <td>North America</td>
      <td>4314768.0</td>
      <td>78.51</td>
      <td>2.30</td>
      <td>22267.037</td>
      <td>9.607710e+10</td>
      <td>94084.0</td>
      <td>2030.0</td>
      <td>336345.0</td>
      <td>77952.047480</td>
      <td>21805.112117</td>
      <td>470.477208</td>
    </tr>
    <tr>
      <th>40</th>
      <td>Chile</td>
      <td>South America</td>
      <td>19116209.0</td>
      <td>80.18</td>
      <td>2.11</td>
      <td>22767.037</td>
      <td>4.352194e+11</td>
      <td>414739.0</td>
      <td>11344.0</td>
      <td>2458762.0</td>
      <td>128621.841287</td>
      <td>21695.671982</td>
      <td>593.423100</td>
    </tr>
    <tr>
      <th>162</th>
      <td>San Marino</td>
      <td>Europe</td>
      <td>33938.0</td>
      <td>84.97</td>
      <td>3.80</td>
      <td>56861.470</td>
      <td>1.929765e+09</td>
      <td>735.0</td>
      <td>42.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>21657.139490</td>
      <td>1237.550828</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Aruba</td>
      <td>North America</td>
      <td>106766.0</td>
      <td>76.29</td>
      <td>NaN</td>
      <td>35973.781</td>
      <td>3.840777e+09</td>
      <td>2211.0</td>
      <td>12.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>20708.839893</td>
      <td>112.395332</td>
    </tr>
    <tr>
      <th>105</th>
      <td>Kuwait</td>
      <td>Asia</td>
      <td>4270563.0</td>
      <td>75.49</td>
      <td>2.00</td>
      <td>65530.537</td>
      <td>2.798523e+11</td>
      <td>86478.0</td>
      <td>535.0</td>
      <td>621616.0</td>
      <td>145558.325682</td>
      <td>20249.789079</td>
      <td>125.276222</td>
    </tr>
    <tr>
      <th>150</th>
      <td>Peru</td>
      <td>South America</td>
      <td>32971846.0</td>
      <td>76.74</td>
      <td>1.60</td>
      <td>12236.706</td>
      <td>4.034668e+11</td>
      <td>663437.0</td>
      <td>29259.0</td>
      <td>584232.0</td>
      <td>17719.117092</td>
      <td>20121.318048</td>
      <td>887.393445</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Brazil</td>
      <td>South America</td>
      <td>212559409.0</td>
      <td>75.88</td>
      <td>2.20</td>
      <td>14103.452</td>
      <td>2.997821e+12</td>
      <td>3997865.0</td>
      <td>123780.0</td>
      <td>4797948.0</td>
      <td>22572.268255</td>
      <td>18808.224105</td>
      <td>582.331314</td>
    </tr>
    <tr>
      <th>199</th>
      <td>United States</td>
      <td>North America</td>
      <td>331002647.0</td>
      <td>78.86</td>
      <td>2.77</td>
      <td>54225.446</td>
      <td>1.794877e+13</td>
      <td>6114406.0</td>
      <td>185744.0</td>
      <td>83898416.0</td>
      <td>253467.507769</td>
      <td>18472.377957</td>
      <td>561.155633</td>
    </tr>
  </tbody>
</table>
</div>


Q: Create a dataframe with 10 countires that have highest number of deaths cases per million people?

```python
highest_deaths_df = combined_df.sort_values('deaths_per_million', ascending=False).head(10)
```

```python
highest_deaths_df
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>location</th>
      <th>continent</th>
      <th>population</th>
      <th>life_expectancy</th>
      <th>hospital_beds_per_thousand</th>
      <th>gdp_per_capita</th>
      <th>gdp</th>
      <th>total_cases</th>
      <th>total_deaths</th>
      <th>total_tests</th>
      <th>tests_per_million</th>
      <th>cases_per_million</th>
      <th>deaths_per_million</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>162</th>
      <td>San Marino</td>
      <td>Europe</td>
      <td>33938.0</td>
      <td>84.97</td>
      <td>3.80</td>
      <td>56861.470</td>
      <td>1.929765e+09</td>
      <td>735.0</td>
      <td>42.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>21657.139490</td>
      <td>1237.550828</td>
    </tr>
    <tr>
      <th>150</th>
      <td>Peru</td>
      <td>South America</td>
      <td>32971846.0</td>
      <td>76.74</td>
      <td>1.60</td>
      <td>12236.706</td>
      <td>4.034668e+11</td>
      <td>663437.0</td>
      <td>29259.0</td>
      <td>584232.0</td>
      <td>17719.117092</td>
      <td>20121.318048</td>
      <td>887.393445</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Belgium</td>
      <td>Europe</td>
      <td>11589616.0</td>
      <td>81.63</td>
      <td>5.64</td>
      <td>42658.576</td>
      <td>4.943965e+11</td>
      <td>85817.0</td>
      <td>9898.0</td>
      <td>2281853.0</td>
      <td>196887.713967</td>
      <td>7404.645676</td>
      <td>854.040375</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Andorra</td>
      <td>Europe</td>
      <td>77265.0</td>
      <td>83.73</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1199.0</td>
      <td>53.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>15518.022390</td>
      <td>685.950948</td>
    </tr>
    <tr>
      <th>177</th>
      <td>Spain</td>
      <td>Europe</td>
      <td>46754783.0</td>
      <td>83.56</td>
      <td>2.97</td>
      <td>34272.360</td>
      <td>1.602397e+12</td>
      <td>479554.0</td>
      <td>29194.0</td>
      <td>6416533.0</td>
      <td>137238.001939</td>
      <td>10256.790198</td>
      <td>624.406705</td>
    </tr>
    <tr>
      <th>198</th>
      <td>United Kingdom</td>
      <td>Europe</td>
      <td>67886004.0</td>
      <td>81.32</td>
      <td>2.54</td>
      <td>39753.244</td>
      <td>2.698689e+12</td>
      <td>338676.0</td>
      <td>41514.0</td>
      <td>13447568.0</td>
      <td>198090.434075</td>
      <td>4988.892850</td>
      <td>611.525168</td>
    </tr>
    <tr>
      <th>40</th>
      <td>Chile</td>
      <td>South America</td>
      <td>19116209.0</td>
      <td>80.18</td>
      <td>2.11</td>
      <td>22767.037</td>
      <td>4.352194e+11</td>
      <td>414739.0</td>
      <td>11344.0</td>
      <td>2458762.0</td>
      <td>128621.841287</td>
      <td>21695.671982</td>
      <td>593.423100</td>
    </tr>
    <tr>
      <th>97</th>
      <td>Italy</td>
      <td>Europe</td>
      <td>60461828.0</td>
      <td>83.51</td>
      <td>3.18</td>
      <td>35220.084</td>
      <td>2.129471e+12</td>
      <td>271515.0</td>
      <td>35497.0</td>
      <td>5214766.0</td>
      <td>86248.897403</td>
      <td>4490.684602</td>
      <td>587.097697</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Brazil</td>
      <td>South America</td>
      <td>212559409.0</td>
      <td>75.88</td>
      <td>2.20</td>
      <td>14103.452</td>
      <td>2.997821e+12</td>
      <td>3997865.0</td>
      <td>123780.0</td>
      <td>4797948.0</td>
      <td>22572.268255</td>
      <td>18808.224105</td>
      <td>582.331314</td>
    </tr>
    <tr>
      <th>182</th>
      <td>Sweden</td>
      <td>Europe</td>
      <td>10099270.0</td>
      <td>82.80</td>
      <td>2.22</td>
      <td>46949.283</td>
      <td>4.741535e+11</td>
      <td>84532.0</td>
      <td>5820.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8370.109919</td>
      <td>576.279276</td>
    </tr>
  </tbody>
</table>
</div>


(Optional) Q: Count number of countries that feature in both the lists of "highest number of tests per million" and "highest number of cases per million".

```python
merged_frame = pd.concat([highest_tests_df, highest_cases_df])
```

```python
merged_frame
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>location</th>
      <th>continent</th>
      <th>population</th>
      <th>life_expectancy</th>
      <th>hospital_beds_per_thousand</th>
      <th>gdp_per_capita</th>
      <th>gdp</th>
      <th>total_cases</th>
      <th>total_deaths</th>
      <th>total_tests</th>
      <th>tests_per_million</th>
      <th>cases_per_million</th>
      <th>deaths_per_million</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>197</th>
      <td>United Arab Emirates</td>
      <td>Asia</td>
      <td>9890400.0</td>
      <td>77.97</td>
      <td>1.200</td>
      <td>67293.483</td>
      <td>6.655595e+11</td>
      <td>71540.0</td>
      <td>387.0</td>
      <td>7177430.0</td>
      <td>725696.635121</td>
      <td>7233.276713</td>
      <td>39.128852</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Bahrain</td>
      <td>Asia</td>
      <td>1701583.0</td>
      <td>77.29</td>
      <td>2.000</td>
      <td>43290.705</td>
      <td>7.366273e+10</td>
      <td>52440.0</td>
      <td>190.0</td>
      <td>1118837.0</td>
      <td>657527.137965</td>
      <td>30818.361490</td>
      <td>111.660730</td>
    </tr>
    <tr>
      <th>115</th>
      <td>Luxembourg</td>
      <td>Europe</td>
      <td>625976.0</td>
      <td>82.25</td>
      <td>4.510</td>
      <td>94277.965</td>
      <td>5.901574e+10</td>
      <td>7928.0</td>
      <td>124.0</td>
      <td>385820.0</td>
      <td>616349.508607</td>
      <td>12665.022301</td>
      <td>198.090662</td>
    </tr>
    <tr>
      <th>122</th>
      <td>Malta</td>
      <td>Europe</td>
      <td>441539.0</td>
      <td>82.53</td>
      <td>4.485</td>
      <td>36513.323</td>
      <td>1.612206e+10</td>
      <td>1931.0</td>
      <td>13.0</td>
      <td>188539.0</td>
      <td>427004.183096</td>
      <td>4373.339614</td>
      <td>29.442473</td>
    </tr>
    <tr>
      <th>53</th>
      <td>Denmark</td>
      <td>Europe</td>
      <td>5792203.0</td>
      <td>80.90</td>
      <td>2.500</td>
      <td>46682.515</td>
      <td>2.703946e+11</td>
      <td>17195.0</td>
      <td>626.0</td>
      <td>2447911.0</td>
      <td>422621.755488</td>
      <td>2968.645954</td>
      <td>108.076323</td>
    </tr>
    <tr>
      <th>96</th>
      <td>Israel</td>
      <td>Asia</td>
      <td>8655541.0</td>
      <td>82.97</td>
      <td>2.990</td>
      <td>33132.320</td>
      <td>2.867782e+11</td>
      <td>122539.0</td>
      <td>969.0</td>
      <td>2353984.0</td>
      <td>271962.665303</td>
      <td>14157.289533</td>
      <td>111.951408</td>
    </tr>
    <tr>
      <th>89</th>
      <td>Iceland</td>
      <td>Europe</td>
      <td>341250.0</td>
      <td>82.99</td>
      <td>2.910</td>
      <td>46482.958</td>
      <td>1.586231e+10</td>
      <td>2121.0</td>
      <td>10.0</td>
      <td>88829.0</td>
      <td>260304.761905</td>
      <td>6215.384615</td>
      <td>29.304029</td>
    </tr>
    <tr>
      <th>157</th>
      <td>Russia</td>
      <td>Europe</td>
      <td>145934460.0</td>
      <td>72.58</td>
      <td>8.050</td>
      <td>24765.954</td>
      <td>3.614206e+12</td>
      <td>1005000.0</td>
      <td>17414.0</td>
      <td>37176827.0</td>
      <td>254750.159763</td>
      <td>6886.653091</td>
      <td>119.327539</td>
    </tr>
    <tr>
      <th>199</th>
      <td>United States</td>
      <td>North America</td>
      <td>331002647.0</td>
      <td>78.86</td>
      <td>2.770</td>
      <td>54225.446</td>
      <td>1.794877e+13</td>
      <td>6114406.0</td>
      <td>185744.0</td>
      <td>83898416.0</td>
      <td>253467.507769</td>
      <td>18472.377957</td>
      <td>561.155633</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Australia</td>
      <td>Oceania</td>
      <td>25499881.0</td>
      <td>83.44</td>
      <td>3.840</td>
      <td>44648.710</td>
      <td>1.138537e+12</td>
      <td>25923.0</td>
      <td>663.0</td>
      <td>6255797.0</td>
      <td>245326.517406</td>
      <td>1016.592979</td>
      <td>26.000121</td>
    </tr>
    <tr>
      <th>155</th>
      <td>Qatar</td>
      <td>Asia</td>
      <td>2881060.0</td>
      <td>80.23</td>
      <td>1.200</td>
      <td>116935.600</td>
      <td>3.368985e+11</td>
      <td>119206.0</td>
      <td>199.0</td>
      <td>634745.0</td>
      <td>220316.480740</td>
      <td>41375.743650</td>
      <td>69.071800</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Bahrain</td>
      <td>Asia</td>
      <td>1701583.0</td>
      <td>77.29</td>
      <td>2.000</td>
      <td>43290.705</td>
      <td>7.366273e+10</td>
      <td>52440.0</td>
      <td>190.0</td>
      <td>1118837.0</td>
      <td>657527.137965</td>
      <td>30818.361490</td>
      <td>111.660730</td>
    </tr>
    <tr>
      <th>147</th>
      <td>Panama</td>
      <td>North America</td>
      <td>4314768.0</td>
      <td>78.51</td>
      <td>2.300</td>
      <td>22267.037</td>
      <td>9.607710e+10</td>
      <td>94084.0</td>
      <td>2030.0</td>
      <td>336345.0</td>
      <td>77952.047480</td>
      <td>21805.112117</td>
      <td>470.477208</td>
    </tr>
    <tr>
      <th>40</th>
      <td>Chile</td>
      <td>South America</td>
      <td>19116209.0</td>
      <td>80.18</td>
      <td>2.110</td>
      <td>22767.037</td>
      <td>4.352194e+11</td>
      <td>414739.0</td>
      <td>11344.0</td>
      <td>2458762.0</td>
      <td>128621.841287</td>
      <td>21695.671982</td>
      <td>593.423100</td>
    </tr>
    <tr>
      <th>162</th>
      <td>San Marino</td>
      <td>Europe</td>
      <td>33938.0</td>
      <td>84.97</td>
      <td>3.800</td>
      <td>56861.470</td>
      <td>1.929765e+09</td>
      <td>735.0</td>
      <td>42.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>21657.139490</td>
      <td>1237.550828</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Aruba</td>
      <td>North America</td>
      <td>106766.0</td>
      <td>76.29</td>
      <td>NaN</td>
      <td>35973.781</td>
      <td>3.840777e+09</td>
      <td>2211.0</td>
      <td>12.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>20708.839893</td>
      <td>112.395332</td>
    </tr>
    <tr>
      <th>105</th>
      <td>Kuwait</td>
      <td>Asia</td>
      <td>4270563.0</td>
      <td>75.49</td>
      <td>2.000</td>
      <td>65530.537</td>
      <td>2.798523e+11</td>
      <td>86478.0</td>
      <td>535.0</td>
      <td>621616.0</td>
      <td>145558.325682</td>
      <td>20249.789079</td>
      <td>125.276222</td>
    </tr>
    <tr>
      <th>150</th>
      <td>Peru</td>
      <td>South America</td>
      <td>32971846.0</td>
      <td>76.74</td>
      <td>1.600</td>
      <td>12236.706</td>
      <td>4.034668e+11</td>
      <td>663437.0</td>
      <td>29259.0</td>
      <td>584232.0</td>
      <td>17719.117092</td>
      <td>20121.318048</td>
      <td>887.393445</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Brazil</td>
      <td>South America</td>
      <td>212559409.0</td>
      <td>75.88</td>
      <td>2.200</td>
      <td>14103.452</td>
      <td>2.997821e+12</td>
      <td>3997865.0</td>
      <td>123780.0</td>
      <td>4797948.0</td>
      <td>22572.268255</td>
      <td>18808.224105</td>
      <td>582.331314</td>
    </tr>
    <tr>
      <th>199</th>
      <td>United States</td>
      <td>North America</td>
      <td>331002647.0</td>
      <td>78.86</td>
      <td>2.770</td>
      <td>54225.446</td>
      <td>1.794877e+13</td>
      <td>6114406.0</td>
      <td>185744.0</td>
      <td>83898416.0</td>
      <td>253467.507769</td>
      <td>18472.377957</td>
      <td>561.155633</td>
    </tr>
  </tbody>
</table>
</div>


```python
country_count = merged_frame.groupby('location')['location'].count().sort_values(ascending=False)
```

```python
country_count
```

    location
    United States           2
    Bahrain                 2
    United Arab Emirates    1
    Australia               1
    Brazil                  1
    Chile                   1
    Denmark                 1
    Iceland                 1
    Israel                  1
    Kuwait                  1
    Luxembourg              1
    Malta                   1
    Panama                  1
    Peru                    1
    Qatar                   1
    Russia                  1
    San Marino              1
    Aruba                   1
    Name: location, dtype: int64




```python
print("There are 2 countries that feature in both \nthe lists of \"highest number of tests per million\" and \"highest number of cases per million\".")
```

    There are 2 countries that feature in both 
    the lists of "highest number of tests per million" and "highest number of cases per million".


(Optional) Q: Count number of countries that feature in both the lists "20 countries with lowest GDP per capita" and "20 countries with the lowest number of hospital beds per thousand population". Only consider countries with a population higher than 10 million while creating the list.


```python
gdp_20 = countries_df[countries_df.population > 10000000].sort_values('gdp_per_capita', ascending=True).head(20)
```

```python
gdp_20
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>location</th>
      <th>continent</th>
      <th>population</th>
      <th>life_expectancy</th>
      <th>hospital_beds_per_thousand</th>
      <th>gdp_per_capita</th>
      <th>gdp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>32</th>
      <td>Burundi</td>
      <td>Africa</td>
      <td>11890781.0</td>
      <td>61.58</td>
      <td>0.8</td>
      <td>702.225</td>
      <td>8.350004e+09</td>
    </tr>
    <tr>
      <th>52</th>
      <td>Democratic Republic of Congo</td>
      <td>Africa</td>
      <td>89561404.0</td>
      <td>60.68</td>
      <td>NaN</td>
      <td>808.133</td>
      <td>7.237753e+10</td>
    </tr>
    <tr>
      <th>140</th>
      <td>Niger</td>
      <td>Africa</td>
      <td>24206636.0</td>
      <td>62.42</td>
      <td>0.3</td>
      <td>926.000</td>
      <td>2.241534e+10</td>
    </tr>
    <tr>
      <th>118</th>
      <td>Malawi</td>
      <td>Africa</td>
      <td>19129955.0</td>
      <td>64.26</td>
      <td>1.3</td>
      <td>1095.042</td>
      <td>2.094810e+10</td>
    </tr>
    <tr>
      <th>132</th>
      <td>Mozambique</td>
      <td>Africa</td>
      <td>31255435.0</td>
      <td>60.85</td>
      <td>0.7</td>
      <td>1136.103</td>
      <td>3.550939e+10</td>
    </tr>
    <tr>
      <th>117</th>
      <td>Madagascar</td>
      <td>Africa</td>
      <td>27691019.0</td>
      <td>67.04</td>
      <td>0.2</td>
      <td>1416.440</td>
      <td>3.922267e+10</td>
    </tr>
    <tr>
      <th>207</th>
      <td>Yemen</td>
      <td>Asia</td>
      <td>29825968.0</td>
      <td>66.12</td>
      <td>0.7</td>
      <td>1479.147</td>
      <td>4.411699e+10</td>
    </tr>
    <tr>
      <th>176</th>
      <td>South Sudan</td>
      <td>Africa</td>
      <td>11193729.0</td>
      <td>57.85</td>
      <td>NaN</td>
      <td>1569.888</td>
      <td>1.757290e+10</td>
    </tr>
    <tr>
      <th>85</th>
      <td>Haiti</td>
      <td>North America</td>
      <td>11402533.0</td>
      <td>64.00</td>
      <td>0.7</td>
      <td>1653.173</td>
      <td>1.885036e+10</td>
    </tr>
    <tr>
      <th>195</th>
      <td>Uganda</td>
      <td>Africa</td>
      <td>45741000.0</td>
      <td>63.37</td>
      <td>0.5</td>
      <td>1697.707</td>
      <td>7.765482e+10</td>
    </tr>
    <tr>
      <th>31</th>
      <td>Burkina Faso</td>
      <td>Africa</td>
      <td>20903278.0</td>
      <td>61.58</td>
      <td>0.4</td>
      <td>1703.102</td>
      <td>3.560041e+10</td>
    </tr>
    <tr>
      <th>63</th>
      <td>Ethiopia</td>
      <td>Africa</td>
      <td>114963583.0</td>
      <td>66.60</td>
      <td>0.3</td>
      <td>1729.927</td>
      <td>1.988786e+11</td>
    </tr>
    <tr>
      <th>39</th>
      <td>Chad</td>
      <td>Africa</td>
      <td>16425859.0</td>
      <td>54.24</td>
      <td>NaN</td>
      <td>1768.153</td>
      <td>2.904343e+10</td>
    </tr>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>38928341.0</td>
      <td>64.83</td>
      <td>0.5</td>
      <td>1803.987</td>
      <td>7.022622e+10</td>
    </tr>
    <tr>
      <th>158</th>
      <td>Rwanda</td>
      <td>Africa</td>
      <td>12952209.0</td>
      <td>69.02</td>
      <td>NaN</td>
      <td>1854.211</td>
      <td>2.401613e+10</td>
    </tr>
    <tr>
      <th>209</th>
      <td>Zimbabwe</td>
      <td>Africa</td>
      <td>14862927.0</td>
      <td>61.49</td>
      <td>1.7</td>
      <td>1899.775</td>
      <td>2.823622e+10</td>
    </tr>
    <tr>
      <th>82</th>
      <td>Guinea</td>
      <td>Africa</td>
      <td>13132792.0</td>
      <td>61.60</td>
      <td>0.3</td>
      <td>1998.926</td>
      <td>2.625148e+10</td>
    </tr>
    <tr>
      <th>121</th>
      <td>Mali</td>
      <td>Africa</td>
      <td>20250834.0</td>
      <td>59.31</td>
      <td>0.1</td>
      <td>2014.306</td>
      <td>4.079138e+10</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Benin</td>
      <td>Africa</td>
      <td>12123198.0</td>
      <td>61.77</td>
      <td>0.5</td>
      <td>2064.236</td>
      <td>2.502514e+10</td>
    </tr>
    <tr>
      <th>135</th>
      <td>Nepal</td>
      <td>Asia</td>
      <td>29136808.0</td>
      <td>70.78</td>
      <td>0.3</td>
      <td>2442.804</td>
      <td>7.117551e+10</td>
    </tr>
  </tbody>
</table>
</div>


```python
beds_20 = countries_df[countries_df.population > 10000000].sort_values('hospital_beds_per_thousand', ascending=True).head(20)
```

```python
beds_20
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>location</th>
      <th>continent</th>
      <th>population</th>
      <th>life_expectancy</th>
      <th>hospital_beds_per_thousand</th>
      <th>gdp_per_capita</th>
      <th>gdp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>121</th>
      <td>Mali</td>
      <td>Africa</td>
      <td>2.025083e+07</td>
      <td>59.31</td>
      <td>0.10</td>
      <td>2014.306</td>
      <td>4.079138e+10</td>
    </tr>
    <tr>
      <th>117</th>
      <td>Madagascar</td>
      <td>Africa</td>
      <td>2.769102e+07</td>
      <td>67.04</td>
      <td>0.20</td>
      <td>1416.440</td>
      <td>3.922267e+10</td>
    </tr>
    <tr>
      <th>140</th>
      <td>Niger</td>
      <td>Africa</td>
      <td>2.420664e+07</td>
      <td>62.42</td>
      <td>0.30</td>
      <td>926.000</td>
      <td>2.241534e+10</td>
    </tr>
    <tr>
      <th>135</th>
      <td>Nepal</td>
      <td>Asia</td>
      <td>2.913681e+07</td>
      <td>70.78</td>
      <td>0.30</td>
      <td>2442.804</td>
      <td>7.117551e+10</td>
    </tr>
    <tr>
      <th>82</th>
      <td>Guinea</td>
      <td>Africa</td>
      <td>1.313279e+07</td>
      <td>61.60</td>
      <td>0.30</td>
      <td>1998.926</td>
      <td>2.625148e+10</td>
    </tr>
    <tr>
      <th>63</th>
      <td>Ethiopia</td>
      <td>Africa</td>
      <td>1.149636e+08</td>
      <td>66.60</td>
      <td>0.30</td>
      <td>1729.927</td>
      <td>1.988786e+11</td>
    </tr>
    <tr>
      <th>31</th>
      <td>Burkina Faso</td>
      <td>Africa</td>
      <td>2.090328e+07</td>
      <td>61.58</td>
      <td>0.40</td>
      <td>1703.102</td>
      <td>3.560041e+10</td>
    </tr>
    <tr>
      <th>195</th>
      <td>Uganda</td>
      <td>Africa</td>
      <td>4.574100e+07</td>
      <td>63.37</td>
      <td>0.50</td>
      <td>1697.707</td>
      <td>7.765482e+10</td>
    </tr>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>3.892834e+07</td>
      <td>64.83</td>
      <td>0.50</td>
      <td>1803.987</td>
      <td>7.022622e+10</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Benin</td>
      <td>Africa</td>
      <td>1.212320e+07</td>
      <td>61.77</td>
      <td>0.50</td>
      <td>2064.236</td>
      <td>2.502514e+10</td>
    </tr>
    <tr>
      <th>90</th>
      <td>India</td>
      <td>Asia</td>
      <td>1.380004e+09</td>
      <td>69.66</td>
      <td>0.53</td>
      <td>6426.674</td>
      <td>8.868838e+12</td>
    </tr>
    <tr>
      <th>80</th>
      <td>Guatemala</td>
      <td>North America</td>
      <td>1.791557e+07</td>
      <td>74.30</td>
      <td>0.60</td>
      <td>7423.808</td>
      <td>1.330017e+11</td>
    </tr>
    <tr>
      <th>145</th>
      <td>Pakistan</td>
      <td>Asia</td>
      <td>2.208923e+08</td>
      <td>67.27</td>
      <td>0.60</td>
      <td>5034.708</td>
      <td>1.112128e+12</td>
    </tr>
    <tr>
      <th>85</th>
      <td>Haiti</td>
      <td>North America</td>
      <td>1.140253e+07</td>
      <td>64.00</td>
      <td>0.70</td>
      <td>1653.173</td>
      <td>1.885036e+10</td>
    </tr>
    <tr>
      <th>207</th>
      <td>Yemen</td>
      <td>Asia</td>
      <td>2.982597e+07</td>
      <td>66.12</td>
      <td>0.70</td>
      <td>1479.147</td>
      <td>4.411699e+10</td>
    </tr>
    <tr>
      <th>187</th>
      <td>Tanzania</td>
      <td>Africa</td>
      <td>5.973421e+07</td>
      <td>65.46</td>
      <td>0.70</td>
      <td>2683.304</td>
      <td>1.602851e+11</td>
    </tr>
    <tr>
      <th>132</th>
      <td>Mozambique</td>
      <td>Africa</td>
      <td>3.125544e+07</td>
      <td>60.85</td>
      <td>0.70</td>
      <td>1136.103</td>
      <td>3.550939e+10</td>
    </tr>
    <tr>
      <th>32</th>
      <td>Burundi</td>
      <td>Africa</td>
      <td>1.189078e+07</td>
      <td>61.58</td>
      <td>0.80</td>
      <td>702.225</td>
      <td>8.350004e+09</td>
    </tr>
    <tr>
      <th>33</th>
      <td>Cambodia</td>
      <td>Asia</td>
      <td>1.671897e+07</td>
      <td>69.82</td>
      <td>0.80</td>
      <td>3645.070</td>
      <td>6.094182e+10</td>
    </tr>
    <tr>
      <th>204</th>
      <td>Venezuela</td>
      <td>South America</td>
      <td>2.843594e+07</td>
      <td>72.06</td>
      <td>0.80</td>
      <td>16745.022</td>
      <td>4.761605e+11</td>
    </tr>
  </tbody>
</table>
</div>




```python
gdp_list = gdp_20['location'].tolist()
```


```python
beds_list = beds_20['location'].tolist()
```


```python
merged_list = gdp_list + beds_list
```


```python
duplicate_countries = dict()

for i in merged_list:
    if i in duplicate_countries:
        duplicate_countries[i] += 1
    else:
        duplicate_countries[i] = 1
```


```python
duplicate_countries = {key:value for key, value in duplicate_countries.items() if value > 1}
```


```python
duplicate_countries
```




    {'Burundi': 2,
     'Niger': 2,
     'Mozambique': 2,
     'Madagascar': 2,
     'Yemen': 2,
     'Haiti': 2,
     'Uganda': 2,
     'Burkina Faso': 2,
     'Ethiopia': 2,
     'Afghanistan': 2,
     'Guinea': 2,
     'Mali': 2,
     'Benin': 2,
     'Nepal': 2}

