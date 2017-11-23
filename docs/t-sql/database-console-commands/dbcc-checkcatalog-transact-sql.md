---
title: "DBCC CHECKCATALOG (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 11/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC_CHECKCATALOG_TSQL
- DBCC CHECKCATALOG
- CHECKCATALOG_TSQL
- CHECKCATALOG
dev_langs: TSQL
helpviewer_keywords:
- catalogs [SQL Server], consistency checks
- checking catalog consistency
- DBCC CHECKCATALOG statement
- integrity [SQL Server], catalogs
- consistency [SQL Server], catalogs
ms.assetid: 8076eb4e-f049-44bf-9a35-45cdd6ef0105
caps.latest.revision: "51"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 7c554f15df3eae68ea3b5cda1ba5bb316f5dcc17
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="dbcc-checkcatalog-transact-sql"></a>DBCC CHECKCATALOG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Проверяет согласованность каталогов в указанной базе данных. База данных должна быть в режиме в сети.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DBCC CHECKCATALOG   
[   
    (   
    database_name | database_id | 0  
    )  
]  
    [ WITH NO_INFOMSGS ]   
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name* | *database_id* | 0  
 Название или идентификатор базы данных, для которой проверяется согласованность каталогов. Если значение не указано или указано значение 0, используется текущая база данных. Имена баз данных должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md).  
  
 WITH NO_INFOMSGS  
 Подавляет вывод всех информационных сообщений.  
  
## <a name="remarks"></a>Замечания  
После выполнения команды DBCC CATALOG в журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записывается сообщение. При успешном выполнении команды DBCC сообщается об успешном завершении и количестве времени, затраченном на выполнение команды. Если выполнение команды DBCC прерывается до завершения проверки по причине ошибки, сообщение указывает на прерывание команды и приводит значение состояния и количество времени, затраченного на выполнение команды. В следующей таблице перечислены и описаны значения состояний, которые могут быть включены в сообщение.
  
|Состояние|Description|  
|-----------|-----------------|  
|0|Возникла ошибка с номером 8930. Это указывает на повреждение метаданных, вызвавшее прекращение выполнения команды DBCC.|  
|1|Возникла ошибка с номером 8967. Внутренняя ошибка DBCC.|  
|2|При аварийном восстановлении базы данных произошла ошибка.|  
|3|Это указывает на повреждение метаданных, вызвавшее прекращение выполнения команды DBCC.|  
|4|Обнаружено нарушение доступа или утверждения.|  
|5|Возникла неизвестная ошибка, которая привела к прекращению выполнения команды DBCC.|  
  
DBCC CHECKCATALOG выполняет различные проверки подлинности между системными таблицами метаданных. DBCC CHECKCATALOG использует моментальный снимок внутренней базы данных для предоставления согласованности транзакций, которые ему необходимы для выполнения этих проверок. Дополнительные сведения см. в разделе [Просмотр размера разреженного файла моментального снимка базы данных &#40; Transact-SQL &#41; ](../../relational-databases/databases/view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md) и в разделе «DBCC внутренней базы данных моментальных снимков использование» [DBCC &#40; Transact-SQL &#41; ](../../t-sql/database-console-commands/dbcc-transact-sql.md).
Если моментальный снимок базы данных не может быть создан, DBCC CHECKCATALOG применяет монопольную блокировку базы данных для обеспечения необходимой согласованности. Если обнаружены несогласованности, они не подлежат исправлению и база данных должна быть восстановлена из резервной копии.
  
> [!NOTE]  
>  Выполнение инструкции DBCC CHECKCATALOG для **tempdb** не выполняет каких-либо проверок. Это происходит потому, что по соображениям производительности моментальные снимки базы данных недоступны на **tempdb**. Это означает, что нельзя достичь требуемой согласованности транзакций. Очистите сервер для разрешения любых **tempdb** проблем с метаданными.  
  
> [!NOTE]  
>  Инструкция DBCC CHECKCATALOG не проверяет данные FILESTREAM. FILESTREAM сохраняет в файловой системе большие двоичные объекты.  
  
DBCC CHECKCATALOG также выполняется как часть [инструкции DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md).
  
## <a name="result-sets"></a>Результирующие наборы  
Если не указана база данных, DBCC CHECKCATALOG возвращает:
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
Если в качестве базы данных указано [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], DBCC CHECKCATALOG возвращает:
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных.  
  
## <a name="examples"></a>Примеры  
Следующий пример проверяет целостность каталогов в текущей базе данных и в базе данных `AdventureWorks`.
  
```sql
-- Check the current database.  
DBCC CHECKCATALOG;  
GO  
-- Check the AdventureWorks2012 database.  
DBCC CHECKCATALOG (AdventureWorks2012);  
GO  
```  
  
## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[Системные таблицы &#40; Transact-SQL &#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)
  
