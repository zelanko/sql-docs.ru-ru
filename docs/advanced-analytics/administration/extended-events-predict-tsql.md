---
title: Мониторинг T-SQL с использованием расширенных событий
description: Сведения о том, как использовать расширенные события для мониторинга инструкций T-SQL PREDICT в Службах машинного обучения SQL Server, а также устранять связанные с ними неполадки.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9e891ee16ce664e12f12b16c9deda957d0fa2263
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "73727725"
---
# <a name="monitor-predict-t-sql-statements-with-extended-events-in-sql-server-machine-learning-services"></a>Мониторинг инструкций T-SQL PREDICT с использованием расширенных событий в Службах машинного обучения SQL Server

Сведения о том, как использовать расширенные события для мониторинга инструкций T-SQL [PREDICT](../../t-sql/queries/predict-transact-sql.md) в Службах машинного обучения SQL Server, а также устранять связанные с ними неполадки.

## <a name="table-of-extended-events"></a>Таблица расширенных событий

Приведенные ниже расширенные события доступны во всех версиях SQL Server, поддерживающих инструкцию T-SQL [PREDICT](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql). 

|name |object_type|description| 
|----|----|----|
|predict_function_completed |event  |Встроенное разбиение времени выполнения|
|predict_model_cache_hit |event|Происходит при извлечении модели из кэша моделей функции PREDICT. Используйте это событие вместе с другими событиями predict_model_cache_* для решения проблем, вызванных кэшем моделей функции PREDICT.|
|predict_model_cache_insert |event  |   Происходит при вставке модели в кэш моделей функции PREDICT. Используйте это событие вместе с другими событиями predict_model_cache_* для решения проблем, вызванных кэшем моделей функции PREDICT.    |
|predict_model_cache_miss   |event|Происходит, если модель не найдена в кэше моделей функции PREDICT. Если это событие возникает часто, это может указывать на то, что для SQL Server требуется больше памяти. Используйте это событие вместе с другими событиями predict_model_cache_* для решения проблем, вызванных кэшем моделей функции PREDICT.|
|predict_model_cache_remove |event| Происходит при удалении модели из кэша моделей функции PREDICT. Используйте это событие вместе с другими событиями predict_model_cache_* для решения проблем, вызванных кэшем моделей функции PREDICT.|

## <a name="query-for-related-events"></a>Запрос связанных событий

Чтобы просмотреть список столбцов, возвращенных для этих событий, выполните следующий запрос в SQL Server Management Studio:

```sql
SELECT * 
FROM sys.dm_xe_object_columns 
WHERE object_name LIKE `predict%'
```

## <a name="examples"></a>Примеры

Для сбора сведений о производительности сеанса оценки с использованием PREDICT выполните указанные ниже действия.

1. Создайте сеанс расширенных событий с помощью Management Studio или другого поддерживаемого [средства](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events-tools).
2. Добавьте в сеанс события `predict_function_completed` и `predict_model_cache_hit`.
3. Запустите сеанс расширенных событий.
4. Выполните запрос, использующий функцию PREDICT.

В результатах проверьте следующие столбцы:

+ Значение `predict_function_completed` показывает, сколько времени запрос затратил на загрузку модели и оценку.
+ Логическое значение `predict_model_cache_hit` указывает, использовал ли запрос кэшированную модель. 

### <a name="native-scoring-model-cache"></a>Кэш собственных моделей для оценки

Помимо событий, относящихся к функции PREDICT, для получения дополнительных сведений о кэшированной модели и использовании кэша можно использовать следующие запросы:

Просмотр кэша собственных моделей для оценки:

```sql
SELECT *
FROM sys.dm_os_memory_clerks
WHERE type = 'CACHESTORE_NATIVESCORING';
```

Просмотр объектов в кэше моделей:

```sql
SELECT *
FROM sys.dm_os_memory_objects
WHERE TYPE = 'MEMOBJ_NATIVESCORING';
```

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о расширенных событиях и о том, как отслеживать события в рамках сеанса, см. в следующих статьях:

+ [Мониторинг скриптов Python и R с использованием расширенных событий в Службах машинного обучения SQL Server](extended-events.md)
+ [Основные понятия и архитектура расширенных событий](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events)
+ [Настройка сбора событий в SSMS](https://docs.microsoft.com/sql/relational-databases/extended-events/quick-start-extended-events-in-sql-server)
+ [Управление сеансами событий в обозревателе объектов](https://docs.microsoft.com/sql/relational-databases/extended-events/manage-event-sessions-in-the-object-explorer)
