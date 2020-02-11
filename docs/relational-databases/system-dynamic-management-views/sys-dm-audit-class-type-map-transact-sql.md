---
title: sys. dm_audit_class_type_map (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_audit_class_type_map
- sys.dm_audit_class_type_map_TSQL
- dm_audit_class_type_map
- dm_audit_class_type_map_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_audit_class_type_map dynamic management view
ms.assetid: e10b5431-1bb0-47ca-8fd0-c04bd73a4410
author: stevestein
ms.author: sstein
ms.openlocfilehash: ae1c39d5c3ddc36f4ca3007cf9e17c2543055b85
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68099204"
---
# <a name="sysdm_audit_class_type_map-transact-sql"></a>sys.dm_audit_class_type_map (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Возвращает таблицу, которая сопоставляет поле class_type в журнале аудита с полем class_desc в представлении sys.dm_audit_actions. Дополнительные сведения об [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] аудите см. в разделе [SQL Server audit &#40;ядро СУБД&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  

|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**class_type**|**char (2)**|Тип класса сущности, для которой был проведен аудит. Сопоставляется с class_type записывается в журнал аудита и возвращается функцией **get_audit_file ()** . Не допускает значение NULL.|  
|**class_type_desc**|**nvarchar (120)**|Имя сущности, для которой выполняется аудит. Не допускает значение NULL.|  
|**securable_class_desc**|**nvarchar (120)**|Защищаемый объект, сопоставляемый class_type, для которого выполняется аудит. Принимает значение NULL, если class_type не сопоставляется с защищаемым объектом. Может быть связан с class_desc в sys.dm_audit_actions.|  
  
## <a name="permissions"></a>Разрешения  
 Участник должен иметь разрешение **SELECT** . По умолчанию это разрешение предоставлено роли Public.  
  
## <a name="see-also"></a>См. также:  
 [Создание аудита сервера &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [Удаление аудита сервера &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [Создание спецификации аудита сервера &#40;&#41;Transact-SQL](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40;&#41;Transact-SQL](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [УДАЛИТЬ СПЕЦИФИКАЦИю аудита сервера &#40;&#41;Transact-SQL](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [Создание спецификации аудита базы данных &#40;&#41;Transact-SQL](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [&#40;Transact-SQL&#41;спецификации ALTER DATABASE AUDIT](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [УДАЛИТЬ СПЕЦИФИКАЦИю аудита базы данных &#40;&#41;Transact-SQL](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys. fn_get_audit_file &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys. server_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys. server_file_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys. server_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys. server_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys. database_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys. database_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys. dm_server_audit_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys. dm_audit_class_type_map](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Создание аудита сервера и спецификации аудита сервера](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
