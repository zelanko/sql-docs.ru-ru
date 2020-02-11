---
title: sys. security_predicates (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
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
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6cf464370c5c2ca3f5075205c6783e9332309f12
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68135217"
---
# <a name="syssecurity_predicates-transact-sql"></a>sys. security_predicates (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Возвращает строку для каждого предиката безопасности в базе данных.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Идентификатор политики безопасности, содержащей этот предикат.|  
|security_predicate_id|**int**|Идентификатор предиката в этой политике безопасности.|  
|target_object_id|**int**|Идентификатор объекта, к которому привязан этот предикат безопасности.|  
|predicate_definition|**nvarchar(max)**|Полное имя функции, которая будет использоваться в качестве предиката безопасности, включая аргументы. Обратите внимание, что имя `schema.function` может быть нормализовано (т. е. экранировано), как и любой другой элемент в тексте, для обеспечения согласованности. Пример:<br /><br /> `[dbo].[fn_securitypredicate]([wing], [startTime], [endTime])`|  
|predicate_type|**int**|Тип предиката, используемый политикой безопасности:<br /><br /> 0 = ПРЕДИКАТ ФИЛЬТРА<br /><br /> 1 = ПРЕДИКАТ БЛОКИРОВКИ|  
|predicate_type_desc|**nvarchar (60)**|Тип предиката, используемый политикой безопасности:<br /><br /> FILTER<br /><br /> ЗАБЛОКИРОВАТЬ|  
|операция|**int**|Тип операции, указанной для предиката:<br /><br /> NULL = все применимые операции<br /><br /> 1 = ПОСЛЕ ВСТАВКИ<br /><br /> 2 = ПОСЛЕ ОБНОВЛЕНИЯ<br /><br /> 3 = ПЕРЕД ОБНОВЛЕНИЕМ<br /><br /> 4 = ПЕРЕД УДАЛЕНИЕМ|  
|operation_desc|**nvarchar (60)**|Тип операции, указанной для предиката:<br /><br /> NULL<br /><br /> ПОСЛЕ ВСТАВКИ<br /><br /> AFTER UPDATE<br /><br /> ПЕРЕД ОБНОВЛЕНИЕМ<br /><br /> ПЕРЕД УДАЛЕНИЕМ|  
  
## <a name="permissions"></a>Разрешения  
 Участники с разрешением **ALTER ANY Security Policy** имеют доступ ко всем объектам в этом представлении каталога, а также любому пользователю с **определением представления** для объекта.  
  
## <a name="see-also"></a>См. также:  
 [Безопасность на уровне строк](../../relational-databases/security/row-level-security.md)   
 [sys. security_policies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [Создание политики безопасности &#40;&#41;Transact-SQL](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [Представления каталога безопасности &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Участники &#40;ядро СУБД&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
