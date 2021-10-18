# World Bank Data by Indicators 1960-2020

The World Bank has been tracking global human development in 250+ countries and regions [by 20 indicators (e.g., climate change, economy, education, energy, environment, debt, gender, health, infrastructure, poverty, science and technology)](https://data.worldbank.org/indicator), between years 1960-2020. We downloaded their data and **pre-cleaned** it for you to explore in Tableau, Python, and so on.

This repo has 20 folders, each named after one indicator. In each folder you will find:
```js
[indicator].csv // this is our pre-cleaned data
```
among the raw (`[indicator]-raw-2021.csv`) and meta data (`Metadata_*.csv`) from the World Bank.

Note that the data is only "clean" in the sense that Tableau can read it. There are certainly `null` values and perhaps even errors. Please use caution when making discoveries.

We [wrangled](https://www.trifacta.com/start-wrangling/) each raw data file using [this recipe](https://github.com/ZeningQu/World-Bank-Data-by-Indicators/blob/master/recipe.wrangle).

If you have problem using this data, please file an [issue](https://github.com/ZeningQu/World-Bank-Data-by-Indicators/issues) or send a [pull request](https://github.com/ZeningQu/World-Bank-Data-by-Indicators/pulls). Enjoy :D
