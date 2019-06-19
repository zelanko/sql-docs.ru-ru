---
title: Расширенные события для наблюдения за инструкциями PREDICT - службы машинного обучения SQL Server
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: fa0d9d4ed647a6616c525533e696960784d09290
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63142316"
---
# <a name="extended-events-for-monitoring-predict-statements"></a>Расширенные события для наблюдения за инструкциями PREDICT

В этой статье описывается расширенных событий, предоставляемых в SQL Server можно использовать для мониторинга и анализа заданий, использующих [PREDICT](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) для выполнения оценки в режиме реального времени в SQL Server.

Оценки в реальном времени для создания оценок из машинного обучения модели, которые хранились в SQL Server. Функция PREDICT внешних времени выполнения, таких как R или Python, только модель, которая будет создана с использованием конкретного двоичного формата не требуется. Дополнительные сведения см. в разделе [оценки в реальном времени](https://docs.microsoft.com/sql/advanced-analytics/real-time-scoring).

## <a name="prerequisites"></a>предварительные требования

Общие сведения о расширенных событий (иногда называется XEvents) и для отслеживания событий в сеансе см. в статьях:

+ [Расширенные события концепции и архитектура](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events)
+ [Настройка записи событий в среде SSMS](https://docs.microsoft.com/sql/relational-databases/extended-events/quick-start-extended-events-in-sql-server)
+ [Управление сеансами событий в обозревателе объектов](https://docs.microsoft.com/sql/relational-databases/extended-events/manage-event-sessions-in-the-object-explorer)

## <a name="table-of-extended-events"></a>Таблица расширенных событий

Приведенные ниже расширенные события доступны во всех версиях SQL Server, которые поддерживают [ПРОГНОЗИРОВАНИЯ T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) инструкции, включая SQL Server в Linux и базы данных SQL Azure. 

Инструкции T-SQL ПРОГНОЗИРОВАНИЯ появилась в SQL Server 2017. 

|name |object_type|description| 
|----|----|----|
|predict_function_completed |event  |Встроенное разбиение времени выполнения|
|predict_model_cache_hit |event|Происходит при получении модели из кэша моделей функции PREDICT. Используйте это событие вместе с другими событиями predict_model_cache_ * для устранения проблем, вызванных кэшем моделей функции PREDICT.|
|predict_model_cache_insert |event  |   Происходит, когда модель используется в инструкции insert into кэшем моделей функции PREDICT. Используйте это событие вместе с другими событиями predict_model_cache_ * для устранения проблем, вызванных кэшем моделей функции PREDICT.    |
|predict_model_cache_miss   |event|Происходит, когда модель не найдена в кэш моделей функции PREDICT. Частые повторение данного события может означать, что SQL Server требует большего объема памяти. Используйте это событие вместе с другими событиями predict_model_cache_ * для устранения проблем, вызванных кэшем моделей функции PREDICT.|
|predict_model_cache_remove |event| Происходит при удалении модели из кэша моделей функции PREDICT. Используйте это событие вместе с другими событиями predict_model_cache_ * для устранения проблем, вызванных кэшем моделей функции PREDICT.|

## <a name="query-for-related-events"></a>Запрос наличие связанных событий

Чтобы просмотреть список всех столбцов, возвращаемых для этих событий, выполните следующий запрос в SQL Server Management Studio:

```sql
SELECT * FROM sys.dm_xe_object_columns WHERE object_name LIKE `predict%'
```

## <a name="examples"></a>Примеры

Для записи сведений о производительности использование PREDICT оценки сеанса:

1. Создайте новый расширенный сеанс событий, с помощью Management Studio или другой поддерживаемой [средство](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events-tools).
2. Добавьте события `predict_function_completed` и `predict_model_cache_hit` к сеансу.
3. Запуск сеанса расширенных событий.
4. Выполните запрос, использующий PREDICT.

В результатах просмотрите эти столбцы:

+ Значение для `predict_function_completed` показано время, затраченное на загрузку модели и оценки запроса.
+ Логическое значение для `predict_model_cache_hit` указывает, использовать ли этот запрос кэшированной модели. 

### <a name="native-scoring-model-cache"></a>Собственный кэш оценки модели

Помимо событий, определенных для ПРОГНОЗИРОВАНИЯ можно использовать следующие запросы для получения дополнительных сведений о кэшированной модели и использование кэша:

Представление собственный кэш модели оценки:

```sql
SELECT *
FROM sys.dm_os_memory_clerks
WHERE type = 'CACHESTORE_NATIVESCORING';
```

Просмотрите объекты в кэш моделей:

```sql
SELECT *
FROM sys.dm_os_memory_objects
WHERE TYPE = 'MEMOBJ_NATIVESCORING';
```

