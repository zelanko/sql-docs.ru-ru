---
title: Функция IS_SRVROLEMEMBER (Transact-SQL)
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: eb44adf219905a585b922fc280215f1c81465cda
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248524"
---
# <a name="is_srvrolemember-transact-sql"></a>Функция IS_SRVROLEMEMBER (Transact-SQL)

[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Указывает, является ли данное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] членом указанной роли сервера.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
  
IS_SRVROLEMEMBER ( 'role' [ , 'login' ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 **'** *role* **'**  
 Имя проверяемой роли сервера. Аргумент *role* имеет тип **sysname**.  
  
 Допустимыми значениями для параметра *role* являются определяемые пользователем роли сервера, а также следующие предопределенные роли сервера:  

- sysadmin
- serveradmin
- dbcreator
- setupadmin  
- bulkadmin
- securityadmin  
- diskadmin
- таверна  
- processadmin
  
 **'** *login* **'**  
 Проверяемое имя для входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Аргумент *login* имеет тип **sysname** и значение по умолчанию NULL. Если значение не указано, то результат основан на текущем контексте выполнения. Если параметр содержит слово NULL, то возвращается NULL.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **int**  
  
|Возвращаемое значение|Описание|  
|------------------|-----------------|  
|0|*login* не является членом роли *role*.<br /><br /> В [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] эта инструкция всегда возвращает 0.|  
|1|*login* является членом роли *role*.|  
|NULL|Аргумент *role* или *login* недопустим, либо у вас нет разрешения на просмотр членства в роли.|  
  
## <a name="remarks"></a>Remarks  
 Функция IS_SRVROLEMEMBER определяет, может ли текущий пользователь выполнить действие, требующее разрешений роли сервера.  
  
 Если для аргумента *login* определено имя входа Windows, например Contoso\Mary5, то функция **IS_SRVROLEMEMBER** возвращает значение **NULL**, если имени входа не предоставлен или не запрещен прямой доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если не указан необязательный параметр *login* и в качестве *имени входа* используется имя входа для домена Windows, оно может входить в предопределенную роль сервера посредством членства в группе Windows. Чтобы решить проблему косвенного членства, функция IS_SRVROLEMEMBER запрашивает у контроллера домена сведения о членстве в группах Windows. Если контроллер домена недоступен или не отвечает, то функция **IS_SRVROLEMEMBER** возвращает сведения о членстве в роли, принимая во внимание только учетную запись пользователя и ее локальные группы. Если указанный пользователь не является текущим пользователем, то значение, возвращаемое функцией IS_SRVROLEMEMBER, может отличаться от значения в структуре проверки подлинности (например, Active Directory), полученного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при последнем обновлении данных.  
  
 Если указан необязательный параметр входа, то запрашиваемое имя входа Windows должно присутствовать в таблице sys.server_principals. В противном случае функция IS_SRVROLEMEMBER возвратит значение NULL. Это свидетельствует о недопустимости имени входа.  
  
 Если параметром входа является имя входа домена или имя, основанное на группе Windows, и контроллер домена недоступен, то вызовы функции IS_SRVROLEMEMBER завершатся ошибкой и могут вернуть неверные или неполные данные.  
  
 Если контроллер домена недоступен, то вызов функции IS_SRVROLEMEMBER возвратит правильные данные при условии, что проверку подлинности участника Windows можно выполнить локально (например, для локальной учетной записи Windows или имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]).  
  
 **IS_SRVROLEMEMBER** всегда возвращает значение 0, если группа Windows используется как аргумент имени входа, а сама группа при этом является членом другой группы Windows, которая, в свою очередь, является членом указанной роли сервера.  
  
 Параметр контроля учетных записей (UAC) также может приводить к возврату разных результатов. Это зависит от того, обращался ли пользователь к серверу в качестве члена группы Windows или как определенный пользователь [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Эта функция вычисляет членство в роли, а не базовое разрешение. Например, у предопределенной роли сервера **sysadmin** имеется разрешение **CONTROL SERVER**. Если у пользователя есть разрешение **CONTROL SERVER**, но он не является членом этой роли, то эта функция справедливо сообщает, что пользователь не является членом роли **sysadmin**, даже несмотря на то, что имеет те же разрешения.  
  
## <a name="related-functions"></a>Связанные функции  
 Чтобы определить, является ли текущий пользователь членом указанной группы Windows или роли базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], воспользуйтесь функцией [IS_MEMBER (Transact-SQL)](../../t-sql/functions/is-member-transact-sql.md). Чтобы определить, является ли имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] членом роли базы данных, воспользуйтесь функцией [IS_ROLEMEMBER (Transact-SQL)](../../t-sql/functions/is-rolemember-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
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
  
 В приведенном ниже примере указывается, является ли имя входа домена Pat членом предопределенной роли сервера **diskadmin**.  
  
```  
SELECT IS_SRVROLEMEMBER('diskadmin', 'Contoso\Pat');  
```  
  
## <a name="see-also"></a>См. также:  
 [IS_MEMBER (Transact-SQL)](../../t-sql/functions/is-member-transact-sql.md)   
 [Функции безопасности &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
