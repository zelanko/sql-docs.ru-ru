---
title: "ALTER DATABASE (база данных Azure SQL) | Документы Microsoft"
ms.custom: 
ms.date: 12/20/2017
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: t-sql|statements
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6fc5fd95-2045-4f20-a914-3598091bc7cc
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a5c22e2ce58189f396835f65748fdbab7ef8f9d5
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2018
---
# <a name="alter-database-azure-sql-database"></a>ALTER DATABASE (база данных Azure SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Изменяет [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Изменяет имя базы данных, выпуск и службы цель базы данных, соединения в пуле эластичных БД и наборы параметров базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Azure SQL Database Syntax  
ALTER DATABASE { database_name }  
{  
    MODIFY NAME = new_database_name  
  | MODIFY ( <edition_options> [, ... n] )   
  | SET { <option_spec> [ ,... n ] }   
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
    | EDITION = { 'basic' | 'standard' | 'premium' | 'premiumrs' }   
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
                 | 'P1' | 'P2' | 'P4'| 'P6' | 'P11'  | 'P15' | 
                 | 'PRS1' | 'PRS2' | 'PRS4' | 'PRS6' | }

```  
  
```
-- SET OPTIONS AVAILABLE FOR SQL Database  
-- Full descriptions of the set options are available in the topic   
-- ALTER DATABASE SET Options. The supported syntax is listed here.  

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
  
<auto_option> ::=   
{  
    AUTO_CREATE_STATISTICS { OFF | ON [ ( INCREMENTAL = { ON | OFF } ) ] }   
  | AUTO_SHRINK { ON | OFF }   
  | AUTO_UPDATE_STATISTICS { ON | OFF }   
  | AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }  
}  

<change_tracking_option> ::=  
{  
  CHANGE_TRACKING   
   {   
       = OFF  
     | = ON [ ( <change_tracking_option_list > [,...n] ) ]   
     | ( <change_tracking_option_list> [,...n] )  
   }  
}  

   <change_tracking_option_list> ::=  
   {  
       AUTO_CLEANUP = { ON | OFF }   
     | CHANGE_RETENTION = retention_period { DAYS | HOURS | MINUTES }  
   }  

<cursor_option> ::=   
{  
    CURSOR_CLOSE_ON_COMMIT { ON | OFF }   
}  
  
<db_encryption_option> ::=  
    ENCRYPTION { ON | OFF }  
  
<db_update_option> ::=  
    { READ_ONLY | READ_WRITE }  
  
<db_user_access_option> ::=  
    { RESTRICTED_USER | MULTI_USER }  
  
<delayed_durability_option> ::=    DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }  
  
<parameterization_option> ::=  
    PARAMETERIZATION { SIMPLE | FORCED }  
  
<query_store_options> ::=  
{  
    QUERY_STORE   
    {  
          = OFF   
        | = ON [ ( <query_store_option_list> [,... n] ) ]  
        | ( < query_store_option_list> [,... n] )  
        | CLEAR [ ALL ]  
    }  
}   
  
<query_store_option_list> ::=  
{  
      OPERATION_MODE = { READ_WRITE | READ_ONLY }   
    | CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = number )  
    | DATA_FLUSH_INTERVAL_SECONDS = number   
    | MAX_STORAGE_SIZE_MB = number   
    | INTERVAL_LENGTH_MINUTES = number   
    | SIZE_BASED_CLEANUP_MODE = [ AUTO | OFF ]  
    | QUERY_CAPTURE_MODE = [ ALL | AUTO | NONE ]  
    | MAX_PLANS_PER_QUERY = number  
}  
  
<snapshot_option> ::=  
{  
    ALLOW_SNAPSHOT_ISOLATION { ON | OFF }  
  | READ_COMMITTED_SNAPSHOT {ON | OFF }  
  | MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT {ON | OFF }  
}  
<sql_option> ::=   
{  
    ANSI_NULL_DEFAULT { ON | OFF }   
  | ANSI_NULLS { ON | OFF }   
  | ANSI_PADDING { ON | OFF }   
  | ANSI_WARNINGS { ON | OFF }   
  | ARITHABORT { ON | OFF }   
  | COMPATIBILITY_LEVEL = { 100 | 110 | 120 | 130 | 140 }  
  | CONCAT_NULL_YIELDS_NULL { ON | OFF }   
  | NUMERIC_ROUNDABORT { ON | OFF }   
  | QUOTED_IDENTIFIER { ON | OFF }   
  | RECURSIVE_TRIGGERS { ON | OFF }   
}  
  
<termination>  ::=   
{  
    ROLLBACK AFTER integer [ SECONDS ]   
  | ROLLBACK IMMEDIATE   
  | NO_WAIT  
}  

<temporal_history_retention>  ::=  TEMPORAL_HISTORY_RETENTION { ON | OFF }
```  
  
 Полное описание параметров инструкции set см [параметры ALTER DATABASE SET &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) и [изменить уровень совместимости базы данных &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя изменяемой базы данных.  
  
 CURRENT  
 Определяет, что должна быть изменена текущая используемая база данных.  
  
 Параметр MODIFY NAME **= *** новое_имя_базы_данных*  
 Переименование базы данных с именем, указанным в качестве *новое_имя_базы_данных*. В следующем примере изменяется имя базы данных `db1` для `db2`:   

```  
ALTER DATABASE db1  
    MODIFY Name = db2 ;  
```    

 ИЗМЕНИТЬ (выпуск  **=**  [«basic» | «стандартный» | «premium» | «premiumrs»])    
 Изменяет уровень обслуживания базы данных. В следующем примере изменяется выпуск `premium`:
  
```  
ALTER DATABASE current 
    MODIFY (EDITION = 'premium');
``` 

Изменение выпуска завершается неудачей, если свойство MAXSIZE для базы данных задано значение за пределами допустимого диапазона, поддерживаемого этим выпуском.  

 ИЗМЕНИТЬ (MAXSIZE  **=**  [100 МБ | 500 МБ | 1 | 1024... 4096] ГБ)  
 Указывает максимальный размер базы данных. Максимальный размер должен соответствовать допустимому набору значений для свойства EDITION базы данных. Смена максимального размера базы данных может потребовать также смены значения EDITION базы данных. В следующей таблице приведены поддерживаемые значения MAXSIZE и значения, заданные по умолчанию (D) для уровней служб [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
|**ПАРАМЕТР MAXSIZE**|**Basic**|**S0-S2**|**S3-S12**|**P1 P6 и PRS1 PRS6**|**P11-P15**|  
|-----------------|---------------|------------------|-----------------|-----------------|-----------------|-----------------|  
|100 МБ|√|√|√|√|√|  
|250 МБ|√|√|√|√|√|  
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
|750 ГБ|Недоступно|√|√|√|√|  
|1024 ГБ|Недоступно|√|√|√|√ (D)|  
|От 1024 ГБ до 4096 ГБ с приращением 256 ГБ *|Недоступно|Недоступно|Недоступно|Недоступно|√|√|  
  
 \* P11 и P15 позволяют MAXSIZE до 4 ТБ 1024 ГБ, размер по умолчанию.  P11 и P15 могут использовать до 4 ТБ хранилища включены без дополнительной платы. На уровне Premium MAXSIZE больше 1 ТБ, доступен в следующих областях: нам East2, Запад США, Вирджиния государственных организаций США, Западной Европе, Германия центра, Южная Восточная Азия, восток Японии, Восточная Австралия, Канады центра и Восточная Канада. Текущие ограничения в разделе [одной базы данных](https://docs.microsoft.com/azure/sql-database-single-database-resources).  

  
 Следующие правила применяются к аргументам MAXSIZE и EDITION:  
  
-   Значение MAXSIZE, если указан, должно быть допустимое значение показано в предыдущей таблице.  
  
-   Если параметр EDITION указан, а параметр MAXSIZE — нет, то в качестве выпуска будет использоваться значение по умолчанию. Например, если параметру EDITION задано значение Standard, а параметр MAXSIZE не задан, то параметру MAXSIZE будет автоматически присвоено значение 500 МБ.  
  
-   Если не указаны ни MAXSIZE, ни EDITION, выпуск задано значение Standard (S0), а параметру MAXSIZE задано значение 250 ГБ.  
 

 ИЗМЕНИТЬ (SERVICE_OBJECTIVE = \<цель обслуживания >)  
 Определяет уровень производительности. В следующем примере изменяется службы цель расширенной базы данных для `P6`:
 
```  
ALTER DATABASE current 
    MODIFY (SERVICE_OBJECTIVE = 'P6');
```  
 Доступные значения для обслуживания:: `S0`, `S1`, `S2`, `S3`, `S4`, `S6`, `S7`, `S9`, `S12`, `P1`, `P2`, `P4`, `P6`, `P11`, `P15`, `PRS1`, `PRS2`, `PRS4`, и `PRS6`. Для описания цели службы и Дополнительные сведения о размере, выпусках и комбинациях служб см. в разделе [уровни служб базы данных SQL Azure и уровни производительности](http://msdn.microsoft.com/library/azure/dn741336.aspx). Если указанное значение SERVICE_OBJECTIVE не поддерживается выпуском, возникает ошибка. Чтобы изменить значение SERVICE_OBJECTIVE с одного уровня на другой (например, с S1 на P1), необходимо также изменить значение EDITION.  
  
 ИЗМЕНИТЬ (SERVICE_OBJECTIVE = ГИБКОМУ\_ПУЛА (имя = \<elastic_pool_name >)  
 Чтобы добавить существующую базу данных в пуле эластичных БД, ELASTIC_POOL значение SERVICE_OBJECTIVE базы данных и укажите имя эластичного пула. Этот параметр служит для изменения различных эластичный пул с таким же сервером базы данных. Дополнительные сведения см. в разделе [Создание и управление ими эластичного пула баз данных SQL](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/). Чтобы удалить базу данных из эластичного пула, значение SERVICE_OBJECTIVE одного уровня производительности базы данных с помощью инструкции ALTER DATABASE.  

 Добавление сервера-ПОЛУЧАТЕЛЯ ON \<partner_server_name >  
 Создает базы данных-получателя географическую репликацию данных с тем же именем на сервере-партнере превращение локальной базы данных в географическую репликацию основной и начинает асинхронной репликации данных с сервера-источника на новом сервере-получателе. Если база данных с тем же именем уже существует на сервере-получателе, команда завершается ошибкой. Команда выполняется в базе данных master на сервере с локальной базы данных, который становится основной.  
  
 С ALLOW_CONNECTIONS {ВСЕ | **НЕТ** }  
 Если ALLOW_CONNECTIONS не указан, ему присваивается нет по умолчанию. Если все равно, это база данных только для чтения, позволяющий все имена входа с соответствующими разрешениями для подключения.  
  
 С SERVICE_OBJECTIVE {'S0» | «S1» | «S2» | «S3» | 'S4» | «S6» | «S7» | «S9» | «S12» | «P1» | «P2» | «P4» | «P6» | «P11» | «P15» | «PRS1» | «PRS2» | «PRS4» | «PRS6»}  
 При SERVICE_OBJECTIVE не указан, база данных-получатель создается на том же уровне службы базы данных-источника. Если указано значение SERVICE_OBJECTIVE, база данных-получатель создается на заданном уровне. Этот параметр поддерживает создание получатели с менее дорогих уровней обслуживания. Значение SERVICE_OBJECTIVE указан должно быть в один и тот же выпуск как источник. Например если выпуск premium нельзя указать S0.  
  
 ELASTIC_POOL (имя = \<elastic_pool_name)  
 Если ELASTIC_POOL не указан, в пуле эластичных баз данных-получателей не создается. При ELASTIC_POOL указано, в указанный пул создается база данных-получатель.  
  
> [!IMPORTANT]  
>  Пользователь, выполняющий команду Добавить ПОЛУЧАТЕЛЕЙ должно быть DBManager на сервере-источнике, db_owner членство в локальной базе данных и DBManager на сервере-получателе.  
  
 Удаление сервера-ПОЛУЧАТЕЛЯ ON \<partner_server_name >  
 Удаляет указанный географическая репликация базы данных-получателя на указанном сервере. Команда выполняется в базе данных master на сервере, содержащем базы данных-источника.  
  
> [!IMPORTANT]  
>  Пользователь, выполняющий команду Удалить ПОЛУЧАТЕЛЯ должен быть DBManager на сервере-источнике.  
  
 FAILOVER  
 Повышает уровень базы данных-получателя в сотрудничестве географической репликации, на котором команда выполняется становится основным и можно понизить уровень текущей первичной реплике станет новой вторичной репликацией. В рамках этого процесса географическую репликацию данных в режиме временно переключить в асинхронном режиме в синхронном режиме. Во время процесса отработки отказа:  
  
1.  Основной останавливает получение новых транзакций.  
  
2.  Все невыполненные транзакции записываются в базу данных-получатель.  
  
3.  Сервер-получатель становится первичной и начинается асинхронная репликация geo старым первичным и новом сервере-получателе.  
  
 Эта последовательность гарантирует, что происходит без потери данных. Период, во время которого недоступны обеих баз данных составляет примерно 0-25 секунд во время переключения ролей. Общее операции займет не более около одной минуты. Если база данных-источник недоступна, при этом команды, команда выдает сообщение о недоступности базы данных-источника. Если зависает процесс отработки отказа не была завершена, можно использовать команду принудительной отработки отказа и принять потеря данных — и если необходимо восстановить ее потерянные данные вызова devops (CSS), чтобы восстановить потерянные данные.  
  
> [!IMPORTANT]  
>  Пользователь, выполняющий команду отработки ОТКАЗА должен быть DBManager на сервере-источнике и сервере-получателе.  
  
 FORCE_FAILOVER_ALLOW_DATA_LOSS  
 Повышает уровень базы данных-получателя в сотрудничестве географической репликации, на котором команда выполняется становится основным и можно понизить уровень текущей первичной реплике станет новой вторичной репликацией. Эта команда используется только в том случае, когда текущая первичная больше не доступен. Она предназначена для аварийного восстановления, только когда восстановление доступности является критическим, потеря некоторых данных допустима.  
  
 Во время принудительной отработки отказа:  
  
1.  Указанной базы данных-получателя немедленно становится основной базой данных и начинает принимать новые транзакции.  
  
2.  Когда первичная могут повторно установить соединение с источником, добавочное резервное копирование берется на исходный основной, а первичная становится новом сервере-получателе.  
  
3.  Чтобы восстановить данные из этого добавочного резервного копирования на сервере-источнике старого, пользователь подключает devops/CSS.  
  
4.  При наличии дополнительных баз данных-получателей, они автоматически настраиваются в качестве новой основной базы данных-получатели. Этот процесс является асинхронным и может возникнуть задержка до момента завершения этого процесса. До завершения повторной настройки баз данных-получателей остаются из старого основных баз данных-получателей.  
  
> [!IMPORTANT]  
>  Пользователь, выполняющий команду FORCE_FAILOVER_ALLOW_DATA_LOSS должен быть DBManager на сервере-источнике и сервере-получателе.  
  
## <a name="remarks"></a>Remarks  
 Чтобы удалить базу данных, используйте [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md).  
  
 Чтобы уменьшить размер базы данных, используйте [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
 Инструкция ALTER DATABASE должна выполняться в режиме автоматической фиксации (режим управления транзакциями по умолчанию) и не разрешена в явной или неявной транзакции.  
  
 Очистка кэша планов становится причиной перекомпиляции всех последующих планов выполнения и приводит к непредвиденному временному снижению производительности обработки запросов. Для каждого удаленного хранилища кэша в кэше планов журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит следующее информационное сообщение: «[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил %d экземпляров, записанных на диск хранилищ кэша для хранилища кэша "%s" (части кэша планов) в результате операций по обслуживанию или изменению конфигурации базы данных». Это сообщение добавляется в журнал каждые пять минут при сбросе кэша в течение этого интервала времени.  
  
 Кроме того, кэш процедур сбрасывается в следующих случаях.  
  
-   В базе данных включен параметр базы данных AUTO_CLOSE. Если отсутствуют ссылки соединений пользователя или базы данных, фоновая задача предпримет попытку закрыть и отключить базу данных автоматически.  
  
-   Выполняется нескольких запросов в базе данных с параметрами по умолчанию. Затем база данных уничтожается.  
  
-   Успешное перестроение журнала транзакций базы данных.  
  
-   Восстановление резервной копии базы данных.  
  
-   Отсоединение базы данных.  
  
## <a name="viewing-database-information"></a>Просмотр сведений о базе данных  
 Для возврата сведений о базах данных, файлах и файловых группах можно использовать представления каталогов, системные функции и системные хранимые процедуры.  
  
## <a name="permissions"></a>Разрешения  
 Изменять базу данных могут только имя входа субъект серверного уровня (созданное в процессе провизионирования) или члены роли базы данных `dbmanager`.  
  
> [!IMPORTANT]  
>  Владелец базы данных не может изменять базу данных, если он не является членом роли `dbmanager`.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-check-the-edition-options-and-change-them"></a>A. Проверьте параметры выпуска и измените их:

```
SELECT Edition = DATABASEPROPERTYEX('db1', 'EDITION'),
        ServiceObjective = DATABASEPROPERTYEX('db1', 'ServiceObjective'),
        MaxSizeInBytes =  DATABASEPROPERTYEX('db1', 'MaxSizeInBytes');

ALTER DATABASE [db1] MODIFY (EDITION = 'Premium', MAXSIZE = 1024 GB, SERVICE_OBJECTIVE = 'P15');
```

### <a name="b-moving-a-database-to-a-different-elastic-pool"></a>Б. База данных перемещается в другой пул эластичных  
 Существующая база данных перемещается в пул с именем pool1:  
  
```  
ALTER DATABASE db1   
MODIFY ( SERVICE_OBJECTIVE = ELASTIC_POOL ( name = pool1 ) ) ;  
```  
  
### <a name="c-add-a-geo-replication-secondary"></a>В. Добавление получателя Георепликации  
 Создает db1 недоступного для чтения базы данных-получателя на сервере `secondaryserver` из db1 на локальном сервере.  
  
```  
ALTER DATABASE db1   
ADD SECONDARY ON SERVER secondaryserver   
WITH ( ALLOW_CONNECTIONS = NO )  
```  
  
### <a name="d-remove-a-geo-replication-secondary"></a>Г. Удалить вторичный географической репликации  
 Удаляет db1 базы данных-получателя на сервере `secondaryserver`.  
  
```  
ALTER DATABASE db1   
REMOVE SECONDARY ON SERVER testsecondaryserver   
```  
  
### <a name="e-failover-to-a-geo-replication-secondary"></a>Д. Отработка отказа на вторичную географической репликации  
 Повышает уровень db1 базы данных-получателя на сервере `secondaryserver` становится новой основной базой данных при выполнении на сервере `secondaryserver`.  
  
```  
ALTER DATABASE db1 FAILOVER  
```  
  
## <a name="see-also"></a>См. также:  
 [Создание базы данных &#40; База данных Azure SQL &#41;](../../t-sql/statements/create-database-azure-sql-database.md)   
 [DATABASEPROPERTYEX (Transact-SQL)](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [DROP DATABASE (Transact-SQL)](../../t-sql/statements/drop-database-transact-sql.md)   
 [SET TRANSACTION ISOLATION LEVEL &#40; Transact-SQL &#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [sp_spaceused (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.database_mirroring_witnesses &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [sys.data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [sys.filegroups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys.master_files &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Системные базы данных](../../relational-databases/databases/system-databases.md)  
  
  
