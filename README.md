# Лабораторная работа

## Пример (ее в отчет включать не нужно!)

В данной лабораторной работе научимся работать c одним из самых мощных и часто используемых инструментов в Linux для поиска текста и анализа содержимого файлов - `grep`.

1. Создайте файл с расширением .txt и запишите туда это стихотворение:
```
Sun of the sleepless! Melancholy star!
Whose tearful beam glows tremulously far,
That show’st the darkness thou canst not dispel,
How like art thou to joy remember’d well!

So gleams the past, the light of other days,
Which shines, but warms not with its powerless rays;
A night-beam Sorrow watcheth to behold,
Distinct, but distant — clear, but oh, how cold! 
```
2. Создадим скрипт-bash для анализа этого стихотворения

    - Например, найдем строки которые заканчиваются на "!"<br>
    `grep "!$" filename.txt`<br>
    - Тут `$` - специальный символ, который указывает на конец строки<br>

    - Запустите скрипт и проверьте его работу

3. Сохранение данных в переменную

   Выполняя предыдущее задание вы заметили, что команда по умолчанию выводит данные в консоль,<br>
   но полученные данные также можно сохранять и в переменную.

   В качестве упражнения давайте решим следующую задачу для все того же стихотворения:<br>
   - Сохраним в переменную строки содержащие "the" или "to", _важно чтобы это были отдельные слова, а не части других_.<br>
   `lines=$(grep -i -E '\b(the|to)\b' filename.txt)`<br>
   - Давайте подробней разберем эту команду:<br>
     `-i` Игнорирует регистр при поиске<br>
     `-E` включает поддержку расширенных регулярных выражений (чтобы использовать | для логического ИЛИ)<br>
     `\b` — это границы слова, которые гарантируют, что будут найдены только целые слова "the" и "to"<br>
     `(the|to)` — ищет строки, которые содержат либо "the", либо "to".<br>
   - Добавим в скрипт запись найденных строк в другой файл:<br>
    `echo "$lines" > filename2.txt`

   - Запустите скрипт и проверьте его работу
    
## Задание лабораторной работы (его нужно включить в отчет!)

Перед тем как выполнять задания, проделайте следующие действия:
 - В той же директории, где будет находится скрипт создайте папку `DataPhoneNumbers`
 - В ней создайте несколько файлов с названиями формата *cityname.txt*
 - Заполните их номерами телефонов в формате `+7(xxx)xxx-xx-xx` (добавьте также в каждый файл номера, не подходящие под формат)<br>
 
Теперь напишите скрипт следующий скрипт:
- Получает на вход названия городов через пробел
- Считывает номера телефонов из соответствующих городам файлов из папки `DataPhoneNumbers`
- Проверяет валидность номеров, то есть соблюдение формата `+7(xxx)xxx-xx-xx`
- Правильные номера следует сохранить в файл *valid_numbers.txt*, а иные в файл *not_valid_numbers.txt* соответственно

*Подсказка, используйте grep :)*

### Как успешно сдать работу?

Создать свой репозиторий из шаблона этого. Как это делается - "Use this template" -> "Create a new repository" и сделайте его public. 

Находясь уже в своем репозитории - создайте новый файл формата .md и там оформляйте отчет. В отчете опишите все шаги которые вы делали, чтобы получить финальный результат работы. Необходимы только скриншоты скрипта и примера его выполнения!

Что вам нужно знать, чтобы успешно защитить работу:

Основные возможности команды grep. Флаги и их назначение. Как фильтровать и обрабатывать результаты поиска с помощью команды grep и других команд. Регулярные выражения: как создавать и использовать шаблоны для поиска текста. Использование метасимволов в регулярных выражениях: как искать слова, числа, сочетания символов, а также как использовать границы слова.

## Дополнительные источники

1. [Присваивание значений переменным.](https://se.ifmo.ru/~ad/Documentation/ABS_Guide_ru.html#VARASSIGNMENT)
2. [Подстановка переменных.](https://se.ifmo.ru/~ad/Documentation/ABS_Guide_ru.html#VARSUBN)
3. [Арифметические операции.](https://se.ifmo.ru/~ad/Documentation/ABS_Guide_ru.html#ARITHEXP)
4. [Проверка условий.](https://se.ifmo.ru/~ad/Documentation/ABS_Guide_ru.html#TESTS)
5. stackoverflow.com
6. Хорошая ĸнига по Shell/bash в Linux - "Learn Linux Shell Scripting – Fundamentals of Bash 4.4" Sebastiaan
Tammer
7. [Функции.](https://se.ifmo.ru/~ad/Documentation/ABS_Guide_ru.html#FUNCTIONS)
8. [Функции и рекурсивные функции.](https://habr.com/ru/company/ruvds/blog/327248/)
9. [Циклы.](https://se.ifmo.ru/~ad/Documentation/ABS_Guide_ru.html#LOOPS)
10. [Массивы](https://se.ifmo.ru/~ad/Documentation/ABS_Guide_ru.html#ARRAYS)
11. [Про двоичную систему и IP-адрес](https://zametkinapolyah.ru/kompyuternye-seti/4-4-dvoichnye-chisla-i-dvoichnaya-sistema-schisleniya-perevod-chisla-v-dvoichnuyu-sistemu-schisleniya-iz-desyatichnoj.html)
12.  В. Олифер, Н. Олифер "Компьютерные сети. Принципы, технологии, протоколы. Учебник" (2016)
