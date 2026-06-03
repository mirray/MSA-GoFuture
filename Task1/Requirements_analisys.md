# GoFuture - Software Requirements Specification (FURPS+ Model)

## 1. Functional Requirements (F)
*Define the capabilities, features, and intended behaviors of the system.*
- **F1:** Поддержка динамического ценообразования в режиме реального времени
- **F2:** Оптимизация загрузки водителей в часы пик с помощью «умного» перераспределения (ожидание подходящего водителя вместо выбора ближайшего, чтобы избежать «горячих зон», где концентрируется большинство водителей)
- **F3:** Используются data-driven решения: ML-модели для прогнозирования спроса и предотвращения фрода

## 2. Usability (U)
*Define user interface requirements, aesthetics, consistency, and documentation.*
- **U1:** Реализована возможность самообслуживания через API для внешних разработчиков и партнёров
- **U2:** Улучшен клиентский опыт: приложение стало более стабильным и быстрым
- **U3:** Платформа «GoFuture» стала целой экосистемой: партнёры могут запускать свои сервисы без глобальных изменений, включая локальные сервисы такси, банки, e-commerce и другие - after 1 year

## 3. Reliability (R)
*Define requirements for failure frequency, recovery, and availability.*
- **R1:** Обеспечение 99,95% доступности критических сервисов
- **R2:** количество инцидентов снижено на 70% - after 2 months
- **R3:** среднее время восстановления системы (MTTR) сокращено с более чем четырёх часов до одного - after 2 months
- **R4:** система обрабатывает более 200 тысяч конкурентных поездок без каскадных отказов - after 2 months

## 4. Performance (P)
*Define speed, throughput, efficiency, and resource utilization.*
- **P1:** Обработка 500 тысяч конкурентных поездок - after 1 year
- **P2:** Горизонтальное масштабирование сразу в нескольких географических регионах
- **P2:**  Обеспечено глобальное масштабирование с развёртыванием в более чем трёх географических регионах - after 1 year

## 5. Supportability (S)
*Define testability, maintainability, scalability, and compatibility.*
- **S1:** Время разработки сокращено до трёх месяцев - after 2 months
- **S1:** Сокращение времени выхода на рынок новых функций до двух недель
- **S2:** ускорен выход на новые рынки и запуск в новых странах занимает от двух до четырёх недель вместо полугода (а то и дольше)
- **S3:** возможности быстрого тестирования

## 6. "+" (Constraints & Supplementary Requirements)
*This section covers additional constraints that are not part of the core FURPS categories.*

### 6.1 Design Constraints

### 6.2 Implementation Requirements
- **IR1:** время сборки уменьшено с более чем получаса до 15 минут - after 2 months

### 6.3 Interface Requirements
- **IF1:** Интеграция с локальными платёжными и картографическими сервисами
- **IF2:** Платёжный шлюз — Яндекс Пэй.
- **IF3:** Картографический сервис — Яндекс Карты.
- **IF4:** Push-уведомления — Firebase Cloud Messaging (FCM) для Android, Apple Push Notification Service (APNS) для iOS и Huawei Push Kit для Huawei-устройств.
- **IF5:** Банковские API — интеграции с банками для выплат.

### 6.4 Physical Requirements


### 6.5 Business Rules
 - **BR1:** Соответствие локальным регуляторным требованиям
 - **BR2:** Снижены затраты за счёт оптимизации использования ресурсов на 40% через автоскейлинг
 - **BR2:** Созданы новые источники дохода через партнёрские программы

