---
title: Вопросы производительности оптимизированных для памяти темпоральных таблиц с системным управлением версиями | Документация Майкрософт
ms.custom: ''
ms.date: 03/28/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 2e110984-7703-4806-a24b-b41e8c3018c6
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5b385a3fd6c8cb0afab3e3d4eda86370bc064b56
ms.sourcegitcommit: 0a4879dad09c6c42ad1ff717e4512cfea46820e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412849"
---
# <a name="memory-optimized-system-versioned-temporal-tables-performance"></a>Вопросы производительности оптимизированных для памяти темпоральных таблиц с системным управлением версиями

[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

В этом разделе рассматриваются некоторые вопросы производительности при использовании темпоральных таблиц с системным управлением версиями, оптимизированных для памяти.

- При добавлении системы управления версиями в существующую нетемпоральную таблицу будьте готовы к тому, что это повлияет на производительность операций обновления и удаления, так как таблица журнала обновляется автоматически.
- Каждое действие обновления и удаления записывается во внутреннюю таблицу журнала, оптимизированную для памяти, поэтому потребление памяти может неожиданно возрастать, если ваша рабочая нагрузка активно использует эти две операции. Поэтому рекомендуется выполнить следующие действия.

  - Не выполняйте значительных операций удаления из текущей таблицы, чтобы увеличить доступную оперативную память, очистив пространство. Рассмотрите возможность удаления данных несколькими пакетами, вызывая вручную запись данных на диск в интервалах между пакетами посредством вызова [sp_xtp_flush_temporal_history](../../relational-databases/system-stored-procedures/temporal-table-sp-xtp-flush-temporal-history.md)или когда **SYSTEM_VERSIONING = OFF**.
  - Не выполняйте массовые обновления таблиц одновременно, так как это может привести к использованию объема памяти в два раза большего, чем требуется для обновления оптимизированной для памяти нетемпоральной таблицы. Удвоенное потребление памяти является временным, так как задача записи данных на диск выполняется регулярно и сохраняет потребление памяти внутренней промежуточной таблицей в пределах прогнозируемых границ в устойчивом состоянии (около 10 % от объема памяти, потребляемого текущей темпоральной таблицей). Попробуйте выполнять массовые обновления несколькими пакетами или когда **SYSTEM_VERSIONING = OFF**, например, используя обновления, чтобы задать значения по умолчанию для только что добавленных столбцов.

- Период активации для задачи записи данных на диск не настраивается, но можно принудительно выполнить этот процесс посредством вызова [sp_xtp_flush_temporal_history](../../relational-databases/system-stored-procedures/temporal-table-sp-xtp-flush-temporal-history.md).
- Рассмотрите возможность использования кластеризованного columnstore для хранения таблицы журнала на диске, особенно если планируется выполнять аналитические запросы к данным журнала, использующие агрегатные или ранжирующие функций. В этом случае кластеризованный индекс columnstore будет оптимальным решением для таблицы журнала, так как он обеспечивает качественное сжатие данных и приспособлен для операций вставки, что хорошо согласуется с методом формирования данных журнала.

## <a name="see-also"></a>См. также:

- [Темпоральные таблицы с системным управлением версиями и таблицы, оптимизированные для памяти](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)
- [Создание оптимизированной для памяти темпоральной таблицы с системным управлением версиями](../../relational-databases/tables/creating-a-memory-optimized-system-versioned-temporal-table.md)
- [Работа с оптимизированными для памяти темпоральными таблицами с системным управлением версиями](../../relational-databases/tables/working-with-memory-optimized-system-versioned-temporal-tables.md)
- [Мониторинг оптимизированных для памяти темпоральных таблиц с системным управлением версиями](../../relational-databases/tables/monitoring-memory-optimized-system-versioned-temporal-tables.md)
- [Темпоральные таблицы](../../relational-databases/tables/temporal-tables.md)
- [Проверка согласованности системной темпоральной таблицы](../../relational-databases/tables/temporal-table-system-consistency-checks.md)
- [Управление хранением данных журнала в темпоральных таблицах с системным управлением версиями](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)
- [Представления и функции метаданных для временной таблицы](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)
