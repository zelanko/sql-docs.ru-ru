---
title: "IS_ROLEMEMBER (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IS_ROLEMEMBER
- IS_ROLEMEMBER_TSQL
dev_langs: TSQL
helpviewer_keywords:
- roles [SQL Server], members
- IS_ROLEMEMBER function
- members [SQL Server], verifying
ms.assetid: 73efa688-ae91-4014-98bc-1cabe47321f7
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: fd8574c27bea00127096dc1f0040c8c3f93e96cb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="isrolemember-transact-sql"></a>IS_ROLEMEMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Указывает, является ли данный участник базы данных членом заданной роли базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IS_ROLEMEMBER ( 'role' [ , 'database_principal' ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *роли* **"**  
 Имя роли базы данных, проверяемой в данный момент. *роль* — **sysname**.  
  
 **"** *database_principal* **"**  
 Имя пользователя базы данных, роли базы данных или роли приложения для проверки. *database_principal* — **sysname**, значение по умолчанию NULL. Если значение не указано, то результат основан на текущем контексте выполнения. Если параметр содержит слово NULL, то возвращается NULL.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
|Возвращаемое значение|Description|  
|------------------|-----------------|  
|0|*database_principal* не является членом *роли*.|  
|1|*database_principal* является членом *роли*.|  
|NULL|*database_principal* или *роли* является недопустимым, или у вас нет разрешения на просмотр членства в роли.|  
  
## <a name="remarks"></a>Замечания  
 Чтобы определить, может ли текущий пользователь выполнить действие, требующее разрешений роли базы данных, воспользуйтесь функцией IS_ROLEMEMBER.  
  
 Если *database_principal* основан на имени входа Windows, например Contoso\Mary5, IS_ROLEMEMBER возвращает значение NULL, если не *database_principal* разрешен или запрещен прямой доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если необязательный *database_principal* — параметр не указан, а *database_principal* основано на имени входа домена Windows, может быть членом роли базы данных посредством членства в группе Windows . Чтобы решить проблему косвенного членства, функция IS_ROLEMEMBER запрашивает у контроллера домена сведения о членстве в группах Windows. Если контроллер домена недоступен или не отвечает, то функция IS_ROLEMEMBER возвращает сведения о членстве в роли, принимая во внимание только учетную запись пользователя и локальные группы. Если указанный пользователь не является текущим, то значение, возвращаемое функцией IS_ROLEMEMBER, может отличаться от значения в структуре проверки подлинности (например, Active Directory), полученного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при последнем обновлении данных.  
  
 Если необязательный *database_principal* параметр указан, участник базы данных, в которой выполняется запрос должен присутствовать в sys.database_principals или IS_ROLEMEMBER возвратит значение NULL. Это означает, что *database_principal* не допускается в этой базе данных.  
  
 Когда *database_principal* параметра является на основе имени входа домена или группе Windows и контроллер домена недоступен, вызовы функции IS_ROLEMEMBER завершится ошибкой и могут вернуть неверные или неполные данные.  
  
 Если контроллер домена недоступен, то вызов функции IS_ROLEMEMBER вернет правильные данные при условии, что проверку подлинности участника Windows можно выполнить локально (например, для локальной учетной записи Windows или имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]).  
  
 **IS_ROLEMEMBER** всегда возвращает 0, если группа Windows используется как основной аргумент базы данных, и эта группа Windows является членом другой группы Windows, который, в свою очередь, является членом роли указанной базы данных.  
  
 Найти элемент управления учетных записей пользователей (UAC) в [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] и Windows Server 2008 также может возвращать разные результаты. Это зависит от того, обращался ли пользователь к серверу в качестве члена группы Windows или как определенный пользователь [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Эта функция вычисляет членство в роли, а не базовое разрешение. Например **db_owner** предопределенной роли базы данных имеет **базы данных системы УПРАВЛЕНИЯ** разрешение. Если у пользователя есть **базы данных системы УПРАВЛЕНИЯ** разрешение но он не является членом роли, эта функция неправильно сообщает, что пользователь не является членом **db_owner** роли, даже если пользователь имеет те же разрешения.  
  
## <a name="related-functions"></a>Связанные функции  
 Чтобы определить, является ли текущий пользователь членом указанной группы Windows или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] роли базы данных, используйте [IS_MEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-member-transact-sql.md). Чтобы определить, является ли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа является членом роли сервера, используйте [IS_SRVROLEMEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-srvrolemember-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Требует разрешения VIEW DEFINITION для роли базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере определяется принадлежность имени входа текущего пользователя к предопределенной роли базы данных `db_datareader`.  
  
```  
IF IS_ROLEMEMBER ('db_datareader') = 1  
   print 'Current user is a member of the db_datareader role'  
ELSE IF IS_ROLEMEMBER ('db_datareader') = 0  
   print 'Current user is NOT a member of the db_datareader role'  
ELSE IF IS_ROLEMEMBER ('db_datareader') IS NULL  
   print 'ERROR: The database role specified is not valid.';  
```  
  
## <a name="see-also"></a>См. также:  
 [СОЗДАТЬ РОЛИ &#40; Transact-SQL &#41;](../../t-sql/statements/create-role-transact-sql.md)   
 [ИЗМЕНИТЬ РОЛИ &#40; Transact-SQL &#41;](../../t-sql/statements/alter-role-transact-sql.md)   
 [УДАЛИТЬ РОЛЬ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [СОЗДАТЬ РОЛЬ сервера &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-role-transact-sql.md)   
 [ALTER SERVER ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-role-transact-sql.md)   
 [УДАЛИТЬ РОЛЬ сервера &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-role-transact-sql.md)   
 [IS_MEMBER &#40; Transact-SQL &#41;](../../t-sql/functions/is-member-transact-sql.md)   
 [Функция IS_SRVROLEMEMBER &#40; Transact-SQL &#41;](../../t-sql/functions/is-srvrolemember-transact-sql.md)   
 [Функции безопасности &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
