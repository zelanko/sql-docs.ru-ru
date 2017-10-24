---
title: "Функции безопасности (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], security
- security functions
- roles [SQL Server], functions
- users [SQL Server], security functions
- security [SQL Server], functions
ms.assetid: 7773a87d-2f1b-4951-a225-baf159a7291b
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3f2aa53bf4313ec13f8d506c214e0e2d9130a353
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="security-functions-transact-sql"></a>Функции безопасности (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Следующие функции возвращают сведения, полезные для управления безопасностью. Дополнительные функции перечислены в разделе [криптографических функций &#40; Transact-SQL &#41; ](../../t-sql/functions/cryptographic-functions-transact-sql.md).  
  
|||  
|-|-|  
|[CERTENCODED &#40; Transact-SQL &#41;](../../t-sql/functions/certencoded-transact-sql.md)|[PWDCOMPARE &#40; Transact-SQL &#41;](../../t-sql/functions/pwdcompare-transact-sql.md)|  
|[CERTPRIVATEKEY &#40; Transact-SQL &#41;](../../t-sql/functions/certprivatekey-transact-sql.md)|[PWDENCRYPT &#40; Transact-SQL &#41;](../../t-sql/functions/pwdencrypt-transact-sql.md)|  
|[Функция CURRENT_USER &#40; Transact-SQL &#41;](../../t-sql/functions/current-user-transact-sql.md)|[SCHEMA_ID &#40; Transact-SQL &#41;](../../t-sql/functions/schema-id-transact-sql.md)|  
|[DATABASE_PRINCIPAL_ID &#40; Transact-SQL &#41;](../../t-sql/functions/database-principal-id-transact-sql.md)|[Schema_name &#40; Transact-SQL &#41;](../../t-sql/functions/schema-name-transact-sql.md)|  
|[функция sys.fn_builtin_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)|[Функция SESSION_USER &#40; Transact-SQL &#41;](../../t-sql/functions/session-user-transact-sql.md)|  
|[sys.fn_get_audit_file (Transact-SQL)](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)|[SUSER_ID &#40; Transact-SQL &#41;](../../t-sql/functions/suser-id-transact-sql.md)|  
|[sys.fn_my_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)|[Функция SUSER_SID &#40; Transact-SQL &#41;](../../t-sql/functions/suser-sid-transact-sql.md)|  
|[HAS_PERMS_BY_NAME (Transact-SQL)](../../t-sql/functions/has-perms-by-name-transact-sql.md)|[SUSER_SNAME (Transact-SQL)](../../t-sql/functions/suser-sname-transact-sql.md)|  
|[IS_MEMBER &#40;Transact-SQL&#41;](../../t-sql/functions/is-member-transact-sql.md)|[Функция SYSTEM_USER &#40; Transact-SQL &#41;](../../t-sql/functions/system-user-transact-sql.md)|  
|[IS_ROLEMEMBER &#40; Transact-SQL &#41;](../../t-sql/functions/is-rolemember-transact-sql.md)|[SUSER_NAME &#40; Transact-SQL &#41;](../../t-sql/functions/suser-name-transact-sql.md)|  
|[Функция IS_SRVROLEMEMBER (Transact-SQL)](../../t-sql/functions/is-srvrolemember-transact-sql.md)|[Функция USER_ID &#40; Transact-SQL &#41;](../../t-sql/functions/user-id-transact-sql.md)|  
|[Функция ORIGINAL_LOGIN &#40; Transact-SQL &#41;](../../t-sql/functions/original-login-transact-sql.md)|[Имя_пользователя &#40; Transact-SQL &#41;](../../t-sql/functions/user-name-transact-sql.md)|  
|[РАЗРЕШЕНИЯ &#40; Transact-SQL &#41;](../../t-sql/functions/permissions-transact-sql.md)||  
  
 Сведения о членстве в группах Windows см. в разделе [xp_logininfo &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md) и [xp_enumgroups &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/xp-enumgroups-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Безопасность хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Криптографические функции &#40; Transact-SQL &#41;](../../t-sql/functions/cryptographic-functions-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [Инструкции по безопасности](http://msdn.microsoft.com/library/aebe2ec7-31bc-4697-a493-dcfcd0903a7b)  
  
  

