# Illegal-fishing-classification

## Requirements

``` python
python 3.14
```

run:

``` bash
python -m pip install -r requirements.txt
```

## Objectives

* Analise da qualidade dos dados
* Limpesa e criação de dataset nivel ouro
* Preparação de processo de auto ml com multiplos modelos de ML e deeplearn
* Demonstração de resultados e comparação com artigo
* Explicabilidade dos modelos

## Dados

csvs fornecidos: drifting_longlines, fixed_gear, pole_and_line, purse_seines, trawlers, unknown

**Columns :**

* mmsi: Maritime Mobile Service Identity, a unique identifier for ships
* timestamp: date and time of the position
* distance_from_shore: distance from the nearest shore in meters
* distance_from_port: distance from the nearest port in meters
* speed: speed of the ship in knots
* course: Vessel course
* lat: Latitude in decimal degrees
* lon: Longitude in decimal degrees
* is_fishing: Label indicating fishing activity.
  0 = Not fishing
  >0 = Fishing. Data values between 0 and 1 indicate the average score for the position if scored by multiple people.
  -1 = No data
* source: The training data batch. Data was prepared by GFW, Dalhousie, and a crowd sourcing campaign. False positives are marked as false_positives.

## ETL


## Analise Exploratoria

* Todos os csvs consistem de tipos diferentes de embarcações com os os mesmos tipos de informação
* dados com pontos duplicados de fontes diferentes
* Dados parecem estar bem desbalanceados, o que pode ser um problema para treinar um modelo de classificação.
* tempo entre registros é irregular o que pode dificultar uma abordagem mais classica
* Dados de boa qualidade, poucas informações faltantes, sem erros de tipo, provavelmente dados extraidos de equipamentos de registro autonomo
* Foi definido que uma rota consiste de um grupo de pontos que começão em um timestamp onde distance_from_shore e distance_from_port são 0 e terminam em um timestamp onde essas mesmas colunas são 0



* Ideal para resultado do modelo é ter verdadeiros negativos ter verdadeiros positivos não ter falsos negativos e ter falsos positivos 
* falsos positivos são mais faceis de lidar se o foco for proteção ambiental, pois em caso de aplicação de multa para pescadores ilegais pescadores multados erroneamente podem recorer a multa ja pescadores que deveriam ter recebido multa e não receberam não teram interesse na correção.