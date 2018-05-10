---
title: ALTER DATABASE (база данных SQL Azure) | Документы Майкрософт
ms.custom: ''
ms.date: 02/13/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: t-sql|statements
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6fc5fd95-2045-4f20-a914-3598091bc7cc
caps.latest.revision: 37
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: c7d3f93304f08cbbf316e092b62ed7c4b62e199d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="alter-database-azure-sql-database"></a>ALTER DATABASE (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Изменяет [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Изменяет имя базы данных, выпуск и цель службы базы данных, присоединяет пул эластичных БД и задает параметры базы данных.  
  
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
      | 'GP_GEN4_1' | 'GP_GEN4_2' | 'GP_GEN4_4' | 'GP_GEN4_8' | 'GP_GEN4_16' 
      | 'BC_GEN4_1' | 'BC_GEN4_2' | 'BC_GEN4_4' | 'BC_GEN4_8' | 'BC_GEN4_16' | 
      }

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
  
<delayed_durability_option> ::=  DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }  
  
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
  
 Полное описание параметров Set см. в разделах [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md) и [Уровень совместимости ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="arguments"></a>Аргументы  

*database_name*  

Имя изменяемой базы данных.  
  
CURRENT  

Определяет, что должна быть изменена текущая используемая база данных.  
  
MODIFY NAME **=***new_database_name*  

Присваивает базе данных имя, указанное в аргументе *новое_имя_базы_данных*. В следующем примере имя базы данных `db1` изменяется на `db2`.   

```  
ALTER DATABASE db1  
    MODIFY Name = db2 ;  
```    

MODIFY (EDITION **=** ['basic' | 'standard' | 'premium' |'GeneralPurpose' | 'BusinessCritical'])    

Изменяет уровень службы базы данных. Поддержка "premiumrs" была упразднена. При возникновении вопросов пишите на следующий адрес premium-rs@microsoft.com.

В следующем примере выпуск изменяется на `premium`.
  
```  
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

**Уровень служб "Общего назначения"**

|MAXSIZE|GP_Gen4_1|GP_Gen4_2|GP_Gen4_4|GP_Gen4_8|GP_Gen4_16|
|:--- | --: |--: |--: |--: |--: |
|Максимальный размер данных (ГБ)|1024|1024|1536|3072|4096|

**Уровень служб "Критически важный для бизнеса"**

|Уровень производительности|BC_Gen4_1|BC_Gen4_2|BC_Gen4_4|BC_Gen4_8|BC_Gen4_16|
|:--- | --: |--: |--: |--: |--: |
|Максимальный размер данных (ГБ)|1024|1024|1536|2048|2048|

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

Определяет уровень производительности. Доступные значения для цели службы: `S0`, `S1`, `S2`, `S3`, `S4`, `S6`, `S7`, `S9`, `S12`, `P1`, `P2`, `P4`, `P6`, `P11`, `P15`, `GP_GEN4_1`, `GP_GEN4_2`, `GP_GEN4_4`, `GP_GEN4_8`, `GP_GEN4_16`, `BC_GEN4_1` `BC_GEN4_2` `BC_GEN4_4` `BC_GEN4_8` `BC_GEN4_16`. 

Описания целей служб и дополнительные сведения о сочетаниях размеров, выпусков и целей служб см. в разделах [Уровни служб и уровни производительности баз данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/), [Пределы для ресурсов на основе DTU](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits) и [Пределы для ресурсов на основе виртуальных ядер](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits). Поддержка целей служб PRS была удалена. При возникновении вопросов пишите на следующий адрес premium-rs@microsoft.com. 
  
MODIFY (SERVICE_OBJECTIVE = ELASTIC\_POOL (name = \<elastic_pool_name>)  

Чтобы добавить существующую базу данных в эластичный пул, задайте параметру SERVICE_OBJECTIVE базы данных значение ELASTIC_POOL и укажите имя эластичного пула. Этот параметр также служит для изменения базы данных в другом эластичном пуле на том же сервере. Дополнительные сведения см. в разделе [Создание эластичного пула баз данных SQL и управление им](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/). Чтобы удалить базу данных из эластичного пула, используйте инструкцию ALTER DATABASE, чтобы задать в качестве значения SERVICE_OBJECTIVE один уровень производительности базы данных.  

ADD SECONDARY ON SERVER \<partner_server_name>  

Создает базу данных-получатель с географической репликаций с тем же именем на сервере-участнике, преобразуя локальную базу данных в базу данных-источник с георепликацией, и начинает асинхронную репликацию данных с источника в новую базу данных-получатель. Команда завершается ошибкой, если на сервере-получателе уже существует база данных с таким именем. Команда выполняется в базе данных master на сервере с локальной базой данных, которая становится базой данных-источником.  
  
WITH ALLOW_CONNECTIONS { **ALL** | NO }  

Если параметр ALLOW_CONNECTIONS не указан, ему по умолчанию присваивается значение ALL. Если указано значение ALL, это база данных только для чтения, позволяющая подключаться всем именам входа с соответствующими разрешениями.  
  
WITH SERVICE_OBJECTIVE {  `S0`, `S1`, `S2`, `S3`, `S4`, `S6`, `S7`, `S9`, `S12`, `P1`, `P2`, `P4`, `P6`, `P11`, `P15`, `GP_GEN4_1`, `GP_GEN4_2`, `GP_GEN4_4`, `GP_GEN4_8`, `GP_GEN4_16`, `BC_GEN4_1` `BC_GEN4_2` `BC_GEN4_4` `BC_GEN4_8` `BC_GEN4_16` }  

Если параметр SERVICE_OBJECTIVE не указан, база данных-получатель создается на том же уровне службы, что и база данных-источник. Если параметр SERVICE_OBJECTIVE указан, база данных-получатель создается на указанном уровне. Этот параметр поддерживает создание геореплицированных объектов-получателей с менее дорогими уровнями обслуживания. Указанный параметр SERVICE_OBJECTIVE должен находиться в том же выпуске, что и источник. Например, если используется выпуск Premium, параметр S0 указать невозможно.  
  
ELASTIC_POOL (name = \<elastic_pool_name)  

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
  
Кроме того, кэш процедур сбрасывается в следующих случаях:  
  
- В базе данных включен параметр базы данных AUTO_CLOSE. Если отсутствуют ссылки соединений пользователя или базы данных, фоновая задача предпримет попытку закрыть и отключить базу данных автоматически.  
  
- Выполняется несколько запросов в базе данных с параметрами по умолчанию. Затем база данных уничтожается.  
  
- Успешное перестроение журнала транзакций базы данных.  
  
- Восстановление резервной копии базы данных.  
  
- Отсоединение базы данных.  
  
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
  
[CREATE DATABASE — база данных SQL Azure](../../t-sql/statements/create-database-azure-sql-database.md)   
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
  
  
