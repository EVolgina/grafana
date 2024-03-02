# Домашнее задание к занятию 14 «Средство визуализации Grafana»
- Задание повышенной сложности. При решении задания 1 не используйте директорию help для сборки проекта. Самостоятельно разверните grafana, где в роли источника данных будет выступать prometheus, а сборщиком данных будет node-exporter:
- grafana;
- prometheus-server;
- prometheus node-exporter.
- За дополнительными материалами можете обратиться в официальную документацию grafana и prometheus.
- В решении к домашнему заданию также приведите все конфигурации, скрипты, манифесты, которые вы использовали в процессе решения задания.
- При решении задания 3 вы должны самостоятельно завести удобный для вас канал нотификации, например, Telegram или email, и отправить туда тестовые события.
- В решении приведите скриншоты тестовых событий из каналов нотификаций.
![1](https://github.com/EVolgina/grafana/blob/main/docker1.PNG)
## Задание 1
- Используя директорию help внутри этого домашнего задания, запустите связку prometheus-grafana.
- Зайдите в веб-интерфейс grafana, используя авторизационные данные, указанные в манифесте docker-compose.
- Подключите поднятый вами prometheus, как источник данных.
- Решение домашнего задания — скриншот веб-интерфейса grafana со списком подключенных Datasource.
![2](https://github.com/EVolgina/grafana/blob/main/прометеус.jpg)
![3](https://github.com/EVolgina/grafana/blob/main/графана.jpg)
![3.1](https://github.com/EVolgina/grafana/blob/main/grafana.png)
## Задание 2
- Изучите самостоятельно ресурсы:
- PromQL tutorial for beginners and humans. Understanding Machine CPU usage. Introduction to PromQL, the Prometheus query language.
- Создайте Dashboard и в ней создайте Panels:утилизация CPU для nodeexporter (в процентах, 100-idle); CPULA 1/5/15;
- количество свободной оперативной памяти;
- количество места на файловой системе.
- Для решения этого задания приведите promql-запросы для выдачи этих метрик, а также скриншот получившейся Dashboard.
```
100 - (avg by (instance) (irate(node_cpu_seconds_total{mode="idle"}[5m])) * 100)
node_memory_MemFree_bytes
node_filesystem_avail_bytes{mountpoint="/"
```
![4](https://github.com/EVolgina/grafana/blob/main/панелль.jpg)
![5](https://github.com/EVolgina/grafana/blob/main/метрики.jpg)
## Задание 3
- Создайте для каждой Dashboard подходящее правило alert — можно обратиться к первой лекции в блоке «Мониторинг».
- В качестве решения задания приведите скриншот вашей итоговой Dashboard.
![6](https://github.com/EVolgina/grafana/blob/main/аллерт4.jpg)
![7](https://github.com/EVolgina/grafana/blob/main/алерт3.jpg)
## Задание 4
- Сохраните ваш Dashboard.Для этого перейдите в настройки Dashboard, выберите в боковом меню «JSON MODEL». Далее скопируйте отображаемое json-содержимое в отдельный файл и сохраните его.
- В качестве решения задания приведите листинг этого файла. [file](https://github.com/EVolgina/grafana/blob/main/JSON%20MODEL)
