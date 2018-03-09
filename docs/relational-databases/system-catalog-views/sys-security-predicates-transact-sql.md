---
title: "sys.security_predicates (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
f1_keywords:
- SYS.SECURITY_PREDICATES
- SECURITY_PREDICATES
- SECURITY_PREDICATES_TSQL
- SYS.SECURITY_PREDICATES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.security_predicates catalog view
- security_predicates catalog view
ms.assetid: c7a2f28c-98da-463d-8b8a-8e5619e2c6a6
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 472c9c6504b010d6abfea0d3161ada98e9e0f5f6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="syssecuritypredicates-transact-sql"></a>sys.security_predicates (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает строку для каждого предиката безопасности в базе данных.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Идентификатор политики безопасности, содержащей этот предикат.|  
|security_predicate_id|**int**|Идентификатор предиката в этой политике безопасности.|  
|target_object_id|**int**|Идентификатор объекта, к которому привязан этот предикат безопасности.|  
|predicate_definition|**nvarchar(max)**|Полное имя функции, которая будет использоваться в качестве предиката безопасности, включая аргументы. Обратите внимание, что `schema.function` может быть нормализовано (т. е. экранировано) как и любой другой элемент в тексте для обеспечения согласованности. Например:<br /><br /> `[dbo].[fn_securitypredicate]([wing], [startTime], [endTime])`|  
|predicate_type|**int**|Тип предикат, используемый в соответствии с политикой безопасности:<br /><br /> 0 = ПРЕДИКАТ ФИЛЬТРА<br /><br /> 1 = ПРЕДИКАТА БЛОКИРОВКИ|  
|predicate_type_desc|**nvarchar(60)**|Тип предикат, используемый в соответствии с политикой безопасности:<br /><br /> FILTER<br /><br /> БЛОК|  
|операции|**int**|Тип операции, заданной для предиката:<br /><br /> NULL = всех применимых операций.<br /><br /> 1 = ПОСЛЕ ВСТАВКИ<br /><br /> 2 = ПОСЛЕ ОБНОВЛЕНИЯ<br /><br /> 3 = ДО ОБНОВЛЕНИЯ<br /><br /> 4 = ДО УДАЛЕНИЯ|  
|operation_desc|**nvarchar(60)**|Тип операции, заданной для предиката:<br /><br /> NULL<br /><br /> ПОСЛЕ ВСТАВКИ<br /><br /> AFTER UPDATE<br /><br /> ПЕРЕД ОБНОВЛЕНИЕМ<br /><br /> ПРЕЖДЕ ЧЕМ УДАЛИТЬ|  
  
## <a name="permissions"></a>Permissions  
 Участники **ALTER ANY SECURITY POLICY** разрешение имеют доступ ко всем объектам в этом представлении каталога, а также все, кто имеет **VIEW DEFINITION** в объекте.  
  
## <a name="see-also"></a>См. также:  
 [Безопасность на уровне строк](../../relational-databases/security/row-level-security.md)   
 [sys.security_policies (Transact-SQL)](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [CREATE SECURITY POLICY (Transact-SQL)](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
