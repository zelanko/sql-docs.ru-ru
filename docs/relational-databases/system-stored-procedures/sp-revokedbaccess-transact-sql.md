---
title: sp_revokedbaccess (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_revokedbaccess_TSQL
- sp_revokedbaccess
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revokedbaccess
ms.assetid: c997cfa1-539d-485c-a664-9c6f76bfe0c2
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: c1db15a2f8c8e1d7616065ff88aa40b08f92127a
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58530277"
---
# <a name="sprevokedbaccess-transact-sql"></a>sp_revokedbaccess (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет пользователя из текущей базы данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [DROP USER](../../t-sql/statements/drop-user-transact-sql.md) вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_revokedbaccess [ @name_in_db = ] 'name'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @name_in_db = ] 'name'` — Имя удаляемого пользователя базы данных. *имя* — **sysname** не имеет значения по умолчанию. *имя* может быть именем входа сервера, имя входа Windows или группу Windows и должен существовать в текущей базе данных. При указании имени входа Windows или группы Windows задавайте имя, известное в базе данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 При удалении пользователя базы данных также удаляются разрешения и псевдонимы этого пользователя.  
  
 **sp_revokedbaccess** можно удалить только пользователи базы данных из текущей базы данных. Перед удалением пользователя базы данных, которому принадлежат объекты в текущей базе данных, необходимо передать принадлежность этих объектов или удалить их из базы данных. Дополнительные сведения см. в разделе [ALTER AUTHORIZATION (Transact-SQL)](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
 **sp_revokedbaccess** не может выполняться внутри пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER ANY USER для базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется пользователь базы данных, сопоставленный `Edmonds\LolanSo` из текущей базы данных.  
  
```  
EXEC sp_revokedbaccess 'Edmonds\LolanSo';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [DROP USER (Transact-SQL)](../../t-sql/statements/drop-user-transact-sql.md)   
 [ALTER AUTHORIZATION (Transact-SQL)](../../t-sql/statements/alter-authorization-transact-sql.md)  
  
  
