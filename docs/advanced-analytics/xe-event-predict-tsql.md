---
title: Расширенные события для наблюдения за инструкции ПРОГНОЗА | Документы Microsoft
titleSuffix: SQL Server
ms.custom: ''
ms.date: 03/01/2018
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: d517da44f989620003fef35d2e4721eead15d5d5
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="extended-events-for-monitoring-predict-statements"></a>Расширенные события для наблюдения за инструкции ПРОГНОЗА

В этой статье описываются расширенные события, предоставляемые в SQL Server, можно использовать для мониторинга и анализа заданий, использующих [PREDICT](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) для выполнения оценки в режиме реального времени в SQL Server.

Оценки в режиме реального времени приводит к возникновению ошибки оценки из машинного обучения модели, которая будет сохранено в SQL Server. Функция PREDICT не требуется внешний во время выполнения, например R или Python, только модель, которая будет создана с использованием определенного двоичного формата. Дополнительные сведения см. в разделе [оценки в реальном времени](https://docs.microsoft.com/sql/advanced-analytics/real-time-scoring).

## <a name="prerequisites"></a>предварительные требования

Общие сведения о расширенных событий (иногда называемых XEvents), а также отслеживать события в сеансе см. статьи:

+ [Расширенные Общие сведения о событиях и архитектура](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events)
+ [Настройка отслеживания событий в среде SSMS](https://docs.microsoft.com/sql/relational-databases/extended-events/quick-start-extended-events-in-sql-server)
+ [Управление сеансами событий в обозревателе объектов](https://docs.microsoft.com/sql/relational-databases/extended-events/manage-event-sessions-in-the-object-explorer)

## <a name="table-of-extended-events"></a>Таблица расширенных событий

Следующие расширенные события доступны во всех версиях SQL Server, которые поддерживают [ПРОГНОЗИРОВАНИЯ T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) инструкции, включая SQL Server в Linux и базы данных SQL Azure. 

Инструкции T-SQL ПРОГНОЗИРОВАНИЯ впервые появился в 2017 г. SQL Server. 

|имя |object_type|description| 
|----|----|----|
|predict_function_completed |event  |Декомпозиция Builtin времени выполнения|
|predict_model_cache_hit |event|Происходит, когда модель извлекается из кэша модели функция PREDICT. Используйте это событие вместе с другими событиями predict_model_cache_ * для устранения неполадок, связанных с кэшем функции модели ПРОГНОЗИРОВАНИЯ.|
|predict_model_cache_insert |event  |   Происходит, когда модель — вставки в кэш модели функция PREDICT. Используйте это событие вместе с другими событиями predict_model_cache_ * для устранения неполадок, связанных с кэшем функции модели ПРОГНОЗИРОВАНИЯ.    |
|predict_model_cache_miss   |event|Происходит, когда модель не найден в кэше модели функция PREDICT. Частое Повторение этого события может означать, что SQL Server требуется больше памяти. Используйте это событие вместе с другими событиями predict_model_cache_ * для устранения неполадок, связанных с кэшем функции модели ПРОГНОЗИРОВАНИЯ.|
|predict_model_cache_remove |event| Происходит, когда модель удаляется из кэша модели для ПРОГНОЗИРОВАНИЯ функции. Используйте это событие вместе с другими событиями predict_model_cache_ * для устранения неполадок, связанных с кэшем функции модели ПРОГНОЗИРОВАНИЯ.|

## <a name="query-for-related-events"></a>Запрос связанные события

Чтобы просмотреть список всех столбцов, возвращаемых для этих событий, выполните следующий запрос в SQL Server Management Studio:

```sql
SELECT * FROM sys.dm_xe_object_columns WHERE object_name LIKE `predict%'
```

## <a name="examples"></a>Примеры

Для сбора данных о производительности оценки сеанса, использующего ПРОГНОЗА:

1. Создайте новый расширенных событий сеанса, с помощью среды Management Studio или другой поддерживаемой [средство](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events-tools).
2. Добавьте события `predict_function_completed` и `predict_model_cache_hit` в сеанс.
3. Запуск сеанса расширенных событий.
4. Выполнение запроса, который использует PREDICT.

В результатах просмотрите следующие столбцы:

+ Значение для `predict_function_completed` показано время, затраченное на загрузку модели и оценки запроса.
+ Логическое значение для `predict_model_cache_hit` указывает, используется ли запрос кэшированной модели, или нет. 

### <a name="native-scoring-model-cache"></a>Собственный кэш оценки модели

Дополнение к событиям, определенных для ПРОГНОЗИРОВАНИЯ Чтобы получить дополнительные сведения о кэшированных модели и использование кэша можно использовать следующие запросы:

Представление собственный кэш оценки модели:

```sql
SELECT *
FROM sys.dm_os_memory_clerks
WHERE type = 'CACHESTORE_NATIVESCORING';
```

Просмотр объектов в кэше модели:

```sql
SELECT *
FROM sys.dm_os_memory_objects
WHERE TYPE = 'MEMOBJ_NATIVESCORING';
```

