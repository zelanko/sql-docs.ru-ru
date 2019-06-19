---
title: Функции безопасности (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: abed63415825fbf3f30800260cf2284205489b74
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65945317"
---
# <a name="security-functions-transact-sql"></a>Функции безопасности (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Следующие функции возвращают сведения, полезные для управления безопасностью. Дополнительные функции перечислены в статье [Криптографические функции (Transact-SQL)](../../t-sql/functions/cryptographic-functions-transact-sql.md).  
  
|||  
|-|-|  
|[CERTENCODED (Transact-SQL)](../../t-sql/functions/certencoded-transact-sql.md)|[PWDCOMPARE (Transact-SQL)](../../t-sql/functions/pwdcompare-transact-sql.md)|  
|[CERTPRIVATEKEY (Transact-SQL)](../../t-sql/functions/certprivatekey-transact-sql.md)|[PWDENCRYPT (Transact-SQL)](../../t-sql/functions/pwdencrypt-transact-sql.md)|  
|[CURRENT_USER (Transact-SQL)](../../t-sql/functions/current-user-transact-sql.md)|[SCHEMA_ID (Transact-SQL)](../../t-sql/functions/schema-id-transact-sql.md)|  
|[DATABASE_PRINCIPAL_ID (Transact-SQL)](../../t-sql/functions/database-principal-id-transact-sql.md)|[SCHEMA_NAME (Transact-SQL)](../../t-sql/functions/schema-name-transact-sql.md)|  
|[sys.fn_builtin_permissions (Transact-SQL)](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)|[SESSION_USER (Transact-SQL)](../../t-sql/functions/session-user-transact-sql.md)|  
|[sys.fn_get_audit_file (Transact-SQL)](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)|[SUSER_ID (Transact-SQL)](../../t-sql/functions/suser-id-transact-sql.md)|  
|[sys.fn_my_permissions (Transact-SQL)](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)|[SUSER_SID (Transact-SQL)](../../t-sql/functions/suser-sid-transact-sql.md)|  
|[HAS_PERMS_BY_NAME (Transact-SQL)](../../t-sql/functions/has-perms-by-name-transact-sql.md)|[SUSER_SNAME (Transact-SQL)](../../t-sql/functions/suser-sname-transact-sql.md)|  
|[IS_MEMBER &#40;Transact-SQL&#41;](../../t-sql/functions/is-member-transact-sql.md)|[SYSTEM_USER (Transact-SQL)](../../t-sql/functions/system-user-transact-sql.md)|  
|[IS_ROLEMEMBER (Transact-SQL)](../../t-sql/functions/is-rolemember-transact-sql.md)|[SUSER_NAME (Transact-SQL)](../../t-sql/functions/suser-name-transact-sql.md)|  
|[Функция IS_SRVROLEMEMBER (Transact-SQL)](../../t-sql/functions/is-srvrolemember-transact-sql.md)|[USER_ID (Transact-SQL)](../../t-sql/functions/user-id-transact-sql.md)|  
|[ORIGINAL_LOGIN (Transact-SQL)](../../t-sql/functions/original-login-transact-sql.md)|[USER_NAME (Transact-SQL)](../../t-sql/functions/user-name-transact-sql.md)|  
|[PERMISSIONS (Transact-SQL)](../../t-sql/functions/permissions-transact-sql.md)||  
  
 Сведения о членстве в группах Windows см. в статьях [xp_logininfo (Transact-SQL)](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md) и [xp_enumgroups (Transact-SQL)](../../relational-databases/system-stored-procedures/xp-enumgroups-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Криптографические функции (Transact-SQL)](../../t-sql/functions/cryptographic-functions-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [Инструкции безопасности](https://msdn.microsoft.com/library/aebe2ec7-31bc-4697-a493-dcfcd0903a7b)  
  
  
