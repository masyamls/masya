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

