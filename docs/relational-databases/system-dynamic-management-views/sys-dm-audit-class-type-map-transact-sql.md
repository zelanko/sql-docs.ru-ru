---
title: "sys.dm_audit_class_type_map (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_audit_class_type_map
- sys.dm_audit_class_type_map_TSQL
- dm_audit_class_type_map
- dm_audit_class_type_map_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_audit_class_type_map dynamic management view
ms.assetid: e10b5431-1bb0-47ca-8fd0-c04bd73a4410
caps.latest.revision: "12"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 739b29cfb6b6bbf36d20dc086f39b0d30c4cdac0
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmauditclasstypemap-transact-sql"></a>sys.dm_audit_class_type_map (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает таблицу, которая сопоставляет поле class_type в журнале аудита с полем class_desc в представлении sys.dm_audit_actions. Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] аудита, в разделе [подсистемы аудита SQL Server &#40; компонент Database Engine &#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  

|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**class_type**|**char(2)**|Тип класса сущности, для которой был проведен аудит. Сопоставляется class_type, записываются в журнал аудита и возвращенный **get_audit_file()** функции. Не допускает значение NULL.|  
|**class_type_desc**|**nvarchar(120)**|Имя сущности, для которой выполняется аудит. Не допускает значение NULL.|  
|**securable_class_desc**|**nvarchar(120)**|Защищаемый объект, сопоставляемый class_type, для которого выполняется аудит. Принимает значение NULL, если class_type не сопоставляется с защищаемым объектом. Может быть связан с class_desc в sys.dm_audit_actions.|  
  
## <a name="permissions"></a>Permissions  
 Участник должен иметь **ВЫБЕРИТЕ** разрешение. По умолчанию это разрешение предоставлено роли Public.  
  
## <a name="see-also"></a>См. также:  
 [Создание АУДИТА сервера &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [Создание СПЕЦИФИКАЦИИ АУДИТА сервера &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [СОЗДАТЬ СПЕЦИФИКАЦИЮ АУДИТА базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [УДАЛИТЬ СПЕЦИФИКАЦИЮ АУДИТА базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.fn_get_audit_file &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys.server_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_class_type_map](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Создание аудита сервера и спецификации аудита сервера](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
