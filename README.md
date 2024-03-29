# ***Дипломный проект по профессии "Тестировщик"***

_Дипломный проект — автоматизация тестирования комплексного сервиса, взаимодействующего с СУБД и API Банка._

## О проекте:

_Приложени веб-сервиса, которое предлагает купить тур по определённой цене двумя способами:_

1. Обычная оплата по дебетовой карте.
2. Уникальная технология: выдача кредита по данным банковской карты.

![путешествие дня](https://raw.githubusercontent.com/Urvantseva/DiplomQA-67/main/img_1.png)

_Само приложение не обрабатывает данные по картам, а пересылает их банковским сервисам:_

+ сервису платежей Payment Gate;
+ кредитному сервису Credit Gate.

_Приложение в собственной СУБД должно сохранять информацию о том, успешно ли был совершён платёж и каким способом. Данные карт при этом сохранять не допускается._

# ***Инструкция по запуску тестирования***

## _Предусловия:_

Установлено ПО: Git Bash, IntelliJ IDEA и Docker Desktop, DBeaver. Дополнительно: Java 11.

## _Последовательность действий:_

1. Клонировать репозиторий командой git clone 
2. Открыть скопированный проект в IntelliJ IDEA.
3. Запустить Docker Desktop.
4. В терминале IntelliJ IDEA запустить необходимые базы данных и нужные контейнеры командой docker-compose up.
5. Открыть новую вкладку в терминале IntelliJ IDEA.
6. В терминале IntelliJ IDEA запустить команду java -jar ./artifacts/aqa-shop.jar.
+ java "-Dspring.datasource.url=jdbc:mysql://localhost:3306/app" -jar artifacts/aqa-shop.jar.
+ java "-Dspring.datasource.url=jdbc:postgresql://localhost:5432/app" -jar artifacts/aqa-shop.jar.
7. Запустить "DBeaver" и создать подключение к mysql или postgresql (данные для подключения - порт, имя БД, пользователь, пароль - взять из файла docker-compose.yml).
8. Открыть новую вкладку в терминале IntelliJ IDEA.
9. Запустить тестирование командой:
+ для mysql: ./gradlew clean test "-Ddb.url=jdbc:mysql://localhost:3306/app"
+ для postgresql: ./gradlew clean test "-Ddb.url=jdbc:postgresql://localhost:5432/app"
10. Открыть новую вкладку в терминале IntelliJ IDEA.
11. Сформировать отчёт по тестированию командой ./gradlew allureReport и открыть в браузере.
12. Завершить работу:
+ остановить работу приложения командой Ctrl+C или закрыть окно терминала, в котором оно было запущено;
+ остановить контейнер командой docker-compose down или командой Ctrl+C в окне терминала, в котором он был запущен.
13. Остановить контейнеры: docker-compose down







