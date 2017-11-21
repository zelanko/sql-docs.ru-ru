---
title: "CREATE DATABASE (база данных Azure SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/28/2017
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: t-sql|statements
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SERVICE_OBJECTIVE
- SERVICE_OBJECTIVE_TSQL
- ELASTIC_POOL
- ELASTIC_POOL_TSQL
- EDITION
- EDITION_TSQL
- MAXSIZE
- MAXSIZE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SERVICE_OBJECTIVE
- ELASTIC_POOL
- EDITION SQL Database
- MAXSIZE SQL Database
ms.assetid: 22b167f7-ae86-490b-adb3-ec02ca1c1508
caps.latest.revision: 62
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: e9781bd657f094c7be57ae513cc2c4a026ad4746
ms.contentlocale: ru-ru
ms.lasthandoff: 09/27/2017

---
# <a name="create-database-azure-sql-database"></a>CREATE DATABASE (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Создает новую базу данных.  
  
## <a name="syntax"></a>Синтаксис  
  
``` 
  
CREATE DATABASE database_name [ COLLATE collation_name ]  
{  
   (<edition_options> [, ...n])   
}  

[ WITH CATALOG_COLLATION = { DATABASE_DEFAULT | SQL_Latin1_General_CP1_CI_AS }  ]
  
<edition_options> ::=   
{  

      MAXSIZE = { 100 MB | 250 MB | 500 MB | 1 … 1024 … 4096 GB }    
    | ( EDITION = {  'basic' | 'standard' | 'premium' | 'premiumrs'}   
    | SERVICE_OBJECTIVE =   
          {  'basic' | 'S0' | 'S1' | 'S2' | 'S3' | 'S4'| 'S6'| 'S7'| 'S9'| 'S12' | 
            | 'P1' | 'P2' | 'P4'| 'P6' | 'P11'  | 'P15'  
            | 'PRS1' | 'PRS2' | 'PRS4' | 'PRS6' 
            | { ELASTIC_POOL(name = <elastic_pool_name>) } }  ) 
}  

 [;]  
  

```  

```
To copy a database:  
CREATE DATABASE database_name  
    AS COPY OF [source_server_name.] source_database_name  
    [ ( SERVICE_OBJECTIVE =   
          {  'basic' | 'S0' | 'S1' | 'S2' | 'S3' | 'S4'| 'S6'| 'S7'| 'S9'| 'S12' |  
            | 'P1' | 'P2' | 'P4'| 'P6' | 'P11' | 'P15'  
            | 'PRS1' | 'PRS2' | 'PRS4' | 'PRS6' 
            | { ELASTIC_POOL(name = <elastic_pool_name>) } } )  
    ]  
 [;] 
 
```  
  
## <a name="arguments"></a>Аргументы  
 Следующая диаграмма синтаксиса демонстрирует поддерживаемые аргументы в среде [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 *database_name*  
 Имя новой базы данных. Это имя должно быть уникальным на сервере SQL server, который может разместить оба [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] баз данных и [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] базы данных и соответствовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] правилам для идентификаторов. Дополнительные сведения см. в разделе [идентификаторы](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
 *Collation_name*  
 Задает параметры сортировки по умолчанию для базы данных. Именем параметров сортировки может быть либо имя параметров сортировки Windows, либо имя параметров сортировки SQL. Если параметры не указаны, база данных использует параметры сортировки по умолчанию: SQL_Latin1_General_CP1_CI_AS.  
  
 Дополнительные сведения об именах параметров сортировки Windows и SQL [COLLATE (Transact-SQL)](http://msdn.microsoft.com/library/ms184391.aspx).  
  
 *CATALOG_COLLATION*  
Задает параметры сортировки по умолчанию для каталога метаданных. *DATABASE_DEFAULT* указывает метаданных каталога для системных представлений и системных таблицах сортируются в соответствии параметров сортировки по умолчанию для базы данных.  Это поведение, имеющихся в SQL Server. 

*SQL_Latin1_General_CP1_CI_AS* указывает метаданных каталога для системных представлений и таблиц нужно сопоставить для фиксированных параметров сортировки SQL_Latin1_General_CP1_CI_AS.  Это параметр по умолчанию в базе данных SQL Azure, если значение не указано.

 *ВЫПУСК*  
 Указывает уровень службы базы данных. Возможные значения: «basic», «стандартные», «premium» и «premiumrs».  
  
 Если указан выпуск, но MAXSIZE не задан, параметру MAXSIZE задано наиболее ограничительному размеру, поддерживаемому этим выпуском.  
  
 *ПАРАМЕТР MAXSIZE*  
 Указывает максимальный размер базы данных. Значение параметра MAXSIZE должно быть допустимо для указанного значения параметра EDITION (уровень службы). Далее приведены поддерживаемые значения MAXSIZE и значения по умолчанию (D) для уровней службы.  
  
|**ПАРАМЕТР MAXSIZE**|**Basic**|**S0 S2**|**S3 S12**|**P1 P6 и PRS1 PRS6**| **P11 P15** 
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
|300 ГБ|Недоступно|Недоступно|√|√|√|  
|400 ГБ|Недоступно|Недоступно|√|√|√|
|500 ГБ|Недоступно|Недоступно|√|√ (D)|√|
|750 ГБ|Недоступно|Недоступно|√|√|√|
|1024 ГБ|Недоступно|Недоступно|√|√|√ (D)|
|От 1024 ГБ до 4096 ГБ с приращением 256 ГБ * |Недоступно|Недоступно|Недоступно|Недоступно|√|√|  
  
 \*P11 и P15 позволяют MAXSIZE до 4 ТБ 1024 ГБ, размер по умолчанию.  P11 и P15 могут использовать до 4 ТБ хранилища включены без дополнительной платы. На уровне Premium MAXSIZE больше 1 ТБ, доступен в следующих областях: нам East2, Запад США, Вирджиния государственных организаций США, Западной Европе, Германия центра, Южная Восточная Азия, восток Японии, Восточная Австралия, Канады центра и Восточная Канада. Текущие ограничения в разделе [одной базы данных](https://docs.microsoft.com/azure/sql-database-single-database-resources).  
  
 Следующие правила применяются к аргументам MAXSIZE и EDITION:  
  
-   Значение MAXSIZE, если оно задано, должно быть одним из допустимых значений, приведенных в таблице выше.  
  
-   Если параметр EDITION указан, а параметр MAXSIZE — нет, то в качестве выпуска будет использоваться значение по умолчанию. Например если выпуск задано значение Standard, а параметр MAXSIZE не задан, то параметр MAXSIZE автоматически задается 250 МБ.  
  
-   Если не указаны ни MAXSIZE, ни EDITION, выпуск задано значение Standard (S0), а параметру MAXSIZE задано значение 250 ГБ.  
  
 SERVICE_OBJECTIVE  
 Определяет уровень производительности. Для описания цели службы и Дополнительные сведения о размере, выпусках и комбинациях служб см. в разделе [уровни служб базы данных SQL Azure и уровни производительности](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/) и [ресурса базы данных SQL ограничения](https://azure.microsoft.com/documentation/articles/sql-database-resource-limits). Если указанное значение SERVICE_OBJECTIVE не поддерживается для значения EDITION, вы получите сообщение об ошибке.  
  
 ELASTIC_POOL (имя = \<elastic_pool_name >) для создания новой базы данных в пул эластичных баз данных, равным ELASTIC_POOL SERVICE_OBJECTIVE базы данных и укажите имя пула. Дополнительные сведения см. в разделе [создания и управления пулом эластичных баз данных базы данных SQL (Предварительная версия)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/).  
  
 *КАК копия [имя_исходного_сервера.] имя_исходной_базы_данных*  
 Для копирования базы данных на тот же или другой сервер [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 *имя_исходного_сервера*  
 Имя сервера [!INCLUDE[ssSDS](../../includes/sssds-md.md)], на котором размещена база данных-источник. Этот параметр не является обязательным, если исходная и конечная базы данных расположены на одном сервере [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Примечание: `AS COPY OF` аргумент не поддерживает полные уникальные имена доменов. Другими словами, если полное доменное имя сервера —`serverName.database.windows.net`, во время копирования базы данных используйте только `serverName`.  
  
 *имя_исходной_базы_данных*  
 Имя копируемой базы данных.  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]не поддерживает следующие аргументы и параметры при использовании `CREATE DATABASE` инструкции:  
  
-   Параметры, связанные с физическим расположением файла, такие как \<filespec > и \<файловая группа >  
  
-   Параметры внешнего доступа, например DB_CHAINING и TRUSTWORTHY.  
  
-   Присоединение базы данных.  
  
-   Параметры Service Broker, например ENABLE_BROKER NEW_BROKER и ERROR_BROKER_CONVERSATIONS.  
  
-   Моментальный снимок базы данных  
  
 Дополнительные сведения об аргументах и `CREATE DATABASE` инструкции в разделе [CREATE DATABASE &#40; Transact SQL Server-SQL &#41; ](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
## <a name="remarks"></a>Замечания  
 Базы данных в [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] используют несколько параметров по умолчанию, устанавливаемых при создании базы данных. Дополнительные сведения об этих параметрах см. в разделе список значений в [DATABASEPROPERTYEX &#40; Transact-SQL &#41; ](../../t-sql/functions/databasepropertyex-transact-sql.md).  
  
 Параметр MAXSIZE позволяет ограничить размер базы данных. Если размер базы данных достигает значения MAXSIZE, вы получите код ошибки 40544. В этом случае данные нельзя вставить или обновить данные и создать новые объекты (например, таблицы, представления, хранимые процедуры и функции). Однако можно по-прежнему читать и удалять данные, усекать и удалять таблицы и индексы, а также выполнять перестроение индексов. Затем можно изменить значение MAXSIZE на значение, превышающее текущий размер базы данных, или удалить некоторые данные, чтобы освободить место в хранилище. Перед возобновлением возможности вставлять новые данные может пройти до 15 минут.  
  
> [!IMPORTANT]  
>  Инструкция `CREATE DATABASE` должна быть единственной инструкцией в пакете [!INCLUDE[tsql](../../includes/tsql-md.md)]. 
  
 Чтобы изменить размер, выпуск или служебные значения позже, используйте [инструкции ALTER DATABASE &#40; База данных Azure SQL &#41; ](../../t-sql/statements/alter-database-azure-sql-database.md).  

Аргумент CATALOG_COLLATION доступен только при создании базы данных. 
  
## <a name="database-copies"></a>Копирование баз данных  
 Копирование базы данных с помощью `CREATE DATABASE` инструкция является асинхронной операцией. Поэтому соединение с сервером [!INCLUDE[ssSDS](../../includes/sssds-md.md)] не требуется в течение всего процесса копирования. `CREATE DATABASE` Оператор возвращает управление пользователю после записи в sys.databases, но перед копированием базы данных операция не будет завершена. Другими словами, инструкция `CREATE DATABASE` возвращает контроль, когда база данных все еще копируется.  
  
-   Наблюдение за процессом копирования на [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] сервера: запрос `percentage_complete` или `replication_state_desc` столбцы в [dm_database_copies](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md) или `state` столбца в **sys.databases** представление. [Sys.dm_operation_status](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md) представление может использоваться также он возвращает состояние операции базы данных, включая копирование базы данных.  
  
 После успешного завершения копирования целевая база данных транзакционно согласована с базой данных-источником.  
  
 К аргументу `AS COPY OF` применяются следующие синтаксические и семантические правила.  
  
-   Имя исходного и целевого сервера для копирования могут совпадать или отличаться. Если они совпадают, этот параметр является необязательным и по умолчанию используется контекст сервера текущего сеанса.  
  
-   Необходимо указать имена исходной и целевой базы данных. Они должны быть уникальными и соответствовать правилам для идентификаторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [идентификаторы](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
-   Инструкция `CREATE DATABASE` должна выполняться в контексте базы данных master на сервере [!INCLUDE[ssSDS](../../includes/sssds-md.md)], на котором будет создана новая база данных.  
  
-   После завершения копирования целевой базой данных необходимо управлять как независимой базой данных. Инструкции `ALTER DATABASE` и `DROP DATABASE` для новой базы данных можно выполнять независимо от базы данных-источника. Новую базу данных также можно скопировать в другую новую базу данных.  
  
-   Пока выполняется копирование базы данных, база данных-источник остается доступной.  
  
 Дополнительные сведения см. в разделе [создать копию базы данных Azure SQL, с помощью Transact-SQL](https://azure.microsoft.com/documentation/articles/sql-database-copy-transact-sql/).  
  
## <a name="permissions"></a>Permissions  
 Создание имени входа базы данных должен быть одним из следующих:  
  
-   Имя входа субъекта серверного уровня  
  
-   Администратор Azure AD для локального сервера SQL Azure  
  
-   Имя входа, которое является членом `dbmanager` роли базы данных  
  
 **Дополнительные требования для использования `CREATE DATABASE ... AS COPY OF` синтаксис:** входа, выполняющего инструкцию на локальном сервере, необходимо по крайней мере `db_owner` на исходном сервере. Если имя входа на основе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности, имени входа, выполняющего инструкцию на локальном сервере должен иметь совпадающего имени входа для источника [!INCLUDE[ssSDS](../../includes/sssds-md.md)] сервера с идентичным именем и паролем.  
  
## <a name="examples"></a>Примеры  
Краткое руководство, показывая, как соединение с базой данных Azure SQL с помощью SQL Server Management Studio, в разделе [базы данных SQL Azure: использование SQL Server Management Studio для подключения и запроса данных](/azure/sql-database/sql-database-connect-query-ssms).  
  
### <a name="simple-example"></a>Простой пример  
 Простой пример для создания базы данных.  
  
```tsql  
CREATE DATABASE TestDB1;  
```  
  
### <a name="simple-example-with-edition"></a>Простой пример с выпуском  
 Простой пример для создания стандартной базы данных.  
  
```tsql  
CREATE DATABASE TestDB2  
( EDITION = 'standard' );  
```  
  
### <a name="example-with-additional-options"></a>Пример с дополнительными параметрами  
 Пример с использованием нескольких параметров.  
  
```tsql  
CREATE DATABASE hito   
COLLATE Japanese_Bushu_Kakusu_100_CS_AS_KS_WS   
( MAXSIZE = 500 MB, EDITION = 'standard', SERVICE_OBJECTIVE = 'S1' ) ;  
```  
  
### <a name="creating-a-copy"></a>Создание копии  
 Пример создания копии базы данных.  
  
```tsql  
CREATE DATABASE escuela   
AS COPY OF school;  
```  
  
### <a name="creating-a-database-in-an-elastic-pool"></a>Создание базы данных в пуле эластичных БД  
 Создает новую базу данных в пул с именем S3M100:  
  
```tsql  
CREATE DATABASE db1 ( SERVICE_OBJECTIVE = ELASTIC_POOL ( name = S3M100 ) ) ;  
```  
  
### <a name="creating-a-copy-of-a-database-on-another-server"></a>Создание копии базы данных на другом сервере  
 В следующем примере создается копия базы данных db_original, с именем db_copy в уровнем производительности P2 для одной базы данных.  Это верно независимо от того, db_original в пуле эластичных БД или уровня производительности для одной базы данных.  
  
```tsql  
CREATE DATABASE db_copy   
    AS COPY OF ozabzw7545.db_original ( SERVICE_OBJECTIVE = 'P2' )  ;  
```  
  
 В следующем примере создается копия базы данных db_original, с именем db_copy в пуле эластичных БД с именем ep1.  Это верно независимо от того, db_original в пуле эластичных БД или уровня производительности для одной базы данных.  Если db_original находится в пуле эластичных БД с другим именем, db_copy по-прежнему создается в ep1.  
  
```tsql  
CREATE DATABASE db_copy   
    AS COPY OF ozabzw7545.db_original   
    (SERVICE_OBJECTIVE = ELASTIC_POOL( name = ep1 ) ) ;  
```  

### <a name="create-database-with-specified-catalog-collation-value"></a>Создание базы данных со значением указанного каталога параметров сортировки

Следующий пример задает параметры сортировки каталога DATABASE_DEFAULT во время создания базы данных, который задает параметры сортировки каталога же параметры сортировки базы данных.

```tsql
CREATE DATABASE TestDB3 COLLATE Japanese_XJIS_140  (MAXSIZE = 100 MB, EDITION = ‘basic’)  
      WITH CATALOG_COLLATION = DATABASE_DEFAULT 
```
  
## <a name="see-also"></a>См. также:  

-  [sys.dm_database_copies &#40; База данных Azure SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)

-   [ALTER DATABASE &#40; База данных Azure SQL &#41;](alter-database-azure-sql-database.md)   
    
  


