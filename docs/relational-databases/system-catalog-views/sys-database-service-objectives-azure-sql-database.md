---
title: sys.database_service_objectives
titleSuffix: Azure SQL Database
ms.custom: seo-dt-2019
ms.date: 03/21/2018
ms.service: sql-database
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.topic: conceptual
keywords:
- Эластичный пул
- Эластичный пул, управление
f1_keywords:
- DATABASE_SERVICE_OBJECTIVES_TSQL
ms.assetid: cecd8c31-06c0-4aa7-85d3-ac590e6874fa
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 7a7dc1ff6c67845a02af431d2e36727c83fd279a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826464"
---
# <a name="sysdatabase_service_objectives-azure-sql-database"></a>sys.database_service_objectives (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Возвращает выпуск (уровень служб), Цель обслуживания (ценовая категория) и имя эластичного пула (если таковые имеются) для базы данных SQL Azure или хранилища данных SQL Azure. В системе базы данных master на сервере Базы данных SQL Azure возвращает сведения обо всех базах данных. Для использования хранилища данных SQL Azure необходимо подключиться к базе данных master.  
  
  
 Сведения о ценах см. в разделе [Параметры и производительность базы данных SQL: цены на базу данных SQL](https://azure.microsoft.com/pricing/details/sql-database/) и [цены на хранилище данных SQL](https://azure.microsoft.com/pricing/details/sql-data-warehouse/).  
  
 Сведения об изменении параметров службы см. в разделе [ALTER DATABASE (база данных SQL Azure)](../../t-sql/statements/alter-database-azure-sql-database.md) и [ALTER DATABASE (хранилище данных SQL Azure)](https://docs.microsoft.com/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest).  
  
 Представление sys. database_service_objectives содержит следующие столбцы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|INT|Идентификатор базы данных, уникальный в пределах экземпляра сервера базы данных SQL Azure. Соединение с [sys. databases &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|edition|sysname|Уровень служб для базы данных или хранилища данных: " **базовый**", " **стандартный**", " **премиум** " или " **хранилище данных**".|  
|service_objective|sysname|Ценовая категория базы данных. Если база данных находится в эластичном пуле, возвращает **ElasticPool**.<br /><br /> На уровне " **базовый** " возвращает значение " **базовый**".<br /><br /> **Одна база данных на уровне служб уровня "Стандартный** " возвращает одно из следующих состояний: S0, S1, S2, S3, S4, S6, S7, S9 или S12.<br /><br /> **Одна база данных на уровне Premium** возвращает следующие: P1, P2, P4, P6, P11 или P15.<br /><br /> **Хранилище данных SQL** возвращает DW100 через DW30000c.<br /><br /> Дополнительные сведения см. в разделе [отдельные базы данных](/azure/sql-database/sql-database-dtu-resource-limits-single-databases/), [эластичные пулы](/azure/sql-database/sql-database-dtu-resource-limits-elastic-pools/), [хранилища данных](/azure/sql-data-warehouse/what-is-a-data-warehouse-unit-dwu-cdwu/) .|  
|elastic_pool_name|sysname|Имя [эластичного пула](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/) , к которому принадлежит база данных. Возвращает **значение NULL** , если база данных является отдельной базой данных или варехауе данных.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение **dbManager** на базу данных master.  На уровне базы данных пользователь должен быть создателем или владельцем.  
  
## <a name="examples"></a>Примеры  
 Этот пример можно выполнить в базе данных master или в базах данных пользователей базы данных SQL Azure. Запрос возвращает сведения об имени, службе и уровне производительности баз данных.  
  
```sql  
SELECT  d.name,   
     slo.*    
FROM sys.databases d   
JOIN sys.database_service_objectives slo    
ON d.database_id = slo.database_id;  
  
```  
  
  
