# Инструкция по нагрузочному тестированию с помощью Jmeter

## Подготовка к тестированию 
Нагрузочное тестирование проводится на программе Apache JMeter.

1. Для работы с *Apache JMeter*, необходимо установить *Java 8+*,

2.	Скачать *Java 8+*: https://www.java.com/ru/download/manual.jsp, 

3.	После установки *Java 8+*, скачать *Jmeter*,

4.	Скачать *Jmeter*: https://jmeter.apache.org/download_jmeter.cgi, 

5.	Скачать в формате zip: apache-jmeter-5.6.2.zip, 

6.	Скачивается *Jmeter* архивом, необходимо его разархивировать, 

7.	Рекомендуется перенести *jmeter* на дополнительный диск (например, диск D), 

8.	Если на компьютере только диск C, то в корневую папку C:\Program Files (x86),

9. В пути к папке не должно быть русского языка, т.к. при выгрузке результатов, система не сможет найти путь к папке.

## Создание сценария тестирования 

1.	Открыть папку *Jmeter* (обычно называется, apache-jmeter-5.6.2),

2. Открыть папку *bin*,

3. Запустить программу файлом *jmeter.bat (или jmeter)*, 

4.	После запуска, открывается окно программы и окно командной строки,

5.	Командную строку не закрывать, без нее программа работать не будет,

6.	При запуске программы, автоматически создается *Test Plan*: пустой файл для создания сценария тестирования, 

7.	В *Test Plan* добавить *HTTP Cookie Manager*:

    7.1. *HTTP Cookie Manager* нужен для авторизации на сайте,

    7.2. Заполнить таблицу *User-Defined Cookies* данными из Devtools (F12), вкладка Application, 

8.	Добавить группу потоков:

    8.1. Правой кнопкой мыши кликнуть на *Test Plan*,

    8.2. Выбрать *Add → Threads (Users) → Thread Group*,

    8.3. Заполнить данные в группе потоков (*Threads Group*):

        Поменять имя группы (Name),

        Добавить комментарии (Comments),

        Указать количество пользователей (Number of Threads (users)),

        Указать период времени входа в систему пользователей (Ramp-up period (seconds)),
        
        Время указывается в секундах,


9. В группу потоков (*Threads Group*) добавить запрос, который будет отправляться в систему: 

    9.1. *Threads Group* → правая кнопка мыши → *Add* → *Sampler* →  *HTTP Request*,

10.	Заполнить поля запроса: поля *Protocol* [http], *Server name or IP*, *Port number*, *Path*,

11.	Добавить отчеты по результатам: *HTTP Request* → правая кнопка мыши → *Add* → *Listener*,

    11.1. *View Results Tree*: показывает успешность запросов, куки-файлы, html код страницы,

    11.2. *View Results in Table*: показывает результаты запросов в таблице (время, статус),

    11.3. *Summary Report*: показывает результаты запросов в более подробной таблице.

## Запуск тестирования

1. Тестирование запускается зеленой кнопкой Start,

2.	Очистка результатов тестирования только в 1 папке: значок метлы,

3.	Очистка всех результатов тестирования: значок 2х мётел,

4.	Функция *Disable* (правой кнопкой мыши по сценарию тестирования): не использовать папку при тестировании,

22. Функция *Toggle* (правой кнопкой мыши по сценарию тестирования): использовать папку при тестировании.

## Выгрузка результатов тестирования

1.	Открыть командную строку (Windows Powershell), 

2.	Прописать путь к файлу jmeter.bat, 

3.	Перейти в папку: команда cd.. + имя папки,

    Например, PS C:\Program Files (x86)\jmeter\bin> 

4. Из *PS C:\Program Files (x86)\JMETER\bin>* отправляем команду на выгрузку результатов тестирования:

    .\jmeter -n -t .\Platus.jmx -l log1500.jtl -e -o .\ RESULT4\

5.	Где, 

    Platus.jmx => название файла, из которого выгружаем;

    log1500.jtl => название папки для логов (создается автоматически);

    RESULT4 => название папки для результатов (создаётся автоматически).

### Дополнительная информация: 

1.	Функция *HTTP Request* + чекбокс *Redirect Automatically*: перенаправлять автоматически, т.е. программа рассматривает перенаправление 1 запрос, 

2.	Функция *HTTP Request* + чекбокс *Follow Redirects*: следовать за перенаправлениями, т.е. каждое перенаправление является отдельным запросом (например, сначала запрос на авторизацию, после нее запрос в справочник/отчет), 

3. Перед проведением нового тестирования обновлять куки-файлы в *HTTP Cookie Manager* с главной страницы тестируемой системы. 

### Используемый материал: 

1.	Урок на ютубе: https://www.youtube.com/watch?v=ik3FY5Qhq9o&t=52s&ab_channel=ADV-IT

2. Инструкция Apache JMeter: https://jmeter.apache.org/

