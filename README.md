Для запуска необходимо установленые VirtualBox и Vagrant
Склонируйте репозиторий в отдельную директорию и выполните в cmd: vagrant up

После выполнения команды произойдёт:
- скачивание box Ubuntu 20.04 с репозитория Ubuntu, если его нет на хосте
- создание VM и импортирование образа с параметрами, указаными в Vagrantfile
- выполнение sh скрипта firstStartScript для установки ansible, выполнения playbook и запуска docker-compose сценария
- выполнение playbook для установки docker-compose с сопутствующими пакетами из репозитория Ubuntu
- запуск docker-compose сценария
  - скачивание latest: node-exporter, grafana, prometheus
  - запуск контейнеров с настройками по умолчанию, за исключением конфигурации grafana, которая расположена в директории grafana-provisioning
    - в конфигурации grafana-provisioning добавлены параметры для подключения к prometheus и дашборд node exporter full, который в docker-compose сценарии указан дефолтным
В результате выполнения grafana будет доступнв по адресу http://localhost:3000 с дефолтными кредами: admin:admin, которые попросит изменить при первой аутентификации.
После аутентификации в графане откроется node exporter full.
