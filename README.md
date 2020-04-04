# COVID-19 SIR mathematical model for Madrid

SIR mathematical model for infectious diseases optimized for COVID-19 using Spanish Ministry of Health public available data for Madrid.

-----

![sir-cases](https://github.com/agastalver/sir-covid-19-madrid/raw/master/images/generated-sir-cases.png "SIR Model Cases")

![sir](https://github.com/agastalver/sir-covid-19-madrid/raw/master/images/generated-sir.png "SIR Model")

**Note**: 

* `susceptible`, `infected`, and `recovered`, stand for the observable population; thus, the ones that can be detected. The actual values could be higher.
* `susceptible` is an estimated value calculated from `N` with respect to the `infected` and `recovered`, the actual value is not provided by the government.
* `recovered` stands for people who has recovered from the virus or has died; as considered in the SIR model.

-----

## Last optimization

### Case forecasting table

| Date           | Infected  | Cases      |
|:--------------:|:---------:|:----------:|
| 2020-04-04     | 16070     | 35346      |
| **2020-04-05** | **16166** | **37010**  |
| 2020-04-06     | 16147     | 38563      |
| 2020-04-07     | 16022     | 40004      |
| 2020-04-08     | 15801     | 41332      |
| 2020-04-09     | 15497     | 42550      |
| 2020-04-10     | 15120     | 43663      |
| 2020-04-11     | 14684     | 44677      |
| 2020-04-12     | 14200     | 45598      |
| **2020-04-13** | **14334** | **47121**  |
| 2020-04-14     | 14302     | 48483      |
| 2020-04-15     | 14123     | 49688      |
| 2020-04-16     | 13821     | 50745      |

### Optimized SIR parameters

```
59631.444914830536
beta = 0.47474126209024964
gamma = 0.09628565943098083
delta = 0.5471821453736916
delay = 0
```

* `delta` stands for a factor of reduction of `beta` during the lockdown.
* All results are available in the folders `images` and `data`.

-----

## Last data information

### Madrid total cases

![total](https://github.com/agastalver/sir-covid-19-madrid/raw/master/images/generated-total.png "Total cases")

-----

## Methodology

### Data sources

Main data source:

* Spanish government: https://www.mscbs.gob.es/profesionales/saludPublica/ccayes/alertasActual/nCov-China/situacionActual.htm
  * https://covid19.isciii.es/
  * https://covid19.isciii.es/resources/serie_historica_acumulados.csv

### Epidemiology model

This is based on the SIR epidemiology model proposed by W. O. Kermack and A. G. McKendrick in:

```
Kermack, W. O.; McKendrick, A. G. (1927). "A Contribution to the Mathematical Theory of Epidemics". Proceedings of the Royal Society A: Mathematical, Physical and Engineering Sciences. 115 (772): 700. Bibcode:1927RSPSA.115..700K. doi:10.1098/rspa.1927.0118. JSTOR 94815.
```

You can find the description on wikipedia: https://en.wikipedia.org/wiki/Mathematical_modelling_of_infectious_disease#The_SIR_model

### Optimization

The parameters `N`, `beta`, and `gamma`, are unknown. Additionally, a `delay` parameter is considered; defined as a time synchronization parameter in case the available data is not adjusted to day 0.

The optimization method is Nendel-Mead, adjusting mean squares on `I(t)` and `R(t)` to the available data. `S(t)` and `N` are calculated backwards.

```
Nelder, John A.; R. Mead (1965). "A simplex method for function minimization". Computer Journal. 7 (4): 308–313. doi:10.1093/comjnl/7.4.308.
```

## Usage

Execute:

```
$ python main.py
```

## Important note

The mathematical model could not adjust to the real behaviour of the virus. Furthermore, the data can have errors, delays, or be incomplete, so the adjustment can vary in the future.
