---
title: sp_helprolemember (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helprolemember_TSQL
- sp_helprolemember
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helprolemember
ms.assetid: 42797510-aa5d-4564-85ac-27418419af9c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 547ac1bce010e1f25eb2fce178844ff2b3f77bd1
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526946"
---
# <a name="sphelprolemember-transact-sql"></a>sp_helprolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о непосредственно заданных членах роли в текущей базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helprolemember [ [ @rolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @rolename = ] ' role '` — Имя роли в текущей базе данных. *роль* — **sysname**, значение по умолчанию NULL. *роль* должен существовать в текущей базе данных. Если *роли* не указан, возвращаются все роли, которые содержат хотя бы один член из текущей базы данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**DbRole**|**sysname**|Имя роли в текущей базе данных.|  
|**Имя пользователя**|**sysname**|Имя члена **DbRole.**|  
|**MemberSID**|**varbinary(85)**|Идентификатор безопасности **MemberName.**|  
  
## <a name="remarks"></a>Примечания  
 Если база данных содержит вложенные роли, **MemberName** может быть именем роли. **sp_helprolemember** отображаются сведения о членстве, полученном через вложенные роли. Например, если пользователь User1 является членом роли Role1, а роль Role1 — членом роли Role2, `EXEC sp_helprolemember 'Role2'`, происходит возврат роли Role1, но не членов роли Role1 (в этом примере — пользователя User1). Для возврата вложенной в группах, необходимо выполнить **sp_helprolemember** несколько раз для каждой вложенной роли.  
  
 Используйте **sp_helpsrvrolemember** для отображения членов предопределенной роли сервера.  
  
 Используйте [IS_ROLEMEMBER &#40;Transact-SQL&#41; ](../../t-sql/functions/is-rolemember-transact-sql.md) для проверки членства в роли для указанного пользователя.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере производится отображение членов роли `Sales`.  
  
```  
EXEC sp_helprolemember 'Sales';  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Хранимая процедура sp_addrolemember (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_helprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_helpsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
