---
description: sys. security_policies (Transact-SQL)
title: sys. security_policies (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
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
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ae97e6f310561339c24e712dd3d0f07552232bf2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490154"
---
# <a name="syssecurity_policies-transact-sql"></a>sys. security_policies (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Возвращает строку для каждой политики безопасности в базе данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Уникальное имя политики безопасности в базе данных.|  
|object_id|**int**|Идентификатор политики безопасности.|  
|principal_id|**int**|Идентификатор владельца политики безопасности, зарегистрированный в базе данных. Значение NULL, если владелец определяется посредством схемы.|  
|schema_id|**int**|Идентификатор схемы, в которой находится объект.|  
|parent_object_id|**int**|Идентификатор объекта, которому принадлежит данная политика. Должно быть равно 0.|  
|тип|**вачар (2)**|Должно быть **SP**.|  
|type_desc|**nvarchar(60)**|**SECURITY_POLICY**.|  
|create_date|**datetime**|Дата создания политики безопасности в формате UTC.|  
|modify_date|**datetime**|Дата последнего изменения политики безопасности в формате UTC.|  
|is_ms_shipped|**bit**|Всегда имеет значение false.|  
|is_enabled|**bit**|Состояние спецификации политики безопасности.<br /><br /> 0 = отключен<br /><br /> 1 = включен|  
|is_not_for_replication|**bit**|Политика была создана с параметром NOT FOR REPLICATION.|  
|uses_database_collation|**bit**|Использует те же параметры сортировки, что и база данных.|  
|is_schemabinding_enabled|**bit**|Состояние SCHEMABINDING для политики безопасности:<br /><br /> 0 или NULL = включено<br /><br /> 1 = отключено|  
  
## <a name="permissions"></a>Разрешения  
 Участники с разрешением **ALTER ANY Security Policy** имеют доступ ко всем объектам в этом представлении каталога, а также любому пользователю с **определением представления** для объекта.  
  
## <a name="see-also"></a>См. также:  
 [Безопасность на уровне строк](../../relational-databases/security/row-level-security.md)   
 [sys. security_predicates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)   
 [CREATE SECURITY POLICY (Transact-SQL)](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
