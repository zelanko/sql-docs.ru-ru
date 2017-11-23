---
title: "Динамические административные представления (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- database scoped dynamic management objects [SQL Server]
- dynamic management objects [SQL Server], about dynamic management objects
- server state information [SQL Server]
- dynamic management functions [SQL Server]
- metadata [SQL Server], dynamic management objects
- dynamic management views [SQL Server]
- DMVs [SQL Server]
- functions [SQL Server], dynamic management
- server scoped dynamic management objects [SQL Server]
- dynamic management objects [SQL Server]
ms.assetid: cf893ecb-0bf6-4cbf-ac00-8a1099e405b1
caps.latest.revision: "41"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 97d8db9f9e697b72deecc59f6dbb0674b5061f0d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="system-dynamic-management-views"></a>Динамические административные представления системы
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Динамические административные представления и функции возвращают данные о состоянии сервера, которые могут использоваться для контроля исправности экземпляра сервера, диагностики проблем и настройки производительности.  
  
> [!IMPORTANT]  
>  Динамические административные представления и функции возвращают внутренние данные о состоянии, зависящие от реализации. Возвращаемые ими схемы и данные могут быть изменены в будущих выпусках сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Поэтому в будущих выпусках динамические административные представления и функции могут быть несовместимы с динамическими административными представлениями и функциями сервера в этой версии. Например, в будущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определение любого динамического административного представления может быть расширено путем добавления столбцов в конец списка столбцов. Из-за того что число возвращаемых столбцов может измениться и нарушить работу приложения, использование синтаксиса `SELECT * FROM dynamic_management_view_name` в конечном коде не рекомендуется.  
  
 Есть два типа динамических административных представлений и функций:  
  
-   динамические административные представления и функции области сервера. Для них необходимо разрешение VIEW SERVER STATE на сервере;  
  
-   динамические административные представления и функции области базы данных. Для них необходимо разрешение VIEW DATABASE STATE на базе данных.  
  
## <a name="querying-dynamic-management-views"></a>Запросы к динамическим административным представлениям  
 Ссылки на динамические административные представления в инструкциях языка [!INCLUDE[tsql](../../includes/tsql-md.md)] могут выполняться при помощи имен, состоящих из двух, трех и четырех частей. А ссылки на динамические административные функции в инструкциях языка [!INCLUDE[tsql](../../includes/tsql-md.md)] могут выполняться при помощи двух- или трехкомпонентных имен. Ссылаться на динамические административные представления и функции в инструкциях языка [!INCLUDE[tsql](../../includes/tsql-md.md)] с помощью однокомпонентных имен нельзя.  
  
 Все динамические административные представления и функции существуют в схеме sys и следуют соглашению по именованию следующего вида: dm_*. При использовании динамического административного представления или функции перед именем представления или функции должен стоять префикс схемы sys. Например, для запроса к динамическому административному представлению dm_os_wait_stats выполните следующие инструкции:  
  
 ```tsql
SELECT wait_type, wait_time_ms  
FROM sys.dm_os_wait_stats;  
```  
  
### <a name="required-permissions"></a>Необходимые разрешения  
 Для выполнения запроса к динамическому административному представлению и функции необходимо разрешение SELECT на объект, а также разрешения VIEW SERVER STATE или VIEW DATABASE STATE. Тем самым обеспечивается выборочное ограничение доступа пользователя или имени входа к динамическим административным представлениям и функциям. Для этого вначале создайте в базе данных master учетную запись пользователя, а затем запретите для пользователя разрешение SELECT на динамические административные представления и функции, на которые не хотите предоставлять доступ этому пользователю. После этого пользователь не сможет делать выборку из этих представлений и результатов функций независимо от контекста базы данных пользователя.  
  
> [!NOTE]  
>  Так как инструкция DENY имеет более высокий приоритет, если пользователю было предоставлено разрешение VIEW SERVER STATE, но был запрет на разрешение VIEW DATABASE STATE, пользователь сможет получать данные области сервера, но не базы данных.  
  
## <a name="in-this-section"></a>В этом разделе  
 Динамические административные представления и функции организованы в следующие категории:  
  
|||  
|-|-|  
|[Динамические административные представления и Funtions (Transact-SQL) с группами доступности Always On](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)|[Динамические административные представления таблиц, оптимизированных для памяти &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)|  
|[Динамические административные представления, связанные с системой отслеживания измененных данных (Transact-SQL)](http://msdn.microsoft.com/library/2a771d7d-693a-4f56-9227-02cd00e0e200)|[Объект &#40; динамические административные представления и функции Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/object-related-dynamic-management-views-and-functions-transact-sql.md)|  
|[Динамические административные представления, связанные с отслеживания изменений](http://msdn.microsoft.com/library/dc8a0af9-fcd8-4c34-9453-5132717c9bdb)|[Уведомления о запросах, связанные с динамическим административным представлениям &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/92eb22d8-33f3-4c17-b32e-e23acdfbd8f4)|  
|[Общеязыковая среда выполнения, связанные с динамическим административным представлениям &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)|[Динамические административные представления &#40; связанные с репликацией Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)|  
|[Зеркальное отображение базы данных, связанные с динамическим административным представлениям #40; Transact-SQL &#41;](http://msdn.microsoft.com/library/04fb21de-1b5e-4a8e-9ca6-1b78ad278db1)|[Регулятор ресурсов, связанные с динамическим административным представлениям &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)|  
|[Динамические административные представления &#40; относящиеся к базе данных Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)|[Динамические представления управления и функции, связанные с безопасностью (Transact-SQL)](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)|  
|[&#40; динамические административные представления и функции, связанные с выполнением Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)|[Динамические административные представления и функции, связанные с сервером (Transact-SQL)](../../relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql.md)|  
|[Динамические административные представления расширенных событий](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md)|[Динамические административные представления, связанные с компонентом Service Broker (Transact-SQL)](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)|  
|[FileStream и динамические административные представления FileTable &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)|[&#40; динамические административные представления и функции, связанные с пространственными данными Transact-SQL &#41;](http://msdn.microsoft.com/library/c542ac38-451f-43a5-bf8c-4edd38bb738e)|  
|[Компонент Full-Text Search и семантический поиск динамические административные представления и функции &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)|[Хранилище данных SQL и динамические административные представления хранилища параллельных данных &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)|  
|[Георепликация динамические административные представления и функции &#40; База данных Azure SQL &#41;](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)|[Относящиеся к операционной системе SQL Server динамические административные представления &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)|  
|[Индекс динамические административные представления и функции &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)|[Динамические административные представления базы данных Stretch &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/1193efce-a105-49a9-a8b8-26b063485567)|  
|[Я O связанные динамические административные представления и функции &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)|[Динамические административные представления и функции, связанные с транзакциями (Transact-SQL)](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)|  

  
## <a name="see-also"></a>См. также:  
 [Предоставление разрешений Server &#40; Transact-SQL &#41;](../../t-sql/statements/grant-server-permissions-transact-sql.md)   
 [ПРЕДОСТАВИТЬ разрешения базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md)   
 [Системные представления &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
