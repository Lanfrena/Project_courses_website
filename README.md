### Project_courses_website
⚒️ `Стек: python, pandas, pandahouse, numpy, seaborn, matplotlib, scipy, bootstrap, requests, urlencode, SQL, ClickHouse, Jupyter Notebook`
### Блок 1
В ходе тестирования одной гипотезы целевой группе была предложена новая механика оплаты услуг на сайте продажи курсов, у контрольной группы оставалась базовая механика. 

Данные для анализа:
- groups.csv – файл с информацией о принадлежности пользователя к контрольной или экспериментальной группе (А – контроль, B – целевая группа) 
- groups_add.csv – дополнительный файл с пользователями, который вам прислали спустя 2 дня после передачи данных
- active_studs.csv – файл с информацией о пользователях, которые зашли на платформу в дни проведения эксперимента. 
- checks.csv – файл с информацией об оплатах пользователей в дни проведения эксперимента.
### Цель:
Мне необходимо проанализировать итоги эксперимента и ответить на следующие вопросы:
1. На какие метрики вы смотрите в ходе анализа и почему?
2. Имеются ли различия в показателях и с чем они могут быть связаны?
3. Являются ли эти различия статистически значимыми?
4. Стоит ли запускать новую механику на всех пользователей?

### Этапы работы:
1. написала функцию выгрузки файлов, проанализировала данные;
2. провела математические расчеты метрик: CR, ARPU, ARPPU;
3. проверила группы на нормальность и равенство дисперсий;
4. провела АВ-тестирование метрик и проверила гипотезы на различия между группами с помощью метода Хи-квадрат Пирсона и Bootstrap. <br>

### По результатам анализа 
я выявила, что в группе с новой механикой оплат значительно выше ARPPU и конверсия статистически значимо не отличается от контрольной группы. Новую механику оплат необходимо выкатить для всех пользователей, она увеличит доход компании и комфортные условия для пользователей сайта. 

### Блок 2
Образовательные курсы состоят из различных уроков, каждый из которых состоит из нескольких маленьких заданий. Каждое такое маленькое задание называется "горошиной". Под **усердным студентом** мы понимаем студента, который правильно **решил 20 задач за текущий месяц.** Данные для анализа: таблица default.peas <br>
### Результат
Написала оптимальный запрос, который дал информацию о количестве очень усердных студентов. 


### Оптимизация воронки
Образовательная платформа предлагает пройти студентам курсы по модели trial: студент может решить бесплатно лишь 30 горошин в день. Для неограниченного количества заданий в определенной дисциплине студенту необходимо приобрести полный доступ. Команда провела эксперимент, где был протестирован новый экран оплаты. Данные для анализа: default.peas, default.studs и default.final_project_check

ARPU считается относительно всех пользователей, попавших в группы.
- **Активным** считается пользователь, за все время решивший **больше 10 задач** правильно в любых дисциплинах.
- **Активным по математике** считается пользователь, за все время решивший **2 или больше задач** правильно по математике.

### Цель:
Мне необходимо в одном запросе выгрузить следующую информацию о группах пользователей:
1. ARPU
2. ARPAU
3. CR в покупку
4. СR активного пользователя в покупку
5. CR пользователя из активности по математике (subject = ’math’) в покупку курса по математике
6. нужно написать функцию, которая будет автоматически подгружать информацию из дополнительного файла groups_add.csv (заголовки могут отличаться) и на основании дополнительных параметров пересчитывать метрики
7. нужно написать функцию, которая будет строить графики по получаемым метрикам

### Результат
Сделала SQL-запрос создания сводной таблицы с расчетом основных метрик: ARPU, ARPAU, CR, CR_active, CR_math и выгрузила в Jupyter Notebook.

### Блок 3
Написала функцию для дополнительного файла к задаче #1, которая вычисляет основные метрики для анализа в одну сводную таблицу, и функцию для визуализации полученных результатов в виде графиков.
