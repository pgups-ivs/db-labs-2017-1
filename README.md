Лабораторные работы по курсу "Базы данных", часть 1
================================

Работы этого семестра будут использовать в качестве примера БД с сайта http://postgresqltutorial.com/, которая была, в свою очередь, портирована из проекта Sakila для MySQL (http://dev.mysql.com/doc/sakila/en/).

#Расписание
Занятия в этом семестре будут проходить один раз в две недели, начиная с 20 февраля:

Дата | Тема
---- | ----
20.02.2017 | Вводное занятие. Установка PG, импорт данных, простейшие запросы.
06.03.2017 | Операторы DDL и DML. Разработка своей схемы, наполнение данными.
20.03.2017 | Операция Select, операторы, функции
03.04.2017 | Select с 
17.04.2017 | Триггеры/Функции/Процедуры
01.05.2017 | -
15.05.2017 | Индексы, планы запросов, просмотр статистики
29.05.2017 | Защита выполненных работ


#Начало работы
Для подготовки к выполнению работ необходимо скачать-установить сервер СУБД, и потом скачать и импортировать образ базы данных:
[dvdrental.zip](files/dvdrental.zip) или http://www.postgresqltutorial.com/postgresql-sample-database/

#Схема базы данных
![Схема данных](http://www.postgresqltutorial.com/wp-content/uploads/2013/05/PostgreSQL-Sample-Database.png)


# Что читать
В первую очередь стоит просмотреть обучающий раздел на сайте Postgresql.org ( [Tutorial](http://www.postgresql.org/docs/9.5/static/tutorial.html) ) и первые уроки на [postresqltutorial.com](http://www.postgresqltutorial.com). Также можно скачать электронные книги с диска F: или из чата.

# Тема 1: Оператор Select
[Полный синтаксис оператора Select](http://www.postgresql.org/docs/9.4/static/sql-select.html)

Изучение оператора разделено на два занятия:

1. Базовая структура оператора select (выборки данных из одной таблицы)
  * Однострочные функции
    *	[агрегатные функции](http://www.postgresql.org/docs/9.4/static/functions-aggregate.html) (COUNT, SUM, AVG, MAX, MIN)
    *	использование [строковых](http://www.postgresql.org/docs/9.4/static/functions-string.html), [числовых](http://www.postgresql.org/docs/9.4/static/functions-math.html) и функций для работы с [датами](http://www.postgresql.org/docs/9.4/static/functions-datetime.html)
    *	функции [преобразования типов данных](http://www.postgresql.org/docs/9.4/static/functions-formatting.html)
    *	условные выражения: [CASE и COALESCE](http://www.postgresql.org/docs/9.4/static/functions-conditional.html)
    *	[операторы сравнения строк](http://www.postgresql.org/docs/9.4/static/functions-matching.html): LIKE, SIMILAR TO и регулярные выражения
  * [Группировка данных](http://www.postgresql.org/docs/9.4/static/queries-table-expressions.html#QUERIES-GROUP)
    * группировка данных с помощью фразы GROUP BY
    * исключение итоговых строк при помощи фразы HAVING
  * Сортировка данных - фраза [ORDER BY](http://www.postgresql.org/docs/9.4/static/queries-order.html)
  * Ограничение размера результата выборки - фразы [LIMIT и OFFSET](http://www.postgresql.org/docs/9.4/static/queries-limit.html)
2. Выборка данных из нескольких таблиц
  * [соединения таблиц](http://www.postgresql.org/docs/9.4/static/queries-table-expressions.html#QUERIES-FROM)
    * декартово произведение - CROSS JOIN
    * внутренее соединение - INNER JOIN
      * эквисоединение - условия ON и USING
      * естественное соединение - условие NATURAL
    * внешние соединения (LEFT [OUTER] JOIN, RIGHT [OUTER] JOIN, FULL [OUTER] JOIN)
    * соединение более двух таблиц
    * соединение таблицы с собой
  * объединение запросов
    * [операторы UNION, INTERSECT, EXCEPT](http://www.postgresql.org/docs/9.4/static/queries-union.html)
  * Подзапросы
    * подзапросы в фразах FROM и HAVING
    * коррелированные подзапросы
    * использование операторов [EXISTS, ANY, SOME, ALL, IN, NOT IN](http://www.postgresql.org/docs/9.4/static/functions-subquery.html)

Задачи смотрите в файле [tasks1.md](tasks1.md).

Результатом выполненных работ должны быть sql-скрипты, демонстрирующие применение перечисленных возможностей select.

# Тема 1: Разработка схем данных
Следующая тема для изучения - средства описания схем данных, операторы DDL - Data Definition Language. В документации Postgres есть соотвествующая глава - [Data Definition](http://www.postgresql.org/docs/9.4/static/ddl.html), на сайте PGT - серия уроков, начиная с [Create Table](http://www.postgresqltutorial.com/postgresql-create-table/). В учебной схеме следует просмотреть скрипты создания таблиц и представлений.

Изучаемые вопросы:
* Создание таблиц - операция [CREATE TABLE](http://www.postgresql.org/docs/9.4/static/sql-createtable.html)
* [Типы данных](http://www.postgresql.org/docs/9.4/static/datatype.html)
* [Типы ограничений](http://www.postgresql.org/docs/9.4/static/ddl-constraints.html)
* Создание [индексов](http://www.postgresql.org/docs/9.4/static/indexes.html)
* Создание [представлений](http://www.postgresql.org/docs/9.4/static/rules-views.html) и [схем](http://www.postgresql.org/docs/9.4/static/ddl-schemas.html)
* Изменение таблиц - операция [ALTER TABLE](http://www.postgresql.org/docs/9.4/static/ddl-alter.html)

После описания схемы, изучаются операторы добавления и изменения данных в базе - [Data Manupulation Languate](http://www.postgresql.org/docs/9.4/static/dml.html):
* [INSERT](http://www.postgresql.org/docs/9.4/static/sql-insert.html) и [COPY](http://www.postgresql.org/docs/9.4/static/sql-copy.html)
* [UPDATE](http://www.postgresql.org/docs/9.4/static/sql-update.html)
* [DELETE](http://www.postgresql.org/docs/9.4/static/sql-delete.html)

Результатом изучения должнен быть набор sql-скриптов, содержащих команды создания схемы, наполнения схемы данными, очистки и удаления схемы, плюс примеры обновления и удаления данных.

Задачи смотрите в файле [tasks2.md](tasks2.md)

# Тема 3: Хранимые процедуры
В теме рассматриваются основы написания серверных процедур на языке [PL/pgSQL](http://www.postgresql.org/docs/9.4/static/plpgsql.html). На сайте PG Tutorial отдельных уроков нет, но в схеме примера есть несколько функций, которые нужно изучить.

Вопросы в теме:
* Основы программирования на PL/pgSQL - [объявление](http://www.postgresql.org/docs/9.4/static/plpgsql-declarations.html) функций,  переменных, [управляющие операторы](http://www.postgresql.org/docs/9.4/static/plpgsql-control-structures.html) - условные операторы, циклы, обработка ошибок, [операции](http://www.postgresql.org/docs/9.4/static/plpgsql-statements.html) над данными
* [Курсоры](http://www.postgresql.org/docs/9.4/static/plpgsql-cursors.html)
* [Триггеры](http://www.postgresql.org/docs/9.4/static/triggers.hml) и [триггерные процедуры](http://www.postgresql.org/docs/9.4/static/plpgsql-trigger.html)
* [Правила](http://www.postgresql.org/docs/9.4/static/rules.html)

Результатом изучения должен быть sql-скрипт, демонстрирующий создание триггеров и функций в разработанной в предыдущей теме схеме данных.

Задачи к теме см. в файле [tasks3.md](tasks3.md)
