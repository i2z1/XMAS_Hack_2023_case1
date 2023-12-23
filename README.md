<h1 align="center">Разведочный анализ данных с Wi-Fi роутеров о перемещениях пользовательских устройств по городу</h1>

![Debian](https://img.shields.io/badge/Debian-D70A53?style=for-the-badge&logo=debian&logoColor=white) ![ClickHouse](https://img.shields.io/badge/ClickHouse-FFFAFA?style=for-the-badge&logo=ClickHouse&logoColor=yellow) ![YandexCloud](https://img.shields.io/badge/YandexCloud-FF0000?style=for-the-badge&logo=Yandex&logoColor=FF0000) ![R](https://img.shields.io/badge/r-%23276DC3.svg?style=for-the-badge&logo=r&logoColor=white) ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

## Стек технологий:
+  Debian
+  ClickHouse
+  YandexCloud
+  R (tidyverse, ggplot2)
+  Python (osmnx, networkx, numpy)

## Исходные данные:
 1. Справочник расположения WiFi роутеров.
 2. Граф улично-дорожной сети (набор дуг и узлов).
 3. Набор данных за год (с выбросами, пропусками).


## Подготовка к работе с данными 
+ Импорт данных
```
rd_network <- readr::read_csv2("data/road_network.csv")
routers <- readr::read_csv2("data/wifi_routers.csv")
```
+ Анализ данных и исключение данных с пропущенными значениями

## Размещение данных в СУБД на виртуальном сервере
+ На базе YandexCloud был создан виртаульный сервер Debian
+ Импорт данных с ЯндексДиска при помощи `wget`
+ Установка ClickHouse на виртуальный сервер
+ Загрузка данных в ClickHouse `cat $(ls | grep wifi_logs_.*.csv) | tr ';' ',' | tr -d '"' | clickhouse-client`
<br>

## Проведение разведочного анализа данных
+  Проанализированы изменения дорожно-транспортной ситуации скорости движения в течении дня на основе перемещений между роутери       
  <br>
Утро      
<img src="./img/sunrise.jpeg" height="500" width="835"></img>
Полдень    
<img src="./img/day.jpeg" height="500" width="835"></img>
Вечер    
<img src="./img/sunset.jpeg" height="500" width="835"></img>
Определены зоны с низким потоком трафика
<img src="./img/stats_problem_zones.jpeg" height="500" width="835"></img>
Построена временная шкала по неделям нагруженности транспортных узлов
<img src="./img/nofile.jpeg" height="500" width="835"></img><br>
   
## Составление матрицы перемещений     
+  Матрица передвижений по городу
<p><img src="./img/realmap02.PNG" height="500" width="460"></img><img src="./img/cty_map.PNG" height="500" width="460"></img></p><br>

## Визуализация данных
+ Построена тепловая карта наиболее используемых роутеров        
<img src="./img/poprouts.jpeg" height="500" width="835"></img><br>

## Предоставление комментариев
### В ходе проведённой работы были выроботаны рекомендации относительно эффективного расположения роутеров
+ Необходимо переместить роутеры с низкой проходимостью
<br><br><br>

## Авторы решения - Команда DSFans   
<p><img src="https://raw.githubusercontent.com/i2z1/XMAS_Hack_2023_case1/main/img/xmashack_logo.jpg" width="390" height="390" align="center" /></p>
