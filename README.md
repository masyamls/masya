# masya
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

Выкачиваем репозиторий с сайта 
`sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo`

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

Команда git clone https://github.com/skl256/grafana_stack_for_docker.git используется для создания локальной копии репозитория, находящегося на GitHub. После выполнения этой команды в текущем каталоге будет создан новый каталог с именем grafana_stack_for_docker, в который будет скопировано содержимое удаленного репозитория.

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

![image](https://github.com/user-attachments/assets/84f33dd6-2263-4a20-8a64-ece71f31c772)
![image](https://github.com/user-attachments/assets/2fd54fca-1a92-4520-846b-d418b62a733a)


![image](https://github.com/user-attachments/assets/0ef344a5-cd6d-4c0f-910e-3c41bd369d79)

![image](https://github.com/user-attachments/assets/8021d304-56de-4fce-963b-e18f9a1d5e33)

![image](https://github.com/user-attachments/assets/d74fed06-7e3f-4ad8-aee4-5ba8e7668bc3)


![image](https://github.com/user-attachments/assets/bb4529f3-f929-49c5-a2a1-cedb08cc3f43)

![image](https://github.com/user-attachments/assets/0ae961fc-a9e2-4a1c-918b-3a5b6cd00d62)

![image](https://github.com/user-attachments/assets/97513e42-2f7a-4d24-b181-f197d91573c4)

![image](https://github.com/user-attachments/assets/a6acaef0-dbcf-43a8-81bb-4fcc024ca476)

![image](https://github.com/user-attachments/assets/4455687e-5029-4512-9f12-3868b66b90e5)
