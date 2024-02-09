Первым делом запустим докер контейнер и установим в него все, что нам необходимо

```apt update```
```apt upgrade```
```apt install libfcgi-dev libfcgi0ldbl spawn-fcgi gcc```

Перенесем наш сервер и nginx.conf в докер, а затем перезапустим nginx внутри докер-образа через команду exec

![task_3_1](./../screenshots/task_3_1.jpg "task_3_1")

Чтобы скомпилировать сервер, используем

```gcc -o server server.c -lfcgi```

Затем запускаем

```spawn-fcgi -p 8080 server```

UPD: Docker контейнер запускаем с маппингом портов 80:81, тогда страница будет отдаваться по адресу http://localhost:80 

![task_3_2](./../screenshots/task_3_2.jpg "task_3_2")

![task_3_3](./../screenshots/task_3_3.jpg "task_3_3")

![task_3_4](./../screenshots/task_3_4.jpg "task_3_4")