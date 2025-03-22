Вводим команду `sudo yum install wget`
для установки утилиты wget. Возникает ошибка, что указывает на проблемы с правами доступа, начинаем ее исправление.

![image](https://github.com/user-attachments/assets/7444c749-516c-417a-9fc2-e44262c9b851)

Вводим команду `su root`.
После открываем в конфигурационный файл `vi /etc/sudoers` 
и производим изменения, выходим с сохранением (esc, shift+Ж, :wq!). 

![image](https://github.com/user-attachments/assets/3648054e-0f98-4ca1-adfa-914b80650abb)

После изменения добавляем окно и видим, что пакет `wget-1.21.1-8.el 9_4.x86_64` установлен.

![image](https://github.com/user-attachments/assets/b78083ad-8bd5-40cf-a114-d5b33cd2bf1b)

Вводим команду `sudo yum install curl`
для установки утилиты curl

![image](https://github.com/user-attachments/assets/dc9c6ec0-7be5-4f72-868e-5c76f0d45806)

`sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo` - выкачиваем репозиторий с сайта

![image](https://github.com/user-attachments/assets/94c7771f-91cd-425d-a417-3559927d7501)

Устанавлием докер `sudo yum install docker-ce docker-ce-cli containerd.io`

Docker (docker-ce), интерфейс командной строки Docker (docker-ce-cli) и containerd, который является инструментом для управления контейнерами.
![image](https://github.com/user-attachments/assets/526265b0-2b00-4c8d-a6d0-01be2b24e182)

Cоглашаемся, чтобы завершить процесс установки всех перечисленных пакетов

![image](https://github.com/user-attachments/assets/65a5c293-79ca-4178-9c0b-880226951a60)

Запускаем Docker с помощью команды:  `sudo systemctl enable docker --now`

![image](https://github.com/user-attachments/assets/177bc2db-5c30-4eac-8648-5b468329ec29)


`COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)`
вся команда получает последнюю версию Docker Compose из ответа API GitHub и сохраняет её значение в переменную `COMVER`.

`sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose` - эта команда загружает файл последней версии Docker Compose и помещает его в каталог /usr/bin/ с именем docker-compose.

Команда `sudo chmod +x /usr/bin/docker-compose` изменяет права доступа к файлу docker-compose, который находится в каталоге /usr/bin.

Команда `docker-compose --version` выводит текущую установленную версию Docker Compose (Docker Compose version v2.33.0)

![image](https://github.com/user-attachments/assets/852d58c4-bfc8-42cb-82c0-db185fa893dd)

Команда `git clone https://github.com/skl256/grafana_stack_for_docker.git` используется для создания локальной копии репозитория, находящегося на GitHub. После выполнения этой команды в текущем каталоге будет создан новый каталог с именем grafana_stack_for_docker, в который будет скопировано содержимое удаленного репозитория.

![image](https://github.com/user-attachments/assets/6b55e5ca-c15c-4b1e-94e4-d3966c3a4e2c)

Выполнили команду `cd grafana_stack_for_docker`, чтобы перейти в каталог, который был создан в результате клонирования.

![image](https://github.com/user-attachments/assets/22742d0b-c063-4a21-a846-faf6e82258c2)

`sudo mkdir -p /mnt/common_volume/swarm/grafana/config` - после выполнения этой команды будет создан каталог config по указанному пути, а также все необходимые родительские каталоги, если они отсутствовали.

![image](https://github.com/user-attachments/assets/2df3c7b3-512a-4b47-836f-92ef55f37da4)

`sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data}`- после выполнения этой команды будет создан каталог grafana по пути /mnt/common_volume, если он не существует, а также три подкаталога grafana-config, grafana-data и prometheus-data внутри него.

![image](https://github.com/user-attachments/assets/36052422-e89b-4419-9cc5-c5ab7bfb8223)

`sudo chown -R $(id -u):$(id -g) {/mnt/common_volume/swarm/grafana/config,/mnt/common_volume/grafana}` - после выполнения этой команды текущий пользователь станет владельцем и группы для каталогов config и grafana, а также всех их содержимых. 

![image](https://github.com/user-attachments/assets/4e95ac2e-c5f0-4ca8-b66a-4504d12b351e)

`touch /mnt/common_volume/grafana/grafana-config/grafana.ini` - после выполнения этой команды будет создан пустой файл grafana.ini в каталоге grafana-config
![image](https://github.com/user-attachments/assets/1428c7eb-40a7-4d1b-bff5-a7ede55e7aa9)

`cp config/* /mnt/common_volume/swarm/grafana/config/` - после выполнения этой команды все файлы из каталога config будут скопированы в каталог /mnt/common_volume/swarm/grafana/config/.
![image](https://github.com/user-attachments/assets/dae22369-8ef7-4280-b46e-40a27aa573fb)

`mv grafana.yaml docker-compose.yaml` - после выполнения этой команды файл grafana.yaml будет переименован в docker-compose.yaml.
![image](https://github.com/user-attachments/assets/fe9fbefc-fd2b-4994-8bf2-1002b47ea941)

`sudo docker compose up -d`/ . Docker Compose начинает создавать и запускать все сервисы, указанные в docker-compose.yml файле.
флаг -d:
Ctrl + C: Прерывает (остановливает) выполнение текущей команды или процесса в терминале. Если запустили контейнеры без флага -d, использование Ctrl + C остановит их.
Ctrl + Z: Приостанавливает выполнение текущего процесса и переводит его в фоновый режим. Это позволяе вернуться к терминалу и продолжить работу, но при этом процесс останется приостановленным. Чтобы вернуть процесс в активное состояние, можно использовать команду fg.

![image](https://github.com/user-attachments/assets/84f33dd6-2263-4a20-8a64-ece71f31c772)
![image](https://github.com/user-attachments/assets/2fd54fca-1a92-4520-846b-d418b62a733a)


![image](https://github.com/user-attachments/assets/0ef344a5-cd6d-4c0f-910e-3c41bd369d79)

Переходи в каталог с помощью команды `cd grafana_stack_for_docker`. 
Команда `sudo docker compose up -d` используется для запуска контейнеров Docker.

![image](https://github.com/user-attachments/assets/8021d304-56de-4fce-963b-e18f9a1d5e33)

Заходим в `vi docker-compose.yaml` и выходим без сохранения
![image](https://github.com/user-attachments/assets/d74fed06-7e3f-4ad8-aee4-5ba8e7668bc3)

Команда `sudo docker-compose stop` используется для остановки запущенных контейнеров
![image](https://github.com/user-attachments/assets/bb4529f3-f929-49c5-a2a1-cedb08cc3f43)

 `sudo docker-compose up -d` - снова запустили контейнеры, и они были успешно запущены
![image](https://github.com/user-attachments/assets/0ae961fc-a9e2-4a1c-918b-3a5b6cd00d62)

Команда `sudo docker-compose down` - остановили и удалили все контейнеры
![image](https://github.com/user-attachments/assets/97513e42-2f7a-4d24-b181-f197d91573c4)

Команда `sudo docker-compose up -d`- снова запустили контейнеры
![image](https://github.com/user-attachments/assets/a6acaef0-dbcf-43a8-81bb-4fcc024ca476)

Команда `sudo docker-compose ps`- вывели список запущенных контейнеров с их статусами и портами
![image](https://github.com/user-attachments/assets/4455687e-5029-4512-9f12-3868b66b90e5)

Перемещаемся в папку `cd grafana_stack_for_docker` загружаем репозиторий masya с GitHub в командой `git clone https://github.com/masyamls/masya.git`

![image](https://github.com/user-attachments/assets/223cf3eb-c58f-48aa-bd8c-497e3c94f533)

Создаем копию файла(docker-compose.yaml) командой `cp docker-compose.yaml  docker-compose.yaml1`
![image](https://github.com/user-attachments/assets/3263039d-b5fb-494d-a85f-e68be62fb437)

Перемещаемся в директорию, где находятся конфигурационные файлы `cd /mnt/common_volume/swarm/grafana/config` и создаем копию файла (prometheus.yaml) следущей командой `cp prometheus.yaml  prometheus.yaml1`

![image](https://github.com/user-attachments/assets/cdc38987-4c41-4b3b-8ccd-ae9a2b7e94f9)

останавливает и удаляет все контейнеры, которые были запущены с помощью Docker Compose командой `sudo docker-compose down` и  далее запускаем контейнеры `sudo docker-compose up -d`
![image](https://github.com/user-attachments/assets/f67004f2-eaf5-488b-a9bf-64377e5e493c)

`sudo docker-compose stop` - останавливаем работающие контейнеры
![image](https://github.com/user-attachments/assets/63acc442-1c09-48ee-86eb-82ac74254307)

Вносим необходимые изменения `sudo vi prometheus.yaml`(после редактирования нажмимаем Esc, затем :wq и Enter, чтобы сохранить изменения и выйти.)
![image](https://github.com/user-attachments/assets/d3112ee1-50a8-4c5c-b958-7621d5b57da9)

Снова запускаем контейнеры `sudo docker-compose up -d`

![image](https://github.com/user-attachments/assets/5a6ef78e-b2df-493e-bcd5-2685f295fcdf)

```Grafana```

переходим на сайт ``localhost:3000``

User & Password GRAFANA: ``admin``

После того как зашли, нужно создать Dashboards. 

``Home -> Connections -> Data sources -> Add data source``

После нажимаем ``+Add visualization -> Configure a new data source -> Prometheus``

Настройки прометеуса: 

http://prometheus:9090 
Authentication: Basic authentication 
Save & test

Cоздав Dashboards импортируем его: ``Home -> Dashboards -> Import dashboard``

Далее

``1860 -> Load Select Prometheus -> Import -> Название Prometheus``

![image](https://github.com/user-attachments/assets/18c48c5e-91d0-4ee5-a5f8-45f04361ab14)
