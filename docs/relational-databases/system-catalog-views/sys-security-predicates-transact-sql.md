---
title: sys.security_predicates (Transact-SQL) | Документация Майкрософт
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68135217"
---
# <a name="syssecuritypredicates-transact-sql"></a>sys.security_predicates (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Возвращает строку для каждого предиката безопасности в базе данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Идентификатор политики безопасности, содержащей этот предикат.|  
|security_predicate_id|**int**|Идентификатор предиката в этой политике безопасности.|  
|target_object_id|**int**|Идентификатор объекта, к которому привязан этот предикат безопасности.|  
|predicate_definition|**nvarchar(max)**|Полное имя функции, которая будет использоваться в качестве предиката безопасности, включая аргументы. Обратите внимание, что имя `schema.function` может быть нормализовано (т. е. экранировано), как и любой другой элемент в тексте, для обеспечения согласованности. Пример:<br /><br /> `[dbo].[fn_securitypredicate]([wing], [startTime], [endTime])`|  
|predicate_type|**int**|Тип предикат, используемый с такой политикой безопасности:<br /><br /> 0 = ПРЕДИКАТА ФИЛЬТРА<br /><br /> 1 = ПРЕДИКАТ БЛОКИРОВКИ|  
|predicate_type_desc|**nvarchar(60)**|Тип предикат, используемый с такой политикой безопасности:<br /><br /> FILTER<br /><br /> БЛОК|  
|operation|**int**|Тип операции, заданной для предиката:<br /><br /> NULL = все применимые операции<br /><br /> 1 = ПОСЛЕ ВСТАВКИ<br /><br /> 2 = ПОСЛЕ ОБНОВЛЕНИЯ<br /><br /> 3 = ДО ОБНОВЛЕНИЯ<br /><br /> 4 = ДО УДАЛЕНИЯ|  
|operation_desc|**nvarchar(60)**|Тип операции, заданной для предиката:<br /><br /> NULL<br /><br /> ПОСЛЕ ВСТАВКИ<br /><br /> AFTER UPDATE<br /><br /> ПЕРЕД ОБНОВЛЕНИЕМ<br /><br /> ДО УДАЛЕНИЯ|  
  
## <a name="permissions"></a>Разрешения  
 Участники с **ALTER ANY SECURITY POLICY** разрешение имеют доступ ко всем объектам в этом представлении каталога, а также любой пользователь с **VIEW DEFINITION** в объекте.  
  
## <a name="see-also"></a>См. также  
 [Безопасность на уровне строк](../../relational-databases/security/row-level-security.md)   
 [sys.security_policies (Transact-SQL)](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [CREATE SECURITY POLICY (Transact-SQL)](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
