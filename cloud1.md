# Лабораторная работа №1
## Знакомство с IaaS, PaaS, SaaS сервисами в облаке на примере AWS. Создание сервисной модели.

### Цель работы
Освоить классификацию облачных сервисов по уровням абстракции и типам потребления на примере данных биллинга AWS.

### Исходные данные
- Файл `Mapping Rules AWS team 1.csv` – полупустой биллинг.
- Файл `Mapping Rules AWS Example.csv` – образец.

### Пары IT Tower / Service Family (из примера)

| IT Tower | Service Family |
|----------|----------------|
| Networking | Networking |
| Cloud Services | Application Services |
| Compute | Compute |
| Database | Database |
| Storage | Storage&Content Delivery |
| Support | Support |
| Cloud Services | Analytics |
| Cloud Services | Artificial Intelligence |
| Cloud Services | Blockchain |
| Cloud Services | Developer Tools |
| Cloud Services | Enterprise Applications |
| Cloud Services | Internet of Things |
| Cloud Services | Management Tools |
| Cloud Services | Mobile Services |
| Cloud Services | Security and Identity |

### Выполненные шаги

1. **Анализ Product Code и классификация** – для каждого Product Code определены IT Tower и Service Family в соответствии с данными из доков aws и примера:

| Product Code | IT Tower | Service Family | Обоснование |
|--------------|----------|----------------|-------------|
| AmazonRedshift | Cloud Services | Analytics | Fully managed cloud data warehouse для OLAP-аналитики |
| AWSDirectoryService | Cloud Services | Security and Identity | Managed Microsoft AD, сервис управления идентификацией  |
| AmazonGlacier | Storage | Storage&Content Delivery | Архивное хранилище, класс хранения S3 |
| AmazonS3 | Storage | Storage&Content Delivery | Объектное хранилище |
| AmazonSNS | Cloud Services | Application Services | Управляемый Pub/Sub сервис для микросервисов |
| translate/transcribe/polly/ML | Cloud Services | Artificial Intelligence | AI/ML сервисы |
| CodePipeline/CodeBuild | Cloud Services | Developer Tools | CI/CD сервисы |

2. **Детализация Service Type, Service Sub Type, Service Usage Type** – определены на основе назначения каждого Usage Type:
   - Redshift: Node Usage (вычислительные узлы), RMS (управляемое хранилище), Spectrum (запросы к S3)
   - Directory Service: по типам директорий (Microsoft AD, Simple AD, Small, AD Connector)
   - Glacier: Provisioning, Storage, Requests, Early Delete
   - S3: по типам запросов (Tier1-6) и классам хранения (GDA, INT, ZIA, SIA)
   - SNS: по протоколам доставки (HTTP, SQS, SMS, APNS)
   - Transcribe: Streaming/Batch
   - ML: Train/Evaluate Model

### Обоснование ключевых классификаций

**Почему Redshift в Analytics, а не Database?**
- Amazon Redshift — это **columnar OLAP data warehouse**, а не OLTP база данных
- AWS официально относит Redshift к категории **Analytics** наравне с Athena, EMR, QuickSight
- Основное назначение — сложные аналитические запросы и BI, а не транзакционная обработка

**Почему Directory Service в Security and Identity?**
- AWS Directory Service входит в официальную категорию **Security, Identity & Compliance**
- Сервис предоставляет managed Microsoft Active Directory для аутентификации и авторизации

**Почему Glacier в Storage?**
- Glacier — это архивный класс хранения Amazon S3
- В биллинге отображается как ProductCode AmazonS3 для некоторых операций (EarlyDelete)

### Вывод
В ходе лабораторной работы освоено:
- сопоставление сырых данных биллинга с официальной документацией AWS;
- построение иерархической сервисной модели (Tower → Family → Type → Sub Type → Usage Type);
- разделение сервисов по уровням: PaaS (Redshift, SNS, Transcribe), IaaS (S3), SaaS (Polly, Directory Service);
- применение строгих правил классификации на основе примера.

Созданная модель позволяет анализировать потребление от общего (IT Tower) к частному (Usage Type)
