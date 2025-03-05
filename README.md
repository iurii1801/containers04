# Лабораторная работа №4: Запуск Apache в контейнере Docker

## Цель работы

Данная лабораторная работа знакомит с основами работы с Docker, включая запуск контейнеров, установку и настройку веб-сервера Apache, а также развертывание веб-страницы внутри контейнера.

---

## Задание

Запустить контейнер Ubuntu, установить Web-сервер Apache и вывести в браузере страницу с текстом "Hello, World!".

## Выполнение

1. Создание репозитория `containers04` и клонирование его себе на компьютер.

![image](https://i.imgur.com/hIRcBX5.png)

2. Откроваем терминал в папке containers04 и выполняем команду:

```sh
docker run -ti -p 8000:80 --name containers04 ubuntu bash
```

![image](https://i.imgur.com/F4p3LIV.png)

3. В открывшемся окне выполняем следующие команды:

```sh
    apt update
```

![image](https://i.imgur.com/nWFVSxQ.png)

- Обновляет список доступных пакетов

```sh
    apt install apache2 -y
```

![image](https://i.imgur.com/P4t5qAq.png)

- Устанавливает веб-сервер Apache

```sh
    service apache2 start
```

![image](https://i.imgur.com/cjx1UcM.png)

- Запускает Apache

4. Проверяем работу сервера: в браузере открываем `http://localhost:8000`. Появляется стандартная страница Apache.

![image](https://i.imgur.com/63Xv49R.png)

## Создание веб-страницы "Hello, World!"

5. Выполняем следующие команды:

- Смотрим содержимое директории веб-сервера

```sh
    ls -l /var/www/html/
```

![image](https://i.imgur.com/7FElvd3.png)

- Создаем HTML-файл:

```sh
    echo '<h1>Hello, World!</h1>' > /var/www/html/index.html
```

![image](https://i.imgur.com/NLiieaZ.png)


### Обновляем страницу в браузере `http://localhost:8000`. Теперь мы видим сайт с надписью "Hello, World!".

![image](https://i.imgur.com/7CdlulA.png)

## Просмотр настроек Apache

6. Выполняем следующие команды:

```sh
    cd /etc/apache2/sites-enabled/
```

```sh
    cat 000-default.conf
```

- Переходим в каталог конфигурации Apache и открываем конфигурацию

![image](https://i.imgur.com/5UQozga.png)

- В файле находятся настройки виртуального хоста Apache.

## Завершение работы и удаление контейнера

7. Закрываем контейнер:

```sh
    exit
```

![image](https://i.imgur.com/rkO3fxY.png)

8. Просматриваем список всех контейнеров (запущенных и остановленных):

```sh
    docker ps -a
```

![image](https://i.imgur.com/iG0aTLh.png)

9. Удаляем контейнер:

```sh
    docker rm containers04
```

![image](https://i.imgur.com/kt0XPRk.png)

10. Проверяем, что контейнер удалён:

```sh
    docker ps -a
```

![image](https://i.imgur.com/W8GFiKc.png)

## Выводы

В ходе лабораторной работы был создан и собран образ на основе ubuntu:latest, содержащий веб-сервер Apache. Контейнер был успешно запущен, и веб-страница корректно отображалась в браузере по адресу `http://localhost:8000`.

В процессе работы освоены основные команды Docker: `создание образов`, `запуск контейнеров`, `просмотр содержимого файловой системы контейнера`, `удаление контейнеров` и другие. Полученные знания и навыки являются основой для дальнейшего изучения контейнеризации и работы с `Docker` в практических проектах.

---

## Используемые источники

- [Официальная документация Docker](https://docs.docker.com/)
- [Официальная документация Apache](https://httpd.apache.org/docs/)
- [Docker — основы контейнеризации](https://opensource.com/resources/what-docker)
- [Практическое руководство по работе с Docker](https://www.baeldung.com/docker)
- [Linux Basics for Docker](https://linuxize.com/post/how-to-use-docker-on-linux/)