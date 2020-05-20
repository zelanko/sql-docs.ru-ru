---
title: sys. server_audit_specifications (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 04/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_audit_specifications_TSQL
- sys.server_audit_specifications_TSQL
- server_audit_specifications
- sys.server_audit_specifications
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_audit_specifications catalog view
ms.assetid: fa496c6c-2a54-4fda-a238-db490c6b3afd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 58ddd6013cb3289cb99ab6e600d2c771cc366f41
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82820959"
---
# <a name="sysserver_audit_specifications-transact-sql"></a>sys.server_audit_specifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения о спецификациях аудита сервера в подсистеме аудита SQL Server на экземпляре сервера. Дополнительные сведения об аудите SQL Server см. в разделе [Подсистема аудита SQL Server (ядро СУБД)](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**Имеет sysname**|Имя спецификации сервера.|  
|**server_specification_id**|**Int**|Идентификатор **server_specification**.|  
|**create_date**|**DateTime**|Дата создания спецификации аудита сервера.|  
|**modified_date**|**DateTime**|Дата последнего изменения спецификации аудита сервера.|  
|**is_state_enabled**|**tinyint**|Состояние спецификации аудита:<br /><br /> 0 — ОТКЛЮЧЕНО<br /><br /> 1 — ВКЛЮЧЕНО|  
|**audit_GUID**|**uniqueidentifier**|Идентификатор GUID аудита, содержащего эту спецификацию. Используется в процессе перечисления спецификаций аудита рядового сервера при запуске сервера.|  
  
## <a name="permissions"></a>Разрешения  
 Участники с разрешением **ALTER ANY SERVER AUDIT** или **View ANY DEFINITION** имеют доступ к этому представлению каталога. Кроме того, участнику не должно быть запрещено разрешение **View ANY DEFINITION** .  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
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
 [sys. server_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys. database_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys. database_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys. dm_server_audit_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys. dm_audit_actions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys. dm_audit_class_type_map &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Создание аудита сервера и спецификации аудита сервера](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
