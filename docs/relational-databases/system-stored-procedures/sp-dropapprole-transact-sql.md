---
title: sp_dropapprole (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropapprole_TSQL
- sp_dropapprole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropapprole
ms.assetid: ea1aefe6-8f7d-46e9-a3cb-7b037b393e73
ms.author: vanto
manager: craigg
ms.openlocfilehash: 5cc9f79ab588a042894c199564820d06d9585bf1
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58533392"
---
# <a name="spdropapprole-transact-sql"></a>sp_dropapprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет роль приложения из текущей базы данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [DROP APPLICATION ROLE](../../t-sql/statements/drop-application-role-transact-sql.md) вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropapprole [@rolename = ] 'role'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @rolename = ] 'role'` — Это роль приложения для удаления. *роль* — **sysname**, не имеет значения по умолчанию. *роль* должен существовать в текущей базе данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_dropapprole** может использоваться только для удаления ролей приложения. Если роли принадлежат какие-либо защищаемые объекты, то эту роль удалить нельзя. Перед удалением роли приложения, которой принадлежат защищаемые объекты, следует сначала перенести данные о принадлежности защищаемых объектов или удалить эти объекты.  
  
 **sp_dropapprole** не может выполняться внутри пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо наличие разрешения ALTER ANY APPLICATION ROLE для этой базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере данных роль приложения `SalesApp` удаляется из текущей базы данных.  
  
```  
EXEC sp_dropapprole 'SalesApp';  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addapprole-transact-sql.md)   
 [DROP APPLICATION ROLE (Transact-SQL)](../../t-sql/statements/drop-application-role-transact-sql.md)   
 [sp_changeobjectowner &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changeobjectowner-transact-sql.md)   
 [sp_setapprole (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
