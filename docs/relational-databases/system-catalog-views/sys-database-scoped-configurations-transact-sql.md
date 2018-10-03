---
title: sys.database_scoped_configurations (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- database_scoped_configurations
- database_scoped_configurations_TSQL
- sys.database_scoped_configurations
- sys.database_scoped_configurations_TSQL
helpviewer_keywords:
- sys.database_scoped_configurations catalog view
ms.assetid: 8899310a-3464-4d38-9f2f-88396c4e7dc2
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 350f3af1bfd6e2765f74d074727577541378d2e2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47733842"
---
# <a name="sysdatabasescopedconfigurations-transact-sql"></a>sys.database_scoped_configurations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Содержит по одной строке на каждую конфигурацию. 
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**int**|Идентификатор параметра конфигурации.|  
|**name**|**nvarchar(60)**|Имя параметра конфигурации. Сведения о возможных конфигурациях см. в разделе [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|  
|**Значение**|**SQLVARIANT**|Значение, заданное для этого параметра конфигурации для первичной реплики.|  
|**value_for_secondary**|**SQLVARIANT**|Значение, заданное для этого параметра конфигурации для вторичных реплик.|  
|**elevate_online**|**nvarchar(60)** |Базы данных с заданной областью набора по умолчанию для параметра online для операций с индексами |
|**elevate_resumable**|nvarchar(60)|Базы данных с заданной областью набора по умолчанию для Возобновляемый параметр для операций с индексами| 
  
##  <a name="Permissions"></a> Permissions  
 Необходимо быть членом роли **public**.  
  
## <a name="remarks"></a>Примечания  
 Если возвращается значение NULL в качестве значения для **value_for_secondary**, это означает, что получатель присвоено ОСНОВНОЙ.  
 
 Параметры конфигурации уровня базы данных будут перенесены вместе с базой данных. Это означает, что при восстановлении или прикреплении заданной базы данных существующие параметры конфигурации будут сохранены.
  
## <a name="see-also"></a>См. также  
 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)  
  
  
