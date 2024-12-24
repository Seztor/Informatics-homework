# Лабораторная работа: Инструмент Grep

## Пример (его в отчет включать не нужно!)

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

   Выполняя предыдущее задание вы могли заметить, что команда по умолчанию выводит данные в консоль,<br>
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

Перед тем как выполнять задание, проделайте следующие действия:
 - В той же директории, где будет находится скрипт создайте папку `DataPhoneNumbers`
 - В ней создайте несколько файлов с названиями формата *cityname.txt*
 - Заполните для каждого файла несколько номеров телефонов, каждый с новой строки, в определенном формате `+7(xxx)xxx-xx-xx` (добавьте также в каждый файл номера, не подходящие под формат)<br>
 
 К примеру, вот содержание файла "moscow.txt"
```
+7(963)999-15-43
+7(965)325-5-65
7(963)191-28-41
+7986342443
+7(900)123-45-67
+7(963)1241526-05
```

 
Теперь напишите скрипт следующий скрипт сортировки номеров по валидности:
- Получает на вход названия городов через пробел
- Считывает номера телефонов из соответствующих городам файлов .txt из папки `DataPhoneNumbers`
- Проверяет валидность номеров, то есть соблюдение формата `+7(xxx)xxx-xx-xx`
- Правильные номера со всех городов следует сохранить в файл *valid_numbers.txt*<br> (сохраняйте их в формате *`cityname - number`*, каждый с новой строки)

Для представленного выше файла "moscow.txt" ответ должен представлять собой:
```
moscow - +7(963)999-15-43
moscow - +7(900)123-45-67
...
```

*Подсказка, используйте grep для фильтрации :)*

### Как успешно сдать работу?

Создать свой репозиторий из шаблона этого. Как это делается - "Use this template" -> "Create a new repository" и сделайте его public. 

Находясь уже в своем репозитории - создайте новый файл формата .md и там оформляйте отчет. В отчете опишите все шаги которые вы делали, чтобы получить финальный результат работы.

Что вам нужно знать, чтобы успешно защитить работу:

Основные возможности команды grep. Флаги и их назначение. Как фильтровать и обрабатывать результаты поиска с помощью команды grep и других команд. Регулярные выражения: как создавать и использовать шаблоны для поиска текста. Использование метасимволов в регулярных выражениях: как искать слова, числа, сочетания символов, а также как использовать границы слова.

## Дополнительные источники

1. stackoverflow.com
2. Хорошая ĸнига по Shell/bash в Linux - "Learn Linux Shell Scripting – Fundamentals of Bash 4.4" Sebastiaan
Tammer
3. google.com
4. selectel.ru/blog/tutorials/grep-command-in-linux/
5. dzen.ru/a/Y6RANdocTxjhXSYM
