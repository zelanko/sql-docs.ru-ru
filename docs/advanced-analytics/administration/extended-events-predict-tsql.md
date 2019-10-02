---
title: Мониторинг ПРОГНОЗного T-SQL с помощью расширенных событий
description: Узнайте, как использовать расширенные события для отслеживания и устранения неполадок в инструкциях ПРОГНОЗИРОВАНИя T-SQL в SQL Server Службы машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 958ac3e24a9deec231e7fd4d5da14477d693f4de
ms.sourcegitcommit: fd3e81c55745da5497858abccf8e1f26e3a7ea7d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2019
ms.locfileid: "71714308"
---
# <a name="monitor-predict-t-sql-statements-with-extended-events-in-sql-server-machine-learning-services"></a>Отслеживание инструкций ПРОГНОЗИРОВАНИя T-SQL с расширенными событиями в SQL Server Службы машинного обучения

Узнайте, как использовать расширенные события для отслеживания и устранения неполадок в инструкциях [прогнозирования](../../t-sql/queries/predict-transact-sql.md) T-SQL в SQL Server службы машинного обучения.

## <a name="table-of-extended-events"></a>Таблица расширенных событий

Следующие расширенные события доступны во всех версиях SQL Server, поддерживающих инструкцию T-SQL [Predict](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) . 

|name |object_type|description| 
|----|----|----|
|predict_function_completed |event  |Разбиение встроенного времени выполнения|
|predict_model_cache_hit |event|Происходит при извлечении модели из кэша модели ПРОГНОЗИРУЮЩИх функций. Используйте это событие вместе с другими событиями predict_model_cache_ * для устранения неполадок, вызванных кэшем модели ПРОГНОЗИРУЮЩИх функций.|
|predict_model_cache_insert |event  |   Происходит при вставке модели в кэш модели ПРОГНОЗИРУЮЩИх функций. Используйте это событие вместе с другими событиями predict_model_cache_ * для устранения неполадок, вызванных кэшем модели ПРОГНОЗИРУЮЩИх функций.    |
|predict_model_cache_miss   |event|Происходит, когда модель не найдена в кэше модели ПРОГНОЗИРУЮЩИх функций. Частые экземпляры этого события могут указывать на то, что SQL Server требуется больше памяти. Используйте это событие вместе с другими событиями predict_model_cache_ * для устранения неполадок, вызванных кэшем модели ПРОГНОЗИРУЮЩИх функций.|
|predict_model_cache_remove |event| Происходит при удалении модели из кэша модели для функции PREDICT. Используйте это событие вместе с другими событиями predict_model_cache_ * для устранения неполадок, вызванных кэшем модели ПРОГНОЗИРУЮЩИх функций.|

## <a name="query-for-related-events"></a>Запрос связанных событий

Чтобы просмотреть список всех столбцов, возвращенных для этих событий, выполните следующий запрос в SQL Server Management Studio:

```sql
SELECT * 
FROM sys.dm_xe_object_columns 
WHERE object_name LIKE `predict%'
```

## <a name="examples"></a>Примеры

Для сбора сведений о производительности сеанса оценки с помощью PREDICT:

1. Создайте новый сеанс расширенных событий, используя Management Studio или другое поддерживаемое [средство](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events-tools).
2. Добавьте события `predict_function_completed` и `predict_model_cache_hit` в сеанс.
3. Запустите сеанс расширенных событий.
4. Выполните запрос, использующий PREDICT.

В результатах проверьте следующие столбцы:

+ Значение для `predict_function_completed` показывает, сколько времени затратил запрос на загрузку модели и оценки.
+ Логическое значение `predict_model_cache_hit` указывает, используется ли в запросе кэшированная модель. 

### <a name="native-scoring-model-cache"></a>Кэш собственной оценки модели

В дополнение к событиям, предназначенным для ПРОГНОЗИРОВАНИя, для получения дополнительных сведений о кэшированной модели и использовании кэша можно использовать следующие запросы:

Просмотр кэша модели собственной оценки:

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

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о расширенных событиях (иногда называемых XEvents) и о том, как отслеживаниь событий в сеансе, см. в следующих статьях:

+ [Мониторинг скриптов Python и R с помощью расширенных событий в SQL Server Службы машинного обучения](extended-events.md)
+ [Основные понятия и архитектура расширенных событий](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events)
+ [Настройка записи событий в SSMS](https://docs.microsoft.com/sql/relational-databases/extended-events/quick-start-extended-events-in-sql-server)
+ [Управление сеансами событий в обозревателе объектов](https://docs.microsoft.com/sql/relational-databases/extended-events/manage-event-sessions-in-the-object-explorer)
