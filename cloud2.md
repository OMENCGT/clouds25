 
### Сравнение сервисов Amazon Web Services и Microsoft Azure. Создание единой кросс-провайдерной сервисной модели.

#### 1 Сохранение принципов классификации

Из лабораторной работы №1 были зафиксированы следующие уровни:
- IT Tower (Compute, Storage, Database, Analytics, Machine Learning, Developer Tools, Security, Application Integration и др.)
- Service Family (Object Storage, Data Warehouse, AI Services, CI/CD, Messaging и т.д.)
- Service Type (конкретный сервис AWS или Azure)
- Service Sub Type (уточнение типа ресурса)
- Service Usage Type (единица потребления)

Для Azure были подобраны аналоги AWS-сервисов на основе функционального соответствия.

#### 2 Сопоставление сервисов AWS ↔ Azure

| AWS Service | Azure Equivalent | Примечание |
|-------------|------------------|-------------|
| Amazon S3 | Azure Blob Storage | Объектное хранилище |
| Amazon S3 Glacier | Azure Archive Storage | Холодное / архивное хранилище |
| Amazon Redshift | Azure Synapse Analytics | Хранилище данных (ранее SQL DW) |
| AWS Directory Service | Azure Active Directory Domain Services | Управляемые доменные службы |
| Amazon SNS | Azure Event Grid / Notification Hubs | Управление уведомлениями |
| Amazon Translate | Azure Translator Text | Машинный перевод |
| Amazon Transcribe | Azure Speech to Text | Распознавание речи |
| AWS CodePipeline | Azure Pipelines | CI/CD конвейеры |
| AWS CodeBuild | Azure Pipelines (Build) | Сборка кода |
| Amazon Machine Learning | Azure Machine Learning | Платформа машинного обучения |
| Amazon Polly | Azure Text to Speech | Синтез речи |

#### 3 Построение единой кросс-провайдерной модели

| IT Tower | Service Family | AWS Service Type | Azure Service Type |
|----------|----------------|------------------|--------------------|
| Storage | Object Storage | Amazon S3 | Azure Blob Storage |
| Storage | Archive Storage | Amazon S3 Glacier | Azure Archive Storage |
| Analytics | Data Warehouse | Amazon Redshift | Azure Synapse Analytics |
| Security, Identity & Compliance | Directory Service | AWS Directory Service | Azure AD Domain Services |
| Application Integration | Messaging | Amazon SNS | Azure Event Grid / Notification Hubs |
| Machine Learning | AI Services (Translation) | Amazon Translate | Azure Translator Text |
| Machine Learning | AI Services (Speech) | Amazon Transcribe | Azure Speech to Text |
| Machine Learning | AI Services (Speech Synthesis) | Amazon Polly | Azure Text to Speech |
| Developer Tools | CI/CD | AWS CodePipeline + CodeBuild | Azure Pipelines |
| Machine Learning | ML Platform | Amazon Machine Learning | Azure Machine Learning |

#### 4 Пример унификации потребления (Service Usage Type)

| Service Family | Service Usage Type (логическая) | AWS метрика | Azure метрика |
|----------------|--------------------------------|-------------|---------------|
| Object Storage | Хранение (ГБ в месяц) | TimedStorage-ByteHrs | Blob Storage Capacity (GB/month) |
| Object Storage | Запросы (PUT/GET) | Requests-Tier1..6 | Storage Transactions |
| Data Warehouse | Вычисление (узел-час) | Redshift Node (RA, DC, DS) | Synapse DWU‑hour |
| AI Services (Translation) | Количество символов | TranslateText | Translator Text – characters |
| CI/CD | Минуты сборки | Build Minutes (CodeBuild) | Build minutes (Azure Pipelines) |

### Источники информации

1. AWS to Azure services comparison – Microsoft Learn: https://learn.microsoft.com/en-us/azure/architecture/aws-professional/services  
2. Azure Pricing overview – https://azure.microsoft.com/en-us/pricing/  
3. AWS Pricing (см. источники к лабораторной работе №1) 
