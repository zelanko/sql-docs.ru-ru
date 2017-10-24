---
title: "IS_MEMBER (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IS_MEMBER
- IS_MEMBER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database roles [SQL Server], members
- current member status
- roles [SQL Server], members
- testing member status
- members [SQL Server]
- checking member status
- IS_MEMBER function
- verifying member status
- groups [SQL Server], members
- members [SQL Server], verifying
ms.assetid: 77cb68a0-19b7-4fe1-ab17-e5587699631b
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 472d8f1cc258fdc57ef454fbb35f51e3f83b288d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="ismember-transact-sql"></a>IS_MEMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Указывает, является ли текущий пользователь членом указанной группы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows или роли базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IS_MEMBER ( { 'group' | 'role' } )  
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *группы* **"**  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Имя группы Windows, которая проверяется; должно быть в формате *домена*\\*группы*. *Группа* — **sysname**.  
  
 **"** *роли* **"**  
 Имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] роль, проверяемой в данный момент. *роль* — **sysname** и может включать предопределенных ролей или определяемые пользователем роли, но не роли сервера базы данных.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
## <a name="remarks"></a>Замечания  
 Функция IS_MEMBER возвращает следующие значения.  
  
|Возвращаемое значение|Description|  
|------------------|-----------------|  
|0|Текущий пользователь не является членом *группы* или *роли*.|  
|1|Текущий пользователь является членом *группы* или *роли*.|  
|NULL|Либо *группы* или *роли* является недопустимым. В случае запроса от имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или имени, использующего роль приложения, возвращает NULL для группы Windows.|  
  
 Функция IS_MEMBER определяет членство в группе Windows, проверяя токен доступа, созданный Windows. Токен доступа не отражает изменения членства в группе, внесенные после подключения пользователя к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Членство группы Windows не может запрашиваться именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или ролью приложения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Для добавления и удаления членов из роли базы данных, используйте [ALTER ROLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-role-transact-sql.md). Для добавления и удаления членов из роли сервера, используйте [ALTER SERVER ROLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
 Эта функция вычисляет членство в роли, а не базовое разрешение. Например **db_owner** предопределенной роли базы данных имеет **базы данных системы УПРАВЛЕНИЯ** разрешение. Если у пользователя есть **базы данных системы УПРАВЛЕНИЯ** разрешение но он не является членом роли, эта функция неправильно сообщает, что пользователь не является членом **db_owner** роли, даже если пользователь имеет те же разрешения.  
  
 Члены **sysadmin** предопределенной роли сервера введите каждой базы данных как **dbo** пользователя. Проверка разрешений для элемента **sysadmin** предопределенной роли сервера, проверяет разрешения для **dbo**, не первоначального имени входа. Поскольку **dbo** нельзя добавить к роли базы данных или не существует в группах Windows **dbo** всегда возвращает 0 (или значение NULL, если эта роль не существует).  
  
## <a name="related-functions"></a>Связанные функции  
 Чтобы определить, является ли другое [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа является членом роли базы данных, используйте [IS_ROLEMEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-rolemember-transact-sql.md). Чтобы определить, является ли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа является членом роли сервера, используйте [IS_SRVROLEMEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-srvrolemember-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере проверяется, является ли текущий пользователь членом роли базы данных или группы домена Windows.  
  
```  
-- Test membership in db_owner and print appropriate message.  
IF IS_MEMBER ('db_owner') = 1  
   PRINT 'Current user is a member of the db_owner role'  
ELSE IF IS_MEMBER ('db_owner') = 0  
   PRINT 'Current user is NOT a member of the db_owner role'  
ELSE IF IS_MEMBER ('db_owner') IS NULL  
   PRINT 'ERROR: Invalid group / role specified';  
GO  
  
-- Execute SELECT if user is a member of ADVWORKS\Shipping.  
IF IS_MEMBER ('ADVWORKS\Shipping') = 1  
   SELECT 'User ' + USER + ' is a member of ADVWORKS\Shipping.';   
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Функция IS_SRVROLEMEMBER &#40; Transact-SQL &#41;](../../t-sql/functions/is-srvrolemember-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Функции безопасности &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  

