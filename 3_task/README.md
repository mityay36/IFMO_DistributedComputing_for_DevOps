# Мониторинг с Grafana и Prometheus

Этот проект разворачивает базовый стек мониторинга с использованием Grafana и Prometheus с помощью Ansible.

## Описание

Роль `3_task` устанавливает и настраивает следующие компоненты:

- **Prometheus**: сбор и хранение метрик
- **Grafana**: визуализация метрик и создание дашбордов
- **Node Exporter**: сбор метрик с хоста (CPU, память, диск, сеть)


## Переменные по умолчанию

| Переменная               | Описание                   |
|--------------------------|----------------------------|
| `monitoring_dir`         | Директория для мониторинга |
| `prometheus_port`        | Порт Prometheus            |
| `grafana_port`           | Порт Grafana               |
| `grafana_admin_user`     | Пользователь Grafana       |
| `grafana_admin_password` | Пароль Grafana             |
| `prometheus_retention`   | Время хранения метрик      |

## Требования

- Ansible 2.9+
- Docker и Docker Compose на целевом хосте
- Коллекция `community.docker`

## Установка зависимостей

Установка коллекции Docker для Ansible
    
    ansible-galaxy collection install community.docker

Либо установка зависимостей из requirements.yml

    ansible-galaxy install -r requirements.yml

Запустите плейбук для развертывания мониторинга:

    ansible-playbook playbook3.yml

После успешного запуска сервисы будут доступны по адресам:

- **Grafana**: `http://localhost:3000`
- **Prometheus**: `http://localhost:9090`
- **Node Exporter**: `http://localhost:9100/metrics`

## Первоначальная настройка Grafana

1. Войдите в Grafana 
2. Добавьте Prometheus как источник данных:
   - URL: `http://prometheus_server_ip:9090`
   - Сохраните и протестируйте соединение
3. Импортируйте готовые дашборды для Node Exporter (например, Dashboard ID: 1860)

## Дополнительная информация

[Документация Prometheus](https://prometheus.io/docs/)\
[Документация Grafana](https://grafana.com/docs/)\
[Node Exporter метрики](https://github.com/prometheus/node_exporter)
