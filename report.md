1. Создадим файлы городов в папке DataPhoneNumbers<br>
   ![image](https://github.com/user-attachments/assets/91c5682a-1fbb-452e-83fa-b6480021b43e)
2. Заполним эти файлы (пример заполнения одного из файлов):<br>
![image](https://github.com/user-attachments/assets/968fe4ce-1a6d-43cc-8e81-3b4602e96aee)
3. Напишем скрипт сортировки номеров<br>
   Используем `grep`, чтобы фильтровать названия файла и валидные номера через регулярное выражение
```bash
#!/bin/bash
 
if [ $# -eq 0 ]; then
 echo "Города не введены"
 exit 0
fi
 
> valid_numbers.txt
 
for city in "$@"; do

  file_name=$(find DataPhoneNumbers/ -type f | grep -i "$city\.txt")
  if [ -z $file_name ]; then
    echo "Файл города $city не найден"
    continue
  else 
    echo "Сортировка файла города $city..."
  fi
   
  valid_numbers=$(grep -P '^\+7\([0-9]{3}\)[0-9]{3}-[0-9]{2}-[0-9]{2}' $file_name)
  for val_number in $valid_numbers; do
    echo "$city - $val_number" >> valid_numbers.txt
  done

done
```
5. Запускаем наш скрипт<br>
![image](https://github.com/user-attachments/assets/97acc015-c66d-40b4-82c3-90d586b484dd)
6. Видим результат в файле *valid_numbers.txt*<br>
![image](https://github.com/user-attachments/assets/c34623f6-0f45-442c-b8d9-5691e6a6e23c)

