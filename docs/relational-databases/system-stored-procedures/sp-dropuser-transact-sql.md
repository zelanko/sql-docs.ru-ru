---
title: sp_dropuser (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_dropuser
- sp_dropuser_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropuser
ms.assetid: e28f18f9-7ecf-4568-89f4-fe5c520df386
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9af8a740ae349f748acc6c8385d95b97a0e2490d
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243201"
---
# <a name="spdropuser-transact-sql"></a>sp_dropuser (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет пользователя из текущей базы данных. **sp_dropuser** обеспечивает совместимость с предыдущими версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [DROP USER](../../t-sql/statements/drop-user-transact-sql.md) вместо него.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropuser [ @name_in_db = ] 'user'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@name_in_db =**] **"***пользователя***"**  
 Имя пользователя, которого необходимо удалить. *пользователь* — **sysname**, не имеет значения по умолчанию. *пользователь* должен существовать в текущей базе данных. Указывая имя входа Windows, используйте имя, по которому база данных сможет его определить.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
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
 [УДАЛИТЬ пользователя & #40; Transact-SQL & #41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [sp_revokedbaccess (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-revokedbaccess-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
