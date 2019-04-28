---
title: Хранимая процедура sp_grantlogin (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_grantlogin_TSQL
- sp_grantlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grantlogin
ms.assetid: 0c873d99-c3bf-4eb1-948b-a46cb235ccd4
ms.author: vanto
manager: craigg
ms.openlocfilehash: def5041286ade754020a5c84e8d2ac91fc79afa3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796574"
---
# <a name="spgrantlogin-transact-sql"></a>sp_grantlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает имя входа на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md) вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_grantlogin [@loginame=] 'login'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @loginame = ] 'login'` — Имя пользователя Windows или группы. Windows пользователь или группа должны быть дополнены именем домена Windows в виде *домена*\\*пользователя*, например **London\Joeb**. *Имя входа* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_grantlogin** вызывает CREATE LOGIN, которая поддерживает дополнительные параметры. Сведения о создании имен входа SQL Server, см. в разделе [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)  
  
 **sp_grantlogin** не может выполняться внутри пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER ANY LOGIN на сервере.  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется `CREATE LOGIN` для создания [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имени входа Windows пользователя `Corporate\BobJ.` Это предпочтительный метод.  
  
```  
CREATE LOGIN [Corporate\BobJ] FROM WINDOWS;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE LOGIN (Transact-SQL)](../../t-sql/statements/create-login-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
