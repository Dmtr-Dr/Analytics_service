# Analytics_service
## Дизайн ML системы - Сервис аналитики для инвесторов - 1

### 1. Цели и предпосылки

### 1.1. Зачем идем в разработку продукта?

- Бизнес-цель: Реализация MVP версии сервиса аналитики для инвесторов
- Почему станет лучше, чем сейчас, от использования ML: Внедрение методов машинного обучения в наш сервис аналитики позволит инвесторам получать более точные и прогнозируемые аналитические данные. ML-модели будут способствовать автоматическому выявлению трендов, анализу рисков и предоставлению персонализированных рекомендаций для оптимизации инвестиционных стратегий.
- Что будем считать успехом итерации с точки зрения бизнеса:
    1. Завершение разработки и успешный запуск MVP версии сервиса аналитики в установленные сроки.
    2. Положительные отзывы и обратная связь от первых пользователей сервиса, подчеркивающие удобство использования и ценность предоставляемой аналитической информации.
    3. Увеличение числа активных пользователей сервиса на 20% в первые три месяца после запуска.
    4. Повышение уровня вовлеченности пользователей, измеряемое по времени, проведенному на платформе, и частоте использования аналитических инструментов.

### 1.2. Бизнес-требования и ограничения

- Краткое описание БТ и ссылки на детальные документы с бизнес-требованиями: Проект направлен на создание сервиса аналитики для инвесторов. Бизнес-требования подробно описаны в [документе](https://www.notion.so/04b4b12e93e24a5d9f6a2106140618fb?pvs=21)
- Бизнес-ограничения:
    1. Для первой версии необходимо использовать только российские источники данных.
    2. Интеграция с другими системами ограничена сторонними API.
    3. Для первой версии прогнозы делаются исключительно для нефтяного сектора
- Что мы ожидаем от конкретной итерации:
    1. Разработка и успешный запуск MVP версии сервиса аналитики для инвесторов.
    2. Получение обратной связи от пользователей для дальнейшего улучшения продукта.
- Описание бизнес-процесса пилота, насколько это возможно - как именно мы будем использовать модель в существующем бизнес-процессе? В рамках пилота модель будет использоваться для предоставления рекомендаций инвесторам на основе анализа новостей, показателей и рыночных трендов. Модель будет интегрирована в сервис аналитики, предоставляя пользователям доступ к новым функциональностям.
- Что считаем успешным пилотом? Критерии успеха и возможные пути развития проекта:
    1. Увеличение активности пользователей после внедрения модели.
    2. Улучшение показателей вовлеченности пользователей.
    3. Получение положительных отзывов и обратной связи. Возможные пути развития:
    4. Масштабирование сервиса на основе успешных результатов пилота.
    5. Исследование возможностей интеграции с дополнительными источниками данных.
    6. Доработка модели на основе обратной связи и изменений в требованиях пользователей.

### 1.3. Что входит в скоуп проекта/итерации, что не входит

- На закрытие каких БТ подписываемся в данной итерации: Подписываемся на закрытие бизнес-требований, связанных с разработкой и внедрением модели аналитики для инвесторов. Это может включать в себя успешную обучение модели, ее интеграцию в продукт и проверку на соответствие заданным бизнес-критериям.
- Что не будет закрыто: В данной итерации, возможно, не будут закрыты все технические задачи, связанные с оптимизацией производительности модели или ее доработкой после получения обратной связи от пользователей.
- Описание результата с точки зрения качества кода и воспроизводимости решения: Код должен соответствовать стандартам оформления, быть документированным и легко читаемым. Модель должна быть воспроизводимой, что позволит другим специалистам легко повторить эксперименты и внести улучшения.
- Описание планируемого технического долга (что оставляем для дальнейшей продуктивизации): Могут остаться некоторые аспекты технического долга, такие как оптимизация производительности, дополнительная настройка гиперпараметров, улучшение обработки данных. Также, возможно, потребуется провести дополнительные исследования для улучшения точности модели. Эти аспекты могут оставаться для будущих итераций с учетом обратной связи от пользователей и изменений в требованиях.

### 1.4. Предпосылки решения

- Описание всех общих предпосылок решения, используемых в системе – с обоснованием от запроса бизнеса: Для обучения модели используются исторические данные с различных новостных источников с 2000 года по 2024 год. Кроме того, возможно использование показателей компании, отчетности, а также метрик, полученных на основе анализа котировок активов. Прогнозируется изменения стоимости котировок на временной промежуток 1 час, 1 день, 1 месяц после выхода новости. Модель будет создаваться индивидуально под каждый сектор экономики.

### 2. Методология

### 2.1. Постановка задачи

Разрабатываем модель для прогнозирования изменения стоимости котировок с использованием временных рядов и других соответствующих методов машинного обучения. Это позволит инвесторам получать предсказания относительно будущих изменений рыночных условий, что может быть ключевой информацией для принятия инвестиционных решений.

### 2.2. Блок-схема решения

### 2.3. Этапы решения задачи

Этап 1 - Парсинг данных

| Название данных | Есть ли данные ( источник данных) | Требуемый ресурс для получения данных (какие роли нужны) | Проверено ли качество данных (да, нет) |
| --- | --- | --- | --- |
| Новости | Lenta | DE | + |

На выходе: Датасет с новостями для обучения модели

Этап 2 - Получение котировок

| Название данных | Есть ли данные ( источник данных) | Требуемый ресурс для получения данных (какие роли нужны) | Проверено ли качество данных (да, нет) |
| --- | --- | --- | --- |
| Котировки | Tinkoff Invest API | DE | + |

На выходе: Датасет с котировками для обучения модели

Этап 3 - Подготовка данных

| Признак 1 | Признак 2 | Изменение стоимости |
| --- | --- | --- |
| Новости | Индикаторы | Число |

На выходе: Итоговый датасет для обучения модели

Этап 4 - Обучение модели

В первой итерации использованы несколько моделей предсказания изменения стоимости и выбрана оптимальная по точности

На выходе: Оптимальная модель для использования

Этап 5 - Разработка базы данных 

В первой итерации в базе данных хранятся id диалогов в telegram, чтобы была возможность рассылать уведомления.

Этап 6 - Разработка бота 

Пользователю предоставляется минимальный набор команд для взаимодействия с ботом.

| Команда | Описание |
| --- | --- |
| /start | Подписка на уведомления от бота |
| /stop | Отписка от бота |

Отдельно поднят сервис для вызова планировщиком задач, который после получения id пользователей рассылает им через telegram бота уведомления о появлении новости, которая может потенциально повлиять на нефтяной сектор. Также в уведомлении отправляются прогнозы модели.

### 3. Подготовка пилота

### 3.1. Способ оценки пилота

Способ оценки пилота - обратная связь от пользователей

### 3.2. Что считаем успешным пилотом

1. Точность модели более 80%
2. За первые три месяца есть 100 активных пользователей

### 3.3. Подготовка пилота

- Реализован телеграм-бот с базовыми функциями анализа новостей и отправкой уведомлений пользователям.

### 4. Внедрение

### 4.1. Архитектура решения

- Блок схема и пояснения: сервисы, назначения, методы API

[Архитектура приложения](https://accurate-napkin-52f.notion.site/9cb5a85b67d648c483135a8eb991484a?pvs=4)

### 4.2. Описание инфраструктуры и масштабируемости

### **Облачная инфраструктура для системы аналитики:**

### Плюсы выбора:

1. **Масштабируемость:**
    - *Почему:* Облачная инфраструктура предоставляет широкий спектр сервисов, позволяющих легко масштабировать инфраструктуру в зависимости от роста объемов данных и нагрузки.
2. **Гибкость и многофункциональность:**
    - *Почему:* Облачная инфраструктура предоставляет множество инструментов для аналитики данных.
3. **Управление затратами:**
    - *Почему:* Модель оплаты "по мере использования" позволяет оптимизировать затраты, платя только за реальное использование ресурсов.
4. **Безопасность и соблюдение нормативов:**
    - *Почему:* Облачная инфраструктура предоставляет инструменты для обеспечения безопасности данных, а также соответствие различным нормативам (например, GDPR).

### Минусы выбора:

1. **Зависимость от интернет-соединения:**
    - *Почему:* Использование облачных услуг требует надежного интернет-соединения, и отсутствие связи может повлиять на доступность.
2. **Зависимость от поставщика:**
    - *Почему:* Переход к облачной инфраструктуре делает компанию зависимой от поставщика облачных услуг. Это может создавать трудности при переходе на другого поставщика.

### 4.3. Требования к работе системы

### Требования к работе системы

1. **SLA (Уровень сервиса):**
    - **Цель:** Обеспечение высокого уровня доступности и производительности системы.
    - **SLA:**
        - Доступность системы: не менее 99.9% в течение каждого месяца.
        - Время восстановления после сбоя (RTO): не более 1 часа.
        - Время восстановления после отказа (RPO): не более 15 минут.
        - Проактивный мониторинг и реагирование на инциденты в течение 24/7.
2. **Пропускная способность:**
    - **Цель:** Обеспечение достаточной пропускной способности для обработки запросов от пользователей.
    - **Пропускная способность:**
        - Минимальная пропускная способность сервера: 100 запросов в секунду.
        - Масштабируемость системы для поддержки увеличения нагрузки в случае роста числа пользователей.
3. **Задержка:**
    - **Цель:** Минимизация задержек для обеспечения отзывчивости системы.
    - **Задержка:**
        - Среднее время отклика (Average Response Time): не более 500 миллисекунд.
        - Максимальное время отклика (Maximum Response Time): не более 1 секунды.
        - Минимизация задержек при выполнении сложных операций, таких как генерация аналитических отчетов.
4. **Мониторинг и репортинг:**
    - **Цель:** Обеспечение постоянного мониторинга состояния системы и предоставление своевременной отчетности.
    - **Мониторинг:**
        - Интеграция системы мониторинга производительности и доступности.
        - Автоматическое уведомление о сбоях или низкой производительности.
    - **Репортинг:**
        - Предоставление регулярных отчетов о производительности и использовании системы.
5. **Безопасность:**
    - **Цель:** Защита данных пользователей и предотвращение несанкционированного доступа.
    - **Безопасность:**
        - Шифрование данных в покое и в передаче.
        - Использование механизмов аутентификации и авторизации.
        - Регулярные аудиты безопасности и применение актуальных патчей для системы.

### 4.4. Безопасность системы

1. **Проблемы с аутентификацией и авторизацией:**
    - **Слабые учетные данные:** Использование слабых паролей или хранение учетных данных в ненадежном формате может предоставить возможность для атак на систему.
2. **Безопасность кода:**
    - **Уязвимости в программном обеспечении:** Неправильно обработанный ввод данных, отсутствие валидации или использование устаревших библиотек могут предоставить возможности для атак.

### 4.5. Безопасность данных

Планируется подписывать с пользователем “Согласие на обработку персональных данных”.

### 4.6. Издержки

**Инфраструктурные расходы:**

- **Хостинг и облачные услуги:** Расходы на использование серверов, прокси-серверов, вычислительных ресурсов, хранилища данных и других облачных услуг.
- **Сетевые расходы:** Расходы на передачу данных внутри сети и между компонентами системы

**Лицензионные и программные расходы:**

- **Лицензии на программное обеспечение:** Расходы на лицензии для операционных систем, баз данных, средств мониторинга и другого программного обеспечения, используемого в системе.

**Расходы на обеспечение безопасности:**

- **Антивирусные и анти-малварные программы:** Расходы на программы и сервисы по обеспечению безопасности системы.

**Расходы на резервное копирование и восстановление данных:**

- **Системы резервного копирования:** Расходы на оборудование и программное обеспечение для создания резервных копий данных и их восстановления в случае сбоев.

**Прочие расходы:**

- **Службы поддержки и техническая консультация:** Расходы на сторонние службы поддержки и консультации.

### 4.7. Integration points

- Котировки получаем через Tinkoff Invest Api
- Новости получаем через API соответствующих новостных сайтов
- Взаимодействие с пользователем происходит через API Telegram

### 4.8. Риски

### Риски и Неопределенности

1. **Качество данных:**
    - **Риск:** Низкое качество или неполные данные могут негативно повлиять на обучение модели и, как результат, на качество предсказаний.
    - **Меры по снижению риска:** Регулярная проверка и очистка данных, использование методов обработки выбросов и аномалий, поиск дополнительных источников данных для улучшения качества.
2. **Нехватка обратной связи:**
    - **Риск:** Отсутствие обратной связи от пользователей может затруднить оценку эффективности модели и ее соответствие ожиданиям инвесторов.
    - **Меры по снижению риска:** Активная коммуникация с пользователями, сбор обратной связи с использованием опросов и анализа пользовательского поведения.
3. **Риски безопасности:**
    - **Риск:** Угрозы безопасности данных могут привести к утечкам конфиденциальной информации инвесторов.
    - **Меры по снижению риска:** Внедрение современных методов шифрования данных, регулярные аудиты безопасности, обеспечение соответствия стандартам безопасности.
4. **Неопределенность рыночных условий:**
    - **Риск:** Изменения в макроэкономических условиях, политической ситуации или других факторах могут существенно влиять на рынок и усложнить прогнозирование.
    - **Меры по снижению риска:** Внедрение системы мониторинга рыночных условий, постоянное обновление модели в соответствии с изменениями в окружающей среде.
5. **Технические риски:**
    - **Риск:** Сбои в системе, технические проблемы или неудачные обновления могут привести к потере данных или временным простоям.
    - **Меры по снижению риска:** Регулярные резервные копии данных, тестирование на прочность системы, поддержка и обновления программного обеспечения.
6. **Риски изменения законодательства:**
    - **Риск:** Изменения в финансовом или конфиденциальном законодательстве могут потребовать адаптации системы или повлечь за собой юридические последствия.
    - **Меры по снижению риска:** Регулярное отслеживание изменений в законодательстве, сотрудничество с юридическими экспертами для оценки рисков и соответствия.
