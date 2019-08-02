---
title: Расширенные события для наблюдения за инструкциями PREDICT
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 283e128285fc50b9109d7950b171e30224fb9692
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714646"
---
# <a name="extended-events-for-monitoring-predict-statements"></a>Расширенные события для наблюдения за инструкциями PREDICT

В этой статье описываются расширенные события, предоставляемые в SQL Server, которые можно использовать для мониторинга и анализа заданий, использующих [Прогноз](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) для выполнения оценки в реальном времени в SQL Server.

Оценка в реальном времени создает баллы из модели машинного обучения, хранящейся в SQL Server. Функция PREDICT не требует внешнего времени выполнения, такого как R или Python, только модели, созданной с помощью определенного двоичного формата. Дополнительные сведения см. в разделе Оценка в режиме [реального времени](https://docs.microsoft.com/sql/advanced-analytics/real-time-scoring).

## <a name="prerequisites"></a>предварительные требования

Общие сведения о расширенных событиях (иногда называемых XEvents) и о том, как отслеживаниь событий в сеансе, см. в следующих статьях:

+ [Основные понятия и архитектура расширенных событий](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events)
+ [Настройка записи событий в SSMS](https://docs.microsoft.com/sql/relational-databases/extended-events/quick-start-extended-events-in-sql-server)
+ [Управление сеансами событий в обозревателе объектов](https://docs.microsoft.com/sql/relational-databases/extended-events/manage-event-sessions-in-the-object-explorer)

## <a name="table-of-extended-events"></a>Таблица расширенных событий

Следующие расширенные события доступны во всех версиях SQL Server, которые поддерживают инструкцию [прогнозирования T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) , включая SQL Server на Linux и базу данных SQL Azure. 

Инструкция T-SQL PREDICT была введена в SQL Server 2017. 

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
SELECT * FROM sys.dm_xe_object_columns WHERE object_name LIKE `predict%'
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

