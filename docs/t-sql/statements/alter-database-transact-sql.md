---
title: ALTER DATABASE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/03/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 11a17e013933456a092f1ef3f9da9a3695271963
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39452658"
---
# <a name="alter-database-transact-sql"></a>ALTER DATABASE (Transact-SQL)

Вносит изменения в базу данных. 

Щелкните одну из следующих вкладок, чтобы изучить синтаксис, аргументы, примечания, разрешения и примеры для используемой вам версии SQL.

Дополнительные сведения о соглашениях о синтаксисе см. в статье [Соглашения о синтаксисе в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md). 

# <a name="sql-servertabsqlserver"></a>[SQL Server](#tab/sqlserver)
  
## <a name="overview"></a>Обзор

В SQL Server эта инструкция изменяет базу данных или файлы и файловые группы, связанные с базой данных. Добавляет или удаляет файлы и файловые группы из базы данных, изменяет атрибуты базы данных или ее файлов и файловых групп, изменяет параметры сортировки базы данных и устанавливает параметры базы данных. Моментальные снимки базы данных изменить нельзя. Чтобы изменить параметры базы данных, связанные с репликацией, используйте процедуру [sp_replicationdboption](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md).  
   
Так как синтаксис ALTER DATABASE имеет значительную длину, мы разделили его описание на несколько разделов.  

ALTER DATABASE  
В этом разделе описывается синтаксис для изменения имени и параметров сортировки базы данных, а также содержится дополнительная информация.  
  
[Параметры инструкции ALTER DATABASE для файлов и файловых групп](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)  
Синтаксис для добавления или удаления файлов и файловых групп в базе данных, для изменения атрибутов файлов и файловых групп, а также дополнительная информация об этом.  
  
[Параметры ALTER DATABASE SET](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
Синтаксис для изменения атрибутов базы данных с помощью параметров SET команды ALTER DATABASE, а также дополнительная информация об этом.  
  
[Зеркальное отображение базы данных ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)  
Синтаксис параметров SET команды ALTER DATABASE, используемых в процессе зеркального отображения базы данных, а также дополнительная информация об этом.  
  
[ALTER DATABASE SET HADR](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)  
Синтаксис для параметров [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] инструкции ALTER DATABASE для настройки базы данных-получателя вторичной реплики группы доступности AlwaysOn, а также дополнительная информация об этом.  
  
[Уровень совместимости ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
Синтаксис параметров SET инструкции ALTER DATABASE, имеющих отношение к уровням совместимости базы данных, и дополнительная информация об этом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- SQL Server Syntax  
ALTER DATABASE { database_name  | CURRENT }  
{  
    MODIFY NAME = new_database_name   
  | COLLATE collation_name  
  | <file_and_filegroup_options>  
  | SET <option_spec> [ ,...n ] [ WITH <termination> ] 
  | SET COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 | 90 }   
  
}  
[;]  
  
<file_and_filegroup_options>::=  
  <add_or_modify_files>::=  
  <filespec>::=   
  <add_or_modify_filegroups>::=  
  <filegroup_updatability_option>::=  
  
<option_spec>::=  
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
 
<compatibility_level>
   { 140 | 130 | 120 | 110 | 100 | 90 }   
```  
  
## <a name="arguments"></a>Аргументы  
*database_name*  
Имя изменяемой базы данных.  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
CURRENT  
**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
Определяет, что должна быть изменена текущая используемая база данных.  
  
MODIFY NAME **=***new_database_name*  
Присваивает базе данных имя, указанное в аргументе *новое_имя_базы_данных*.  
  
COLLATE *collation_name*  
Задает параметры сортировки для базы данных. Аргументом *collation_name* может быть либо имя параметров сортировки Windows, либо имя параметров сортировки SQL. Если аргумент не указан, базе данных будут назначены параметры сортировки экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
При создании баз данных с параметрами сортировки, отличными от параметров сортировки по умолчанию, данные в базе данных всегда учитывают указанные параметры сортировки. Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при создании автономной базы данных сведения внутреннего каталога поддерживаются с использованием параметров сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию **Latin1_General_100_CI_AS_WS_KS_SC**.  
  
Список имен параметров сортировки Windows и SQL см. в статье [Параметры сортировки](~/t-sql/statements/collations.md).  
  
**\<delayed_durability_option> ::=**  
**Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
Дополнительные сведения см. в статьях [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md) и [Управление устойчивостью транзакций](../../relational-databases/logs/control-transaction-durability.md).  
  
**\<file_and_filegroup_options>::=**  
Дополнительные сведения см. в статье [Параметры инструкции ALTER DATABASE для файлов и файловых групп (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md).  
  
## <a name="remarks"></a>Remarks  
Чтобы удалить базу данных, используйте инструкцию [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md).  
  
Чтобы уменьшить размер базы данных, используйте предложение [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
Инструкция ALTER DATABASE должна выполняться в режиме автоматической фиксации (режим управления транзакциями по умолчанию) и не разрешена в явной или неявной транзакции.  
  
Состояние файла базы данных (например "в сети" или "вне сети") поддерживается независимо от состояния базы данных. Дополнительные сведения см. в разделе [Состояния файлов](../../relational-databases/databases/file-states.md). Состояние файлов в пределах файловой группы определяет доступность файловой группы в целом. Чтобы файловая группа была доступна, необходимо, чтобы все файлы в файловой группе находились в режиме в сети. Если файловая группа вне сети, то любая попытка обращения к файловой группе с помощью инструкции SQL закончится ошибкой. При создании планов запросов для инструкций SELECT оптимизатор запросов избегает некластеризованных индексов и индексированных представлений, которые находятся в файловых группах вне сети. Это позволяет успешно выполнить эти инструкции. Однако если файловая группа, находящаяся в режиме вне сети, содержит кучу или кластеризованный индекс целевой таблицы, инструкция SELECT не будет выполнена. Кроме того, любая инструкция INSERT, UPDATE или DELETE, изменяющая таблицу с любым индексом в файловой группе, находящихся в режиме вне сети, также не будет выполнена.  
  
Если база данных находится в состоянии RESTORING, выполнение большинства инструкций ALTER DATABASE закончится неудачей. Исключением является настройка параметров зеркального отображения базы данных. База данных может находиться в состоянии RESTORING во время выполнения операции восстановления или тогда, когда при операции восстановления базы данных или файла журнала происходит сбой из-за поврежденного файла резервной копии.  
  
Кэш планов для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] очищается при установке одного из следующих параметров.  
  
|||  
|-|-|  
|OFFLINE|READ_WRITE|  
|ONLINE|MODIFY FILEGROUP DEFAULT|  
|MODIFY_NAME|MODIFY FILEGROUP READ_WRITE|  
|COLLATE|MODIFY FILEGROUP READ_ONLY|  
|READ_ONLY|PAGE_VERIFY|  
  
Очистка кэша планов становится причиной перекомпиляции всех последующих планов выполнения и приводит к непредвиденному временному снижению производительности обработки запросов. Для каждого удаленного хранилища кэша в кэше планов журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит следующее информационное сообщение: "[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил %d экземпляров, записанных на диск хранилищ кэша для хранилища кэша "%s" (части кэша планов) в результате операций по обслуживанию или изменению конфигурации базы данных". Это сообщение добавляется в журнал каждые пять минут при сбросе кэша в течение этого интервала времени.  
  
Кроме того, кэш процедур сбрасывается в следующих случаях:  
  
- В базе данных включен параметр базы данных AUTO_CLOSE. Если отсутствуют ссылки соединений пользователя или базы данных, фоновая задача предпримет попытку закрыть и отключить базу данных автоматически.  
- Выполняется несколько запросов в базе данных с параметрами по умолчанию. Затем база данных уничтожается.  
- Моментальный снимок базы данных для базы данных-источника удален.  
- Успешное перестроение журнала транзакций базы данных.  
- Восстановление резервной копии базы данных.  
- Отсоединение базы данных.  
  
## <a name="changing-the-database-collation"></a>Изменение параметров сортировки в базе данных  
Прежде чем применить другие параметры сортировки к базе данных, убедитесь, что соблюдены следующие условия.  
  
- Вы являетесь единственным пользователем базы данных в настоящее время.  
- Ни один объект, привязанный к схеме, не зависит от параметров сортировки базы данных.  
  
  Если следующие объекты, зависящие от параметров сортировки базы данных, существуют в базе данных, выполнение инструкции ALTER DATABASE*database_name*COLLATE завершится ошибкой. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает сообщение об ошибке для каждого объекта, блокирующего действие ALTER:  
  
  - определяемые пользователем функции и представления, созданные с помощью предложения SCHEMABINDING;  
  
  - вычисляемые столбцы;  
  
  - ограничения CHECK;  
  
  - возвращающие табличное значение функции, которые возвращают таблицы с символьными столбцами, имеющими параметры сортировки, унаследованные из параметров сортировки базы данных по умолчанию.  
  
    Информация о зависимостях не привязанных к схеме сущностей обновляется автоматически при изменении параметров сортировки базы данных.  
  
При изменении параметров сортировки базы данных дубликаты любых системных имен для объектов базы данных не создаются. Если новые параметры сортировки вызывают повторяющиеся имена, следующие пространства имен могут вызвать сбой при изменении параметров сортировки базы данных:  
  
- имена объектов, такие как процедуры, таблицы, триггеры или представления;  
- имена схем;  
- участники, такие как группы, роли или пользователи;  
- имена скалярных типов, таких как системные и определяемые пользователем типы;  
- имена полнотекстовых каталогов;  
- имена столбцов или параметров в пределах объекта;  
- имена индексов в пределах таблицы.  
  
Повторяющиеся имена, полученные с помощью новых параметров сортировки, могут быть причиной сбоя операции изменения, а [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвратит сообщение об ошибке, указывающее пространство имен, в котором был найден дубликат.  
  
## <a name="viewing-database-information"></a>Просмотр сведений о базе данных  
Для возврата сведений о базах данных, файлах и файловых группах можно использовать представления каталогов, системные функции и системные хранимые процедуры.  
  
## <a name="permissions"></a>Разрешения  
Необходимо разрешение ALTER на базу данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-the-name-of-a-database"></a>A. Изменение имени базы данных  
В следующем примере имя базы данных `AdventureWorks2012` изменяется на `Northwind`.  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
Modify Name = Northwind ;  
GO  
```  
  
### <a name="b-changing-the-collation-of-a-database"></a>Б. Изменение параметров сортировки базы данных  
В следующем примере создается база данных `testdb`, параметры сортировки которой имеют значение `SQL_Latin1_General_CP1_CI_A`. Затем имя базы данных `testdb` изменяется на `COLLATE French_CI_AI`.  
  
**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```sql  
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
- [CREATE DATABASE](../../t-sql/statements/create-database-transact-sql.md?&tabs=sqlserver)   
- [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)   
- [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)   
- [SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
- [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
- [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
- [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
- [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
- [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
- [sys.database_mirroring_witnesses](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
- [sys.data_spaces](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
- [sys.filegroups](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
- [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
- [Системные базы данных](../../relational-databases/databases/system-databases.md)  
  
# <a name="sql-db-logical-servertabsqldbls"></a>[Логический сервер базы данных SQL](#tab/sqldbls)

## <a name="overview"></a>Обзор

В базе данных SQL Azure эта инструкция предназначена для изменения базы данных на логическом сервере. Используйте эту инструкцию, чтобы изменить имя базы данных, изменить выпуск и цель обслуживания базы данных, присоединить или удалить базы данных из эластичного пула, настроить параметры базы данных, добавить или удалить дополнительные базы данных для георепликации или настроить уровень совместимости базы данных.

Так как синтаксис ALTER DATABASE имеет значительную длину, мы разделили его описание на несколько разделов.  

ALTER DATABASE  
В этом разделе описывается синтаксис для изменения имени и параметров сортировки базы данных, а также содержится дополнительная информация.  
  
[Параметры ALTER DATABASE SET](../../t-sql/statements/alter-database-transact-sql-set-options.md?&tabs=sqldbls)  
Синтаксис для изменения атрибутов базы данных с помощью параметров SET команды ALTER DATABASE, а также дополнительная информация об этом.  
  
[Уровень совместимости ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md?&tabs=sqldbls)  
Синтаксис параметров SET инструкции ALTER DATABASE, имеющих отношение к уровням совместимости базы данных, и дополнительная информация об этом.  

## <a name="syntax"></a>Синтаксис 

```  
-- Azure SQL Database Syntax  
ALTER DATABASE { database_name | CURRENT }  
{  
    MODIFY NAME = new_database_name  
  | MODIFY ( <edition_options> [, ... n] ) 
  | SET { <option_spec> [ ,... n ] WITH <termination>} 
  | SET COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 }   
  | ADD SECONDARY ON SERVER <partner_server_name>  
    [WITH ( <add-secondary-option>::= [, ... n] ) ]  
  | REMOVE SECONDARY ON SERVER <partner_server_name>  
  | FAILOVER  
  | FORCE_FAILOVER_ALLOW_DATA_LOSS  
}  
[;] 

<edition_options> ::= 
{  

  MAXSIZE = { 100 MB | 250 MB | 500 MB | 1 … 1024 … 4096 GB }  
  | EDITION = { 'basic' | 'standard' | 'premium' | 'GeneralPurpose' | 'BusinessCritical'} 
  | SERVICE_OBJECTIVE = 
       {  <service-objective>
       | { ELASTIC_POOL (name = <elastic_pool_name>) } 
       } 
}  

<add-secondary-option> ::=  
   {  
      ALLOW_CONNECTIONS = { ALL | NO }  
     | SERVICE_OBJECTIVE = 
       {  <service-objective> 
       | { ELASTIC_POOL ( name = <elastic_pool_name>) } 
       } 
   }  

<service-objective> ::=  { 'S0' | 'S1' | 'S2' | 'S3'| 'S4'| 'S6'| 'S7'| 'S9'| 'S12' |
       | 'P1' | 'P2' | 'P4'| 'P6' | 'P11'  | 'P15'
      | 'GP_GEN4_1' | 'GP_GEN4_2' | 'GP_GEN4_4' | 'GP_GEN4_8' | 'GP_GEN4_16' | 'GP_GEN4_24' |
      | 'BC_GEN4_1' | 'BC_GEN4_2' | 'BC_GEN4_4' | 'BC_GEN4_8' | 'BC_GEN4_16' | 'BC_GEN4_24' |
      | 'GP_GEN5_2' | 'GP_GEN5_4' | 'GP_GEN5_8' | 'GP_GEN5_16' | 'GP_GEN5_24' | 'GP_GEN5_32' | 'GP_GEN5_48' | 'GP_GEN5_80' |
      | 'BC_GEN5_2' | 'BC_GEN5_4' | 'BC_GEN5_8' | 'BC_GEN5_16' | 'BC_GEN5_24' | 'BC_GEN5_32' | 'BC_GEN5_48' | 'BC_GEN5_80' |
      }

<option_spec> ::= 
{  
    <auto_option> 
  | <change_tracking_option> 
  | <cursor_option> 
  | <db_encryption_option>  
  | <db_update_option> 
  | <db_user_access_option> 
  | <delayed_durability_option>  
  | <parameterization_option>  
  | <query_store_options>  
  | <snapshot_option>  
  | <sql_option> 
  | <target_recovery_time_option> 
  | <termination>  
  | <temporal_history_retention>  
}  
```
  
## <a name="arguments"></a>Аргументы  

*database_name*  

Имя изменяемой базы данных.  
  
CURRENT  

Определяет, что должна быть изменена текущая используемая база данных.  
  
MODIFY NAME **=***new_database_name*  

Присваивает базе данных имя, указанное в аргументе *новое_имя_базы_данных*. В следующем примере имя базы данных `db1` изменяется на `db2`.   

```sql  
ALTER DATABASE db1  
    MODIFY Name = db2 ;  
```    

MODIFY (EDITION **=** ['basic' | 'standard' | 'premium' |'GeneralPurpose' | 'BusinessCritical'])    

Изменяет уровень службы базы данных. Поддержка "premiumrs" была упразднена. При возникновении вопросов пишите на следующий адрес premium-rs@microsoft.com.

В следующем примере выпуск изменяется на `premium`.
  
```sql  
ALTER DATABASE current 
    MODIFY (EDITION = 'premium');
``` 

Смена значения параметра EDITION завершается неудачей, если для свойства MAXSIZE базы данных задано значение вне допустимого диапазона, поддерживаемого этим выпуском.  

MODIFY (MAXSIZE **=** [100 MB | 500 MB | 1 | 1024…4096] GB)  

Указывает максимальный размер базы данных. Максимальный размер должен соответствовать допустимому набору значений для свойства EDITION базы данных. Смена максимального размера базы данных может потребовать также смены значения EDITION базы данных. В следующей таблице приведены поддерживаемые значения MAXSIZE и значения, заданные по умолчанию (D) для уровней служб [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
**Модель на основе DTU**

|**MAXSIZE**|**Basic**|**S0–S2**|**S3–S12**|**P1–P6**|**P11–P15**|  
|-----------------|---------------|------------------|-----------------|-----------------|-----------------|-----------------|  
|100 МБ|√|√|√|√|√|  
|250 МБ|√|√|√|√|√|  
|500 МБ|√|√|√|√|√|  
|1 ГБ|√|√|√|√|√|  
|2 ГБ|√ (D)|√|√|√|√|  
|5 ГБ|Недоступно|√|√|√|√|  
|10 ГБ|Недоступно|√|√|√|√|  
|20 ГБ|Недоступно|√|√|√|√|  
|30 ГБ|Недоступно|√|√|√|√|  
|40 ГБ|Недоступно|√|√|√|√|  
|50 ГБ|Недоступно|√|√|√|√|  
|100 ГБ|Недоступно|√|√|√|√|  
|150 ГБ|Недоступно|√|√|√|√|  
|200 ГБ|Недоступно|√|√|√|√|  
|250 ГБ|Недоступно|√ (D)|√ (D)|√|√|  
|300 ГБ|Недоступно|√|√|√|√|  
|400 ГБ|Недоступно|√|√|√|√|  
|500 ГБ|Недоступно|√|√|√ (D)|√|  
|750 ГБ|Недоступно|√|√|√|√|  
|1024 ГБ|Недоступно|√|√|√|√ (D)|  
|От 1024 до 4096 ГБ с шагом приращения 256 ГБ *|Недоступно|Недоступно|Недоступно|Недоступно|√|√|  
  
\* P11 и P15 позволяют задавать параметру MAXSIZE значение до 4 ТБ, при этом размер по умолчанию — 1024 ГБ.  P11 и P15 могут использовать до 4 ТБ включенного объема хранилища без дополнительной платы. На уровне Premium использование MAXSIZE со значением более 1 ТБ сейчас доступно в следующих регионах: восточная часть США 2, западная часть США, Виргиния (для обслуживания государственных организаций США), Западная Европа, Центральная Германия, Юго-Восточная Азия, Восточная Япония, Восточная Австралия, Центральная Канада и Восточная Канада. Дополнительные сведения об ограничениях по ресурсам для модели на основе DTU см. в разделе [Пределы для ресурсов на основе DTU](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits).  

Значение MAXSIZE для модели на основе DTU, если оно задано, должно быть одним из допустимых значений, приведенных в таблице выше для указанного уровня служб.
 
**Модель на основе виртуальных ядер**

**Уровень обслуживания общего назначения — вычислительная платформа поколения 4**
|MAXSIZE|GP_Gen4_1|GP_Gen4_2|GP_Gen4_4|GP_Gen4_8|GP_Gen4_16|GP4_24|
|:--- | --: |--: |--: |--: |--: |--:|
|Максимальный размер данных (ГБ)|1024|1024|1536|3072|4096|4096|

**Уровень обслуживания общего назначения — вычислительная платформа поколения 5**
|MAXSIZE|GP_Gen5_2|GP_Gen5_4|GP_Gen5_8|GP_Gen5_16|GP_Gen5_24|GP_Gen5_32|GP_Gen5_48|GP_Gen5_80|
|:----- | ------: |-------: |-------: |--------: |--------: |---------:|--------: |---------: |
|Максимальный размер данных (ГБ)|1024|1024|1536|3072|4096|4096|4096|4096|


**Уровень обслуживания "Критически важный для бизнеса" — вычислительная платформа поколения 4**
|Уровень производительности|BC_Gen4_1|BC_Gen4_2|BC_Gen4_4|BC_Gen4_8|BC_Gen4_16|
|:--- | --: |--: |--: |--: |--: |--: |
|Максимальный размер данных (ГБ)|1024|1024|1024|1024|1024|1024|

**Уровень обслуживания "Критически важный для бизнеса" — вычислительная платформа поколения 5**
|MAXSIZE|BC_Gen5_2|BC_Gen5_4|BC_Gen5_8|BC_Gen5_16|BC_Gen5_24|BC_Gen5_32|BC_Gen5_48|BC_Gen5_80|
|:----- | ------: |-------: |-------: |--------: |--------: |---------:|--------: |---------: |
|Максимальный размер данных (ГБ)|1024|1024|1024|1024|2048|4096|4096|4096|

Если при использовании модели виртуальных ядер значение `MAXSIZE` не задано, используется значение по умолчанию, равное 32 ГБ. Дополнительные сведения об ограничениях по ресурсам для модели на основе виртуальных ядер см. в разделе [Пределы для ресурсов на основе виртуальных ядер](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits).
  
Следующие правила применяются к аргументам MAXSIZE и EDITION:  
  
- Если параметр EDITION указан, а параметр MAXSIZE — нет, то в качестве выпуска будет использоваться значение по умолчанию. Например, если параметру EDITION задано значение Standard, а параметр MAXSIZE не задан, то параметру MAXSIZE будет автоматически присвоено значение 500 МБ.  
  
- Если не указаны значения ни для MAXSIZE, ни для EDITION, то параметру EDITION задается значение Standard (S0), а параметру MAXSIZE — 250 ГБ.  

MODIFY (SERVICE_OBJECTIVE = \<service-objective>)  

Определяет уровень производительности. В следующем примере изменяется цель службы базы данных уровня Premium на `P6`:
 
```sql  
ALTER DATABASE current 
    MODIFY (SERVICE_OBJECTIVE = 'P6');
```  

Определяет уровень производительности. Доступные значения для целевого уровня обслуживания: `S0`, `S1`, `S2`, `S3`, `S4`, `S6`, `S7`, `S9`, `S12`, `P1`, `P2`, `P4`, `P6`, `P11`, `P15`, `GP_GEN4_1`, `GP_GEN4_2`, `GP_GEN4_4`, `GP_GEN4_8`, `GP_GEN4_16`, `GP_GEN4_24`, `BC_GEN4_1` `BC_GEN4_2` `BC_GEN4_4` `BC_GEN4_8` `BC_GEN4_16`, `BC_GEN4_24`, `GP_Gen5_2`, `GP_Gen5_4`, `GP_Gen5_8`, `GP_Gen5_16`, `GP_Gen5_24`, `GP_Gen5_32`, `GP_Gen5_48`, `GP_Gen5_80`, `BC_Gen5_2`, `BC_Gen5_4`, `BC_Gen5_8`, `BC_Gen5_16`, `BC_Gen5_24`, `BC_Gen5_32`, `BC_Gen5_48`, `BC_Gen5_80`.  

Описания целей служб и дополнительные сведения о сочетаниях размеров, выпусков и целей служб см. в разделах [Уровни служб и уровни производительности баз данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/), [Пределы для ресурсов на основе DTU](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits) и [Пределы для ресурсов на основе виртуальных ядер](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits). Поддержка целей служб PRS была удалена. При возникновении вопросов пишите на следующий адрес premium-rs@microsoft.com. 
  
MODIFY (SERVICE_OBJECTIVE = ELASTIC\_POOL (name = \<elastic_pool_name>)  

Чтобы добавить существующую базу данных в эластичный пул, задайте параметру SERVICE_OBJECTIVE базы данных значение ELASTIC_POOL и укажите имя эластичного пула. Этот параметр также служит для изменения базы данных в другом эластичном пуле на том же сервере. Дополнительные сведения см. в разделе [Создание эластичного пула баз данных SQL и управление им](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/). Чтобы удалить базу данных из эластичного пула, используйте инструкцию ALTER DATABASE, чтобы задать в качестве значения SERVICE_OBJECTIVE один уровень производительности базы данных.  

ADD SECONDARY ON SERVER \<partner_server_name>  

Создает базу данных-получатель с географической репликаций с тем же именем на сервере-участнике, преобразуя локальную базу данных в базу данных-источник с георепликацией, и начинает асинхронную репликацию данных с источника в новую базу данных-получатель. Команда завершается ошибкой, если на сервере-получателе уже существует база данных с таким именем. Команда выполняется в базе данных master на сервере с локальной базой данных, которая становится базой данных-источником.  
  
WITH ALLOW_CONNECTIONS { **ALL** | NO }  

Если параметр ALLOW_CONNECTIONS не указан, ему по умолчанию присваивается значение ALL. Если указано значение ALL, это база данных только для чтения, позволяющая подключаться всем именам входа с соответствующими разрешениями.  
  
WITH SERVICE_OBJECTIVE { `S0`, `S1`, `S2`, `S3`, `S4`, `S6`, `S7`, `S9`, `S12`, `P1`, `P2`, `P4`, `P6`, `P11`, `P15`, `GP_GEN4_1`, `GP_GEN4_2`, `GP_GEN4_4`, `GP_GEN4_8`, `GP_GEN4_16`, `GP_GEN4_24`, `BC_GEN4_1` `BC_GEN4_2` `BC_GEN4_4` `BC_GEN4_8` `BC_GEN4_16`, `BC_GEN4_24`, `GP_Gen5_2`, `GP_Gen5_4`, `GP_Gen5_8`, `GP_Gen5_16`, `GP_Gen5_24`, `GP_Gen5_32`, `GP_Gen5_48`, `GP_Gen5_80`, `BC_Gen5_2`, `BC_Gen5_4`, `BC_Gen5_8`, `BC_Gen5_16`, `BC_Gen5_24`, `BC_Gen5_32`, `BC_Gen5_48`, `BC_Gen5_80` }  

Если параметр SERVICE_OBJECTIVE не указан, база данных-получатель создается на том же уровне службы, что и база данных-источник. Если параметр SERVICE_OBJECTIVE указан, база данных-получатель создается на указанном уровне. Этот параметр поддерживает создание геореплицированных объектов-получателей с менее дорогими уровнями обслуживания. Указанный параметр SERVICE_OBJECTIVE должен находиться в том же выпуске, что и источник. Например, если используется выпуск Premium, параметр S0 указать невозможно.  
  
ELASTIC_POOL (name = \<имя_эластичного_пула>)  

Если параметр ELASTIC_POOL не указан, база данных-получатель не создается в эластичном пуле. Если параметр ELASTIC_POOL указан, база данных-получатель создается в указанном пуле.  
  
> [!IMPORTANT]  
>  Пользователь, выполняющий команду ADD SECONDARY, должен иметь права DBManager на сервере-источнике, членство db_owner в локальной базе данных и права DBManager на сервере-получателе.  
  
REMOVE SECONDARY ON SERVER  \<partner_server_name>  

Удаляет указанную базу данных-получатель с географической репликацией на указанном сервере. Команда выполняется в базе данных master на сервере с локальной базой данных-источником.  
  
> [!IMPORTANT]  
>  Пользователь, выполняющий команду REMOVE SECONDARY, должен иметь права DBManager на сервере-источнике.  
  
FAILOVER  

Повышает уровень базы данных-получателя в отношении с георепликацией, где выполняется команда, до базы данных-источника и снижает уровень текущей базы данных-источника до новой базы данных-получателя. В рамках этого процесса режим георепликации временно переключается с асинхронного на синхронный. Во время процесса отработки отказа выполняются следующий действия.  
  
1.  База данных-источник перестает принимать новые транзакции.  
  
2.  Все невыполненные транзакции переходят в базу данных-получатель.  
  
3.  База данных-получатель становится базой данных-источником и начинает асинхронную георепликацию со старым источником и новым получателем.  
  
Эта последовательность гарантирует отсутствие потери данных. Период, в течение которого обе базы данных недоступны, составляет примерно 0–25 секунд во время переключения ролей. Вся операция не должна занимать более одной минуты. Если во время выполнения этой команды база данных-источник недоступна, команда выводит сообщение об ошибке, информирующее о недоступности базы данных-источника. Если процесс отработки отказа не завершается и зависает, можно использовать команду принудительной отработки отказа и принять потерю данных, а затем, если необходимо восстановить потерянные данные, обратиться в devops (CSS).  
  
> [!IMPORTANT]  
>  Пользователь, выполняющий команду FAILOVER, должен иметь права DBManager на сервере-источнике и сервере-получателе.  
  
FORCE_FAILOVER_ALLOW_DATA_LOSS  

Повышает уровень базы данных-получателя в отношении с георепликацией, где выполняется команда, до базы данных-источника и снижает уровень текущей базы данных-источника до новой базы данных-получателя. Эту команду следует использовать только в том случае, если текущая база данных-источник больше не доступна. Она предназначена для аварийного восстановления, только если очень важно восстановить доступность и допускается потеря некоторых данных.  
  
Во время принудительной отработки отказа выполняются следующие действия.  
  
1. Указанная база данных-получателя немедленно становится базой данных-источником и начинает принимать новые транзакции.  
  
2. Когда исходная база данных-источник может повторно установить соединение с новой базой данных-источником, в исходной базе данных-источнике выполняется добавочное резервное копирование и она становится новой базой данных-получателем.  
  
3. Чтобы восстановить данные из этой добавочной резервной копии в старой базе данных-источнике, пользователь обращается в devops/CSS.  
  
4. Если имеются дополнительные базы данных-получатели, они автоматически настраиваются в качестве баз данных-получателей новой базы данных-источника. Этот процесс является асинхронным и до момента его завершения может возникнуть задержка. До завершения повторной настройки базы данных-получатели остаются базами данных-получателями старой базы данных-источника.  
  
> [!IMPORTANT]  
>  Пользователь, выполняющий команду FORCE_FAILOVER_ALLOW_DATA_LOSS, должен иметь права DBManager на сервере-источнике и сервере-получателе.  
  
## <a name="remarks"></a>Remarks  

Чтобы удалить базу данных, используйте инструкцию [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md).  
Чтобы уменьшить размер базы данных, используйте предложение [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
Инструкция ALTER DATABASE должна выполняться в режиме автоматической фиксации (режим управления транзакциями по умолчанию) и не разрешена в явной или неявной транзакции.  
  
Очистка кэша планов становится причиной перекомпиляции всех последующих планов выполнения и приводит к непредвиденному временному снижению производительности обработки запросов. Для каждого удаленного хранилища кэша в кэше планов журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит следующее информационное сообщение: "[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил %d экземпляров, записанных на диск хранилищ кэша для хранилища кэша "%s" (части кэша планов) в результате операций по обслуживанию или изменению конфигурации базы данных". Это сообщение добавляется в журнал каждые пять минут при сбросе кэша в течение этого интервала времени.  
  
Кроме того, кэш процедур освобождается при выполнении нескольких запросов к базе данных, для которой настроены параметры по умолчанию. Затем база данных уничтожается.    
  
## <a name="viewing-database-information"></a>Просмотр сведений о базе данных  

Для возврата сведений о базах данных, файлах и файловых группах можно использовать представления каталогов, системные функции и системные хранимые процедуры.  
  
## <a name="permissions"></a>Разрешения  

Изменять базу данных могут только имя входа субъект серверного уровня (созданное в процессе провизионирования) или члены роли базы данных `dbmanager`.  
  
> [!IMPORTANT]  
>  Владелец базы данных не может изменять базу данных, если он не является членом роли `dbmanager`.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-check-the-edition-options-and-change-them"></a>A. Проверка параметров выпуска и их изменение

```sql
SELECT Edition = DATABASEPROPERTYEX('db1', 'EDITION'),
        ServiceObjective = DATABASEPROPERTYEX('db1', 'ServiceObjective'),
        MaxSizeInBytes =  DATABASEPROPERTYEX('db1', 'MaxSizeInBytes');

ALTER DATABASE [db1] MODIFY (EDITION = 'Premium', MAXSIZE = 1024 GB, SERVICE_OBJECTIVE = 'P15');
```

### <a name="b-moving-a-database-to-a-different-elastic-pool"></a>Б. Перемещение базы данных в другой пул эластичных БД  

Существующая база данных перемещается в пул с именем pool1:  
  
```sql  
ALTER DATABASE db1   
MODIFY ( SERVICE_OBJECTIVE = ELASTIC_POOL ( name = pool1 ) ) ;  
```  
  
### <a name="c-add-a-geo-replication-secondary"></a>В. Добавление базы данных-получателя с георепликацией  

Создает доступную для чтения базу данных-получатель db1 на сервере `secondaryserver` для базы данных db1 на локальном сервере.  
  
```sql  
ALTER DATABASE db1   
ADD SECONDARY ON SERVER secondaryserver   
WITH ( ALLOW_CONNECTIONS = ALL )  
```  
  
### <a name="d-remove-a-geo-replication-secondary"></a>Г. Удаление базы данных-получается с георепликацией  
 
Удаляет базу данных-получателя db1 на сервере `secondaryserver`.  
  
```sql  
ALTER DATABASE db1   
REMOVE SECONDARY ON SERVER testsecondaryserver   
```  
  
### <a name="e-failover-to-a-geo-replication-secondary"></a>Д. Переход на базу данных-получатель с георепликацией  

Повышает уровень базы данных-получателя db1 на сервере `secondaryserver` до новой базы данных-источника при выполнении на сервере `secondaryserver`.  
  
```sql  
ALTER DATABASE db1 FAILOVER  
```  
  
## <a name="see-also"></a>См. также раздел
  
[CREATE DATABASE — база данных SQL Azure](../../t-sql/statements/create-database-transact-sql.md?&tabs=sqldbls)   
 [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)   
 [SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
 [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.database_mirroring_witnesses](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [sys.data_spaces](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [sys.filegroups](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Системные базы данных](../../relational-databases/databases/system-databases.md)  

# <a name="sql-db-managed-instancetabsqldbmi"></a>[Управляемый экземпляр Базы данных SQL](#tab/sqldbmi)

## <a name="overview"></a>Обзор

В управляемом экземпляре Базы данных SQL Azure эта инструкция используется для настройки параметров базы данных.

Так как синтаксис ALTER DATABASE имеет значительную длину, мы разделили его описание на несколько разделов.  

ALTER DATABASE  
Этот раздел содержит синтаксис для настройки параметров файлов и файловых групп, настройки параметров базы данных и установки уровня совместимости базы данных, а также дополнительную информацию.  
  
[Параметры инструкции ALTER DATABASE для файлов и файловых групп](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md?&tabs=sqldbmi). Синтаксис для добавления или удаления файлов и файловых групп в базе данных, для изменения атрибутов файлов и файловых групп, а также дополнительная информация об этом.  
  
[Параметры ALTER DATABASE SET](../../t-sql/statements/alter-database-transact-sql-set-options.md?&tabs=sqldbmi). Синтаксис для изменения атрибутов базы данных с помощью параметров SET команды ALTER DATABASE, а также дополнительная информацию об этом.  
  
[Уровень совместимости ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md?&tabs=sqldbmi). Синтаксис параметров SET команды ALTER DATABASE, имеющих отношение к уровням совместимости базы данных, а также дополнительная информация об этом.  

## <a name="syntax"></a>Синтаксис 

```  
-- Azure SQL Database Syntax  
ALTER DATABASE { database_name | CURRENT }  
{  
    <file_and_filegroup_options>  
  | SET <option_spec> [ ,...n ]  
  | SET COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 }   
}  
[;] 

<file_and_filegroup_options>::=  
  <add_or_modify_files>::=  
  <filespec>::=   
  <add_or_modify_filegroups>::=  
  <filegroup_updatability_option>::=  

<option_spec> ::= 
{  
    <auto_option> 
  | <change_tracking_option> 
  | <cursor_option> 
  | <db_encryption_option>  
  | <db_update_option> 
  | <db_user_access_option> 
  | <delayed_durability_option>  
  | <parameterization_option>  
  | <query_store_options>  
  | <snapshot_option>  
  | <sql_option> 
  | <target_recovery_time_option> 
  | <temporal_history_retention>  
}  
```
  
## <a name="arguments"></a>Аргументы  

*database_name*  

Имя изменяемой базы данных.  
  
CURRENT  

Определяет, что должна быть изменена текущая используемая база данных.  
  
## <a name="remarks"></a>Remarks  

Чтобы удалить базу данных, используйте инструкцию [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md).  
Чтобы уменьшить размер базы данных, используйте предложение [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
Инструкция ALTER DATABASE должна выполняться в режиме автоматической фиксации (режим управления транзакциями по умолчанию) и не разрешена в явной или неявной транзакции.  
  
Очистка кэша планов становится причиной перекомпиляции всех последующих планов выполнения и приводит к непредвиденному временному снижению производительности обработки запросов. Для каждого удаленного хранилища кэша в кэше планов журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит следующее информационное сообщение: "[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил %d экземпляров, записанных на диск хранилищ кэша для хранилища кэша "%s" (части кэша планов) в результате операций по обслуживанию или изменению конфигурации базы данных". Это сообщение добавляется в журнал каждые пять минут при сбросе кэша в течение этого интервала времени.  
  
Кроме того, кэш процедур освобождается при выполнении нескольких запросов к базе данных, для которой настроены параметры по умолчанию. Затем база данных уничтожается.    
  
## <a name="viewing-database-information"></a>Просмотр сведений о базе данных  

Для возврата сведений о базах данных, файлах и файловых группах можно использовать представления каталогов, системные функции и системные хранимые процедуры.  
  
## <a name="permissions"></a>Разрешения  

Изменять базу данных могут только имя входа субъект серверного уровня (созданное в процессе провизионирования) или члены роли базы данных `dbmanager`.  
  
> [!IMPORTANT]  
>  Владелец базы данных не может изменять базу данных, если он не является членом роли `dbmanager`.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-what-examples-here"></a>A. Какие здесь могут быть примеры??

```sql
```
  
## <a name="see-also"></a>См. также раздел
  
[CREATE DATABASE — база данных SQL Azure](../../t-sql/statements/create-database-transact-sql.md?&tabs=sqldbmi)   
[DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)   
[DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)   
[SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
[EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
[sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
[sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
[sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
[sys.database_mirroring_witnesses](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)  [sys.data_spaces](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
[sys.filegroups](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
[sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
[Системные базы данных](../../relational-databases/databases/system-databases.md)  

# <a name="sql-data-warehousetabsqldw"></a>[Хранилище данных SQL](#tab/sqldw)

## <a name="overview"></a>Обзор

Изменяет имя, максимальный размер или цель обслуживания для базы данных.

## <a name="syntax"></a>Синтаксис  
  
```  
ALTER DATABASE database_name  

  MODIFY NAME = new_database_name  
| MODIFY ( <edition_option> [, ... n] )  
  
<edition_option> ::=   
      MAXSIZE = { 
            250 | 500 | 750 | 1024 | 5120 | 10240 | 20480 
          | 30720 | 40960 | 51200 | 61440 | 71680 | 81920 
          | 92160 | 102400 | 153600 | 204800 | 245760 
      } GB  
      | SERVICE_OBJECTIVE = { 
            'DW100' | 'DW200' | 'DW300' | 'DW400' | 'DW500' 
          | 'DW600' | 'DW1000' | 'DW1200' | 'DW1500' | 'DW2000' 
          | 'DW3000' | 'DW6000' | 'DW1000c' | 'DW1500c' | 'DW2000c' 
          | 'DW2500c' | 'DW3000c' | 'DW5000c' | 'DW6000c' | 'DW7500c' 
          | 'DW10000c' | 'DW15000c' | 'DW30000c'
      }  
```  
  
## <a name="arguments"></a>Аргументы  
*database_name*  
Задает имя изменяемой базы данных.  

MODIFY NAME = *новое_имя_базы_данных*  
Присваивает базе данных имя, указанное в аргументе *новое_имя_базы_данных*.  
  
MAXSIZE  
Значение по умолчанию — 245 760 ГБ (240 ТБ).  

**Область применения:** уровень производительности "Оптимизация под гибкость"

Максимально допустимый размер базы данных. Размер базы данных не может превышать MAXSIZE. 

**Область применения:** уровень производительности "Оптимизация под вычисление"

Максимально допустимый размер данных rowstore в базе данных. Размер данных, хранящихся в таблицах rowstore, разностном хранилище индекса columnstore или некластеризованном индексе на базе кластеризованного индекса columnstore, не может превышать MAXSIZE.  Данные, сжатые в формат columnstore, не имеют ограничений на размер и не ограничивается значением MAXSIZE. 
  
SERVICE_OBJECTIVE  
Определяет уровень производительности. Дополнительные сведения о целевых уровнях служб для [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] см. на странице [Уровни производительности](https://azure.microsoft.com/documentation/articles/performance-tiers/).  
  
## <a name="permissions"></a>Разрешения  
Требуются следующие разрешения:  
  
- имя входа субъекта серверного уровня, созданное процессом подготовки, или  
- член роли базы данных `dbmanager`.  
  
Владелец базы данных не может изменять базу данных, если он не является членом роли `dbmanager`.  
  
## <a name="general-remarks"></a>Общие замечания  
Текущая база данных должна отличаться от изменяемой, поэтому **инструкцию ALTER следует выполнять при подключении к базе данных master**.  
  
Для хранилища данных SQL задано значение COMPATIBILITY_LEVEL 130, изменить которое невозможно. Дополнительные сведения: [Улучшение производительности запросов с уровнем совместимости 130 в базе данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/).
  
Чтобы уменьшить размер базы данных, используйте предложение [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
Для выполнения инструкции ALTER DATABASE база данных должна находиться в сети и не может быть в приостановленном состоянии.  
  
Инструкция ALTER DATABASE должна выполняться в режиме автофиксации, который является режимом управления транзакциями по умолчанию. Он задается в параметрах подключения.  
  
Инструкция ALTER DATABASE не может входить в определенную пользователем транзакцию.

Изменить параметры сортировки базы данных невозможно.  
  
## <a name="examples"></a>Примеры  
Перед выполнением этих примеров убедитесь в том, что изменяемая база данных не является текущей базой данных. Текущая база данных должна отличаться от изменяемой, поэтому **инструкцию ALTER следует выполнять при подключении к базе данных master**.  

### <a name="a-change-the-name-of-the-database"></a>A. Изменение имени базы данных  

```sql  
ALTER DATABASE AdventureWorks2012  
MODIFY NAME = Northwind;  
```  
  
### <a name="b-change-max-size-for-the-database"></a>Б. Изменение максимального размера базы данных  
  
```sql  
ALTER DATABASE dw1 MODIFY ( MAXSIZE=10240 GB );  
```  
  
### <a name="c-change-the-performance-level"></a>В. Изменение уровня производительности  
  
```sql  
ALTER DATABASE dw1 MODIFY ( SERVICE_OBJECTIVE= 'DW1200' );  
```  
  
### <a name="d-change-the-max-size-and-the-performance-level"></a>Г. Изменение максимального размера и уровня производительности  
  
```sql  
ALTER DATABASE dw1 MODIFY ( MAXSIZE=10240 GB, SERVICE_OBJECTIVE= 'DW1200' );  
```  
  
## <a name="see-also"></a>См. также:  
[CREATE DATABASE (хранилище данных SQL Azure)](../../t-sql/statements/create-database-transact-sql.md?&tabs=sqldw.md)
[Список разделов справки по хранилищу данных SQL](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-overview-reference/)  
  

# <a name="sql-parallel-data-warehousetabsqlpdw"></a>[SQL Parallel Data Warehouse](#tab/sqlpdw)

## <a name="overview"></a>Обзор

Изменяет параметры максимального размера базы данных для реплицированных таблиц, распределенных таблиц и журнала транзакций в параллельном хранилище данных. С помощью этой инструкции можно управлять выделением дискового пространства для базы данных по мере изменения ее размера. В разделе также описан синтаксис, связанный с установкой параметров базы данных в Parallel Data Warehouse.

## <a name="syntax"></a>Синтаксис  
  
```  
-- Parallel Data Warehouse  
ALTER DATABASE database_name    
    SET ( <set_database_options>   | <db_encryption_option> )  
[;]  
  
<set_database_options> ::=   
{  
    AUTOGROW = { ON | OFF }  
    | REPLICATED_SIZE = size [GB]  
    | DISTRIBUTED_SIZE = size [GB]  
    | LOG_SIZE = size [GB]
    | SET AUTO_CREATE_STATISTICS { ON | OFF }
    | SET AUTO_UPDATE_STATISTICS { ON | OFF } 
    | SET AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }
}  
  
<db_encryption_option> ::=  
    ENCRYPTION { ON | OFF }  
```  
  
## <a name="arguments"></a>Аргументы  
*database_name*  
Имя изменяемой базы данных. Чтобы получить список баз данных на устройстве, используйте представление [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
AUTOGROW = { ON | OFF }  
Изменяет значение параметра AUTOGROW. Если параметр AUTOGROW имеет значение ON, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] автоматически увеличивает пространство, выделенное для реплицированных таблиц, распределенных таблиц и журнала транзакций, в соответствии с растущими требованиями к хранилищу. Если параметр AUTOGROW имеет значение OFF, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] возвращает ошибку в случае, если размер пространства, занимаемого реплицированными таблицами, распределенными таблицами или журналом транзакций, превышает заданное максимальное значение.  
  
REPLICATED_SIZE = *размер* [ГБ]  
Задает для вычислительного узла новый максимальный размер для хранения всех реплицированных таблиц изменяемой базы данных в гигабайтах. Если вы планируете пространство для хранения данных на устройстве, значение REPLICATED_SIZE необходимо умножить на количество вычислительных узлов на устройстве.  
  
DISTRIBUTED_SIZE = *размер* [ГБ]  
Задает для базы данных новый максимальный размер для хранения всех распределенных таблиц изменяемой базы данных в гигабайтах. Этот размер распределяется по всем вычислительным узлам на устройстве.  
  
LOG_SIZE = *размер* [ГБ]  
Задает для базы данных новый максимальный размер для хранения всех журналов транзакций изменяемой базы данных в гигабайтах. Этот размер распределяется по всем вычислительным узлам на устройстве.  
  
ENCRYPTION { ON | OFF }  
Включает шифрование базы данных (ON) или отключает его (OFF). Шифрование можно настроить для [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] только в том случае, если [sp_pdw_database_encryption](http://msdn.microsoft.com/5011bb7b-1793-4b2b-bd9c-d4a8c8626b6e) имеет значение **1**. Перед настройкой прозрачного шифрования данных необходимо создать ключ шифрования базы данных. Дополнительные сведения о шифровании баз данных см. в статье [Прозрачное шифрование данных (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md).  

SET AUTO_CREATE_STATISTICS { ON | OFF } Если параметр AUTO_CREATE_STATISTICS (автоматическое создание статистики) включен, оптимизатор запросов при необходимости создает статистику по отдельным столбцам в предикате запроса, чтобы улучшить оценку кратности для плана запроса. Такая статистика по отдельным столбцам создается для столбцов, у которых отсутствует гистограмма в существующем объекте статистики.

Параметр включен по умолчанию для новых баз данных, созданных после обновления до AU7. Параметр отключен по умолчанию для баз данных, созданных до обновления. 

Дополнительные сведения о статистике см. в статье [Статистика](/sql/relational-databases/statistics/statistics).

SET AUTO_UPDATE_STATISTICS { ON | OFF } Если параметр AUTO_UPDATE_STATISTICS (автоматическое обновление статистики) включен, оптимизатор запросов определяет, устарела ли статистика, и при необходимости обновляет ее, если она используется в запросе. Статистика становится устаревшей, если операции вставки, обновления, удаления или слияния изменяют распределение данных в таблице или индексированном представлении. Оптимизатор запросов определяет, когда статистика может оказаться устаревшей, подсчитывая операции изменения данных с момента последнего обновления статистики и сравнивая количество изменений с пороговым значением. Пороговое значение основано на количестве строк в таблице или индексированном представлении.

Параметр включен по умолчанию для новых баз данных, созданных после обновления до AU7. Параметр отключен по умолчанию для баз данных, созданных до обновления. 

Дополнительные сведения о статистике см. в статье [Статистика](/sql/relational-databases/statistics/statistics).


SET AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF } Параметр AUTO_UPDATE_STATISTICS_ASYNC, который управляет асинхронным обновлением статистики, определяет, какой режим обновления статистики использует оптимизатор запросов — синхронный или асинхронный. Параметр AUTO_UPDATE_STATISTICS_ASYNC применяется к объектам статистики, создаваемым для индексов, отдельных столбцов в предикатах запросов, и к статистике, создаваемой инструкцией CREATE STATISTICS.

Параметр включен по умолчанию для новых баз данных, созданных после обновления до AU7. Параметр отключен по умолчанию для баз данных, созданных до обновления. 

Дополнительные сведения о статистике см. в статье [Статистика](/sql/relational-databases/statistics/statistics).

## <a name="permissions"></a>Разрешения  
Необходимо разрешение ALTER для базы данных.  
  
## <a name="error-messages"></a>сообщения об ошибках
Если автоматическая статистика отключена, при попытке изменить параметры статистики в PDW выводится сообщение об ошибке: "Этот параметр не поддерживается в PDW". Системный администратор может включить автоматическую статистику, включив переключатель [AutoStatsEnabled](../../analytics-platform-system/appliance-feature-switch.md).

## <a name="general-remarks"></a>Общие замечания  
Значения параметров REPLICATED_SIZE, DISTRIBUTED_SIZE и LOG_SIZE могут быть больше, равны или меньше текущих значений для базы данных.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
Операции увеличения и уменьшения размера являются приблизительными. Полученные фактические размеры могут отличаться от значений параметров.  
  
[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] выполняет инструкцию ALTER DATABASE не как атомарную операцию. Если выполнение инструкции прерывается, уже внесенные изменения сохраняются.  

Параметры статистики работают, только если администратор включил автоматическую статистику.  Для включения или отключения автоматической статистики служит переключатель [AutoStatsEnabled](../../analytics-platform-system/appliance-feature-switch.md). 
  
## <a name="locking-behavior"></a>Режим блокировки  
Принимает совмещаемую блокировку для объекта DATABASE. Изменить базу данных, в которой другой пользователь в настоящее время производит операции чтения или записи, невозможно. Это относится и к сеансам, в рамках которых была выполнена инструкция [USE](http://msdn.microsoft.com/158ec56b-b822-410f-a7c4-1a196d4f0e15) для базы данных.  
  
## <a name="performance"></a>Производительность  
Для сжатия базы данных может требоваться много времени и системных ресурсов в зависимости от фактического размера данных в ней и степени фрагментации на диске. Например, сжатие базы данных может длиться несколько часов.  
  
## <a name="determining-encryption-progress"></a>Определение хода выполнения шифрования  
Чтобы определить ход выполнения прозрачного шифрования данных в базе данных в процентах, используйте следующий запрос:  
  
```sql  
WITH  
database_dek AS (  
    SELECT ISNULL(db_map.database_id, dek.database_id) AS database_id,  
        dek.encryption_state, dek.percent_complete,  
        dek.key_algorithm, dek.key_length, dek.encryptor_thumbprint,  
        type  
    FROM sys.dm_pdw_nodes_database_encryption_keys AS dek  
    INNER JOIN sys.pdw_nodes_pdw_physical_databases AS node_db_map  
        ON dek.database_id = node_db_map.database_id   
        AND dek.pdw_node_id = node_db_map.pdw_node_id  
    LEFT JOIN sys.pdw_database_mappings AS db_map  
        ON node_db_map .physical_name = db_map.physical_name  
    INNER JOIN sys.dm_pdw_nodes nodes  
        ON nodes.pdw_node_id = dek.pdw_node_id  
    WHERE dek.encryptor_thumbprint <> 0x  
),  
dek_percent_complete AS (  
    SELECT database_dek.database_id, AVG(database_dek.percent_complete) AS percent_complete  
    FROM database_dek  
    WHERE type = 'COMPUTE'  
    GROUP BY database_dek.database_id  
)  
SELECT DB_NAME( database_dek.database_id ) AS name,  
    database_dek.database_id,  
    ISNULL(  
       (SELECT TOP 1 dek_encryption_state.encryption_state  
        FROM database_dek AS dek_encryption_state  
        WHERE dek_encryption_state.database_id = database_dek.database_id  
        ORDER BY (CASE encryption_state  
            WHEN 3 THEN -1  
            ELSE encryption_state  
            END) DESC), 0)  
        AS encryption_state,  
dek_percent_complete.percent_complete,  
database_dek.key_algorithm, database_dek.key_length, database_dek.encryptor_thumbprint  
FROM database_dek  
INNER JOIN dek_percent_complete   
    ON dek_percent_complete.database_id = database_dek.database_id  
WHERE type = 'CONTROL';  
```  
  
Подробный пример, демонстрирующий все этапы реализации прозрачного шифрования данных, см. в статье [Прозрачное шифрование данных (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-altering-the-autogrow-setting"></a>A. Изменение параметра AUTOGROW  
Присвойте параметру AUTOGROW значение ON для базы данных `CustomerSales`.  
  
```sql  
ALTER DATABASE CustomerSales  
    SET ( AUTOGROW = ON );  
```  
  
### <a name="b-altering-the-maximum-storage-for-replicated-tables"></a>Б. Изменение максимального пространства для хранения реплицированных таблиц  
В приведенном ниже примере для базы данных `CustomerSales` задается максимальный размер хранилища для реплицированных таблиц, равный 1 ГБ. Это размер хранилища для вычислительного узла.  
  
```sql  
ALTER DATABASE CustomerSales  
    SET ( REPLICATED_SIZE = 1 GB );  
```  
  
### <a name="c-altering-the-maximum-storage-for-distributed-tables"></a>В. Изменение максимального пространства для хранения распределенных таблиц  
 В приведенном ниже примере для базы данных `CustomerSales` задается максимальный размер хранилища для распределенных таблиц, равный 1000 ГБ (один терабайт). Это совокупный размер хранилища для всех вычислительных узлов на устройстве, а не для отдельных вычислительных узлов.  
  
```sql  
ALTER DATABASE CustomerSales  
    SET ( DISTRIBUTED_SIZE = 1000 GB );  
```  
  
### <a name="d-altering-the-maximum-storage-for-the-transaction-log"></a>Г. Изменение максимального пространства для хранения журнала транзакций  
 В приведенном ниже примере для базы данных `CustomerSales` на устройстве задается максимальный размер журнала транзакций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], равный 10 ГБ.  
  
```sql  
ALTER DATABASE CustomerSales  
    SET ( LOG_SIZE = 10 GB );  
```  

### <a name="e-check-for-current-statistics-values"></a>Д. Проверка текущих значений статистики

Следующий запрос возвращает текущие значения статистики для всех баз данных. Значение 1 означает, что функция включена, а 0 — что функция отключена.

```sql
SELECT NAME,
    is_auto_create_stats_on,
    is_auto_update_stats_on,
    is_auto_update_stats_async_on
FROM sys.databases;
```
### <a name="f-enable-auto-create-and-auto-update-stats-for-a-database"></a>Е. Включение автоматического создания и автоматического обновление статистики для базы данных
Используйте следующую инструкцию, чтобы включить автоматическое и асинхронное создание и обновление статистики для базы данных CustomerSales.  В результате по мере необходимости создается и обновляется статистика по отдельным столбцам для формирования высококачественных планов запросов.

```sql
ALTER DATABASE CustomerSales
    SET AUTO_CREATE_STATISTICS ON;
ALTER DATABASE CustomerSales
    SET AUTO_UPDATE_STATISTICS ON; 
ALTER DATABASE CustomerSales
    SET AUTO_UPDATE_STATISTICS_ASYNC ON;
```
  
## <a name="see-also"></a>См. также:  
 [CREATE DATABASE (Parallel Data Warehouse)](../../t-sql/statements/create-database-transact-sql.md?&tabs=sqlpdw)   
 [DROP DATABASE (Transact-SQL)](../../t-sql/statements/drop-database-transact-sql.md)  
  
 
