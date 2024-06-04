## Описание
Необходимо настроить систему с балансировщиком http трафика и автоматической установкой и конфигурированием всех контейнеров используя ansible.
Система должна быть доступна по адресу: http://VipLb. После запуска балансировщик, по алгоритму round-robin, поочередно распределяет запросы между web-серверами. После нескольких неудачных попыток, перенаправить трафик на нерабочий web-сервер, трафик на него больше не направляется. Поднимаем web-сервер, снова прогоняем плейбуки ansible и убеждаемся, что балансировщик снова его видит и направляет на него трафик.

## Инструкция
- клонируем проект: git clone https://github.com/IslamovDF/ansible_proj.git
- добавляем строку "127.0.0.1 VipLb" в файл hosts (для Windows: "C:\Windows\System32\drivers\etc", для linux: "/etc/hosts")
- подразумевается, что на хосте уже установлен Docker и Docker-compose. Из папки с проектом создаем и запускаем контейнеры: docker-compose up --build -d
- открываем консоль контейнера с ansible: docker exec -it ansible bash. В запущенной консоли запускаем плейбук и вводим логин и пароль ansible ansible соответственно: ansible-playbook /etc/ansible/playbooks/nginx.yml -kK

## Ссылки (для себя)
- https://habr.com/ru/companies/first/articles/683870/
- https://www.clusterlabs.org
- https://docs.ansible.com