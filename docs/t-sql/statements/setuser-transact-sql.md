---
title: "Инструкция SETUSER (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SETUSER_TSQL
- SETUSER
dev_langs: TSQL
helpviewer_keywords:
- delegation [SQL Server]
- impersonation [SQL Server]
- SETUSER statement
- user impersonation [SQL Server]
ms.assetid: 7acfac5c-9ad6-4226-b874-7add36c4ea43
caps.latest.revision: "27"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a511e0337201c9b4501b5274fa8270fbebf7da50
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="setuser-transact-sql"></a>SETUSER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Позволяет члену **sysadmin** предопределенной роли сервера или владельца базы данных для олицетворения другого пользователя.  
  
> [!IMPORTANT]  
>  Инструкция SETUSER включена только для обратной совместимости. Инструкция SETUSER может не поддерживаться в следующих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Мы рекомендуем использовать [EXECUTE AS](../../t-sql/statements/execute-as-transact-sql.md) вместо него.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SETUSER [ 'username' [ WITH NORESET ] ]   
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *username* **"**  
 Имя пользователя Windows или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], олицетворение которого выполняется в текущей базе данных. Когда *username* не указан, восстанавливаются первоначальные учетные данные системного администратора или владельца базы данных олицетворения пользователя будет сброшен.  
  
 WITH NORESET  
 Указывает, что последующие инструкции SETUSER (без указания аргумента *username*) не следует сбрасывать удостоверение пользователя к системному администратору или владельцу базы данных.  
  
## <a name="remarks"></a>Замечания  
 Инструкция SETUSER используется член **sysadmin** предопределенной роли сервера или владельца базы данных, чтобы использовать учетные данные другого пользователя для проверки разрешений другого пользователя. Членство в фиксированной роли базы данных db_owner не является достаточным.  
  
 Инструкцию SETUSER следует использовать только с пользователями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. SETUSER не поддерживается с пользователями Windows. Когда инструкция SETUSER используется для использования идентификатора другого пользователя, то все объекты, созданные олицетворяющим пользователем, переходят во владение пользователя, олицетворение которого выполняется. Например, если владелец базы данных использует удостоверение пользователя **Margaret** и создается таблица с именем **заказов**, **заказов** таблицы принадлежат **Margaret** , не системный администратор.  
  
 Инструкция SETUSER остается в действии до тех пор, пока не будет выполнена другая инструкция SETUSER или пока текущая база данных не будет изменена оператором USE.  
  
> [!NOTE]  
>  Если используется инструкция SETUSER WITH NORESET, то владелец базы данных или системный администратор должен выйти и снова войти в систему для восстановления своих собственных прав.  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в **sysadmin** предопределенной роли сервера или должен быть владельцем базы данных. Членство в **db_owner** недостаточно предопределенной роли базы данных  
  
## <a name="examples"></a>Примеры  
 Следующий пример показывает, как владелец базы данных может использовать учетные данные другого пользователя. Пользователь `mary` создала таблицу под названием `computer_types`. Используя SETUSER, владелец базы данных производит олицетворение пользователя `mary` для предоставления пользователю `joe` права доступа к таблице `computer_types`, а затем восстанавливает свои учетные данные.  
  
```  
SETUSER 'mary';  
GO  
GRANT SELECT ON computer_types TO joe;  
GO  
--To revert to the original user  
SETUSER;  
```  
  
## <a name="see-also"></a>См. также:  
 [DENY (Transact-SQL)](../../t-sql/statements/deny-transact-sql.md)   
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE (Transact-SQL)](../../t-sql/statements/revoke-transact-sql.md)   
 [USE (Transact-SQL)](../../t-sql/language-elements/use-transact-sql.md)  
  
  
