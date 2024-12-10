# Лабораторная работа №5 - Отчет

### Основная задача

### Задача 1 - Автоматизация проверки файлов при коммите

Устанавливаем Git for ubuntu на нашу виртуальную машину и копируем созданный нами репозиторий с помощью команды из пункта 2 Введения. Заходим в скрытую папку .git а далее в папку hooks в которой с помощью nano 
создаем файл pre-commit со следующим содержанием:

![Screenshot from 2024-12-07 19-05-50](https://github.com/user-attachments/assets/cd5a02c0-f79b-4cea-ad1d-7cc05c75238e)

### Пояснения к некоторым строчкам:

set -e - заставляет скрипт немедленно завершиться, если какая-либо команда вернет ошибку. Это помогает избежать выполнения последующих шагов, если что-то пошло не так.

check_file_format() - функция, проверяющая существование файла и наличие в его тексте искомой подстроки (в нашем случае "Writer:") с помощью grep (опция -q заставляет grep не 
выводить результат поиска, а только возвращать код: 0 (успех, если строка найдена) или 1 (если строка отсутствует))

files_to_check=$(git diff --cached --name-only --diff-filter=ACM | grep '\.txt$') - эта команда собирает список всех файлов .txt, которые находятся в staging(это промежуточная область в Git, куда
мы добавляем изменения перед коммитом) и были добавлены, изменены или скопированы.

Если измененных файлов нет, завершаем программу успешным выводом (0) сразу

Если файлы есть, вызываем для каждого из них циклом вышеописанную функцию check_file_format и в случае отсутствия ошибок выводим соответствующее сообщение.

### Проверяем

Изменяем тестовый файл так, чтобы в нем не было искомой подстроки. При попытке коммита получаем ошибку:

![Screenshot from 2024-12-07 19-03-00](https://github.com/user-attachments/assets/a89e425c-ed75-4422-a9c5-8b1263c25f81)

![Screenshot from 2024-12-07 19-02-30](https://github.com/user-attachments/assets/b286abc3-8fae-4018-94b5-e0bd6a77399f)

Изменяем тестовый файл снова, но теперь чтобы искомая подстрока в нем была. Получаем сообщение об отсутствии ошибок:

![Screenshot from 2024-12-07 19-03-19](https://github.com/user-attachments/assets/df8eea20-14cd-4e3b-ac40-fd38c6feb55c)

![Screenshot from 2024-12-07 19-03-48](https://github.com/user-attachments/assets/a5204dde-a976-475f-b30d-02b083c5c04f)

Работа соответствует условиям, а значит задание выполнено.

### Задача 2 - Использование Git Flow в проекте

Устанавливаем git flow на локальной машине и инициализируем его в корне нашего репозитория

![Screenshot from 2024-12-10 13-26-10](https://github.com/user-attachments/assets/e98d22d9-152c-4fdb-aeed-efa1a14ac9c3)

Создаем ветку новой функциональности по команде из задания лабораторной, создаем файл task_manager.py и коммитим его

![Screenshot from 2024-12-10 13-24-24](https://github.com/user-attachments/assets/8ca2d181-5d36-485c-89b6-5a0a64cd1350)

Предположим, что мы написали какую-то функцию. Завершаем фичу и объединяем текущую ветку с веткой develop

![Screenshot from 2024-12-10 13-27-06](https://github.com/user-attachments/assets/c73f23a9-efe3-4bc9-9da5-8b82f887fdc4)

Начинаем создание релиза

![Screenshot from 2024-12-10 13-28-21](https://github.com/user-attachments/assets/3a2736f2-9200-4d9c-ad38-99746fe1a53f)

Представим, что вносим изменения, связанные с релизом: создаем файл versions.txt и коммитим его

![Screenshot from 2024-12-10 13-30-04](https://github.com/user-attachments/assets/fde74f12-5b1f-4484-9f75-49928c705cbd)

Завершаем релиз и объединяем его ветку с основной

![Screenshot from 2024-12-10 13-33-40](https://github.com/user-attachments/assets/738b5d4a-4fa5-45ad-a4fd-c55fb746d0b7)

Несмотря на отсутствие конфликтов в ветках, содаем hotfix 

![Screenshot from 2024-12-10 13-35-17](https://github.com/user-attachments/assets/3eae0c21-af3b-4bf5-9473-626da6d3a5a6)

Представляем что вносим изменения для исправления каких-то ошибок (создаем файл file_with_error) и коммитим их, после 
чего закрываем hotfix и объединяем текущую ветку с основной

![Screenshot from 2024-12-10 13-37-56](https://github.com/user-attachments/assets/b4868638-4b05-4b33-8830-817c5a2efce5)

После этого пушим все изменения в ветки develop и main (отправляем изменения в удаленный репозиторий)