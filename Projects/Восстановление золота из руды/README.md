# Постановка задачи

- Задача подготовить прототип модели машинного обучения для компании разрабатывающей решения для эффективной работы промышленных предприятий.
- Модель должна предсказать коэффициент восстановления золота из золотосодержащей руды. В датасете содержутся данные с параметрами добычи и очистки.


# Описание данных

- Rougher feed — исходное сырье
- Rougher additions (или reagent additions) — флотационные реагенты: Xanthate, Sulphate, Depressant
 - Xanthate **— ксантогенат (промотер, или активатор флотации);
 - Sulphate — сульфат (на данном производстве сульфид натрия);
 - Depressant — депрессант (силикат натрия).
- Rougher process  — флотация
- Rougher tails — отвальные хвосты
- Float banks — флотационная установка
- Cleaner process — очистка
- Rougher Au — черновой концентрат золота
- Final Au — финальный концентрат золота

### Параметры этапов

- air amount — объём воздуха
- fluid levels — уровень жидкости
- feed size — размер гранул сырья
- feed rate — скорость подачи

# Расчёт эффективности

- Эффективность обогащения рассчитывается по формуле

![](https://github.com/HorodeckiyMykhailo/Yandex-Praktikum-Projects/blob/main/Projects/images/WhatsApp%20Image%202022-03-12%20at%2012.01.52.jpeg)

   - C — доля золота в концентрате после флотации/очистки;
   - F — доля золота в сырье/концентрате до флотации/очистки;
   - T — доля золота в отвальных хвостах после флотации/очистки.
 
- Для прогноза коэффициента нужно найти долю золота в концентратах и хвостах. Причём важен не только финальный продукт, но и черновой концентрат.

# Метрика качества

- Для решения задачи понадобится метрика качества — sMAPE (англ. Symmetric Mean Absolute Percentage Error, «симметричное среднее абсолютное процентное отклонение»).
- sMAPE выражается не в абсолютных величинах, а в относительных.Она одинаково учитывает масштаб и целевого признака, и предсказания.

![](https://github.com/HorodeckiyMykhailo/Yandex-Praktikum-Projects/blob/main/Projects/images/WhatsApp%20Image%202022-03-12%20at%2012.02.13.jpeg)

- Обозначения:

![](https://github.com/HorodeckiyMykhailo/Yandex-Praktikum-Projects/blob/main/Projects/images/WhatsApp%20Image%202022-03-12%20at%2012.15.09.jpeg)

- Значение целевого признака для объекта с порядковым номером i в выборке, на которой измеряется качество.

![](https://github.com/HorodeckiyMykhailo/Yandex-Praktikum-Projects/blob/main/Projects/images/WhatsApp%20Image%202022-03-12%20at%2012.15.23.jpeg)

- Значение предсказания для объекта с порядковым номером i, например, в тестовой выборке.

![](https://github.com/HorodeckiyMykhailo/Yandex-Praktikum-Projects/blob/main/Projects/images/WhatsApp%20Image%202022-03-12%20at%2012.15.40.jpeg)

- Количество объектов в выборке.

![](https://github.com/HorodeckiyMykhailo/Yandex-Praktikum-Projects/blob/main/Projects/images/WhatsApp%20Image%202022-03-12%20at%2012.15.51.jpeg)

- Суммирование по всем объектам выборки (i меняется от 1 до N).

- Нужно спрогнозировать сразу две величины:
 - эффективность обогащения чернового концентрата rougher.output.recovery;
 - эффективность обогащения финального концентрата final.output.recovery.
- Итоговая метрика складывается из двух величин:

![](https://github.com/HorodeckiyMykhailo/Yandex-Praktikum-Projects/blob/main/Projects/images/WhatsApp%20Image%202022-03-12%20at%2012.34.53.jpeg)
