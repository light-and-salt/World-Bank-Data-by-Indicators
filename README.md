# World Bank Data by Indicators 1960-2017

The World Bank has been tracking global human development in 250+ countries and regions [by 20 indicators](https://data.worldbank.org/indicator). This repo contains our **pre-cleaned data** of their 20 indicators, covering years 1960-2020, ready for you to explore in Tableau, Python, and so on.

There are 20 folders, each named after one indicator. Inside each folder you will find:
```js
[indicator].csv // this is our pre-cleaned data
```
among the raw (`[indicator]-raw-2021.csv`) and meta data (`Metadata_*.csv`) we downloaded from the World Bank.

Note that the data is only "clean" in the sense that Tableau can read it. There are `null` values and perhaps even mistakes. Please use caution when making discoveries.


We [wrangled](https://www.trifacta.com/start-wrangling/) the raw data using the following recipe:
```
delete row: IN($sourcerownumber, [1,3,2,4])
header
unpivot col: {1960}, {1961}, {1962}, {1963}, {1964}, {1965}, {1966}, {1967}, {1968}, {1969}, {1970}, {1971}, {1972}, {1973}, {1974}, {1975}, {1976}, {1977}, {1978}, {1979}, {1980}, {1981}, {1982}, {1983}, {1984}, {1985}, {1986}, {1987}, {1988}, {1989}, {1990}, {1991}, {1992}, {1993}, {1994}, {1995}, {1996}, {1997}, {1998}, {1999}, {2000}, {2001}, {2002}, {2003}, {2004}, {2005}, {2006}, {2007}, {2008}, {2009}, {2010}, {2011}, {2012}, {2013}, {2014}, {2015}, {2016}, {2017}, {2018}, {2019}, {2020} groupEvery: 1
rename type: manual mapping: [key,'Year']
drop col: column67 action: Drop
filter type: missing missing: value action: Delete
pivot col: {Indicator Name} group: {Country Name},{Country Code},Year value: AVERAGE(value) limit: 50
```

If you have problem using this data, please file an [issue](https://github.com/ZeningQu/World-Bank-Data-by-Indicators/issues) or send a [pull request](https://github.com/ZeningQu/World-Bank-Data-by-Indicators/pulls).
