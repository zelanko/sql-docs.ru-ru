---
title: "ALTER ПРИВЯЗКИ УДАЛЕННОЙ службы (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER REMOTE SERVICE BINDING
- ALTER_REMOTE_SERVICE_BINDING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- remote service bindings [Service Broker], modifying
- ALTER REMOTE SERVICE BINDING statement
- modifying remote service bindings
ms.assetid: ee620b4a-9375-4eaa-a016-69916c9e1e68
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5352750b43775b53a508b42de17d33a792a40b1b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-remote-service-binding-transact-sql"></a>ALTER REMOTE SERVICE BINDING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет пользователя, связанного с привязкой удаленной службы, или изменяет настройку привязки, допускающую анонимную проверку подлинности.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER REMOTE SERVICE BINDING binding_name   
   WITH [ USER = <user_name> ] [ , ANONYMOUS = { ON | OFF } ]   
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *binding_name*  
 Имя привязки удаленной службы, которую требуется изменить. Не могут быть указаны имена сервера, базы данных и схемы.  
  
 С ПОЛЬЗОВАТЕЛЕМ = \< *имя_пользователя >*  
 Указывает пользователя базы данных, у которого имеется сертификат для этой привязки, связанный с удаленной службой. Открытый ключ из этого сертификата используется для кодирования и проверки подлинности сообщений, обмен которыми производится удаленной службой.  
  
 ANONYMOUS  
 Указывает, используется ли анонимная проверка подлинности при связи с удаленной службой. При настройке ANONYMOUS = ON используется анонимная проверка подлинности и учетные данные локального пользователя не передаются удаленной службе. При настройке ANONYMOUS = OFF передаются учетные данные пользователя. Если это выражение не задано, по умолчанию параметр принимает значение OFF.  
  
## <a name="remarks"></a>Замечания  
 Открытый ключ в сертификат, связанный с *имя_пользователя* используется для проверки подлинности сообщений, отправленных удаленной службы и для шифрования сеансового ключа, который затем используется для шифрования сообщений. Сертификат для *имя_пользователя* должен соответствовать сертификату для входа в базе данных, на котором находится удаленная служба.  
  
## <a name="permissions"></a>Permissions  
 По умолчанию разрешением на изменения привязки удаленной службы принадлежит владельцу привязки удаленной службы, члены **db_owner** фиксированной роли базы данных, а также члены **sysadmin** предопределенной роли сервера.  
  
 У пользователя, вызывающего инструкцию ALTER REMOTE SERVICE BINDING, должно быть разрешение на олицетворение пользователя, указанного в выражении.  
  
 Чтобы изменить параметр AUTHORIZATION для привязки удаленной службы, используйте инструкцию ALTER AUTHORIZATION.  
  
## <a name="examples"></a>Примеры  
 В следующем примере привязка `APBinding` удаленной службы изменяется таким образом, чтобы шифровать сообщения с помощью сертификатов учетной записи `SecurityAccount`.  
  
```  
ALTER REMOTE SERVICE BINDING APBinding  
    WITH USER = SecurityAccount ;  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE REMOTE SERVICE BINDING (Transact-SQL)](../../t-sql/statements/create-remote-service-binding-transact-sql.md)   
 [Удаление ПРИВЯЗКИ УДАЛЕННОЙ службы &#40; Transact-SQL &#41;](../../t-sql/statements/drop-remote-service-binding-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

