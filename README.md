# Сравнение ClickHouse и MongoDB

## Как запустить хранилище
Скопируйте содержимое env.example в .env<br>
Соберите проект и запустите<br>
```
docker-compose build
docker-compose up
```
## Как запустить файлы jupiter notebook
Открываете файлы  и последовательно запускаете:
```
generate_data.ipynb
test.ipynb
```
# Выводы:

Загрузка больших данных в ClickHouse практически в 8 раз быстрее.<br>
Оба хранилища по чтению удовлетворяют указанным в задании требованиям.<br>
Если говорить о хранилище для аналитика, то я бы использовал ClickHouse, так как он без полной выгрузки данных позволяет писать гибкие запросы на чистом SQL.<br>
Если использовать данные для оперативного отображения в сервисе, то я бы использовал MongoDB, так как время чтения данных выше.

# Тестирование

## Генерация данных
### Лайки
Готово. Сделано 4 161 834 записей.<br>
--- Выполнение скрипта 518.9780321121216 секунд ---
### Закладки
Готово. Сделано 2 079 804 записей.<br>
--- Выполнение скрипта 505.4561140537262 секунд ---
### Рецензии
Готово. Сделано 4161834 записей.<br>
--- Выполнение скрипта 639.8422989845276 секунд ---

### Итого:
Всего подготовлено 10 403 472 тестовых записи.

## Запись данных в Mongo/ClickHouse
### Лайки
Готово. В Mongo внесено 4 161 834 записей.<br>
--- Выполнение скрипта 157.19018268585205 секунд ---<br><br>
**ClickHouse:**<br>
--- Выполнение скрипта 17.33292031288147 секунд ---
### Закладки
Готово. В Mongo внесено 2 079 804 записей.<br>
--- Выполнение скрипта 77.9297935962677 секунд ---
**ClickHouse:**<br>
--- Выполнение скрипта 9.558892965316772 секунд ---
### Рецензии
Готово. В Mongo внесено 4 161 834 записей.<br>
--- Выполнение скрипта 168.21501803398132 секунд ---
**ClickHouse:**<br>
--- Выполнение скрипта 20.28546380996704 секунд ---

### Итого:
Всего в MongoDB внесено 10 403 472 тестовых записи.

## Чтение данных
### Cписок закладок пользователя
Чтение списка закладок по пользователю:<br>
**Mongo:**<br>
--- Выполнение скрипта 0.0046032524108886716 секунд ---<br><br>
**ClickHouse:**<br>
--- Выполнение скрипта 0.004541075229644776 секунд ---<br><br>
Запрос количества закладок у пользователя:<br>
--- Выполнение скрипта 0.0015026712417602539 секунд ---<br><br>
**ClickHouse:**<br>
--- Выполнение скрипта 0.003912692070007324 секунд ---

## Cредняя пользовательская оценка фильма
### Чтение списка пользователей, поставивших оценку фильму
--- Выполнение скрипта 0.037082672119140625 секунд ---
### Чтение количества оценок у фильма
--- Выполнение скрипта 0.006058931350708008 секунд ---
4166
### Три примера:
**Mongo:**<br>
--- Выполнение скрипта 0.017944495677947998 секунд ---<br><br>
**ClickHouse:**<br>
--- Выполнение скрипта 0.004795000553131103 секунд ---<br><br>
```
[{'_id': 'null', 'total': 4.43638982237158}]
```

**Mongo:** <br>
--- Выполнение скрипта 0.017732858657836914 секунд ---<br><br>

```
[{'_id': None, 'total': 4.562169947191551}]
```
--- Выполнение скрипта 0.01915597915649414 секунд ---
```
[{'_id': None, 'total': 4.457033125300048}]
```

## Количество лайков или дизлайков у определённого фильма
### Количество лайков у фильма:
--- Выполнение скрипта 0.016483545303344727 секунд ---<br>
2105
### Количество дизлайков у фильма:
--- Выполнение скрипта 0.01952672004699707 секунд ---<br>
2061

## Список понравившихся пользователю фильмов (список лайков пользователя)
### Чтение списка:
--- Выполнение скрипта 0.009370803833007812 секунд ---
### Количество понравившихся пользователю фильмов:
--- Выполнение скрипта 0.004641294479370117 секунд ---<br>
486
