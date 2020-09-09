---
description: sp_helpsrvrole (Transact-SQL)
title: sp_helpsrvrole (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpsrvrole_TSQL
- sp_helpsrvrole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpsrvrole
ms.assetid: 5c7f39f3-c261-4f70-8beb-08242d4ac242
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 120303a4682ec659bca8a1cea6814506bc364cd4
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89535169"
---
# <a name="sp_helpsrvrole-transact-sql"></a>sp_helpsrvrole (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает список предопределенных ролей сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpsrvrole [ [ @srvrolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @srvrolename = ] 'role'` Имя предопределенной роли сервера. Аргумент *Role* имеет тип **sysname**и значение по умолчанию NULL. *роль* может иметь одно из следующих значений.  
  
|Предопределенная роль сервера|Описание|  
|-----------------------|-----------------|  
|sysadmin|Системные администраторы|  
|securityadmin|Администраторы безопасности.|  
|serveradmin|Администраторы сервера.|  
|setupadmin|Администраторы установки.|  
|processadmin|Администраторы процесса.|  
|diskadmin|Администраторы диска.|  
|dbcreator|Создатели баз данных.|  
|bulkadmin|Имеющие разрешение на выполнение инструкции BULK INSERT.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|ServerRole|**sysname**|Имя роли сервера|  
|Описание|**sysname**|Описание ServerRole|  
  
## <a name="remarks"></a>Примечания  
 Предопределенные роли сервера определены на уровне сервера и имеют разрешения на выполнение специальных административных действий на уровне сервера. Предопределенные роли сервера не могут быть добавлены, удалены или изменены.  
  
 Сведения о добавлении или удалении членов из ролей сервера см. в разделе [ALTER SERVER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
 Все имена входа являются членами общедоступной версии. sp_helpsrvrole не распознает общую роль, так как, внутри, не [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реализует Public как роль.  
  
 sp_helpsrvrole не принимает определяемую пользователем роль сервера в качестве аргумента. Чтобы получить список определяемых пользователем ролей сервера, см. примеры в статье [ALTER SERVER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-the-fixed-server-roles"></a>A. Перечисление предопределенных ролей сервера  
 Следующий запрос возвращает список предопределенных ролей сервера.  
  
```  
EXEC sp_helpsrvrole ;  
```  
  
### <a name="b-listing-fixed-and-user-defined-server-roles"></a>Б. Перечисление предопределенных и определяемых пользователем ролей сервера  
 Следующий запрос возвращает список и предопределенных, и определяемых пользователем ролей сервера.  
  
```  
SELECT * FROM sys.server_principals WHERE type = 'R' ;  
```  
  
### <a name="c-returning-a-description-of-a-fixed-server-role"></a>В. Возврат описания предопределенной роли сервера  
 Следующий запрос возвращает имя и описание предопределенных ролей сервера `diskadmin`.  
  
```  
sp_helpsrvrole 'diskadmin' ;  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Роли уровня сервера](../../relational-databases/security/authentication-access/server-level-roles.md)   
 [sp_addsrvrolemember (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
