# WebHW
Домашнее задание на тему "Работа с Web"
Задание:
Что нужно сделать?
Варианты стенда:
nginx + php-fpm (laravel/wordpress) + python (flask/django) + js(react/angular);
nginx + java (tomcat/jetty/netty) + go + ruby;
можно свои комбинации.
Реализации на выбор:
на хостовой системе через конфиги в /etc;
деплой через docker-compose.
Для усложнения можно попросить проекты у коллег с курсов по разработке
К сдаче принимается:
vagrant стэнд с проброшенными на локалхост портами
каждый порт на свой сайт
через нжинкс
Для начала устанавливаем сервисы для выполнения нашего ДЗ: Vagrant, Ansible, Virtualbox
Установка Vagrant:
wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(grep -oP '(?<=UBUNTU_CODENAME=).*' /etc/os-release || lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install vagrant
Установка Ansible:
apt install software-properties-common
add-apt-repository --yes --update ppa:ansible/ansible
apt install ansible
Установка Virtualbox:
apt install virtualbox
После установки пишем наши скрипты и Vagrantfile.
Делаем запуск и проверяем работу.
После выполнения vagrant up и успешного завершения playbook можете протестировать сервисы прямо с хостовой машины:
bash
# Node.js
curl http://localhost:8082
# Ответ: Hello from node js server
# Django (вернёт HTML)
curl -s http://localhost:8081 | grep -o '<title>.*</title>'
# <title>The install worked successfully! Congratulations!</title>
# WordPress (проверка заголовка ответа)
curl -I http://localhost:8083 2>/dev/null | head -n 1
# HTTP/1.1 200 OK
Если всё работает – задание выполнено.
