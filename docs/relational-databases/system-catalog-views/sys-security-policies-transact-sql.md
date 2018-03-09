---
title: "sys.security_policies (Transact-SQL) | Документы Microsoft"
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
- SYS.SECURITY_POLICIES_TSQL
- SECURITY_POLICIES_TSQL
- SYS.SECURITY_POLICIES
- SECURITY_POLICIES
dev_langs:
- TSQL
helpviewer_keywords:
- sys.security_policies catalog view
- security_policies catalog view
ms.assetid: 35362f5b-e601-4049-9e1d-c5307e823831
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9e30a903e31ce8ba7951f9756a8fd258375fb8e2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="syssecuritypolicies-transact-sql"></a>sys.security_policies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает строку для каждой политики безопасности в базе данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|имя|**sysname**|Уникальное имя политики безопасности в базе данных.|  
|object_id|**int**|Идентификатор политики безопасности.|  
|principal_id|**int**|Идентификатор владельца политики безопасности, зарегистрированный в базе данных. Значение NULL, если владелец определяется посредством схемы.|  
|schema_id|**int**|Идентификатор схемы, в которой находится объект.|  
|parent_object_id|**int**|Идентификатор объекта, которому принадлежит данная политика. Должно быть равно 0.|  
|Тип|**vachar(2)**|Должно быть **SP**.|  
|type_desc|**nvarchar(60)**|**SECURITY_POLICY**.|  
|create_date|**datetime**|Дата создания политики безопасности в формате UTC.|  
|modify_date|**datetime**|Дата последнего изменения политики безопасности в формате UTC.|  
|is_ms_shipped|**bit**|Всегда значение false.|  
|is_enabled|**bit**|Состояние спецификации политики безопасности.<br /><br /> 0 = отключен<br /><br /> 1 = включен|  
|is_not_for_replication|**bit**|Политика была создана с параметром NOT FOR REPLICATION.|  
|uses_database_collation|**bit**|Использует те же параметры сортировки, что и база данных.|  
|is_schemabinding_enabled|**bit**|Состояние предложения SCHEMABINDING для политики безопасности:<br /><br /> 0 или NULL = включено<br /><br /> 1 = отключено|  
  
## <a name="permissions"></a>Permissions  
 Участники **ALTER ANY SECURITY POLICY** разрешение имеют доступ ко всем объектам в этом представлении каталога, а также все, кто имеет **VIEW DEFINITION** в объекте.  
  
## <a name="see-also"></a>См. также:  
 [Безопасность на уровне строк](../../relational-databases/security/row-level-security.md)   
 [sys.security_predicates (Transact-SQL)](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)   
 [CREATE SECURITY POLICY (Transact-SQL)](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
