# World Bank Data by Indicators 1960-2017

The World Bank has tracked global human development for a long period of time. This data could be interesting for exploratory data analysis. This repo contains **20 pre-cleaned datasets, ready to be imported into Tableau**. 

Each folder contains data on one aspect of global human developmnet ("indicator"). Inside each folder you will find one main `.csv` file that's pre-cleaned by us, and two metadata files. Note that the data is only "clean" in the sense that Tableau can read it. Please use caution when making discoveries.

The original data can be browsed on the World Bank website [by countries](https://data.worldbank.org/country) or [by indicators](https://data.worldbank.org/indicator). We downloaded the original data and [wrangled](https://www.trifacta.com/start-wrangling/) it with the following recipe:
```
delete row: IN(SOURCEROWNUMBER(), [1,3,2,4])
textformat col: column2,column3,column4,column5 type: trimquotes
header
unpivot col: {"1960"}, {"1961"}, {"1962"}, {"1963"}, {"1964"}, {"1965"}, {"1966"}, {"1967"}, {"1968"}, {"1969"}, {"1970"}, {"1971"}, {"1972"}, {"1973"}, {"1974"}, {"1975"}, {"1976"}, {"1977"}, {"1978"}, {"1979"}, {"1980"}, {"1981"}, {"1982"}, {"1983"}, {"1984"}, {"1985"}, {"1986"}, {"1987"}, {"1988"}, {"1989"}, {"1990"}, {"1991"}, {"1992"}, {"1993"}, {"1994"}, {"1995"}, {"1960"}, {"1970"}, {"1980"}, {"1990"}, {"2010"}, {"2011"}, {"2012"}, {"2013"}, {"2014"}, {"2015"}, {"2016"}, {"2017"}, {"2009"}, {"2008"}, {"2007"}, {"2006"}, {"2005"}, {"2004"}, {"2003"}, {"2002"}, {"2001"}, {"2000"}, {"1999"}, {"1998"}, {"1997"}, {"1996"} groupEvery: 1
rename type: manual mapping: [key,'Year']
textformat col: Year,value type: trimquotes
drop col: column64 action: Drop
filter type: missing missing: value action: Delete
pivot col: {Indicator Name} group: {Country Name},{Country Code},Year value: SUM(value) limit: 50
```