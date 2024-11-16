# Лабораторная работа №4 - Отчет

### Основная задача
1. Запустить в контейнере aafire
   a) Создаем докерфайл с помощью vim Dockerfile
   
   b) Вписываем в файл:
   ```
   FROM ubuntu:latest
   RUN apt-get update && apt-get install -y libaa-bin fortune
   ```
   c) Cобираем образ контейнера
   
   ![Screenshot from 2024-11-16 19-08-24](https://github.com/user-attachments/assets/b92618ad-83a3-4c33-8acf-e83d6c461f45)

   d) Подключаемся к контейнеру и запускаем файл
   
   ![Screenshot from 2024-11-16 19-08-41](https://github.com/user-attachments/assets/ecff376c-f88d-4c73-9335-44cad3a63a9b)

   Результат:

   ![image](https://github.com/user-attachments/assets/d7cc7378-ed59-47a2-8315-6b69a4648f28)

3. Наладить связь между контейнерами
   
   a) Установим ping, дописав строку RUN
   ```
   ... && apt-get install iputils-ping -y
   ```
   b) Запустим два контейнера командой из шага d) пункта номер 1 (чтобы закрыть контейнер, оставив его работать, можно нажать Сtrl + P и Ctrl + Q последовательно)
   
   Проверка с помощью docker ps:

   ![image](https://github.com/user-attachments/assets/9c5726ae-6a54-4041-ad97-455682ddb580)

   с) Создаем сеть, куда подключаем наши контейнеры

   ![Screenshot from 2024-11-16 19-55-46](https://github.com/user-attachments/assets/fba71c62-ecd8-46d8-b53a-fcda0a9ff9bf)

   d) Включаем контейнеры в созданную ранее сеть

   ![Screenshot from 2024-11-16 20-07-45](https://github.com/user-attachments/assets/86f53178-c7bc-4438-9c51-9f7bb89dcd48)

   ![Screenshot from 2024-11-16 20-11-59](https://github.com/user-attachments/assets/5038f773-d05f-43a9-8379-82585dbdabe5)

   е) Узнаем ip каждого из контейнеров с помощью команды
   ```
   docker network inspect myNetwork
   ```
   Результат:

   ![image](https://github.com/user-attachments/assets/e06390b0-f156-41b2-99ed-9b202f9c4028)

   f) Зайдем в терминал контейнера nice_cohen и проверим его доступ к контейнеру beautiful_swartz

   ![image](https://github.com/user-attachments/assets/367aaf33-1684-4058-8c1b-0e98182467b7)

   Потери данных не происходит, а значит соединение установлено корректно
   
### Вывод

Мы научились создавать контейнеры, запускать в них приложения и устанавливать соединение между контейнерами

### Автор

Сусликова Вероника Денисовна 467632  

