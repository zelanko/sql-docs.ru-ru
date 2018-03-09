---
title: "Удаление базы данных (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/15/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP DATABASE
- DROP_DATABASE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- snapshots [SQL Server database snapshots], deleting
- removing databases
- database snapshots [SQL Server], removing
- deleting databases
- dropping databases
- databases [SQL Server], dropping
- DROP DATABASE statement
- database removal [SQL Server], DROP DATABASE statement
ms.assetid: 477396a9-92dc-43c9-9b97-42c8728ede8e
caps.latest.revision: "83"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 6e963031c1d9f27293a2f0786e7f0ce19183f038
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="drop-database-transact-sql"></a>DROP DATABASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Удаляет одну или несколько пользовательских баз данных или моментальных снимков базы данных из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- SQL Server Syntax  
DROP DATABASE [ IF EXISTS ] { database_name | database_snapshot_name } [ ,...n ] [;]  
```  
  
```  
-- Azure SQL Database, Azure SQL Data Warehouse and Parallel Data Warehouse Syntax   
DROP DATABASE database_name [;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *ЕСЛИ СУЩЕСТВУЕТ*  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Условно удаляется база данных только в том случае, если он уже существует.  
  
 *database_name*  
 Задает имя удаляемой базы данных. Чтобы отобразить список баз данных, используйте [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) представления каталога.  
  
 *имя_моментального_снимка_базы_данных*  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Задает имя удаляемого моментального снимка базы данных.  
  
## <a name="general-remarks"></a>Общие замечания  
 База данных может быть удалена независимо от ее состояния: вне сети, только для чтения, подозрительная и так далее. Для отображения текущего состояния базы данных, используйте **sys.databases** представления каталога.  
  
 Удаленная база данных может быть повторно создана только с помощью восстановления из резервной копии. Резервное копирование моментальных снимков базы данных произвести невозможно, поэтому они не могут быть восстановлены.  
  
 При удалении базы данных [базы данных master](../../relational-databases/databases/master-database.md) должна подвергаться резервному копированию.  
  
 При удалении базы данных удаляется из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и удаляет физический диск файлы, используемые базой данных. Если база данных или один из ее файлов во время удаления находится в режиме вне сети, файлы с диска не удаляются. Эти файлы можно удалить вручную при помощи обозревателя Windows. Чтобы удалить базу данных с текущего сервера без удаления файлов из файловой системы, используйте [sp_detach_db](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md).  
  
> [!WARNING]  
>  При удалении базы данных, имеющий FILE_SNAPSHOT резервные копии, связанные с ним выполняется успешно, однако сделать резервные копии, ссылающиеся на эти файлы базы данных не будут удалены файлы базы данных, в которых имеются связанные моментальные снимки. Файл будет усечено, но не будут физически удалены для хранения резервных копий FILE_SNAPSHOT без изменений. Дополнительные сведения см. в разделе [Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md). **Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658).  
  
### [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 При удалении моментального снимка базы данных он удаляется из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а его физические разреженные файлы удаляются из файловой системы NTFS. Сведения об использовании разреженных файлов моментальных снимков баз данных см. в разделе [моментальные снимки базы данных &#40; SQL Server &#41; ](../../relational-databases/databases/database-snapshots-sql-server.md). Удаление моментального снимка базы данных очищает кэш планов для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Очистка кэша планов становится причиной перекомпиляции всех последующих планов выполнения и приводит к непредвиденному временному снижению производительности обработки запросов. Для каждого удаленного хранилища кэша в кэше планов журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит следующее информационное сообщение: «[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил %d экземпляров, записанных на диск хранилищ кэша для хранилища кэша "%s" (части кэша планов) в результате операций по обслуживанию или изменению конфигурации базы данных». Это сообщение добавляется в журнал каждые пять минут при сбросе кэша в течение этого интервала времени.  
  
## <a name="interoperability"></a>Совместимость  
  
### <a name="sql-server"></a>SQL Server  
 Чтобы удалить базу данных, опубликованную для репликации транзакций либо опубликованную или подписанную на репликацию слиянием, вначале необходимо удалить репликацию из базы данных. Если база данных повреждена или репликация не может быть удалена, скорее всего, базу данных все равно можно будет удалить, использовав инструкцию ALTER DATABASE для перевода базы данных в режим вне сети, после чего удалить ее.  
  
 Если база данных участвует в доставке журнала, отмените доставку журнала перед удалением базы данных. Дополнительные сведения см. в разделе [Сведения о доставке журналов (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md).  
  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 [Системные базы данных](../../relational-databases/databases/system-databases.md) не может быть удален.  
  
 Инструкция DROP DATABASE должна выполняться в режиме автоматической фиксации и не разрешена в явной или неявной транзакции. Режим автоматической фиксации — это режим управления транзакцией по умолчанию.  
  
 Удалить базу данных, которая используется в текущий момент времени, невозможно. Такая база данных может использоваться каким-либо пользователем для чтения или записи данных. Для отключения пользователей от базы данных используйте инструкцию ALTER DATABASE для перевода базы данных в режим SINGLE_USER.  
  
### [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Любые моментальные снимки базы данных должны быть удалены перед удалением базы данных.  
  
 Удаление Включение базы данных для базы данных Stretch не приводит к удалению удаленных данных. Если вы хотите удалить удаленных данных, необходимо удалить вручную.  
  
### [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
 Для удаления базы данных необходимо соединение с базой данных master.
  
 Инструкция DROP DATABASE должна быть единственной инструкцией в пакете SQL, и ее можно удалить только одновременно с базой данных.
  
### [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]  
 Для удаления базы данных необходимо соединение с базой данных master.
  
 Инструкция DROP DATABASE должна быть единственной инструкцией в пакете SQL, и ее можно удалить только одновременно с базой данных.

## <a name="permissions"></a>Permissions  
  
### [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Требуется **УПРАВЛЕНИЯ** разрешения в базе данных или **ALTER ANY DATABASE** разрешения или членства в **db_owner** предопределенной роли базы данных.  
  
### [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
 Только входа субъекта серверного уровня (созданное процессом подготовки) или члены **dbmanager** роли базы данных можно удалить базу данных.  
  
### [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Требуется **УПРАВЛЕНИЯ** разрешения в базе данных или **ALTER ANY DATABASE** разрешения или членства в **db_owner** предопределенной роли базы данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-dropping-a-single-database"></a>A. Удаление одиночной базы данных  
 В следующем примере удаляется база данных `Sales`.  
  
```  
DROP DATABASE Sales;  
```  
  
### <a name="b-dropping-multiple-databases"></a>Б. Удаление нескольких баз данных  
  
**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 В следующем примере удаляется каждая из перечисленных баз данных.  
  
```  
DROP DATABASE Sales, NewSales;  
```  
  
### <a name="c-dropping-a-database-snapshot"></a>В. Удаление моментального снимка базы данных  
  
**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 В следующем примере удаляется моментальный снимок базы данных с именем `sales_snapshot0600`, не затрагивая базы данных-источника.  
  
```  
DROP DATABASE sales_snapshot0600;  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
  
