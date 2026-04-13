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

| Product Code | IT Tower | Service Family | 
|--------------|----------|----------------|
| AmazonRedshift | Cloud Services | Analytics | 
| AWSDirectoryService | Cloud Services | Security and Identity | 
| AmazonGlacier | Storage | Storage&Content Delivery | 
| AmazonS3 | Storage | Storage&Content Delivery | 
| AmazonSNS | Cloud Services | Application Services | 
| translate/transcribe/polly/ML | Cloud Services |
| CodePipeline/CodeBuild | Cloud Services | Developer Tools |

2. **Объяснение сервисов:**

-Amazon Redshift
Корпоративное хранилище данных (OLAP). Нужен, чтобы быстро выполнять сложные аналитические запросы по большим объёмам данных (терабайты и петабайты). Используется для бизнес-аналитики.

- AWS Directory Service --- Управляемая версия Microsoft Active Directory в облаке. Нужен, чтобы администраторы могли управлять пользователями, политиками и доступом к ресурсам так же, как в локальном офисе, но без покупки и обслуживания своих серверов.

Amazon Glacier
Очень дешёвое, но медленное архивное хранилище. Нужно для данных, которые почти не используются, но должны сохраняться годами (например, старые бэкапы, архивы документов, логи). Доступ к данным долгий

Amazon S3
Объектное хранилище для любых данных: картинки, видео, бэкапы, логи, статика сайтов. Автоматически распределяет данные по разным классам хранения в зависимости от того, как часто к ним обращаются (от горячих до ледяных архивов).

Amazon SNS (Simple Notification Service)
Сервис для массовых уведомлений. Позволяет отправить одно сообщение сразу в несколько каналов: email, SMS, на мобильные устройства (iOS/Android) и в другие сервисы AWS. Нужен для оповещений пользователей или микросервисов о событиях.

Amazon Translate
Нейросетевой перевод текста. Переводит между 54 языками. Нужен, чтобы сделать приложение многоязычным или автоматически переводить документы и переписку.

Amazon Transcribe
Превращает речь в текст. Работает как с живым аудиопотоком (например, субтитры в прямом эфире), так и с записями (расшифровка лекций, совещаний, звонков).

AWS CodePipeline
Автоматическая сборка и доставка кода (CI/CD). Нужен разработчикам, чтобы при каждом изменении в репозитории автоматически собиралось приложение, прогонялись тесты и оно разворачивалось на серверах.

AWS CodeBuild
Запускает сборку кода в облаке. Не нужно поднимать свой сервер для компиляции. Просто платишь за минуты сборки.

Amazon Machine Learning
Старый сервис для создания простых моделей машинного обучения (бинарная классификация, регрессия) без глубокого понимания ML. Не требует написания кода.

Amazon Polly
Превращает текст в живую речь (нейросетевой синтез). Нужен для озвучивания статей, книг, голосовых помощников, аудио-версий контента.

3. **Детализация Service Type, Service Sub Type, Service Usage Type** – определены на основе назначения каждого Usage Type:
   - Redshift: Node Usage (вычислительные узлы), RMS (управляемое хранилище), Spectrum (запросы к S3)
   - Directory Service: по типам директорий (Microsoft AD, Simple AD, Small, AD Connector)
   - Glacier: Provisioning, Storage, Requests, Early Delete
   - S3: по типам запросов (Tier1-6) и классам хранения (GDA, INT, ZIA, SIA)
   - SNS: по протоколам доставки (HTTP, SQS, SMS, APNS)
   - Transcribe: Streaming/Batch
   - ML: Train/Evaluate Model

### Обоснование классификаций

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
