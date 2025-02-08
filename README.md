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

Выкачиваем репозиторий с сайта `sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo`

![image](https://github.com/user-attachments/assets/94c7771f-91cd-425d-a417-3559927d7501)

Устанавлием докер `sudo yum install docker-ce docker-ce-cli containerd.io`

![image](https://github.com/user-attachments/assets/526265b0-2b00-4c8d-a6d0-01be2b24e182)

Cоглашаемся, чтобы завершить процесс установки всех перечисленных пакетов

![image](https://github.com/user-attachments/assets/65a5c293-79ca-4178-9c0b-880226951a60)

Запускаем Docker с помощью команды:  `sudo systemctl enable docker --now`

![image](https://github.com/user-attachments/assets/177bc2db-5c30-4eac-8648-5b468329ec29)
