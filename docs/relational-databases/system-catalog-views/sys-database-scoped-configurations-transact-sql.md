---
title: sys.database_scoped_configurations (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/16/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- database_scoped_configurations
- database_scoped_configurations_TSQL
- sys.database_scoped_configurations
- sys.database_scoped_configurations_TSQL
helpviewer_keywords:
- sys.database_scoped_configurations catalog view
ms.assetid: 8899310a-3464-4d38-9f2f-88396c4e7dc2
caps.latest.revision: 13
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d9a7d363dbab2a552c54bffedfc92fe6cf49a708
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdatabasescopedconfigurations-transact-sql"></a>sys.database_scoped_configurations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой конфигурации. 
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**int**|Идентификатор параметра конфигурации.|  
|**name**|**nvarchar(60)**|Имя параметра конфигурации. Сведения о возможных конфигурациях см. в разделе [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|  
|**value**|**SQLVARIANT**|Значение, заданное для этого параметра конфигурации для первичной реплики.|  
|**value_for_secondary**|**SQLVARIANT**|Значение, заданное для этого параметра конфигурации для вторичных реплик.|  
  
##  <a name="Permissions"></a> Разрешения  
 Необходимо быть членом роли **public** .  
  
## <a name="remarks"></a>Замечания  
 Если возвращается значение NULL как значение для **value_for_secondary**, это означает, что сервер-получатель является первичной.  
 
 Параметры конфигурации уровня базы данных будут перенесены вместе с базой данных. Это означает, что при восстановлении или прикреплении заданной базы данных существующие параметры конфигурации будут сохранены.
  
## <a name="see-also"></a>См. также  
 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)  
  
  
