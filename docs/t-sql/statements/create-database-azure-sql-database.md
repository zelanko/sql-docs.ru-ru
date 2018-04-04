---
title: CREATE DATABASE (база данных SQL Azure) | Microsoft Docs
ms.custom: ''
ms.date: 02/13/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: t-sql|statements
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
ms.openlocfilehash: de82cfb595559b738ca8db7d72acd620101d3995
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="create-database-azure-sql-database"></a>CREATE DATABASE (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Создает новую базу данных.  

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]

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
    | ( EDITION = {  'basic' | 'standard' | 'premium' }   
    | SERVICE_OBJECTIVE =   
          {  'basic' | 'S0' | 'S1' | 'S2' | 'S3' | 'S4'| 'S6'| 'S7'| 'S9'| 'S12' | 
            | 'P1' | 'P2' | 'P4'| 'P6' | 'P11'  | 'P15'  
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
            | { ELASTIC_POOL(name = <elastic_pool_name>) } } )  
    ]  
 [;] 
 
```  
  
## <a name="arguments"></a>Аргументы  
 Следующая диаграмма синтаксиса демонстрирует поддерживаемые аргументы в среде [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 *database_name*  
 Имя новой базы данных. Это имя должно быть уникальным на сервере SQL Server, где могут размещаться базы данных [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] и [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Кроме того, оно должно соответствовать правилам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для идентификаторов. Дополнительные сведения: [Идентификаторы](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
 *Collation_name*  
 Задает параметры сортировки по умолчанию для базы данных. Именем параметров сортировки может быть либо имя параметров сортировки Windows, либо имя параметров сортировки SQL. Если параметры не указаны, база данных использует параметры сортировки по умолчанию: SQL_Latin1_General_CP1_CI_AS.  
  
 Дополнительные сведения об именах параметров сортировки Windows и SQL: [COLLATE (Transact-SQL)](http://msdn.microsoft.com/library/ms184391.aspx).  
  
 *CATALOG_COLLATION*  
Задает параметры сортировки по умолчанию для каталога метаданных. *DATABASE_DEFAULT* указывает, что каталог метаданных, используемый для системных представлений и таблиц, должен быть сопоставлен параметрам сортировки по умолчанию для базы данных.  Так происходит в SQL Server. 

*SQL_Latin1_General_CP1_CI_AS* указывает, что каталог метаданных, используемый для системных представлений и таблиц, должен быть сопоставлен фиксированным параметрам сортировки SQL_Latin1_General_CP1_CI_AS.  Это параметр используется в базе данных SQL Azure по умолчанию, если никакое иное значение не указано.

 *EDITION*  
 Указывает уровень службы базы данных. Возможные значения: "basic", "standard" и "premium". Поддержка "premiumrs" была упразднена. При возникновении вопросов пишите на следующий адрес premium-rs@microsoft.com.
  
 Если параметр EDITION задан, а MAXSIZE нет, то параметру MAXSIZE задается самое ограничивающее значение, поддерживаемое этим выпуском.  
  
 *MAXSIZE*  
 Указывает максимальный размер базы данных. Значение параметра MAXSIZE должно быть допустимо для указанного значения параметра EDITION (уровень службы). Далее приведены поддерживаемые значения MAXSIZE и значения по умолчанию (D) для уровней службы.  
  
|**MAXSIZE**|**Basic**|**S0–S2**|**S3–S12**|**P1–P6**| **P11–P15** 
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
|300 ГБ|Недоступно|Недоступно|√|√|√|  
|400 ГБ|Недоступно|Недоступно|√|√|√|
|500 ГБ|Недоступно|Недоступно|√|√ (D)|√|
|750 ГБ|Недоступно|Недоступно|√|√|√|
|1024 ГБ|Недоступно|Недоступно|√|√|√ (D)|
|От 1024 до 4096 ГБ с шагом приращения 256 ГБ * |Недоступно|Недоступно|Недоступно|Недоступно|√|√|  
  
 \* P11 и P15 позволяют задавать параметру MAXSIZE значение до 4 ТБ, при этом размер по умолчанию — 1024 ГБ.  P11 и P15 могут использовать до 4 ТБ включенного объема хранилища без дополнительной платы. На уровне Premium использование MAXSIZE со значением более 1 ТБ сейчас доступно в следующих регионах: восточная часть США 2, западная часть США, Виргиния (для обслуживания государственных организаций США), Западная Европа, Центральная Германия, Юго-Восточная Азия, Восточная Япония, Восточная Австралия, Центральная Канада и Восточная Канада. Текущие ограничения: [отдельные базы данных](https://docs.microsoft.com/azure/sql-database-single-database-resources).  
<!---Loc Comment: Link [Single databases] is not working---> 
  
 Следующие правила применяются к аргументам MAXSIZE и EDITION:  
  
-   Значение MAXSIZE, если оно задано, должно быть одним из допустимых значений, приведенных в таблице выше.  
  
-   Если параметр EDITION указан, а параметр MAXSIZE — нет, то в качестве выпуска будет использоваться значение по умолчанию. Например, если параметру EDITION задано значение Standard, а параметру MAXSIZE значение не задано, MAXSIZE автоматически получает значение 250 МБ.  
  
-   Если не указаны значения ни для MAXSIZE, ни для EDITION, то параметру EDITION задается значение Standard (S0), а параметру MAXSIZE — 250 ГБ.  
  
 SERVICE_OBJECTIVE  
 Определяет уровень производительности. Описания целевых уровней служб и дополнительные сведения о сочетаниях размеров, выпусков и целевых уровней: [Уровни служб и уровни производительности баз данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/), [Ограничения ресурсов базы данных SQL](https://azure.microsoft.com/documentation/articles/sql-database-resource-limits). Если указанное значение SERVICE_OBJECTIVE не поддерживается для значения EDITION, вы получите сообщение об ошибке.  
  
 ELASTIC_POOL (name = \<имя_эластичного_пула>): чтобы создать базу данных в эластичном пуле, задайте параметру SERVICE_OBJECTIVE базы данных значение ELASTIC_POOL и укажите имя пула. Дополнительные сведения: [Управление несколькими базами данных SQL Azure и их масштабирование с помощью эластичных пулов](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/).  
  
 *AS COPY OF [<имя_исходного_сервера>.]<имя_исходной_базы>*  
 Для копирования базы данных на тот же или другой сервер [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 *<имя_исходного_сервера>*  
 Имя сервера [!INCLUDE[ssSDS](../../includes/sssds-md.md)], на котором размещена база данных-источник. Этот параметр не является обязательным, если исходная и конечная базы данных расположены на одном сервере [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Примечание. Аргумент `AS COPY OF` не поддерживает уникальные полные доменные имена. Другими словами, если полное доменное имя сервера —`serverName.database.windows.net`, во время копирования базы данных используйте только `serverName`.  
  
 *<имя_исходной_базы>*  
 Имя копируемой базы данных.  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] не поддерживает следующие аргументы и параметры при использовании инструкции `CREATE DATABASE`:  
  
-   Параметры, связанные с физическим размещением файла, например \<filespec> и \<filegroup>  
  
-   Параметры внешнего доступа, например DB_CHAINING и TRUSTWORTHY.  
  
-   Присоединение базы данных.  
  
-   Параметры Service Broker, например ENABLE_BROKER NEW_BROKER и ERROR_BROKER_CONVERSATIONS.  
  
-   Моментальный снимок базы данных  
  
 Дополнительные сведения об аргументах и инструкции `CREATE DATABASE`: [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
## <a name="remarks"></a>Remarks  
 Базы данных в [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] используют несколько параметров по умолчанию, устанавливаемых при создании базы данных. Дополнительные сведения об этих параметрах по умолчанию см. в списке значений для [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md).  
  
 Параметр MAXSIZE позволяет ограничить размер базы данных. Если размер базы данных достигает ее значения MAXSIZE, выдается ошибка с кодом 40544. В этом случае данные нельзя вставить или обновить данные и создать новые объекты (например, таблицы, представления, хранимые процедуры и функции). Однако можно по-прежнему читать и удалять данные, усекать и удалять таблицы и индексы, а также выполнять перестроение индексов. Затем можно изменить значение MAXSIZE на значение, превышающее текущий размер базы данных, или удалить некоторые данные, чтобы освободить место в хранилище. Перед возобновлением возможности вставлять новые данные может пройти до 15 минут.  
  
> [!IMPORTANT]  
>  Инструкция `CREATE DATABASE` должна быть единственной инструкцией в пакете [!INCLUDE[tsql](../../includes/tsql-md.md)]. 
  
 Используйте [ALTER DATABASE &#40;База данных SQL Azure&#41;](../../t-sql/statements/alter-database-azure-sql-database.md), чтобы в дальнейшем изменять значения размера, выпуска или целевого уровня службы.  

Аргумент CATALOG_COLLATION доступен только во время создания базы данных. 
  
## <a name="database-copies"></a>Копирование баз данных  
 Копирование базы данных с помощью инструкции `CREATE DATABASE` — это асинхронная операция. Поэтому соединение с сервером [!INCLUDE[ssSDS](../../includes/sssds-md.md)] не требуется в течение всего процесса копирования. Инструкция `CREATE DATABASE` возвращает управление пользователю после создания записи в sys.databases, но до завершения операции копирования базы данных. Другими словами, инструкция `CREATE DATABASE` возвращает контроль, когда база данных все еще копируется.  
  
-   Наблюдение за процессом копирования на сервере [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]: запросите столбцы `percentage_complete` или `replication_state_desc` в [dm_database_copies](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md) или столбец `state` в представлении **sys.databases**. Вы также можете использовать представление [sys.dm_operation_status](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md), так как оно возвращает состояние операций с базой данных, включая ее копирование.  
  
 После успешного завершения копирования целевая база данных транзакционно согласована с базой данных-источником.  
  
 К аргументу `AS COPY OF` применяются следующие синтаксические и семантические правила.  
  
-   Имя исходного и целевого сервера для копирования могут совпадать или отличаться. Если они совпадают, этот параметр не является обязательным, а по умолчанию используется контекст сервера текущего сеанса.  
  
-   Необходимо указать имена исходной и целевой базы данных. Они должны быть уникальными и соответствовать правилам для идентификаторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения: [Идентификаторы](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
-   Инструкция `CREATE DATABASE` должна выполняться в контексте базы данных master на сервере [!INCLUDE[ssSDS](../../includes/sssds-md.md)], на котором будет создана новая база данных.  
  
-   После завершения копирования целевой базой данных необходимо управлять как независимой базой данных. Инструкции `ALTER DATABASE` и `DROP DATABASE` для новой базы данных можно выполнять независимо от базы данных-источника. Новую базу данных также можно скопировать в другую новую базу данных.  
  
-   Пока выполняется копирование базы данных, база данных-источник остается доступной.  
  
 Дополнительные сведения: [Копирование базы данных SQL Azure с использованием Transact-SQL](https://azure.microsoft.com/documentation/articles/sql-database-copy-transact-sql/).  
  
## <a name="permissions"></a>Разрешения  
 Создавать базу данных могут следующие пользователи.  
  
-   Субъект серверного уровня  
  
-   Администратор Azure AD для локального сервера SQL Server Azure  
  
-   Участник роли базы данных `dbmanager`  
  
 **Дополнительные требования по использованию синтаксиса `CREATE DATABASE ... AS COPY OF`:** пользователь, запускающий инструкцию на локальном сервере, должен также иметь как минимум роль `db_owner` на исходном сервере. Если вход основан на проверке подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то запускающий инструкцию на локальном сервере пользователь должен также существовать на исходном сервере [!INCLUDE[ssSDS](../../includes/sssds-md.md)] с идентичным именем для входа и паролем.  
  
## <a name="examples"></a>Примеры  
Краткое руководство по подключению к базе данных SQL Azure с помощью SQL Server Management Studio см. в статье [Подключайтесь к базе данных SQL Azure и создавайте запросы к ней с помощью SQL Server Management Studio](/azure/sql-database/sql-database-connect-query-ssms).  
  
### <a name="simple-example"></a>Простой пример  
 Простой пример создания базы данных.  
  
```sql  
CREATE DATABASE TestDB1;  
```  
  
### <a name="simple-example-with-edition"></a>Простой пример с указанием выпуска  
 Простой пример создания базы данных Standard.  
  
```sql  
CREATE DATABASE TestDB2  
( EDITION = 'standard' );  
```  
  
### <a name="example-with-additional-options"></a>Пример с дополнительными параметрами  
 Пример, где используются несколько параметров.  
  
```sql  
CREATE DATABASE hito   
COLLATE Japanese_Bushu_Kakusu_100_CS_AS_KS_WS   
( MAXSIZE = 500 MB, EDITION = 'standard', SERVICE_OBJECTIVE = 'S1' ) ;  
```  
  
### <a name="creating-a-copy"></a>Создание копии  
 Пример создания копии базы данных.  
  
```sql  
CREATE DATABASE escuela   
AS COPY OF school;  
```  
  
### <a name="creating-a-database-in-an-elastic-pool"></a>Создание базы данных в эластичном пуле  
 Создает новую базу данных в пуле с именем S3M100.  
  
```sql  
CREATE DATABASE db1 ( SERVICE_OBJECTIVE = ELASTIC_POOL ( name = S3M100 ) ) ;  
```  
  
### <a name="creating-a-copy-of-a-database-on-another-server"></a>Создание копии базы данных на другом сервере  
 В следующем примере создается копия базы данных db_original с именем db_copy и уровнем производительности P2, заданным для одной базы данных.  Это происходит вне зависимости от того, находится ли db_original в эластичном пуле и имеет ли эта база уровень производительности, заданный для одной базы данных.  
  
```sql  
CREATE DATABASE db_copy   
    AS COPY OF ozabzw7545.db_original ( SERVICE_OBJECTIVE = 'P2' )  ;  
```  
  
 В следующем примере создается копия базы данных db_original с именем db_copy в эластичном пуле с именем ep1.  Это происходит вне зависимости от того, находится ли db_original в эластичном пуле и имеет ли эта база уровень производительности, заданный для одной базы данных.  Если db_original находится в эластичном пуле с другим именем, db_copy все равно создается в ep1.  
  
```sql  
CREATE DATABASE db_copy   
    AS COPY OF ozabzw7545.db_original   
    (SERVICE_OBJECTIVE = ELASTIC_POOL( name = ep1 ) ) ;  
```  

### <a name="create-database-with-specified-catalog-collation-value"></a>Создание базы данных с указанным значением параметров сортировки каталога

В следующем примере во время создания базы данных параметрам сортировки каталога задается значение DATABASE_DEFAULT, за счет чего параметры сортировки каталога совпадают с параметрами сортировки базы данных.

```sql
CREATE DATABASE TestDB3 COLLATE Japanese_XJIS_140  (MAXSIZE = 100 MB, EDITION = ‘basic’)  
      WITH CATALOG_COLLATION = DATABASE_DEFAULT 
```
  
## <a name="see-also"></a>См. также раздел  

-  [sys.dm_database_copies &#40;база данных SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)

-   [ALTER DATABASE &#40;база данных SQL Azure&#41;](alter-database-azure-sql-database.md)   
    
  

