---
title: "Вопросы производительности оптимизированных для памяти темпоральных таблиц с системным управлением версиями | Документация Майкрософт"
ms.custom: 
ms.date: 03/28/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e110984-7703-4806-a24b-b41e8c3018c6
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0cc7a8ac4a47a479e87702ddd429a95ca00b8336
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="memory-optimized-system-versioned-temporal-tables-performance"></a>Вопросы производительности оптимизированных для памяти темпоральных таблиц с системным управлением версиями
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  В этом разделе рассматриваются некоторые вопросы производительности при использовании темпоральных таблиц с системным управлением версиями, оптимизированных для памяти.  
  
-   При добавлении системы управления версиями в существующую нетемпоральную таблицу будьте готовы к тому, что это повлияет на производительность операций обновления и удаления, так как таблица журнала обновляется автоматически.  
  
-   Каждое действие обновления и удаления записывается во внутреннюю таблицу журнала, оптимизированную для памяти, поэтому потребление памяти может неожиданно возрастать, если ваша рабочая нагрузка активно использует эти две операции. Поэтому рекомендуется выполнить следующие действия.  
  
    -   Не выполняйте значительных операций удаления из текущей таблицы, чтобы увеличить доступную оперативную память, очистив пространство. Рассмотрите возможность удаления данных несколькими пакетами, вызывая вручную запись данных на диск в интервалах между пакетами посредством вызова [sp_xtp_flush_temporal_history](../../relational-databases/system-stored-procedures/temporal-table-sp-xtp-flush-temporal-history.md)или когда **SYSTEM_VERSIONING = OFF**.  
  
    -   Не выполняйте массовые обновления таблиц одновременно, так как это может привести к использованию в два раза большего объема памяти, чем требуется для обновления нетемпоральной таблицы, оптимизированной для памяти. Удвоенное потребление памяти является временным, так как задача записи данных на диск выполняется регулярно и сохраняет потребление памяти внутренней промежуточной таблицей в пределах прогнозируемых границ и в устойчивом состоянии (около 10 % от объема памяти, потребляемого текущей темпоральной таблицей). Рассмотрите возможность выполнения массовых обновлений несколькими пакетами или когда **SYSTEM_VERSIONING = OFF**, например используя обновления, чтобы задать значения по умолчанию для только что добавленных столбцов.  
  
-   Период активации для задачи записи данных на диск не настраивается, но можно принудительно выполнить этот процесс посредством вызова [sp_xtp_flush_temporal_history](../../relational-databases/system-stored-procedures/temporal-table-sp-xtp-flush-temporal-history.md).  
  
-   Рассмотрите возможность использования кластеризованного columnstore для хранения таблицы журнала на диске, особенно если планируется выполнять аналитические запросы к данным журнала, использующие агрегатные или ранжирующие функций. В этом случае кластеризованный columnstore будет оптимальным решением для таблицы журнала, так как он обеспечивает качественное сжатие данных и приспособлен для операций вставки, что хорошо согласуется с методом формирования данных журнала.  
  
## <a name="did-this-article-help-you-were-listening"></a>Эта статья помогла вам? Мы слушаем  
 Какие сведения вы искали и удалось ли вам их найти? Мы прислушиваемся к вашим отзывам для совершенствования материалов. Отправляйте свои комментарии по адресу [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Performance%20Considerations%20with%20Memory-Optimized%20System-Versioned%20Temporal%20Tables%20page)  
  
## <a name="see-also"></a>См. также:  
 [Темпоральные таблицы с системным управлением версиями и таблицы, оптимизированные для памяти](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Создание оптимизированной для памяти темпоральной таблицы с системным управлением версиями](../../relational-databases/tables/creating-a-memory-optimized-system-versioned-temporal-table.md)   
 [Работа с оптимизированными для памяти темпоральными таблицами с системным управлением версиями](../../relational-databases/tables/working-with-memory-optimized-system-versioned-temporal-tables.md)   
 [Мониторинг оптимизированных для памяти темпоральных таблиц с системным управлением версиями](../../relational-databases/tables/monitoring-memory-optimized-system-versioned-temporal-tables.md)   
 [Темпоральные таблицы](../../relational-databases/tables/temporal-tables.md)   
 [Проверка согласованности системной темпоральной таблицы](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [Управление хранением данных журнала в темпоральных таблицах с системным управлением версиями](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Представления и функции метаданных для временной таблицы](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  
