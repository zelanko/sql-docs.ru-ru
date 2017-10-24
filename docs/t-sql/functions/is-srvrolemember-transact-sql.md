---
title: "Функция IS_SRVROLEMEMBER (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IS_SRVROLEMEMBER_TSQL
- IS_SRVROLEMEMBER
dev_langs:
- TSQL
helpviewer_keywords:
- roles [SQL Server], members
- IS_SRVROLEMEMBER function
- members [SQL Server], verifying
ms.assetid: 3241a44a-6958-415b-b8b7-2a1207c36ab3
caps.latest.revision: 65
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c26c0c1f4cb6a22f50cdc6a87d7a31f25b65e138
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="issrvrolemember-transact-sql"></a>Функция IS_SRVROLEMEMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Указывает, является ли данное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] членом указанной роли сервера.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IS_SRVROLEMEMBER ( 'role' [ , 'login' ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *роли* **"**  
 Имя проверяемой роли сервера. *роль* — **sysname**.  
  
 Допустимые значения для *роли* , определяемых пользователем ролей сервера, а также следующие предопределенные роли сервера:  
  
|||  
|-|-|  
|sysadmin|serveradmin|  
|dbcreator|setupadmin|  
|bulkadmin|securityadmin|  
|diskadmin|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> public|  
|processadmin||  
  
 **"** *входа* **"**  
 Имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа для проверки. *Имя входа* — **sysname**, значение по умолчанию NULL. Если значение не указано, то результат основан на текущем контексте выполнения. Если параметр содержит слово NULL, то возвращается NULL.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
|Возвращаемое значение|Description|  
|------------------|-----------------|  
|0|*Имя входа* не является членом *роли*.<br /><br /> В [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], эта инструкция всегда возвращает 0.|  
|1|*Имя входа* является членом *роли*.|  
|NULL|*роль* или *входа* не является допустимым, или у вас нет разрешения на просмотр членства в роли.|  
  
## <a name="remarks"></a>Замечания  
 UseIS_SRVROLEMEMBER, чтобы определить, может ли текущий пользователь выполнить действие, требующее разрешений роли сервера.  
  
 Если имя входа Windows, например Contoso\Mary5, указанное для *входа*, **IS_SRVROLEMEMBER** возвращает **NULL**, если не разрешен или запрещен прямой доступ к имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если необязательный *входа* — параметр не указан, а *входа* является имя входа домена Windows, он может быть членом предопределенной роли сервера через членство в группе Windows. Чтобы решить проблему косвенного членства, функция IS_SRVROLEMEMBER запрашивает у контроллера домена сведения о членстве в группах Windows. Если контроллер домена недоступен или не отвечает, **IS_SRVROLEMEMBER** возвращает сведения о членстве в роли, с учетом пользователя и только локальные группы. Если указанный пользователь не является текущим пользователем, то значение, возвращаемое функцией IS_SRVROLEMEMBER, может отличаться от значения в структуре проверки подлинности (например, Active Directory), полученного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при последнем обновлении данных.  
  
 Если указан необязательный параметр входа, то запрашиваемое имя входа Windows должно присутствовать в таблице sys.server_principals. В противном случае функция IS_SRVROLEMEMBER возвратит значение NULL. Это свидетельствует о недопустимости имени входа.  
  
 Если параметром входа является имя входа домена или имя, основанное на группе Windows, и контроллер домена недоступен, то вызовы функции IS_SRVROLEMEMBER завершатся ошибкой и могут вернуть неверные или неполные данные.  
  
 Если контроллер домена недоступен, то вызов функции IS_SRVROLEMEMBER возвратит правильные данные при условии, что проверку подлинности участника Windows можно выполнить локально (например, для локальной учетной записи Windows или имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]).  
  
 **Функция IS_SRVROLEMEMBER** всегда возвращает 0, если группа Windows используется как аргумент имени входа, и эта группа Windows является членом другой группы Windows, который, в свою очередь, является членом указанной роли сервера.  
  
 Параметр управления учетных записей (UAC) также может привести возвращаемое различные результаты. Это зависит от того, обращался ли пользователь к серверу в качестве члена группы Windows или как определенный пользователь [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Эта функция вычисляет членство в роли, а не базовое разрешение. Например **sysadmin** Предопределенная роль сервера обладает **CONTROL SERVER** разрешение. Если у пользователя есть **CONTROL SERVER** разрешение но он не является членом роли, эта функция неправильно сообщает, что пользователь не является членом **sysadmin** роли, даже если пользователь имеет те же разрешения.  
  
## <a name="related-functions"></a>Связанные функции  
 Чтобы определить, является ли текущий пользователь членом указанной группы Windows или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] роли базы данных, используйте [IS_MEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-member-transact-sql.md). Чтобы определить, является ли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа является членом роли базы данных, используйте [IS_ROLEMEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-rolemember-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Требует разрешения VIEW DEFINITION на роль сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, является ли имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] текущего пользователя членом предопределенной роли сервера `sysadmin`.  
  
```  
IF IS_SRVROLEMEMBER ('sysadmin') = 1  
   print 'Current user''s login is a member of the sysadmin role'  
ELSE IF IS_SRVROLEMEMBER ('sysadmin') = 0  
   print 'Current user''s login is NOT a member of the sysadmin role'  
ELSE IF IS_SRVROLEMEMBER ('sysadmin') IS NULL  
   print 'ERROR: The server role specified is not valid.';  
```  
  
 Следующий пример показывает, является ли имя входа домена Pat членом **diskadmin** предопределенной роли сервера.  
  
```  
SELECT IS_SRVROLEMEMBER('diskadmin', 'Contoso\Pat');  
```  
  
## <a name="see-also"></a>См. также:  
 [IS_MEMBER &#40; Transact-SQL &#41;](../../t-sql/functions/is-member-transact-sql.md)   
 [Функции безопасности &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  

