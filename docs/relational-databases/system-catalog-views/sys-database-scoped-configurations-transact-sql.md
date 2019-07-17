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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3439419bd3877b8ab7a951df58585703f169ee4f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68079450"
---
# <a name="sysdatabasescopedconfigurations-transact-sql"></a>sys.database_scoped_configurations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Содержит по одной строке на каждую конфигурацию. 
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**int**|Идентификатор параметра конфигурации.|  
|**name**|**nvarchar(60)**|Имя параметра конфигурации. Сведения о возможных конфигурациях см. в разделе [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|  
|**value**|**SQLVARIANT**|Значение, заданное для этого параметра конфигурации для первичной реплики.|  
|**value_for_secondary**|**SQLVARIANT**|Значение, заданное для этого параметра конфигурации для вторичных реплик.|  
|**is_value_default**|**bit** |Указывает, является ли заданное значение по умолчанию.|
  
##  <a name="Permissions"></a> Permissions  
Необходимо быть членом роли **public**.  
  
## <a name="remarks"></a>Примечания  
Если возвращается значение NULL в качестве значения для **value_for_secondary**, это означает, что получатель присвоено ОСНОВНОЙ.  
 
Параметры конфигурации уровня базы данных будут перенесены вместе с базой данных. Это означает, что при восстановлении или прикреплении заданной базы данных существующие параметры конфигурации будут сохранены.
  
## <a name="see-also"></a>См. также  
 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)  
  
  
