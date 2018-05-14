---
title: CREATE DATABASE (хранилище данных SQL Azure) | Microsoft Docs
ms.custom: ''
ms.date: 02/14/20178
ms.prod: ''
ms.prod_service: sql-data-warehouse
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 621d348cface10d459693fc64b261fc2fa2ddf04
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="create-database-azure-sql-data-warehouse"></a>CREATE DATABASE (хранилище данных SQL Azure)
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
Имя новой базы данных. Это имя должно быть уникальным на сервере SQL Server, где могут размещаться базы данных [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] и [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Кроме того, оно должно соответствовать правилам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для идентификаторов. Дополнительные сведения: [Идентификаторы](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
*collation_name*  
Задает параметры сортировки по умолчанию для базы данных. Именем параметров сортировки может быть либо имя параметров сортировки Windows, либо имя параметров сортировки SQL. Если параметры не указаны, базе данных назначаются параметры сортировки по умолчанию — SQL_Latin1_General_CP1_CI_AS.  
  
Дополнительные сведения об именах параметров сортировки Windows и SQL: [COLLATE (Transact-SQL)](http://msdn.microsoft.com/library/ms184391.aspx).  
  
*EDITION*  
Указывает уровень службы базы данных. Для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] используйте "datawarehouse".  
  
*MAXSIZE*  
Значение по умолчанию — 245 760 ГБ (240 ТБ).  

**Область применения:** уровень производительности "Оптимизация под гибкость"

Максимально допустимый размер базы данных. Размер базы данных не может превышать MAXSIZE. 

**Область применения:** уровень производительности "Оптимизация под вычисление"

Максимально допустимый размер данных rowstore в базе данных. Размер данных, хранящихся в таблицах rowstore, разностном хранилище индекса columnstore или некластеризованном индексе на базе кластеризованного индекса columnstore, не может превышать MAXSIZE.  Данные, сжатые в формат columnstore, не имеют ограничений на размер и не ограничивается значением MAXSIZE.
  
SERVICE_OBJECTIVE  
Определяет уровень производительности. Дополнительные сведения о целевых уровнях служб для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] см. на странице [Уровни производительности](https://azure.microsoft.com/documentation/articles/performance-tiers/).  
  
## <a name="general-remarks"></a>Общие замечания  
Используйте [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md), чтобы просмотреть свойства базы данных.  
  
Используйте [ALTER DATABASE &#40;Хранилище данных SQL Azure&#41;](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md), чтобы в дальнейшем изменять значения максимального размера или целевого уровня службы.   

Для хранилища данных SQL задано значение COMPATIBILITY_LEVEL 130, изменить которое невозможно. Дополнительные сведения: [Улучшение производительности запросов с уровнем совместимости 130 в базе данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/).
  
## <a name="permissions"></a>Разрешения  
Необходимые разрешения:  
  
-   имя входа субъекта серверного уровня, созданное процессом подготовки или  
  
-   член роли базы данных `dbmanager`.  
  
## <a name="error-handling"></a>Обработка ошибок  
Если размер базы данных достигает значения MAXSIZE, выдается ошибка с кодом 40544. В этом случае вы не сможете вставлять и изменять данные или создавать новые объекты (например, таблицы, хранимые процедуры, представления и функции). Вы по-прежнему можете считывать и удалять данные, усекать и удалять таблицы и индексы, а также выполнять перестроение индексов. Затем можно изменить значение MAXSIZE на значение, превышающее текущий размер базы данных, или удалить некоторые данные, чтобы освободить место в хранилище. Перед возобновлением возможности вставлять новые данные может пройти до 15 минут.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
Для создания новой базы данных необходимо подключение к базе данных master.  
  
Инструкция `CREATE DATABASE` должна быть единственной инструкцией в пакете [!INCLUDE[tsql](../../includes/tsql-md.md)].

После создания базы данных изменить ее параметры сортировки будет невозможно.   
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]  
  
### <a name="a-simple-example"></a>A. Простой пример  
Простой пример создания базы данных хранилища данных. В примере создается база данных с наименьшим максимальным размером, равным 10 240 ГБ, параметром сортировки по умолчанию SQL_Latin1_General_CP1_CI_AS и наименьшей вычислительной мощностью DW100.  
  
```  
CREATE DATABASE TestDW  
(EDITION = 'datawarehouse', SERVICE_OBJECTIVE='DW100');  
```  
  
### <a name="b-create-a-data-warehouse-database-with-all-the-options"></a>Б. Создание базы данных хранилища данных со всеми параметрами  
Пример создания хранилища данных объемом 10 ТБ с использованием всех параметров.  
  
```  
CREATE DATABASE TestDW COLLATE Latin1_General_100_CI_AS_KS_WS  
(MAXSIZE = 10240 GB, EDITION = 'datawarehouse', SERVICE_OBJECTIVE = 'DW1000');  
```  
  
## <a name="see-also"></a>См. также:  
[ALTER DATABASE &#40;хранилище данных SQL Azure&#40;](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md)
[CREATE TABLE &#40;хранилище данных SQL Azure&#41;](../../t-sql/statements/create-table-azure-sql-data-warehouse.md) 
[DROP DATABASE &#40;Transact-SQL&#40;](../../t-sql/statements/drop-database-transact-sql.md) 
  

