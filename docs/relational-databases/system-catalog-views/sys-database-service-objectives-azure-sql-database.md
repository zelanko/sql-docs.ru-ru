---
title: sys.database_service_objectives (база данных SQL Azure) | Документы Microsoft
ms.custom: ''
ms.date: 08/30/2016
ms.prod: ''
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords:
- Пул эластичных БД
- пул эластичных управления
f1_keywords:
- DATABASE_SERVICE_OBJECTIVES_TSQL
ms.assetid: cecd8c31-06c0-4aa7-85d3-ac590e6874fa
caps.latest.revision: 16
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: a63c3142cdc5ca670117ef7d14c4d6079b575972
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="sysdatabaseserviceobjectives-azure-sql-database"></a>sys.database_service_objectives (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Возвращает выпуск (уровень службы), цель службы (ценовой категории) и имя эластичного пула, если таковые имеются, для базы данных Azure SQL или хранилище данных SQL Azure. Если в системе базы данных master на сервере базы данных SQL Azure, возвращает сведения обо всех базах данных. Для хранилища данных SQL Azure должен быть подключен к базе данных master.  
  
  
 Сведения о ценах см. в разделе [параметры базы данных SQL и производительность: цены на базы данных SQL](https://azure.microsoft.com/en-us/pricing/details/sql-database/) и [цены на хранилище данных SQL](https://azure.microsoft.com/pricing/details/sql-data-warehouse/).  
  
 Чтобы изменить параметры службы, в разделе [инструкции ALTER DATABASE (база данных SQL Azure)](../../t-sql/statements/alter-database-azure-sql-database.md) и [инструкции ALTER DATABASE (хранилище данных SQL Azure)](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md).  
  
 Представление sys.database_service_objectives содержит следующие столбцы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|int|Идентификатор базы данных, уникальное внутри экземпляра сервера базы данных SQL Azure. Joinable с [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|edition|sysname|Уровень обслуживания для базы данных или хранилища данных: **основные**, **Стандартная**, **Premium** или **хранилища данных**.|  
|значение service_objective|sysname|Ценовой категории базы данных. Если база данных находится в пуле эластичных, возвращает **ElasticPool**.<br /><br /> На **основные** уровня возвращает **основные**.<br /><br /> **Одной базы данных в уровень обслуживания standard** возвращает одно из следующих действий: S0, S1, S2 или S3.<br /><br /> **Одной базы данных в уровня premium** возвращает из следующих: P1, P2, P4, P6/P3 или P11.<br /><br /> **Хранилище данных SQL** возвращает DW100 через DW10000c.|  
|elastic_pool_name|sysname|Имя [эластичного пула](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/) , к которой принадлежит базе данных. Возвращает **NULL** при одной базы данных или warehoue данных базы данных.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется **dbManager** разрешений в базе данных master.  На уровне базы данных пользователь должен быть создателем или владельцем.  
  
## <a name="examples"></a>Примеры  
 Этот пример можно выполнить в базе данных master или для пользовательских баз данных. Запрос возвращает имя, службы и сведения уровня производительности баз данных.  
  
```sql  
SELECT  d.name,   
     slo.*    
FROM sys.databases d   
JOIN sys.database_service_objectives slo    
ON d.database_id = slo.database_id;  
  
```  
  
  
