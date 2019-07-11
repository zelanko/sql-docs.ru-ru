---
title: sys.database_service_objectives (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 03/21/2018
ms.service: sql-database
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.topic: conceptual
keywords:
- пул эластичных баз данных
- эластичный пул, управление
f1_keywords:
- DATABASE_SERVICE_OBJECTIVES_TSQL
ms.assetid: cecd8c31-06c0-4aa7-85d3-ac590e6874fa
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 1bd16b4ac7fb0b27296fb2cc7e47ec683d761ed4
ms.sourcegitcommit: aeb2273d779930e76b3e907ec03397eab0866494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67716645"
---
# <a name="sysdatabaseserviceobjectives-azure-sql-database"></a>sys.database_service_objectives (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Возвращает выпуск (уровень служб), цель обслуживания (ценовой категории) и имя эластичного пула, если таковые имеются, для базы данных Azure SQL или хранилище данных SQL Azure. Если вход в базу данных master на сервере базы данных SQL Azure, возвращает сведения обо всех базах данных. Для хранилища данных SQL Azure должны быть подключены к базе данных master.  
  
  
 Сведения о ценах см. в разделе [параметры базы данных SQL и производительность: Цены на базы данных SQL](https://azure.microsoft.com/pricing/details/sql-database/) и [цены на хранилище данных SQL](https://azure.microsoft.com/pricing/details/sql-data-warehouse/).  
  
 Чтобы изменить параметры службы, см. в разделе [ALTER DATABASE (база данных SQL Azure)](../../t-sql/statements/alter-database-azure-sql-database.md) и [ALTER DATABASE (хранилище данных SQL Azure)](https://docs.microsoft.com/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest).  
  
 Представление sys.database_service_objectives содержит следующие столбцы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|ssNoversion|Идентификатор базы данных, уникальный внутри экземпляра сервера базы данных SQL Azure. Присоединяемая с [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|edition|sysname|Уровень обслуживания для базы данных или хранилища данных: **Основные**, **стандартный**, **уровня "премиум"** или **хранилище данных**.|  
|параметр service_objective|sysname|Ценовая категория базы данных. Если база данных в эластичном пуле, возвращает **ElasticPool**.<br /><br /> На **основные** tier, возвращает **основные**.<br /><br /> **Отдельная база данных в категории "стандартный"** возвращает одно из следующих: S0, S1, S2, S3, S4, S6, S7, S9 и S12.<br /><br /> **Отдельной базы данных уровня "премиум"** возвращает из следующих: P1, P2, P4, P6, P11 или P15.<br /><br /> **Хранилище данных SQL** возвращает DW100 до DW30000c.|  
|elastic_pool_name|sysname|Имя [эластичного пула](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/) , к которой принадлежит базе данных. Возвращает **NULL** база данных находится в отдельной базы данных или warehoue данных.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется **dbManager** разрешений в базе данных master.  На уровне базы данных пользователь должен быть создателем или владельцем.  
  
## <a name="examples"></a>Примеры  
 Этот пример можно выполнить в базе данных master или для пользовательских баз данных базы данных SQL Azure. Запрос возвращает имя, службы и сведения об уровне производительности баз данных.  
  
```sql  
SELECT  d.name,   
     slo.*    
FROM sys.databases d   
JOIN sys.database_service_objectives slo    
ON d.database_id = slo.database_id;  
  
```  
  
  
