---
description: sys.fn_hadr_is_primary_replica (Transact-SQL)
title: sys. fn_hadr_is_primary_replica (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_hadr_is_primary_replica
- fn_hadr_is_primary_replica_TSQL
- fn_hadr_is_primary_replica
- sys.fn_hadr_is_primary_replica_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_hadr_is_primary_replica
- sys.fn_hadr_is_primary_replica
ms.assetid: c9b1969f-be1d-4dfb-a33d-551f380b9e27
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d3a7142e60b1abb4f820caf2f75f8ebdec3a0d8a
ms.sourcegitcommit: 8f062015c2a033f5a0d805ee4adabbe15e7c8f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2020
ms.locfileid: "91227400"
---
# <a name="sysfn_hadr_is_primary_replica-transact-sql"></a>sys.fn_hadr_is_primary_replica (Transact-SQL)
[!INCLUDE[sqlserver](../../includes/applies-to-version/sqlserver.md)]

  Используется для определения, является ли текущая реплика первичной репликой.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
sys.fn_hadr_is_primary_replica ( 'dbname' )  
```  
  
## <a name="arguments"></a>Аргументы  
 "*dbname*"  
 Имя базы данных. Аргумент *dbname* имеет тип sysname.  
  
## <a name="returns"></a>Результаты  
 Возвращает тип данных **bool**: 1, если база данных в текущем экземпляре является первичной репликой, в противном случае — 0.  
  
## <a name="remarks"></a>Remarks  
 Используйте эту функцию, чтобы определить, размещается ли первичная реплика указанной базы данных доступности в локальном экземпляре. Образец кода должен быть аналогичен следующему.  
  
```sql
If sys.fn_hadr_is_primary_replica ( @dbname ) <> 1   
BEGIN  
-- If this is not the primary replica, exit (probably without error).  
END  
-- If this is the primary replica, continue to do the backup.  
```  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-sysfn_hadr_is_primary_replica"></a>A. Использование sys.fn_hadr_is_primary_replica  
 Следующий пример возвращает 1, если указанная база данных на локальном экземпляре является первичной репликой.  
  
```sql
SELECT sys.fn_hadr_is_primary_replica ('TestDB');  
GO  
```    
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также:  
 [Функции группы доступности AlwaysOn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [sys. dm_hadr_database_replica_states &#40;Transact-SQL&#41;](../..//relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md) [группы доступности AlwaysOn &#40;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) SQL Server&#41;   
 [CREATE AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [Группы доступности AlwaysOn представления каталога &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)     
  
  
