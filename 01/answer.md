## Part 1

Сначала  запустим Docker

![Docker start](./../screenshots/task_1_1.png "docker_start")

* Возьмем официальный докер-образ с nginx и выкачаем его при помощи docker pull.

```docker pull nginx```

![Docker pull NGINX](./../screenshots/task_1_2.png "docker_pull_nginx")

* Проверяем наличие докер-образа через 

 ```docker images```

![docker images](./../screenshots/task_1_3.png)

* Запускаем докер-образ через docker run -d [image_id|repository], а также проверим, что образ запустился через docker ps.

```docker run -d nginx```
```docker ps```

![Docker run](./../screenshots/task_1_4.png "docker_run")

* Посмотрим информацию о контейнере через docker inspect [container_id|container_name]. 

```docker inspect 15b5c07df39e```

![docker inspect](./../screenshots/task_1_5.png "docker_inspect")

размер контейнера

![container_size](./../screenshots/task_1_6_1.png "container_size")

Разница в том, что SizeRootFs - это общий размер всех файлов в контейнере в байтах, в то время как SizeRw - это размер файлов, которые были созданы или изменены, если сравнивать контейнер с его базовым образом. Сразу после создания это значение должно быть равно нулю; по мере изменения (или создания) файлов оно будет увеличиваться.

список замапленных портов

![container_port](./../screenshots/task_1_6_2.png "container_port")

ip контейнера

![ip_container](./../screenshots/task_1_6_3.png "ip_container")

Также, часть из этого можно посмотреть используя команду ```docker container ls -s```

![docker_ls](./../screenshots/task_1_6_4.png "docker_ls")

* Остановим докер образ через docker stop [container_id|container_name] и проверим, что образ остановился через docker ps.

```docker stop 15b5c07df39e```
```docker ps```

![docker stop](./../screenshots/task_1_7.png "docker_stop")

* Запустим докер с портами 80 и 443 в контейнере, замапленными на такие же порты на локальной машине, через команду run.

```docker run -d -p 80:80 -p 443:443 nginx```

![docker_80_443](./../screenshots/task_1_8.png "docker_80_443")

* Проверим, что в браузере по адресу localhost:80 доступна стартовая страница nginx.

![nginx_browser](./../screenshots/task_1_9.png "docker_browser")

* Перезапустим докер контейнер через docker restart [container_id|container_name] и проверм, что контейнер запустился.

```docker restart b66e07ce9271```
```docker ps```

![docker_restart](./../screenshots/task_1_10.png "docker_restart")