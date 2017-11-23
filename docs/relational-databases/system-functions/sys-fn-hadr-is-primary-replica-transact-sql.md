---
title: "sys.fn_hadr_is_primary_replica (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.fn_hadr_is_primary_replica
- fn_hadr_is_primary_replica_TSQL
- fn_hadr_is_primary_replica
- sys.fn_hadr_is_primary_replica_TSQL
dev_langs: TSQL
helpviewer_keywords:
- fn_hadr_is_primary_replica
- sys.fn_hadr_is_primary_replica
ms.assetid: c9b1969f-be1d-4dfb-a33d-551f380b9e27
caps.latest.revision: "7"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: a6b9349b2c5240be78dbf9ea58b0da79b056afc7
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysfnhadrisprimaryreplica-transact-sql"></a>sys.fn_hadr_is_primary_replica (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Используется для определения, является ли текущая реплика первичной репликой.  
  
||  
|-|  
|**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_hadr_is_primary_replica ( 'dbname' )  
```  
  
## <a name="arguments"></a>Аргументы  
 "*dbname*"  
 Имя базы данных. *DBName* имеет тип sysname.  
  
## <a name="returns"></a>Возвращает  
 Возвращаемое значение равно 1, если база данных в текущем экземпляре является первичной. В противном случае возвращается 0.  
  
## <a name="remarks"></a>Замечания  
 Используйте эту функцию, чтобы определить, размещается ли первичная реплика указанной базы данных доступности в локальном экземпляре. Образец кода должен быть аналогичен следующему.  
  
```  
If sys.fn_hadr_is_primary_replica ( @dbname ) <> 1   
BEGIN  
-- If this is not the primary replica, exit (probably without error).  
END  
-- If this is the primary replica, continue to do the backup.  
  
```  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-sysfnhadrisprimaryreplica"></a>A. Использование sys.fn_hadr_is_primary_replica  
 Следующий пример возвращает 1, если указанная база данных на локальном экземпляре является первичной репликой.  
  
```  
SELECT sys.fn_hadr_is_primary_replica ('TestDB');  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции &#40; групп доступности AlwaysOn Transact-SQL &#41;](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [Группы доступности AlwaysOn &#40; SQL Server &#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [CREATE AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [Представления каталога &#40; групп доступности AlwaysOn Transact-SQL &#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)  
  
  
