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

2. Наладить связь между контейнерами

   

