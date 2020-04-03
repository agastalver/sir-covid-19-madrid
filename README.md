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
| 2020-04-03     | 15762     | 33244      |
| 2020-04-04     | 15953     | 34951      |
| **2020-04-05** | **16026** | **36552**  |
| 2020-04-06     | 15987     | 38044      |
| 2020-04-07     | 15845     | 39423      |
| 2020-04-08     | 15611     | 40692      |
| 2020-04-09     | 15295     | 41853      |
| 2020-04-10     | 14911     | 42912      |
| 2020-04-11     | 14470     | 43875      |
| 2020-04-12     | 13984     | 44749      |
| 2020-04-13     | 14027     | 46131      |
| 2020-04-14     | 13925     | 47365      |
| 2020-04-15     | 13697     | 48457      |

### Optimized SIR parameters

```
N = 57880.05926253996
beta = 0.4545665968403414
gamma = 0.09456620009302807
delta = 0.5704225207551669
delay = 1
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
