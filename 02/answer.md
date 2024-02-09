## Part 2

* Прочитаем конфигурационный файл nginx.conf внутри докер контейнера через команду exec.

```docker run -d nginx```
```docker ps```

узнали id контейнера

```docker exec f697e2 cat /etc/nginx/nginx.conf```

![docker exec](./../screenshots/task_2_1.png "docker_exec")

* Создадим на локальной машине файл nginx.conf.

![nginx.conf](./../screenshots/task_2_2.png "nginx.conf")

* Настроим в нем по пути /status отдачу страницы статуса сервера nginx.

![nginx.status](./../screenshots/task_2_3.png "nginx.status")

* Скопируем созданный файл nginx.conf внутрь докер-образа через команду docker cp, а также перезапустим nginx внутри докер-образа через команду exec.

```docker cp nginx.conf f697e2:/etc/nginx/nginx.conf```
```docker exec f697e2 nginx -s reload```

![docker cp](./../screenshots/task_2_4.png "docker_cp")

* Проверим, что по адресу localhost:80/status отдается страничка со статусом сервера nginx.

![docker_run_nginx_status](./../screenshots/task_2_5.png "docker_run_nginx_status")

* Экспортируем контейнер в файл container.tar через команду export.

```docker export f697e2 > container.tar```

![docker export](./../screenshots/task_2_6.png "docker_export")

* Остановим контейнер.

```docker stop f697e2```

![docker_stop_container](./../screenshots/task_2_7.png "docker_stop_container")

* Удалим образ через docker rmi [image_id|repository], не удаляя перед этим контейнеры.

```docker rmi -f nginx```

![docker rmi](./../screenshots/task_2_8.png "docker_rmi")

* Удалим остановленный контейнер.

```docker rm f697e2```

![docker rm](./../screenshots/task_2_9.png "docker_rm")

* Импортируем контейнер обратно через команду import. И запустим импортированный контейнер.

```docker import -c 'cmd ["nginx", "-g", "daemon off;"]' -c 'ENTRYPOINT ["/docker-entrypoint.sh"]' container.tar nginx```
```docker run -d -p 80:80 -p 443:443 41683089a223```

![docker_import](./../screenshots/task_2_10.png "docker_import")

* Проверим, что по адресу localhost:80/status отдается страничка со статусом сервера nginx.

![nginx restart](./../screenshots/task_2_11.png "nginx_restart")