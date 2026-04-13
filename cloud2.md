# Лабораторная работа №2
## Сравнение сервисов Amazon Web Services и Microsoft Azure. Создание единой кросс-провайдерной сервисной модели.

### Цель работы
Получение навыков аналитики и понимания спектра публичных облачных сервисов без привязки к вендору. Формирование комплексного видения Облака через единую сервисную модель.

### Исходные данные
- Файл `Azure lab team 1.csv` – полупустой биллинг Azure.
- Классификация из первой лабы

### Выполненные шаги

1. **Сохранение принципов классификации из ЛР №1**  
   В ЛР №1 были установлены следующие правила:
   - Data warehouse сервисы → `Cloud Services` / `Analytics`
   - OLTP базы данных → `Database` / `Database`
   - Хранилища → `Storage` / `Storage&Content Delivery`
   - Вычисления → `Compute` / `Compute`
   - Сетевые сервисы → `Networking` / `Networking`
   - AI/ML → `Cloud Services` / `Artificial Intelligence`
   - Security сервисы → `Cloud Services` / `Security and Identity`

2. **Классификация Azure сервисов**

| Meter Category | IT Tower | Service Family | Обоснование (сравнение с AWS) |
|----------------|----------|----------------|-------------------------------|
| Analysis Services / Azure Analysis Services | Cloud Services | Analytics | Аналог AWS Redshift – OLAP аналитика |
| Azure Data Factory | Cloud Services | Analytics | Аналог AWS Glue / ETL сервис |
| Azure Database for PostgreSQL | Database | Database | OLTP база данных, аналог AWS RDS |
| Cache / Redis Cache | Cloud Services | Application Services | Аналог AWS ElastiCache |
| CDN / Content Delivery Network | Networking | Networking | Аналог AWS CloudFront |
| Cloud Services (A,D,F,G,H,N серии) | Compute | Compute | Аналог AWS EC2 (разные семейства инстансов) |
| Data Box | Storage | Storage&Content Delivery | Аналог AWS Snowball (офлайн перенос данных) |
| Key Vault | Cloud Services | Security and Identity | Аналог AWS Secrets Manager / KMS |
| Scheduler | Cloud Services | Application Services | Аналог AWS EventBridge / CloudWatch Events |
| Sentinel | Cloud Services | Security and Identity | Аналог AWS GuardDuty + Security Hub (SIEM/SOAR) |

3. **Детализация Service Type, Service Sub Type, Service Usage Type** – определены на основе назначения:
   - Analysis Services: Tabular / Basic / Developer / Standard
   - Data Factory: v2 / Business Analytics – Data Movement и Orchestration (Cloud vs Self Hosted IR)
   - Redis Cache: по типам C%
   - CDN: Standard CDN Data Transfer
   - Cloud Services: по сериям виртуальных машин (A, D, F, G, H, N)
   - Scheduler: Free / Standard Units
   - Sentinel: Free Trial / Analysis

### Сравнительная таблица AWS ↔ Azure (на основе классификации)

| IT Tower | Service Family | AWS сервис | Azure сервис |
|----------|----------------|------------|--------------|
| Cloud Services | Analytics | Amazon Redshift | Azure Analysis Services |
| Cloud Services | Analytics | AWS Glue | Azure Data Factory |
| Database | Database | Amazon RDS | Azure Database for PostgreSQL |
| Cloud Services | Application Services | Amazon ElastiCache | Azure Redis Cache |
| Networking | Networking | Amazon CloudFront | Azure CDN |
| Compute | Compute | Amazon EC2 | Azure Cloud Services (VM) |
| Storage | Storage&Content Delivery | AWS Snowball | Azure Data Box |
| Cloud Services | Security and Identity | AWS KMS / Secrets Manager | Azure Key Vault |
| Cloud Services | Application Services | Amazon EventBridge | Azure Scheduler |
| Cloud Services | Security and Identity | AWS GuardDuty + Security Hub | Azure Sentinel |

### Сохранение логической концепции из ЛР №1

В ЛР №1 было установлено, что:
- **Redshift (Analytics)** – потому что это columnar OLAP data warehouse
- В Azure **Analysis Services** выполняет ту же функцию – аналитические модели и OLAP кубы

- **AWS Directory Service (Security and Identity)** – управление идентификацией
- В Azure **Key Vault** и **Sentinel** – управление секретами и SIEM, что также относится к Security and Identity

- **AWS SNS (Application Services)** – управляемые сообщения
- В Azure **Scheduler** и **Redis Cache** – управляемые сервисы приложений (планировщик и кэш)

### Вывод

В ходе лабораторной работы №2:
1. Сопоставлены сервисы AWS с их аналогами в Azure
2. Сохранена иерархия: IT Tower → Service Family → Service Type → Service Sub Type → Service Usage Type
3. Продемонстрирована возможность кросс-провайдерного анализа потребления облачных услуг

Созданная модель позволяет:
- Сравнивать затраты между AWS и Azure на уровне типов сервисов
- Собирать инфу о потреблении по IT Tower и Service Family независимо от вендора
