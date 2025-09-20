InsureTech — архитектурный проект 🏗️

Коротко  агрегатор страховых продуктов для B2C и B2B
Цель  высокая доступность масштабирование отказоустойчивость и новый продукт ОСАГО

Стек  Kubernetes PostgreSQL Kafka или NATS Redis Drawio GraphQL Locust Python Helm опционально
Ветки  main как целевая и insuretech для работы
Документация  смотри директории Task1 Task2 Task3 Task4 Task5


Что внутри 📦

- Task1  технологическая архитектура to be с мультизонным и мультирегиональным дизайном RTO 45 мин RPO 15 мин
- Task2  автоскейлинг в Kubernetes через HPA и нагрузочное тестирование Locust
- Task3  переход к событийным интеграциям и Transactional Outbox
- Task4  дизайн ОСАГО онлайн с сервисом osago-aggregator и паттернами отказоустойчивости
- Task5  миграция client-info на GraphQL схема и примеры запросов

Быстрый старт 🚀

Подготовка Windows

1. Установи Docker Desktop и включи Kubernetes если нужно для Task2
2. Установи Python 3.11 и pip
3. Включи kubectl и minikube для локального кластера если выполняешь Task2

Подготовка Linux 🐧

1. Установи Docker и Docker Compose
2. Установи Python 3.11 и pip
3. Установи kubectl и minikube при необходимости

Task2 запуск локальных манифестов HPA

Windows

1. Запусти Minikube  minikube start
2. Включи metrics-server  minikube addons enable metrics-server
3. Применяй манифесты  kubectl apply -f Task2\deployment.yaml  kubectl apply -f Task2\service.yaml  kubectl apply -f Task2\hpa.yaml
4. Получи URL сервиса  minikube service scaletestapp --url
5. Запусти Locust в консоли PowerShell  python -m pip install locust  locust -f Task2\locustfile.py --host http://<URL из шага 4>

Linux

1. minikube start
2. minikube addons enable metrics-server
3. kubectl apply -f Task2/deployment.yaml  kubectl apply -f Task2/service.yaml  kubectl apply -f Task2/hpa.yaml
4. minikube service scaletestapp --url
5. python3 -m pip install locust  locust -f Task2/locustfile.py --host http://<URL из шага 4>

Task5 GraphQL 📚

Файлы  Task5/schema.graphql и Task5/README.md
Можно выполнять выборочные поля и связи в одном запросе и снижать RPS

Диаграммы 🖼️

Файлы drawio лежат в Task1 Task3 Task4


Docker 🐳

Если нужен контейнер для тестового клиента GraphQL или нагрузочного инструмента собери через compose по месту в каталоге docker если будет добавлен в будущем

Примечание

- Не храни секреты в репозитории  используй переменные окружения и примеры .env.example
- Все артефакты решения находятся в соответствующих директориях заданий
