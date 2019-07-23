---
title: DBCC CHECKALLOC (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CHECKALLOC_TSQL
- DBCC CHECKALLOC
- DBCC_CHECKALLOC_TSQL
- CHECKALLOC
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC CHECKALLOC statement
- checking database space allocation
- database space allocation [SQL Server]
- consistency [SQL Server], disk space allocations
- space allocation [SQL Server]
- allocation checks
- disk space [SQL Server], allocation consistency checks
- space allocation [SQL Server], checking
ms.assetid: bc1218eb-ffff-44ce-8122-6e4fa7d68a79
author: pmasl
ms.author: umajay
ms.openlocfilehash: b1d4cfe23511175ab794cc505509133b4dfb745a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68102127"
---
# <a name="dbcc-checkalloc-transact-sql"></a>DBCC CHECKALLOC (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Проверяет согласованность структур выделения места на диске для указанной базы данных.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```
DBCC CHECKALLOC   
[  
    ( database_name | database_id | 0   
      [ , NOINDEX   
      | , { REPAIR_ALLOW_DATA_LOSS | REPAIR_FAST | REPAIR_REBUILD } ]  
    )  
    [ WITH   
        {   
          [ ALL_ERRORMSGS ]  
          [ , NO_INFOMSGS ]   
          [ , TABLOCK ]   
          [ , ESTIMATEONLY ]   
        }  
    ]  
]  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name* | *database_id* | 0   
 Имя или идентификатор базы данных, для которой выполняется проверка выделения и использования страниц.
Если значение не указано или указано значение 0, используется текущая база данных.
Имена баз данных должны соответствовать правилам построения [идентификаторов](../../relational-databases/databases/database-identifiers.md).

 NOINDEX  
 Указывает, что не следует проверять некластеризованные индексы для таблиц пользователя.<br>Аргумент NOINDEX поддерживается только для обратной совместимости и не влияет на выполнение инструкции DBCC CHECKALLOC.

 REPAIR_ALLOW_DATA_LOSS \| REPAIR_FAST \| REPAIR_REBUILD  
 Указывает, что инструкции DBCC CHECKALLOC следует исправлять обнаруженные ошибки. База данных *database_name* должна работать в однопользовательском режиме.

 REPAIR_ALLOW_DATA_LOSS  
 Предпринимает попытку устранить любые обнаруженные ошибки. Эти исправления могут привести к частичной потере данных. Параметр REPAIR_ALLOW_DATA_LOSS — единственный, который позволяет исправлять ошибки при выделении пространства.

 REPAIR_FAST  
 Синтаксис сохраняется только в целях обратной совместимости. Действия по восстановлению не выполняются.

 REPAIR_REBUILD  
 Неприменимо.  
 Используйте аргументы REPAIR только как последнее средство. Для устранения ошибок рекомендуется восстановление из резервной копии. Операции восстановления не учитывают никакие ограничения, которые могут существовать для таблиц или между таблицами. Если указанная таблица включена в одно или несколько ограничений, рекомендуется выполнить инструкцию DBCC CHECKCONSTRAINTS после операции восстановления. Если необходимо использовать аргументы REPAIR, выполните инструкцию DBCC CHECKDB без параметра восстановления, чтобы узнать требуемый уровень восстановления. При использовании уровня REPAIR_ALLOW_DATA_LOSS, рекомендуется создать резервную копию базы данных перед выполнением инструкции DBCC CHECKDB с этим параметром.

 на  
 Позволяет задавать параметры.

 ALL_ERRORMSGS  
 Отображает все сообщения об ошибках. Все сообщения об ошибках выводятся по умолчанию. Указание или пропуск этого параметра не приводит к изменениям.

 NO_INFOMSGS  
 Подавляет все информационные сообщения и отчет об использованном пространстве.

 TABLOCK  
 Настраивает команду DBCC на получение монопольной блокировки базы данных.

 ESTIMATE ONLY  
 Отображает примерное место на диске, занимаемое базой данных tempdb, которое требуется для запуска инструкции DBCC CHECKALLOC, когда указаны все другие аргументы.
  
## <a name="remarks"></a>Remarks  
Инструкция DBCC CHECKALLOC проверяет выделение всех страниц в базе данных, независимо от типа страницы и типа объекта, к которому они принадлежат. Также проверяются различные внутренние структуры, используемые для отслеживания этих страниц и связей между ними.
Если не указан аргумент NO_INFOMSGS, то инструкция DBCC CHECKALLOC собирает сведения об использовании пространства всеми объектами в базе данных. Впоследствии эти сведения отображаются вместе со всеми обнаруженными ошибками.
  
> [!NOTE]  
> Функциональность инструкции DBCC CHECKALLOC включена в инструкции [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) и [DBCC CHECKFILEGROUP](../../t-sql/database-console-commands/dbcc-checkfilegroup-transact-sql.md). Это означает, что не нужно запускать DBCC CHECKALLOC отдельно от этих инструкций.   Инструкция DBCC CHECKALLOC не проверяет данные FILESTREAM. FILESTREAM сохраняет в файловой системе большие двоичные объекты.  
  
## <a name="internal-database-snapshot"></a>Моментальный снимок внутренней базы данных  
Инструкция DBCC CHECKALLOC использует внутренний моментальный снимок базы данных, чтобы обеспечить согласованность транзакций, необходимую для проведения этих проверок. Если нельзя создать моментальный снимок или указан аргумент TABLOCK, то инструкция DBCC CHECKALLOC пытается получить монопольную блокировку (X) базы данных, чтобы обеспечить необходимую согласованность.
  
> [!NOTE]  
> Запуск инструкции DBCC CHECKALLOC для базы данных tempdb не приводит к выполнению каких-либо проверок. Это обусловлено тем, что по соображениям, связанным с производительностью, моментальные снимки базы данных недоступны для базы данных tempdb. Это означает, что нельзя достичь требуемой согласованности транзакций. Остановите и запустите службу MSSQLSERVER для устранения любых проблем выделения пространства для базы данных tempdb. Это действие удаляет и повторно создает базу данных tempdb.  
  
## <a name="understanding-dbcc-error-messages"></a>Основные сведения о сообщениях об ошибках DBCC  
После завершения команды DBCC CHECKALLOC в журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет записано сообщение. При успешном выполнении команды DBCC сообщается об успешном завершении и количестве времени, затраченном на выполнение команды. Если выполнение команды DBCC прерывается до завершения проверки по причине ошибки, сообщение указывает на прерывание команды и приводит значение состояния и количество времени, затраченного на выполнение команды. В следующей таблице перечислены и описаны значения состояний, которые могут быть включены в сообщение.
  
|Состояние|Описание|  
|---|---|  
|0|Возникла ошибка с номером 8930. Это указывает на повреждение метаданных, вызвавшее прекращение выполнения команды DBCC.|  
|1|Возникла ошибка с номером 8967. Внутренняя ошибка DBCC.|  
|2|При аварийном восстановлении базы данных произошла ошибка.|  
|3|Это указывает на повреждение метаданных, вызвавшее прекращение выполнения команды DBCC.|  
|4|Обнаружено нарушение доступа или утверждения.|  
|5|Возникла неизвестная ошибка, которая привела к прекращению выполнения команды DBCC.|  
  
## <a name="error-reporting"></a>Отчет об ошибках  
При каждом обнаружении командой DBCC CHECKALLOC ошибки повреждения данных в папке LOG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создается мини-файл дампа (SQLDUMP*nnnn*.txt). Если для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] включены функции сбора данных об использовании компонентов и отчетов об ошибках, этот файл автоматически отправляется в [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Собранные данные используются для улучшения функциональности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
Файл дампа содержит результаты выполнения команды DBCC CHECKALLOC и дополнительные диагностические сведения. Доступ к этому файлу ограничен списками управления доступом на уровне пользователей. Доступ ограничен учетной записью службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и членами роли sysadmin. По умолчанию роль sysadmin содержит всех членов группы Windows BUILTIN\Administrators и группы локальных администраторов. В случае ошибки процесса сбора данных команда DBCC не завершается ошибкой.
  
## <a name="resolving-errors"></a>Разрешение ошибок  
Если инструкция DBCC CHECKALLOC сообщает о каких-нибудь ошибках, рекомендуется восстановить базу данных из резервной копии, а не запускать восстановление. Если резервной копии не существует, то процедура исправления может устранить обнаруженные ошибки; однако при устранении ошибок может потребоваться удалить некоторые страницы и, следовательно, их данные.
Устранение ошибок может быть выполнено в ходе пользовательской транзакции. Это позволяет откатить изменения. При откате изменений база данных будет по-прежнему содержать ошибки и ее необходимо будет восстанавливать из резервной копии. После того как исправление ошибок будет завершено, следует создать резервную копию базы данных.
  
## <a name="result-sets"></a>Результирующие наборы  
В следующей таблице описаны данные, возвращаемые инструкцией DBCC CHECKALLOC.
  
|Элемент|Описание|  
|---|---|  
|FirstIAM|Только для внутреннего применения.|  
|Root|Только для внутреннего применения.|  
|Dpages|Число страниц данных.|  
|Pages used|Число выделенных страниц.|  
|Dedicated extents|Экстенты, выделенные для объекта.<br /><br /> Если использованы смешанные страницы размещения, то могут существовать страницы, выделенные без экстентов.|  
  
Инструкция DBCC CHECKALLOC также формирует сводный отчет о размещении для каждого индекса и секции в каждом файле. В этой сводке описано распределение данных.
  
|Элемент|Описание|  
|---|---|  
|Reserved pages|Страницы, выделенные для индекса и неиспользованные страницы в выделенных экстентах.|  
|Used pages|Страницы, выделенные и используемые индексом.|  
|Partition ID|Только для внутреннего применения.|  
|Alloc Unit ID|Только для внутреннего применения.|  
|In-row data|Страницы содержат данные индекса или кучи.|  
|LOB data|Страницы содержат данные типа **varchar(max)** , **nvarchar(max)** , **varbinary(max)** , **text**, **ntext**, **xml** и **image**.|  
|Row-overflow data|Страницы содержат данные столбцов переменной длины, которые включают внестрочные данные.|  
  
Инструкция DBCC CHECKALLOC возвращает следующий результирующий набор (значения могут различаться), за исключением случаев, когда указаны аргументы ESTIMATEONLY или NO_INFOMSGS.
  
```
DBCC results for 'master'.  
***************************************************************  
Table sysobjects                Object ID 1.  
Index ID 1         FirstIAM (1:11)   Root (1:12)    Dpages 22.  
    Index ID 1. 24 pages used in 5 dedicated extents.  
Index ID 2         FirstIAM (1:1368)   Root (1:1362)    Dpages 10.  
    Index ID 2. 12 pages used in 2 dedicated extents.  
Index ID 3         FirstIAM (1:1392)   Root (1:1408)    Dpages 4.  
    Index ID 3. 6 pages used in 0 dedicated extents.  
Total number of extents is 7.  
***************************************************************  
'...'  
***************************************************************  
Table spt_server_info                Object ID 1938105945.  
Index ID 1         FirstIAM (1:520)   Root (1:508)    Dpages 1.  
    Index ID 1. 3 pages used in 0 dedicated extents.  
Total number of extents is 0.  
***************************************************************  
Processed 52 entries in sysindexes for database ID 1.  
File 1. Number of extents = 210, used pages = 1126, reserved pages = 1280.  
           File 1 (number of mixed extents = 73, mixed pages = 184).  
    Object ID 1, Index ID 0, data extents 5, pages 24, mixed extent pages 9.  
'...'  
    Object ID 1938105945, Index ID 0, data extents 0, pages 3, mixed extent pages 3.  
Total number of extents = 210, used pages = 1126, reserved pages = 1280 in this database.  
       (number of mixed extents = 73, mixed pages = 184) in this database.  
CHECKALLOC found 0 allocation errors and 0 consistency errors in database 'master'.  
DBCC results for 'master'.  
***************************************************************  
Table sys.sysrowsetcolumns                Object ID 4.  
Index ID 1, partition ID 262144, alloc unit ID 262144 (type In-row data). FirstIAM (1:98). Root (1:94). Dpages 7.  
Index ID 1, partition ID 262144, alloc unit ID 262144 (type In-row data). 9 pages used in 1 dedicated extents.  
Index ID 1, partition ID 262144, alloc unit ID 262398 (type Row-overflow data). FirstIAM (0:0). Root (0:0). Dpages 0.  
Index ID 1, partition ID 262144, alloc unit ID 262398 (type Row-overflow data). 0 pages used in 0 dedicated extents.  
Total number of extents is 1.  
...  
***************************************************************  
Processed 201 entries in system catalog for database ID 1.  
File 1. Number of extents = 44, used pages = 300, reserved pages = 345.  
           File 1 (number of mixed extents = 29, mixed pages = 225).  
    Object ID 4, index ID 1, partition ID 262144, alloc unit ID 262144 (type In-row data), data extents 1, pages 9, mixed extent pages 8.  
    Object ID 5, index ID 1, partition ID 327680, alloc unit ID 327680 (type In-row data), data extents 0, pages 2, mixed extent pages 2.  
    Object ID 7, index ID 1, partition ID 458752, alloc unit ID 458752 (type In-row data), data extents 0, pages 5, mixed extent pages 5.  
    Object ID 8, index ID 0, partition ID 524288, alloc unit ID 524288 (type In-row data), data extents 0, pages 2, mixed extent pages 2.  
    Object ID 13, index ID 1, partition ID 851968, alloc unit ID 851968 (type In-row data), data extents 1, pages 9, mixed extent pages 8.  
    Object ID 15, index ID 1, partition ID 983040, alloc unit ID 983040 (type In-row data), data extents 0, pages 2, mixed extent pages 2.  
    Object ID 26, index ID 1, partition ID 281474978414592, alloc unit ID 1703937 (type In-row data), data extents 0, pages 3, mixed extent pages 3.  
    Object ID 27, index ID 1, partition ID 281474978480128, alloc unit ID 1769473 (type In-row data), data extents 0, pages 3, mixed extent pages 3.  
    Object ID 27, index ID 2, partition ID 562949955190784, alloc unit ID 1769474 (type In-row data), index extents 0, pages 3, mixed extent pages 3.  
...  
    Object ID 1179151246, index ID 1, partition ID 72057594038845440, alloc unit ID 13435136 (type In-row data), data extents 2, pages 18, mixed extent pages 8.  
    Object ID 1179151246, index ID 2, partition ID 72057594038910976, alloc unit ID 13566208 (type In-row data), index extents 1, pages 16, mixed extent pages 8.  
    Object ID 1911677858, index ID 0, partition ID 72057594039631872, alloc unit ID 15073536 (type In-row data), data extents 0, pages 2, mixed extent pages 2.  
Total number of extents = 41, used pages = 289, reserved pages = 323 in this database.  
       (number of mixed extents = 27, mixed pages = 211) in this database.  
CHECKALLOC found 0 allocation errors and 0 consistency errors in database 'master'.  
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
Если указан параметр ESTIMATEONLY, то инструкция DBCC CHECKALLOC возвращает следующий результирующий набор.
  
```
Estimated TEMPDB space needed for CHECKALLOC (KB)   
-------------------------------------------------   
34  
  
(1 row(s) affected)  
  
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Разрешения  
Необходимо быть членом предопределенной роли сервера sysadmin или предопределенной роли базы данных db_owner.
  
## <a name="examples"></a>Примеры  
В следующем примере выполняется инструкция `DBCC CHECKALLOC` для текущей базы данных и для базы данных `AdventureWorks2012`.
  
```sql  
-- Check the current database.  
DBCC CHECKALLOC;  
GO  
-- Check the AdventureWorks2012 database.  
DBCC CHECKALLOC (AdventureWorks2012);  
GO  
```  
  
## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  

