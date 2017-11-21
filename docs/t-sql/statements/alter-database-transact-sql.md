---
title: "ALTER DATABASE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 04/20/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_DATABASE_TSQL
- ALTER DATABASE
dev_langs:
- TSQL
helpviewer_keywords:
- databases [SQL Server], modifying
- ALTER DATABASE statement
- databases [SQL Server], renaming
- renaming databases
- database modifications [SQL Server]
- ALTER DATABASE statement, syntax described
- database names [SQL Server], ALTER DATABASE
- modifying databases
- collations [SQL Server], modifying
- database mirroring [SQL Server], Transact-SQL
ms.assetid: 15f8affd-8f39-4021-b092-0379fc6983da
caps.latest.revision: 282
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 6c498acedd2821127137ec6be1bd2e04e6b3da09
ms.contentlocale: ru-ru
ms.lasthandoff: 09/27/2017

---
# <a name="alter-database-transact-sql"></a>ALTER DATABASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет базу данных или файлы и файловые группы, связанные с базой данных. Добавляет или удаляет файлы и файловые группы из базы данных, изменяет атрибуты базы данных или ее файлов и файловых групп, изменяет параметры сортировки базы данных и устанавливает параметры базы данных. Моментальные снимки базы данных изменить нельзя. Чтобы изменить параметры базы данных, связанные с репликацией, используйте [sp_replicationdboption](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md).  
   
 Так как синтаксис ALTER DATABASE имеет значительную длину, его разделяют на несколько частей:  
  
 ALTER DATABASE  
 Данный раздел содержит синтаксис, изменяющий имя и параметры сортировки базы данных.  
  
 [ALTER DATABASE для файлов и параметры файловых групп](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)  
 Содержит синтаксис, добавляющий или удаляющий файлы и их группы в базе данных, а также предназначенный для изменения атрибутов указанных файлов.  
  
 [Параметры ALTER DATABASE SET](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
 Содержит синтаксис, изменяющий атрибуты базы данных с помощью параметров SET команды ALTER DATABASE.  
  
 [ALTER Database База данных зеркального отображения](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)  
 Содержит синтаксис параметров SET команды ALTER DATABASE, используемых в процессе зеркального отображения базы данных.  
  
 [ALTER DATABASE SET HADR](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)  
 Предоставляет синтаксис для [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] параметры инструкции ALTER DATABASE для настройки базы данных-получателя на вторичной реплике группы доступности Always On.  
  
 [Уровень совместимости базы данных ALTER](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
 Содержит синтаксис параметров SET команды ALTER DATABASE, относящихся к уровню совместимости базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
 
База данных SQL Azure в разделе [инструкции ALTER DATABASE &#40; База данных Azure SQL &#41;](../../t-sql/statements/alter-database-azure-sql-database.md)  
Хранилище данных SQL Azure в разделе [инструкции ALTER DATABASE &#40; Хранилище данных Azure SQL &#41; ](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md).  
Параллельное хранилище данных. в разделе [инструкции ALTER DATABASE &#40; Параллельное хранилище данных &#41; ](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md).
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- SQL Server Syntax  
ALTER DATABASE { database_name  | CURRENT }  
{  
    MODIFY NAME = new_database_name   
  | COLLATE collation_name  
  | <file_and_filegroup_options>  
  | <set_database_options>  
}  
[;]  
  
<file_and_filegroup_options >::=  
  <add_or_modify_files>::=  
  <filespec>::=   
  <add_or_modify_filegroups>::=  
  <filegroup_updatability_option>::=  
  
<set_database_options>::=  
  <optionspec>::=   
  <auto_option> ::=   
  <change_tracking_option> ::=  
  <cursor_option> ::=   
  <database_mirroring_option> ::=   
  <date_correlation_optimization_option> ::=  
  <db_encryption_option> ::=  
  <db_state_option> ::=  
  <db_update_option> ::=  
  <db_user_access_option> ::=  <delayed_durability_option> ::=  <external_access_option> ::=  
  <FILESTREAM_options> ::=  
  <HADR_options> ::=    
  <parameterization_option> ::=  
  <query_store_options> ::=  
  <recovery_option> ::=   
  <service_broker_option> ::=  
  <snapshot_option> ::=  
  <sql_option> ::=   
  <termination> ::=  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя изменяемой базы данных.  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
 CURRENT  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Определяет, что должна быть изменена текущая используемая база данных.  
  
 ИЗМЕНИТЬ имя  **=**  *новое_имя_базы_данных*  
 Переименование базы данных с именем, указанным в качестве *новое_имя_базы_данных*.  
  
 COLLATE *collation_name*  
 Задает параметры сортировки для базы данных. *collation_name* может быть либо именем параметров сортировки Windows, либо именем параметров сортировки SQL. Если аргумент не указан, базе данных будут назначены параметры сортировки экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 При создании баз данных с параметрами сортировки, отличными от параметров сортировки по умолчанию, данные в базе данных всегда учитывает указанные параметры сортировки. Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], при создании автономной базы данных, сведения внутреннего каталога поддерживаются с использованием [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию параметры сортировки, **Latin1_General_100_CI_AS_WS_KS_SC**.  
  
 Дополнительные сведения об именах параметров сортировки Windows и SQL см. в разделе [COLLATE &#40; Transact-SQL &#41; ](~/t-sql/statements/collations.md).  
  
 **\<delayed_durability_option >:: =**  
 **Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Дополнительные сведения см. [параметры ALTER DATABASE SET &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) и [устойчивостью транзакций](../../relational-databases/logs/control-transaction-durability.md).  
  
 **\<file_and_filegroup_options >:: =**  
 Дополнительные сведения см. в разделе [&#40; ALTER DATABASE File и параметры файловых групп Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md).  
  
## <a name="remarks"></a>Замечания  
 Чтобы удалить базу данных, используйте [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md).  
  
 Чтобы уменьшить размер базы данных, используйте [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
 Инструкция ALTER DATABASE должна выполняться в режиме автоматической фиксации (режим управления транзакциями по умолчанию) и не разрешена в явной или неявной транзакции.  
  
 Состояние файла базы данных (например «в сети» или «вне сети») поддерживается независимо от состояния базы данных. Дополнительные сведения см. в разделе [состояния файла](../../relational-databases/databases/file-states.md). Состояние файлов в пределах файловой группы определяет доступность файловой группы в целом. Чтобы файловая группа была доступна, необходимо, чтобы все файлы в файловой группе находились в режиме в сети. Если файловая группа вне сети, то любая попытка обращения к файловой группе с помощью инструкции SQL закончится ошибкой. При создании планов запросов для инструкций SELECT оптимизатор запросов избегает некластеризованных индексов и индексированных представлений, которые находятся в файловых группах вне сети. Это позволяет успешно выполнить эти инструкции. Однако если файловая группа, находящаяся в режиме вне  сети, содержит кучу или кластеризованный индекс целевой таблицы, инструкция SELECT не будет выполнена. Кроме того, любая инструкция INSERT, UPDATE или DELETE, изменяющая таблицу с любым индексом в файловой группе, находящихся в режиме вне  сети, также не будет выполнена.  
  
 Если база данных находится в состоянии RESTORING, выполнение большинства инструкций ALTER DATABASE закончится неудачей. Исключением является настройка параметров зеркального отображения базы данных. База данных может находиться в состоянии RESTORING во время выполнения операции восстановления или тогда, когда при операции восстановления базы данных или файла журнала происходит сбой из-за поврежденного файла резервной копии.  
  
 Кэш планов для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] очищается при установке одного из следующих параметров.  
  
|||  
|-|-|  
|OFFLINE|READ_WRITE|  
|ONLINE|MODIFY FILEGROUP DEFAULT|  
|MODIFY_NAME|MODIFY FILEGROUP READ_WRITE|  
|COLLATE|MODIFY FILEGROUP READ_ONLY|  
|READ_ONLY|PAGE_VERIFY|  
  
 Очистка кэша планов становится причиной перекомпиляции всех последующих планов выполнения и приводит к непредвиденному временному снижению производительности обработки запросов. Для каждого удаленного хранилища кэша в кэше планов журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит следующее информационное сообщение: «[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил %d экземпляров, записанных на диск хранилищ кэша для хранилища кэша "%s" (части кэша планов) в результате операций по обслуживанию или изменению конфигурации базы данных». Это сообщение добавляется в журнал каждые пять минут при сбросе кэша в течение этого интервала времени.  
  
 Кроме того, кэш процедур сбрасывается в следующих случаях.  
  
-   В базе данных включен параметр базы данных AUTO_CLOSE. Если отсутствуют ссылки соединений пользователя или базы данных, фоновая задача предпримет попытку закрыть и отключить базу данных автоматически.  
  
-   Выполняется нескольких запросов в базе данных с параметрами по умолчанию. Затем база данных уничтожается.  
  
-   Моментальный снимок базы данных для базы данных-источника удален.  
  
-   Успешное перестроение журнала транзакций базы данных.  
  
-   Восстановление резервной копии базы данных.  
  
-   Отсоединение базы данных.  
  
## <a name="changing-the-database-collation"></a>Изменение параметров сортировки в базе данных  
 Прежде чем применить другие параметры сортировки к базе данных, убедитесь, что соблюдены следующие условия.  
  
-   Вы являетесь единственным пользователем базы данных в настоящее время.  
  
-   Ни один объект, привязанный к схеме, не зависит от параметров сортировки базы данных.  
  
     Если следующие объекты, зависящие от параметров сортировки базы данных, существуют в базе данных, инструкция ALTER DATABASE*имя_базы_данных*COLLATE завершится ошибкой. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает сообщение об ошибке для каждого объекта, блокирующего действие ALTER:  
  
    -   определяемые пользователем функции и представления, созданные с помощью предложения SCHEMABINDING;  
  
    -   вычисляемые столбцы;  
  
    -   ограничения CHECK;  
  
    -   возвращающие табличное значение функции, которые возвращают таблицы с символьными столбцами, имеющими параметры сортировки, унаследованные из параметров сортировки базы данных по умолчанию.  
  
     Информация о зависимостях не привязанных к схеме сущностей обновляется автоматически при изменении параметров сортировки базы данных.  
  
 При изменении параметров сортировки базы данных дубликаты любых системных имен для объектов базы данных не создаются. Если новые параметры сортировки вызывают повторяющиеся имена, следующие пространства имен могут вызвать сбой при изменении параметров сортировки базы данных:  
  
-   имена объектов, такие как процедуры, таблицы, триггеры или представления;  
  
-   имена схем;  
  
-   участники, такие как группы, роли или пользователи;  
  
-   имена скалярных типов, таких как системные и определяемые пользователем типы;  
  
-   имена полнотекстовых каталогов;  
  
-   имена столбцов или параметров в пределах объекта;  
  
-   имена индексов в пределах таблицы.  
  
Повторяющиеся имена, полученные с помощью новых параметров сортировки, могут быть причиной сбоя операции изменения, а [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвратит сообщение об ошибке, указывающее пространство имен, в котором был найден дубликат.  
  
## <a name="viewing-database-information"></a>Просмотр сведений о базе данных  
 Для возврата сведений о базах данных, файлах и файловых группах можно использовать представления каталогов, системные функции и системные хранимые процедуры.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение ALTER на базу данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-the-name-of-a-database"></a>A. Изменение имени базы данных  
 В следующем примере имя базы данных `AdventureWorks2012` изменяется на `Northwind`.  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
Modify Name = Northwind ;  
GO  
```  
  
### <a name="b-changing-the-collation-of-a-database"></a>Б. Изменение параметров сортировки базы данных  
 В следующем примере создается база данных `testdb`, параметры сортировки которой имеют значение `SQL_Latin1_General_CP1_CI_A`. Затем имя базы данных `testdb` изменяется на `COLLATE French_CI_AI`.  
  
**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
USE master;  
GO  
  
CREATE DATABASE testdb  
COLLATE SQL_Latin1_General_CP1_CI_AS ;  
GO  
  
ALTER DATABASE testDB  
COLLATE French_CI_AI ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
- [ALTER DATABASE &#40; База данных Azure SQL &#41;](alter-database-azure-sql-database.md)  
- [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
- [DATABASEPROPERTYEX (Transact-SQL)](../../t-sql/functions/databasepropertyex-transact-sql.md)   
- [DROP DATABASE (Transact-SQL)](../../t-sql/statements/drop-database-transact-sql.md)   
- [SET TRANSACTION ISOLATION LEVEL (Transact-SQL)](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
- [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
- [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
- [sp_spaceused &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
- [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
- [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
- [sys.database_mirroring_witnesses &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
- [sys.data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
- [sys.filegroups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
- [sys.master_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
- [Системные базы данных](../../relational-databases/databases/system-databases.md)  
  

