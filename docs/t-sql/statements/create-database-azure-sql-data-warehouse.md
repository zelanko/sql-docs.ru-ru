---
title: "Создание базы данных (хранилище данных Azure SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/16/2017
ms.prod: 
ms.prod_service: sql-data-warehouse
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.openlocfilehash: 7406a538eb4c0f236f2e0d444e96fd2c4fa5d585
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="create-database-azure-sql-data-warehouse"></a>Создание базы данных (хранилище данных Azure SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Создает новую базу данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CREATE DATABASE database_name [ COLLATE collation_name ]  
(  
    [ MAXSIZE = { 
          250 | 500 | 750 | 1024 | 5120 | 10240 | 20480 | 30720 
        | 40960 | 51200 | 61440 | 71680 | 81920 | 92160 | 102400 
        | 153600 | 204800 | 245760 
      } GB ,
    ]  
    EDITION = 'datawarehouse',  
    SERVICE_OBJECTIVE = { 
         'DW100' | 'DW200' | 'DW300' | 'DW400' | 'DW500' | 'DW600' 
        | 'DW1000' | 'DW1200' | 'DW1500' | 'DW2000' | 'DW3000' | 'DW6000' 
        | 'DW1000c' | 'DW1500c' | 'DW2000c' | 'DW2500c' | 'DW3000c' | 'DW5000c' 
        | 'DW6000c' | 'DW7500c' | 'DW10000c' | 'DW15000c' | 'DW30000c'
    }  
)  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
*database_name*  
Имя новой базы данных. Это имя должно быть уникальным на сервере SQL server, который может разместить оба [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] баз данных и [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] базы данных и соответствовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] правилам для идентификаторов. Дополнительные сведения см. в разделе [идентификаторы](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
*collation_name*  
Задает параметры сортировки по умолчанию для базы данных. Именем параметров сортировки может быть либо имя параметров сортировки Windows, либо имя параметров сортировки SQL. Если не указан, базе данных назначаются параметры сортировки по умолчанию, который является SQL_Latin1_General_CP1_CI_AS.  
  
Дополнительные сведения об именах параметров сортировки Windows и SQL см. в разделе [COLLATE (Transact-SQL)](http://msdn.microsoft.com/library/ms184391.aspx).  
  
*ВЫПУСК*  
Указывает уровень службы базы данных. Для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] использовать «хранилище данных».  
  
*ПАРАМЕТР MAXSIZE*  
Значение по умолчанию — базе 10240 ГБ (10 ТБ).  

**Применяется к:** оптимизирован для эластичности уровня производительности

Максимально допустимый размер для базы данных. Базы данных не превысит значение MAXSIZE. 

**Применяется к:** , обеспечивающее уровень производительности вычислений

Максимально допустимый размер базы данных rowstore. Данные, хранящиеся в таблицы rowstore deltastore индекс columnstore и некластеризованный индекс в кластеризованный индекс columnstore не может увеличиваться за пределами MAXSIZE.  Данные, сжатые в формате columnstore не имеет ограничение на размер и не ограничивается MAXSIZE.
  
SERVICE_OBJECTIVE  
Определяет уровень производительности. Дополнительные сведения о цели обслуживания для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], в разделе [уровни производительности](https://azure.microsoft.com/documentation/articles/performance-tiers/).  
  
## <a name="general-remarks"></a>Общие замечания  
Используйте [DATABASEPROPERTYEX &#40; Transact-SQL &#41; ](../../t-sql/functions/databasepropertyex-transact-sql.md) для просмотра свойств базы данных.  
  
Используйте [ALTER базы данных &#40; Хранилище данных Azure SQL &#41; ](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md) для изменения максимального размера или более поздней версии службы значения цели.   

Хранилище данных SQL имеет значение COMPATIBILITY_LEVEL 130 и не может быть изменено. Дополнительные сведения см. в разделе [повысить производительность запросов с 130 уровень совместимости базы данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/).
  
## <a name="permissions"></a>Permissions  
Требуемые разрешения:  
  
-   Сервер уровня имя входа субъекта, созданное процессом подготовки или  
  
-   Член `dbmanager` роли базы данных.  
  
## <a name="error-handling"></a>Обработка ошибок  
Если размер базы данных достигает значения MAXSIZE, вы получите код ошибки 40544. В этом случае нельзя вставлять и обновлять данные или создавать новые объекты (такие как таблицы, хранимые процедуры, представления и функции). Вы можно по-прежнему читать и удалять данные, усекать таблицы, удалять таблицы и индексы и перестроение индексов. Затем можно изменить значение MAXSIZE на значение, превышающее текущий размер базы данных, или удалить некоторые данные, чтобы освободить место в хранилище. Перед возобновлением возможности вставлять новые данные может пройти до 15 минут.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
Для создания новой базы данных необходимо подключение к базе данных master.  
  
Инструкция `CREATE DATABASE` должна быть единственной инструкцией в пакете [!INCLUDE[tsql](../../includes/tsql-md.md)].

Параметры сортировки базы данных нельзя изменить после создания базы данных.   
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd"></a>Примеры:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]  
  
### <a name="a-simple-example"></a>A. Простой пример  
Простой пример для создания базы данных хранилища данных. Это создает базу данных с наименьшим максимальный размер — 10240 ГБ, параметры сортировки по умолчанию: SQL_Latin1_General_CP1_CI_AS и наименьшее вычислительной мощности, который является DW100.  
  
```  
CREATE DATABASE TestDW  
(EDITION = 'datawarehouse', SERVICE_OBJECTIVE='DW100');  
```  
  
### <a name="b-create-a-data-warehouse-database-with-all-the-options"></a>Б. Создать базу данных хранилища данных со всеми параметрами  
Пример создания 10 терабайт хранилища данных, с использованием всех параметров.  
  
```  
CREATE DATABASE TestDW COLLATE Latin1_General_100_CI_AS_KS_WS  
(MAXSIZE = 10240 GB, EDITION = 'datawarehouse', SERVICE_OBJECTIVE = 'DW1000');  
```  
  
## <a name="see-also"></a>См. также:  
[ALTER DATABASE &#40; Хранилище данных Azure SQL &#40; ](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md) 
 [Создание таблицы &#40; Хранилище данных Azure SQL &#41; ](../../t-sql/statements/create-table-azure-sql-data-warehouse.md)  
 [Удалить базы данных &#40; Transact-SQL &#40;](../../t-sql/statements/drop-database-transact-sql.md) 
  

