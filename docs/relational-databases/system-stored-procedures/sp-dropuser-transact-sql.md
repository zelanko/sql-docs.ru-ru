---
title: sp_dropuser (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropuser
- sp_dropuser_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropuser
ms.assetid: e28f18f9-7ecf-4568-89f4-fe5c520df386
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d96004357962ee822df7458a30d740fc836de658
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62723887"
---
# <a name="spdropuser-transact-sql"></a>sp_dropuser (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет пользователя из текущей базы данных. **sp_dropuser** обеспечивает совместимость с предыдущими версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [DROP USER](../../t-sql/statements/drop-user-transact-sql.md) вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropuser [ @name_in_db = ] 'user'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @name_in_db = ] 'user'` — Имя пользователя для удаления. *пользователь* — **sysname**, не имеет значения по умолчанию. *пользователь* должен существовать в текущей базе данных. Указывая имя входа Windows, используйте имя, по которому база данных сможет его определить.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_dropuser** выполняет **sp_revokedbaccess** для удаления пользователя из текущей базы данных.  
  
 Используйте **sp_helpuser** для отображения списка имен пользователей, которые могут быть удалены из текущей базы данных.  
  
 Когда удаляется пользователь базы данных, также удаляются все псевдонимы этого пользователя. Если пользователь является владельцем пустой схемы с тем же именем, что и у пользователя, эта схема будет удалена. Если пользователь владеет любыми другими защищаемыми объектами базы данных, то он не будет удален. Необходимо сначала передать права владения объектами другому участнику. Дополнительные сведения см. в разделе [ALTER AUTHORIZATION (Transact-SQL)](../../t-sql/statements/alter-authorization-transact-sql.md). При удалении пользователя базы данных автоматически удаляются разрешения, связанные с пользователем, а пользователь удаляется из всех ролей базы данных, членом которых он является.  
  
 **sp_dropuser** не может использоваться для удаления владельца базы данных (**dbo**) **INFORMATION_SCHEMA** пользователей, или **гостевой** пользователя из **master**  или **tempdb** баз данных. В несистемных базах данных `EXEC sp_dropuser 'guest'` отменяет разрешение CONNECT для пользователя **гостевой**. Однако сам пользователь не будет удален.  
  
 **sp_dropuser** не может выполняться внутри пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER ANY USER для базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется пользователь `Albert` из текущей базы данных.  
  
```  
EXEC sp_dropuser 'Albert';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_grantdbaccess (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [DROP USER (Transact-SQL)](../../t-sql/statements/drop-user-transact-sql.md)   
 [sp_revokedbaccess (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-revokedbaccess-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
