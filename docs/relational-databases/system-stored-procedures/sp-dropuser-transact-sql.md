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
ms.openlocfilehash: 42628ab49e30a4c6dada2eafb505435b8b389de6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124724"
---
# <a name="sp_dropuser-transact-sql"></a>sp_dropuser (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет пользователя из текущей базы данных. **sp_dropuser** обеспечивает совместимость с более ранними [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]версиями.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Вместо этого используйте [DROP USER](../../t-sql/statements/drop-user-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropuser [ @name_in_db = ] 'user'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @name_in_db = ] 'user'`Имя удаляемого пользователя. *пользователь* имеет тип **sysname**и не имеет значения по умолчанию. *пользователь* должен существовать в текущей базе данных. Указывая имя входа Windows, используйте имя, по которому база данных сможет его определить.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="remarks"></a>Remarks  
 **sp_dropuser** выполняет **sp_revokedbaccess** , чтобы удалить пользователя из текущей базы данных.  
  
 Для вывода списка имен пользователей, которые могут быть удалены из текущей базы данных, используется **sp_helpuser** .  
  
 Когда удаляется пользователь базы данных, также удаляются все псевдонимы этого пользователя. Если пользователь является владельцем пустой схемы с тем же именем, что и у пользователя, эта схема будет удалена. Если пользователь владеет любыми другими защищаемыми объектами базы данных, то он не будет удален. Необходимо сначала передать права владения объектами другому участнику. Дополнительные сведения см. в разделе [ALTER AUTHORIZATION (Transact-SQL)](../../t-sql/statements/alter-authorization-transact-sql.md). При удалении пользователя базы данных автоматически удаляются разрешения, связанные с пользователем, а пользователь удаляется из всех ролей базы данных, членом которых он является.  
  
 **sp_dropuser** нельзя использовать для удаления владельца базы данных (**dbo**) **INFORMATION_SCHEMA** пользователей или **гостевых** пользователей из баз данных **master** или **tempdb** . В несистемных базах `EXEC sp_dropuser 'guest'` данных будет отозвано разрешение CONNECT для пользователя **Guest**. Однако сам пользователь не будет удален.  
  
 **sp_dropuser** не может быть выполнена в пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER ANY USER для базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется пользователь `Albert` из текущей базы данных.  
  
```  
EXEC sp_dropuser 'Albert';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [Удаление пользователя &#40;Transact-SQL&#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [sp_revokedbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokedbaccess-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
