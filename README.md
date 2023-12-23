<h1 align="center">Разведочный анализ данных с Wi-Fi роутеров о перемещениях пользовательских устройств по городу</h1>

![Debian](https://img.shields.io/badge/Debian-D70A53?style=for-the-badge&logo=debian&logoColor=white) ![ClickHouse](https://img.shields.io/badge/ClickHouse-FFFAFA?style=for-the-badge&logo=ClickHouse&logoColor=yellow) ![YandexCloud](https://img.shields.io/badge/YandexCloud-FF0000?style=for-the-badge&logo=Yandex&logoColor=FF0000) ![R](https://img.shields.io/badge/r-%23276DC3.svg?style=for-the-badge&logo=r&logoColor=white) ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

## Стек технологий:
+  Debian
+  ClickHouse
+  YandexCloud
+  R (tidyverse, ggplot2)
+  Python (osmnx, networkx, numpy)

## Исходные данные:
### 1. Справочник расположения WiFi роутеров.
### 2. Граф улично-дорожной сети (набор дуг и узлов).
### 3. Набор данных за год (с выбросами, пропусками).


## Подготовка к работе с данными 
+ Импорт данных
```
rd_network <- readr::read_csv2("data/road_network.csv")
routers <- readr::read_csv2("data/wifi_routers.csv")
```
+ Анализ данных и исключение данных с пропущенными значениями

## Размещение данных в СУБД на виртуальном сервере
+ На базе YandexCloud был создан виртаульный сервер Debian
+ Импорт данных с ЯндексДиска при помощи консольной программы `wget 'https://disk.yandex.ru/d/logsfilename' -O filename.tar.gz`
+ Установка ClickHouse на виртуальный сервер
+ Загрузка данных в ClickHouse `cat $(ls | grep wifi_logs_.*.csv) | tr ';' ',' | tr -d '"' | clickhouse-client`
## Проведение разведочного анализа данных
+  Проанализированы изменения дорожно-транспортной ситуации с течением времений на основе перемещений между роутери     
![road_condition_bytime](%routers.gif%)
+  Построена временная шкала по неделям нагруженности транспортных узлов        
![time_weeks_load](%time_weeks_load.gif%)
## Составление матрицы перемещений
+  Матрица передвижений по городу
![route_matrix](%route_matrix.img%)
## Визуализация данных на диаграммах
Выявлены самые популярные роутеры сети ![most_popular_routers](%routers.img%)
## Предоставление комментариев
### В ходе проведённой работы были выроботаны рекомендации относительно правильного расположения роутеров
+ 1
+ 2
+ 
## Авторы решения - Команда DSFans   
<p><img src="https://raw.githubusercontent.com/i2z1/XMAS_Hack_2023_case1/main/img/xmashack_logo.jpg" width="340" height="340" align="right" /> 
<br> <h3>Захарчук Иван Илларионович<br>  <br>
Скаев Сармат Аланович<br><br>
Рудзик Александр Романович<br><br>
Сысоев Георгий Алексеевич<br><br>
Федосимова Александра Дмитриевна<br></h3></p>




