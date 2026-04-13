#### Принцип классификации

Для каждого сервиса (Product Code) и типа использования (Usage Type) определялись:

- **IT Tower** – верхнеуровневая категория (Compute, Storage, Database, Analytics, Machine Learning, Developer Tools, Security, Application Integration).
- **Service Family** – логическая группа внутри башни (Object Storage, Data Warehouse, AI Services, CI/CD и т.д.).
- **Service Type** – название сервиса AWS (Amazon S3, Amazon Redshift, AWS Directory Service и т.д.).
- **Service Sub Type** – уточнение типа ресурса (Redshift Nodes, Early Delete, HTTP Delivery, ML Box Usage и т.д.).
- **Service Usage Type** – конкретная единица потребления (RA Node, Data Scanned, S3 Standard Requests Tier 1, Train Model и т.д.).

---

### Цель работы

Получение навыков классификации облачных сервисов по уровням абстракции и типам потребления. Построение иерархической модели («IT Tower» → «Service Family» → «Service Type» → «Service Sub Type» → «Service Usage Type») на основе данных биллинга AWS.

---

###  Результаты классификации

Ниже приведены итоговые соответствия для всех записей из исходного файла (в виде таблиц по сервисам).

#### 1 Amazon Redshift

| IT Tower | Service Family | Service Type | Service Sub Type | Service Usage Type |
|----------|----------------|--------------|------------------|--------------------|
| Analytics | Data Warehouse | Amazon Redshift | Redshift Nodes | RA Node |
| Analytics | Data Warehouse | Amazon Redshift | Redshift Managed Storage | RMS |
| Analytics | Data Warehouse | Amazon Redshift | Redshift Spectrum | Data Scanned |
| Analytics | Data Warehouse | Amazon Redshift | Redshift Nodes | DC Node |
| Analytics | Data Warehouse | Amazon Redshift | Redshift Nodes | DS Node |

#### 2 AWS Directory Service

| IT Tower | Service Family | Service Type | Service Sub Type | Service Usage Type |
|----------|----------------|--------------|------------------|--------------------|
| Security, Identity, & Compliance | Directory Service | AWS Directory Service | Microsoft AD | Domain Controller Usage |
| Security, Identity, & Compliance | Directory Service | AWS Directory Service | Simple AD | Simple AD Usage |
| Security, Identity, & Compliance | Directory Service | AWS Directory Service | Small Directory | Small Directory Usage |
| Security, Identity, & Compliance | Directory Service | AWS Directory Service | Large AD Connector | Large AD Connector Usage |
| Security, Identity, & Compliance | Directory Service | AWS Directory Service | Tax | AWS Tax |

#### 3 Amazon S3 Glacier (AmazonGlacier)

| IT Tower | Service Family | Service Type | Service Sub Type | Service Usage Type |
|----------|----------------|--------------|------------------|--------------------|
| Storage | Archive Storage | Amazon S3 Glacier | Provisioned Capacity | Provisioned Capacity Unit |
| Storage | Archive Storage | Amazon S3 Glacier | Timed Storage | Storage Byte‑Hrs |
| Storage | Archive Storage | Amazon S3 Glacier | Requests | Tier 3 Requests |
| Storage | Archive Storage | Amazon S3 Glacier | Requests | Tier 1 Requests |
| Storage | Archive Storage | Amazon S3 Glacier | Early Delete | Early Delete |

#### 4 Amazon S3

| IT Tower | Service Family | Service Type | Service Sub Type | Service Usage Type |
|----------|----------------|--------------|------------------|--------------------|
| Storage | Object Storage | Amazon S3 | Early Delete (GDA) | S3 Glacier Deep Archive |
| Storage | Object Storage | Amazon S3 | Early Delete (INT) | S3 Intelligent‑Tiering |
| Storage | Object Storage | Amazon S3 | Early Delete (ZIA) | S3 Standard‑IA |
| Storage | Object Storage | Amazon S3 | Early Delete (SIA) | S3 One Zone‑IA |
| Storage | Object Storage | Amazon S3 | Requests | S3 Standard Requests Tier 1 |
| Storage | Object Storage | Amazon S3 | Requests | S3 Standard Requests Tier 2 |
| Storage | Object Storage | Amazon S3 | Requests | S3 Standard Requests Tier 3 |
| Storage | Object Storage | Amazon S3 | Requests | S3 Standard Requests Tier 4 |
| Storage | Object Storage | Amazon S3 | Requests | S3 Standard Requests Tier 5 |
| Storage | Object Storage | Amazon S3 | Requests | S3 Standard Requests Tier 6 |
| Storage | Object Storage | Amazon S3 | Tag Storage | Tag Storage Hours |

#### 5 Amazon SNS

| IT Tower | Service Family | Service Type | Service Sub Type | Service Usage Type |
|----------|----------------|--------------|------------------|--------------------|
| Application Integration | Messaging | Amazon SNS | HTTP Delivery | HTTP Delivery Attempts |
| Application Integration | Messaging | Amazon SNS | SQS Delivery | SQS Delivery Attempts |
| Application Integration | Messaging | Amazon SNS | SMS | SMS Price |
| Application Integration | Messaging | Amazon SNS | SMS | SMS Sent |
| Application Integration | Messaging | Amazon SNS | APNS Delivery | APNS Delivery Attempts |

#### 6 Amazon Translate

| IT Tower | Service Family | Service Type | Service Sub Type | Service Usage Type |
|----------|----------------|--------------|------------------|--------------------|
| Machine Learning | AI Services | Amazon Translate | Translation | Text Translation |

#### 7 Amazon Transcribe

| IT Tower | Service Family | Service Type | Service Sub Type | Service Usage Type |
|----------|----------------|--------------|------------------|--------------------|
| Machine Learning | AI Services | Amazon Transcribe | Streaming Audio | Streaming Audio |
| Machine Learning | AI Services | Amazon Transcribe | Batch Audio | Batch Transcription |

#### 8 AWS CodePipeline

| IT Tower | Service Family | Service Type | Service Sub Type | Service Usage Type |
|----------|----------------|--------------|------------------|--------------------|
| Developer Tools | CI/CD | AWS CodePipeline | Pipeline | Trial Pipeline |
| Developer Tools | CI/CD | AWS CodePipeline | Tax | AWS Tax |

#### 9 AWS CodeBuild

| IT Tower | Service Family | Service Type | Service Sub Type | Service Usage Type |
|----------|----------------|--------------|------------------|--------------------|
| Developer Tools | CI/CD | AWS CodeBuild | Build | Build Minutes |

#### 10 Amazon Machine Learning (AmazonML)

| IT Tower | Service Family | Service Type | Service Sub Type | Service Usage Type |
|----------|----------------|--------------|------------------|--------------------|
| Machine Learning | Machine Learning | Amazon Machine Learning | ML Box Usage | Train Model |
| Machine Learning | Machine Learning | Amazon Machine Learning | ML Box Usage | Evaluate Model |

#### 11 Amazon Polly

| IT Tower | Service Family | Service Type | Service Sub Type | Service Usage Type |
|----------|----------------|--------------|------------------|--------------------|
| Machine Learning | AI Services | Amazon Polly | Text‑to‑Speech | Characters |

---

### Выводы по лабораторной работе №1

- Установлена полная классификация всех сервисов из предоставленного биллинга.
- Пятиуровневая модель позволяет проводить анализ затрат от самого общего уровня (IT Tower) до конкретной единицы потребления (Service Usage Type).
- Выявлено, что даже внутри одного сервиса (например, Amazon S3) могут существовать десятки различных типов потребления (раннее удаление, запросы разных уровней, хранение тегов).

###  Источники информации

1. AWS Redshift Pricing – https://aws.amazon.com/redshift/pricing/  
2. AWS Directory Service Pricing – https://aws.amazon.com/directoryservice/pricing/  
3. Amazon S3 Glacier Pricing – https://aws.amazon.com/glacier/pricing/  
4. Amazon S3 Pricing – https://aws.amazon.com/s3/pricing/  
5. Amazon SNS Pricing – https://aws.amazon.com/sns/pricing/  
6. Amazon Translate Pricing – https://aws.amazon.com/translate/pricing/  
7. Amazon Transcribe Pricing – https://aws.amazon.com/transcribe/pricing/  
8. AWS CodePipeline Pricing – https://aws.amazon.com/codepipeline/pricing/  
9. AWS CodeBuild Pricing – https://aws.amazon.com/codebuild/pricing/  
10. Amazon Machine Learning Pricing – https://aws.amazon.com/machine-learning/pricing/  
11. Amazon Polly Pricing – https://aws.amazon.com/polly/pricing/  
