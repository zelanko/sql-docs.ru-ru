---
title: "Выполняющаяся в памяти OLTP (оптимизация в памяти) | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 11/22/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- In-Memory OLTP
- memory-optimized tables
ms.assetid: e1d03d74-2572-4a55-afd6-7edf0bc28bdb
caps.latest.revision: 106
author: MightyPen
ms.author: genemi
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b377f0c359751a5c970ceef2e1d7fa6bc556e3d7
ms.lasthandoff: 04/11/2017

---
# <a name="in-memory-oltp-in-memory-optimization"></a>In-Memory OLTP (оптимизация в памяти)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] может значительно улучшить производительность обработки транзакций, приема и загрузки данных, а также оптимизировать сценарии с использованием временных данных.  Базовый код и сведения, необходимые для быстрого тестирования вашей собственной оптимизированной для памяти таблицы и скомпилированной в собственном коде хранимой процедуры, см. в статье:
 -  [Краткое руководство 1. Технологии выполнения OLTP в памяти для повышения производительности службы Transact-SQL](../../relational-databases/in-memory-oltp/survey-of-initial-areas-in-in-memory-oltp.md)  
 
Видеоролик, длительностью 17 минут, поясняющий выполняющуюся в памяти OLTP и демонстрирующий преимущества с точки зрения производительности:

-  [In-Memory OLTP in SQL Server 2016](https://www.youtube.com/watch?v=l5l5eophmK4)(Выполняющаяся в памяти OLTP в SQL Server 2016)

Чтобы скачать демонстрацию производительности для выполняющейся в памяти OLTP, используемую в этом видео: 

- [In-Memory OLTP Performance Demo v1.0](https://github.com/Microsoft/sql-server-samples/releases/tag/in-memory-oltp-demo-v1.0)

Дополнительные сведения о выполняющейся в памяти OLTP и обзор сценариев, в которых эта технология может значительно улучшать производительность:

- [Общие сведения и сценарии использования](../../relational-databases/in-memory-oltp/overview-and-usage-scenarios.md)
 
 Обратите внимание на то, что [!INCLUDE[hek_2](../../includes/hek-2-md.md)] представляет собой технологию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для повышения производительности при обработке транзакций. Сведения о технологии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , повышающей производительность при обработке отчетов и аналитических запросов, см. в статье [Руководство по индексам columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md).
  
 В [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]для выполняющейся в памяти OLTP было внесено несколько улучшений. Контактная зона Transact-SQL увеличена для облегчения переноса приложений баз данных. Добавлена поддержка выполнения операций ALTER для оптимизированных для памяти таблиц и скомпилированных в собственном коде хранимых процедур, чтобы упростить обслуживание приложений. Сведения о новых функциях [!INCLUDE[hek_2](../../includes/hek-2-md.md)] см. на странице [Новые возможности индексов columnstore](../../relational-databases/indexes/columnstore-indexes-what-s-new.md).  
  
> [!NOTE]  
>  **Попробуйте продукт**  
>   
>  Выполняющаяся в памяти OLTP доступна для баз данных SQL Azure уровня Premium. Сведения о том, как приступить к работе с выполняющейся в памяти OLTP и индексами columnstore в Базе данных SQL Azure, см. в статье [Приступая к работе с In-Memory (в режиме предварительной версии) в базе данных SQL](https://azure.microsoft.com/documentation/articles/sql-database-in-memory/).  
  

## <a name="in-this-section"></a>В этом разделе  
 Здесь приведен список статей с описанием.  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Краткое руководство 1. Технологии выполнения OLTP в памяти для повышения производительности службы Transact-SQL](../../relational-databases/in-memory-oltp/survey-of-initial-areas-in-in-memory-oltp.md)|Подробные сведения о выполняющейся в памяти OLTP.|
|[Общие сведения и сценарии использования](../../relational-databases/in-memory-oltp/overview-and-usage-scenarios.md)|Общие сведения о выполняющейся в памяти OLTP и сценарии, в которых эта технология может улучшать производительность.|
|[Требования для использования таблиц, оптимизированных для памяти](../../relational-databases/in-memory-oltp/requirements-for-using-memory-optimized-tables.md)|Перечисляются требования к программному обеспечению и оборудованию, а также рекомендации по использованию оптимизированных для памяти таблиц.|  
|[Примеры кода In-Memory OLTP](../../relational-databases/in-memory-oltp/in-memory-oltp-code-samples.md)|Содержит образцы кода, которые показывают, как создавать и использовать оптимизированные для памяти таблицы.|  
|[Таблицы, оптимизированные для памяти](../../relational-databases/in-memory-oltp/memory-optimized-tables.md)|Дает вводное описание таблиц, оптимизированных для памяти.|  
|[Основные сведения о табличных переменных, оптимизированных для памяти](http://msdn.microsoft.com/library/bd102e95-53e2-4da6-9b8b-0e4f02d286d3)|Пример кода, показывающий, как использовать переменную оптимизированной для памяти таблицы вместо традиционной табличной переменной для уменьшения использования базы данных tempdb.|  
|[Индексы для оптимизированных для памяти таблиц](http://msdn.microsoft.com/library/86805eeb-6972-45d8-8369-16ededc535c7)|Содержит базовое описание индексов, оптимизированных для памяти.|  
|[Скомпилированные в собственном коде хранимые процедуры](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)|Содержит базовое описание хранимых процедур, скомпилированных в собственном коде.|  
|[Управление памятью для компонента "Выполняющаяся в памяти OLTP"](http://msdn.microsoft.com/library/d82f21fa-6be1-4723-a72e-f2526fafd1b6)|Основные сведения об управлении памятью системы.|  
|[Создание и управление хранилищем для оптимизированных для памяти объектов](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)|Описывает файлы данных и разностные файлы, в которых хранятся сведения о транзакциях в оптимизированных для памяти таблицах.|  
|[Резервное копирование и восстановление оптимизированных для памяти таблиц](http://msdn.microsoft.com/library/3f083347-0fbb-4b19-a6fb-1818d545e281)|Описывает резервное копирование, восстановление и восстановление оптимизированных для памяти таблиц.|  
|[Поддержка Transact-SQL для выполняющейся в памяти OLTP](../../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)|Описывает поддержку службой [!INCLUDE[tsql](../../includes/tsql-md.md)] службы [!INCLUDE[hek_2](../../includes/hek-2-md.md)].|  
|[Поддержка высокого уровня доступности в базах данных OLTP в памяти](../../relational-databases/in-memory-oltp/high-availability-support-for-in-memory-oltp-databases.md)|Описывает группы доступности и отказоустойчивые кластеры в службе [!INCLUDE[hek_2](../../includes/hek-2-md.md)].|  
|[Поддержка SQL Server для In-Memory OLTP](../../relational-databases/in-memory-oltp/sql-server-support-for-in-memory-oltp.md)|Описание нового и обновленного синтаксиса и функций, поддерживающих оптимизированные для памяти таблицы.|  
|[Миграция в выполняющуюся в памяти OLTP](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)|Рассматриваются способы миграции дисковых таблиц в оптимизированные для памяти таблицы.|  
  
 Больше информации о службе [!INCLUDE[hek_2](../../includes/hek-2-md.md)] доступно в:  

- [Видеоролик, поясняющий выполняемую в памяти OLTP и демонстрирующий преимущества с точки зрения производительности](https://www.youtube.com/watch?v=l5l5eophmK4).

- [In-Memory OLTP Performance Demo v1.0](https://github.com/Microsoft/sql-server-samples/releases/tag/in-memory-oltp-demo-v1.0)

-   [Техническая документация по внутренней структуре выполняющейся в памяти OLTP SQL Server](https://msdn.microsoft.com/library/mt764316.aspx)  

-   [Сравнение функций SQL Server In-Memory OLTP и columnstore](http://download.microsoft.com/download/D/0/0/D0075580-6D72-403D-8B4D-C3BD88D58CE4/SQL_Server_2016_In_Memory_OLTP_and_Columnstore_Comparison_White_Paper.pdf)

-   Новые возможности In-Memory OLTP в SQL Server 2016 [Часть 1](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2015/11/12/in-memory-oltp-whats-new-in-sql2016-ctp3/) и [Часть 2](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/25/whats-new-for-in-memory-oltp-in-sql-server-2016-since-ctp3/)
  
-   [In-Memory OLTP – Common Workload Patterns and Migration Considerations](http://msdn.microsoft.com/library/dn673538.aspx)  
  
-   [Блог о выполняющейся в памяти OLTP](http://go.microsoft.com/fwlink/?LinkId=311696)  
  
## <a name="see-also"></a>См. также  
 [Функции базы данных](../../relational-databases/database-features.md)  
  
  

