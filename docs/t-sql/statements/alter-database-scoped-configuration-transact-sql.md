---
title: "ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ALTER_DATABASE_SCOPED_CONFIGURATION
- ALTER_DATABASE_SCOPED_CONFIGURATION_TSQL
- DATABASE_SCOPED_CONFIGURATION_TSQL
- SCOPED_CONFIGURATION_TSQL
- SCOPED_TSQL
- ALTER_DATABASE_SCOPED_TSQL
- DATABASE_SCOPED_TSQL
helpviewer_keywords:
- ALTER DATABASE SCOPED CONFIGURATION statement
- configuration [SQL Server], ALTER DATABASE SCOPED CONFIGURATION statement
ms.assetid: 63373c2f-9a0b-431b-b9d2-6fa35641571a
caps.latest.revision: 32
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 0fbb1f0699328a59749e5bba7efd7661e9b36e5a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/21/2017

---
# <a name="alter-database-scoped-configuration-transact-sql"></a>ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Эта инструкция включает несколько параметров конфигурации базы данных на **отдельная база данных** уровне. Эта инструкция доступен в обеих [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] и [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Эти значения.  
  
- очистить кэш процедур;  
  
- задать для параметра MAXDOP произвольное значение (1, 2,...) для базы данных-источника в зависимости от того, что лучше всего подходит для конкретной базы данных, и указать другое значение (например, 0) всех используемых баз данных-получателей (например, для запросов отчетов);  
  
- настроить модель оценки кратности оптимизатора запросов независимо от уровня совместимости базы данных;  
  
- включить или выключить перехват параметров на уровне базы данных;
  
- включить или выключить исправления оптимизации запросов на уровне базы данных.

- Включить или отключить кэш идентификации на уровне базы данных.
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER DATABASE SCOPED CONFIGURATION  
{        
     {  [ FOR SECONDARY] SET <set_options>  }    
}  
| CLEAR PROCEDURE_CACHE  
| SET IDENTITY_CACHE = { ON | OFF }
[;]    
  
< set_options > ::=    
{  
    MAXDOP = { <value> | PRIMARY}    
    | LEGACY_CARDINALITY_ESTIMATION = { ON | OFF | PRIMARY}    
    | PARAMETER_SNIFFING = { ON | OFF | PRIMARY}    
    | QUERY_OPTIMIZER_HOTFIXES = { ON | OFF | PRIMARY}    
}  
  
```  
  
## <a name="arguments"></a>Аргументы  
 
БАЗЫ ДАННЫХ-ПОЛУЧАТЕЛЯ  
 
Задает параметры для баз данных-получателей (все базы данных-получатели должны иметь одинаковые значения).  
  
MAXDOP ** = ** {\<значение > | ОСНОВНОЙ}  
**\<Значение >**  
  
Указывает значение по умолчанию, следует использовать параметр MAXDOP для инструкций. значение по умолчанию 0 и указывает, что конфигурация сервера будет использоваться вместо этого. Переопределяет MAXDOP на уровне базы данных (если он установлен в 0) **максимальная степень параллелизма** заданы на уровне сервера с процедуры sp_configure. Указания запросов по-прежнему можно переопределить DB области для настройки определенных запросов, требующих другой параметр MAXDOP. Эти параметры ограничены MAXDOP для группы рабочей нагрузки.   

Для ограничения количества процессоров в плане параллельного выполнения может быть использован параметр max degree of parallelism. SQL Server учитывает планы параллельного выполнения для запросов, операций языка DDL индексами, параллельной вставки, сети изменить столбец, collectiion параллельных статистики и курсоры заполнения статических курсоров и.
 
Чтобы задать этот параметр на уровне экземпляра, в разделе [Настройка параметра max degree of parallelism Server Configuration Option](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md). 

> [!TIP] 
> Для выполнения этой задачи на уровне запроса, добавьте **MAXDOP** [указание запроса](../../t-sql/queries/hints-transact-sql-query.md).  
  
PRIMARY  
  
Может устанавливаться только для баз данных-получателей, пока база данных в на сервере-источнике и показывает, что конфигурация одному набору на сервере-источнике. Если конфигурация для основные изменения значения на сервере-получателе изменится соответствующим образом не требуется задать баз данных-получателей значение, явным образом данном. **ОСНОВНОЙ** параметр по умолчанию для баз данных-получателей.  
  
LEGACY_CARDINALITY_ESTIMATION ** = ** {ON | **OFF** | ОСНОВНОЙ}  

Позволяет задать модель оценки кратности оптимизатора запросов SQL Server 2012 и более ранней версии, независимо от уровня совместимости базы данных. Значение по умолчанию — **OFF**, которая задает модель оценки кратности оптимизатора запросов в зависимости от уровня совместимости базы данных. Установка этого параметра **ON** эквивалентен включению [флагу трассировки 9481](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). 

> [!TIP] 
> Для выполнения этой задачи на уровне запроса, добавьте **QUERYTRACEON** [указание запроса](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, для выполнения этой задачи на уровне запроса, добавьте **используйте ПОДСКАЗКУ** [указание запроса](../../t-sql/queries/hints-transact-sql-query.md) вместо использования флага трассировки. 
  
PRIMARY  
  
Это значение допустимо только для баз данных-получателей пока база данных на сервере-источнике в и задает значение, заданное для источника запроса оптимизатор параметр оценки количества элементов модели для всех баз данных-получателей. При изменении конфигурации на сервере-источнике для модель оценки кратности оптимизатора запросов, на сервере-получателе изменится соответствующим образом. **ОСНОВНОЙ** параметр по умолчанию для баз данных-получателей.  
  
PARAMETER_SNIFFING ** = ** { **ON** | ОТКЛЮЧИТЬ | ОСНОВНОЙ}  

Включает или отключает [пробное сохранение параметров](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing). Значение по умолчанию — ON. Это эквивалентно [флагу трассировки 4136](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).   

> [!TIP] 
> Для выполнения этой задачи на уровне запроса, в разделе **OPTIMIZE FOR UNKNOWN** [указание запроса](../../t-sql/queries/hints-transact-sql-query.md). Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, для выполнения этой задачи на уровне запроса **используйте ПОДСКАЗКУ** [указание запроса](../../t-sql/queries/hints-transact-sql-query.md) также доступна. 
  
PRIMARY  
  
Это значение допустимо только для баз данных-получателей пока база данных на сервере-источнике в и указывает, значение на всех баз данных-получателей для этого параметра значение, заданное для источника. Если на сервере-источнике с помощью конфигурации [пробное сохранение параметров](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing) изменений на сервере-получателе изменится соответствующим образом баз данных-получателей не требуется задать значение явным образом данном. Это значение по умолчанию для баз данных-получателей.  
  
QUERY_OPTIMIZER_HOTFIXES ** = ** {ON | **OFF** | ОСНОВНОЙ}  

Включает или отключает исправления оптимизации запросов независимо от уровня совместимости базы данных. Значение по умолчанию — **OFF**. Это эквивалентно Включение [флагу трассировки 4199](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).   

> [!TIP] 
> Для выполнения этой задачи на уровне запроса, добавьте **QUERYTRACEON** [указание запроса](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, для выполнения этой задачи на уровне запроса, добавить ПОДСКАЗКУ используйте [указание запроса](../../t-sql/queries/hints-transact-sql-query.md) вместо использования флага трассировки.  
  
PRIMARY  
  
Это значение допустимо только для баз данных-получателей пока база данных на сервере-источнике в и указывает, значение на всех баз данных-получателей для этого параметра значение, заданное для источника. Если конфигурация для основные изменения значения на сервере-получателе изменится соответствующим образом не требуется задать баз данных-получателей значение, явным образом данном. Это значение по умолчанию для баз данных-получателей.  
  
ОЧИСТИТЬ PROCEDURE_CACHE  

Очищает кэш процедур для базы данных. Это может быть выполнена на сервере-источнике и баз данных-получателей.  

IDENTITY_CACHE = { **ON** | {OFF}  

**Применяется к**: 2017 и Azure SQL базы данных SQL Server (компонент находится в общедоступной предварительной версии) 

Включает или отключает кэш идентификации на уровне базы данных. Значение по умолчанию — **ON**. Кэширование удостоверение используется для повышения производительности INSERT для таблицы со столбцами идентификаторов. Чтобы избежать пропусков значений столбца идентификаторов в случаях, когда сервер неожиданно перезапускается или при сбое сервера-получателя, отключите параметр IDENTITY_CACHE. Этот параметр аналогичен SQL Server трассировки флаг 272, за исключением того, что оно может быть задано на уровне базы данных, а не только на уровне сервера.   

> [!NOTE] 
> Этот параметр можно задать только для ПЕРВИЧНОЙ. Дополнительные сведения см. в разделе [столбцы идентификаторов](create-table-transact-sql-identity-property.md).  
>

##  <a name="Permissions"></a> Разрешения  
 Необходимо изменить любой конфигурации области базы данных   
в базе данных. Это разрешение можно предоставить пользователем, имеющим разрешение CONTROL на базу данных  
  
## <a name="general-remarks"></a>Общие замечания  
 При настройке базы данных-получатели имеют разные области Параметры конфигурации из их основных всех баз данных-получателей будет использовать ту же конфигурацию. Нельзя настроить разные параметры для отдельных баз данных-получателей.  
  
 При выполнении этой инструкции приведет к очистке кэша процедур в текущей базе данных, это означает, что все запросы придется перекомпилировать.  
  
 Для запросов трехчастным, параметры для подключения к текущей базе данных для запроса будут выполняться, отличных от для модулей SQL (например, процедуры, функции и триггеры), которые компилируются в текущем контексте базы данных и поэтому будет использовать параметры База данных, в которой они находятся.  
  
 Событие ALTER_DATABASE_SCOPED_CONFIGURATION добавляется как события DDL, который может использоваться для запуска триггера DDL. Это дочерние группы ALTER_DATABASE_EVENTS триггера.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 **MAXDOP**  
  
 Детализированные параметры можно переопределить глобальных правил и, регулятор ресурсов можно ограничить все остальные параметры MAXDOP.  Логика для параметра MAXDOP выглядит следующим образом:  
  
-   Указание запроса переопределяет sp_configure и уровня базы данных установки. Если группа ресурсов значение MAXDOP для группы рабочей нагрузки:  
  
    -   Если указание запроса имеет значение 0 переопределяется параметр регулятора ресурсов.  
  
    -   Если указание запроса не равно 0, то не может превышать Настройка регулятора ресурсов.  
  
-   DB с областью действия параметра (если он не 0) переопределяет параметр хранимой процедуры sp_configure, при отсутствии указания запроса и ограничен Настройка регулятора ресурсов.  
  
-   Параметр хранимой процедуры sp_configure переопределяется параметр регулятора ресурсов.  
  
 **QUERY_OPTIMIZER_HOTFIXES**  
  
 При использовании QUERYTRACEON подсказки для оптимизатора запросов прежних версий или исправлений оптимизатора запросов будет условие OR между указание запроса и установки, то есть если либо включен, будут применяться параметры конфигурации уровня базы данных.  
  
 **GeoDR**  
  
 Для чтения вторичной базы данных, например группы доступности AlwaysOn и GeoReplication, используйте значение получателей, проверяя состояние базы данных. Хотя мы не перекомпилировать во время отработки отказа и технически основным есть запросы, использующие параметры получателя, идея заключается в том, что параметр между первичной и вторичной зависит только при рабочей нагрузке отличается, поэтому их переполнение кэша запросы используя оптимальной конфигурации, тогда как новые запросы будут принимать новые параметры, которые подходят для них.  
  
 **DacFx**  
  
 Поскольку ALTER DATABASE SCOPED CONFIGURATION — это новая функция в базе данных SQL Azure и SQL Server 2016, которая влияет на схему базы данных, Экспорт схемы (с данными или без) не будет невозможно импортировать с более старой версией SQL Server, например [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или < C2 настроек [!INCLUDE[ssSQLv14](../../includes/sssqlv14-md.md)] . Например, экспорт в [DACPAC](https://msdn.microsoft.com/library/ee210546.aspx#Anchor_3) или [BACPAC](https://msdn.microsoft.com/library/ee210546.aspx#Anchor_4) из [!INCLUDE[ssSDS](../../includes/sssds-md.md)] или [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] базы данных, используемой этой новой функции не удастся импортировать на сервер нижнего уровня.  
  
## <a name="metadata"></a>Метаданные  

[Sys.database_scoped_configurations &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md) системное представление предоставляет сведения о конфигурациях с областью в базе данных. Параметры уровня базы данных конфигурации отображаются только в sys.database_scoped_configurations как это переопределяет параметры по умолчанию сервера. [Sys.configurations &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) системное представление показывает только параметры на уровне сервера.  
  
## <a name="examples"></a>Примеры  
Эти примеры демонстрируют использование инструкции ALTER DATABASE SCOPED CONFIGURATION  
  
### <a name="a-grant-permission"></a>A. Предоставление разрешений  

В этом примере разрешения, необходимые для выполнения инструкции ALTER DATABASE SCOPED CONFIGURATION     
Пользователь [Joe].  
  
```tsql  
GRANT ALTER ANY DATABASE SCOPED CONFIGURATION to [Joe] ;  
```  
  
### <a name="b-set-maxdop"></a>Б. Значение MAXDOP  

В этом примере задается MAXDOP = 1 для базы данных-источника и MAXDOP = 4 для базы данных-получателя в случае географической репликации.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION SET MAXDOP = 1 ;  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=4 ;  
```  
  
В этом примере задается MAXDOP для базы данных-получателя должны совпадать, заданным для его базы данных-источника в случае географической репликации.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=PRIMARY ;
```  
  
### <a name="c-set-legacycardinalityestimation"></a>В. Набор LEGACY_CARDINALITY_ESTIMATION  

Этот пример устанавливает LEGACY_CARDINALITY_ESTIMATION в значение ON для базы данных-получателя в случае географической репликации.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION=ON ;  
```  
  
Этот пример устанавливает LEGACY_CARDINALITY_ESTIMATION для базы данных-получателя, как и для его базы данных-источника в случае географической репликации.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION=PRIMARY ;  
```  
  
### <a name="d-set-parametersniffing"></a>Г. Набор PARAMETER_SNIFFING  

В этом примере задает PARAMETER_SNIFFING OFF для базы данных-источника в случае географической репликации.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION SET PARAMETER_SNIFFING =OFF ;  
```  
  
В этом примере задает PARAMETER_SNIFFING OFF для базы данных-источника в случае географической репликации.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING=OFF ;  
```  
  
В этом примере устанавливается PARAMETER_SNIFFING для базы данных-получателя, он находится в базе данных-источнике   
в случае географической репликации.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING =PRIMARY ;  
```  
  
### <a name="e-set-queryoptimizerhotfixes"></a>Д. Набор QUERY_OPTIMIZER_HOTFIXES  

Значение QUERY_OPTIMIZER_HOTFIXES ON для базы данных-источника   
в случае географической репликации.  

```tsql  
ALTER DATABASE SCOPED CONFIGURATION SET QUERY_OPTIMIZER_HOTFIXES=ON ;  
```  
  
### <a name="f-clear-procedure-cache"></a>Е. Очистить кэш процедур  

Этот пример очищает кэш процедур (доступно только для базы данных-источника).  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE ;  
```  

### <a name="g-set-identitycache"></a>Ж. Набор IDENTITY_CACHE

**Применяется к**: 2017 и Azure SQL базы данных SQL Server (компонент находится в общедоступной предварительной версии) 

В этом примере отключается кэша идентификаторов.

```tsql 
ALTER DATABASE SCOPED CONFIGURATION SET IDENTITY_CACHE=OFF ; 
```

## <a name="additional-resources"></a>Дополнительные ресурсы

### <a name="maxdop-resources"></a>Ресурсы MAXDOP 
* [Рекомендации и инструкции для параметра конфигурации «max degree of parallelism» в SQL Server](https://support.microsoft.com/en-us/kb/2806535) 

### <a name="legacycardinalityestimation-resources"></a>LEGACY_CARDINALITY_ESTIMATION ресурсы    
* [Оценка количества элементов (SQL Server)](/sql-docs/docs/relational-databases/performance/cardinality-estimation-sql-server)
* [Оптимизация планов запроса с помощью средства оценки кратности SQL Server 2014](https://msdn.microsoft.com/library/dn673537.aspx)

### <a name="parametersniffing-resources"></a>PARAMETER_SNIFFING ресурсы    
* [«Я чуждо параметр!»](https://blogs.msdn.microsoft.com/queryoptteam/2006/03/31/i-smell-a-parameter/)

### <a name="queryoptimizerhotfixes-resources"></a>QUERY_OPTIMIZER_HOTFIXES ресурсы    
* [SQL Server модель оптимизатора запросов исправление трассировки флаг 4199 обслуживания](https://support.microsoft.com/en-us/kb/974006)

## <a name="more-information"></a>Дополнительные сведения  
 [sys.database_scoped_configurations &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md)   
 [sys.configurations (Transact-SQL)](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [Представления каталогов баз данных и файлов (Transact-SQL)](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Флаги трассировки &#40; Transact-SQL &#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)   
 [sys.Configurations &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)  
  
  

