---
title: "IS_MEMBER (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e14fc4cf70066c21a8a837760d4325a19ae4ff1c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ismember-transact-sql"></a>IS_MEMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Указывает, является ли текущий пользователь членом указанной группы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows или роли базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IS_MEMBER ( { 'group' | 'role' } )  
```  
  
## <a name="arguments"></a>Аргументы  
 **'** *group* **'**  
**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Имя группы Windows, которая проверяется; должно иметь формат *Домен*\\*Группа*. Аргумент *group* имеет тип **sysname**.  
  
 **'** *role* **'**  
 Имя проверяемой роли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Аргумент *role* имеет тип **sysname** и может содержать предопределенные роли базы данных или пользовательские роли, но не роли сервера.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
## <a name="remarks"></a>Remarks  
 Функция IS_MEMBER возвращает следующие значения.  
  
|Возвращаемое значение|Description|  
|------------------|-----------------|  
|0|Текущий пользователь не является членом группы *group* или роли *role*.|  
|1|Текущий пользователь является членом группы *group* или роли *role*.|  
|NULL|Недопустимое значение *group* или *role*. В случае запроса от имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или имени, использующего роль приложения, возвращает NULL для группы Windows.|  
  
 Функция IS_MEMBER определяет членство в группе Windows, проверяя токен доступа, созданный Windows. Токен доступа не отражает изменения членства в группе, внесенные после подключения пользователя к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Членство группы Windows не может запрашиваться именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или ролью приложения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Для добавления членов в роль базы данных и удаления членов из нее используйте инструкцию [ALTER ROLE (Transact-SQL)](../../t-sql/statements/alter-role-transact-sql.md). Для добавления членов в роль сервера и удаления членов из нее используйте инструкцию [ALTER SERVER ROLE (Transact-SQL)](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
 Эта функция вычисляет членство в роли, а не базовое разрешение. Например, предопределенная роль базы данных **db_owner** имеет разрешение **CONTROL DATABASE**. Если у пользователя есть разрешение **CONTROL DATABASE**, но он не является членом этой роли, то эта функция справедливо сообщает, что пользователь не является членом роли **db_owner**, даже несмотря на то, что имеет те же разрешения.  
  
 Члены предопределенной роли сервера **sysadmin** входят в каждую базу данных как пользователь **dbo**. При проверке разрешения для члена предопределенной роли сервера **sysadmin** проверяются разрешения для пользователя **dbo**, а не исходного имени для входа. Так как пользователя **dbo** невозможно добавить в роль базы данных и он отсутствует в группах Windows, для **dbo** всегда возвращается значение 0 (или NULL, если роль не существует).  
  
## <a name="related-functions"></a>Связанные функции  
 Чтобы определить, является ли другое имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] членом роли базы данных, воспользуйтесь функцией [IS_ROLEMEMBER (Transact-SQL)](../../t-sql/functions/is-rolemember-transact-sql.md). Чтобы определить, является ли имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] членом роли сервера, воспользуйтесь функцией [IS_SRVROLEMEMBER (Transact-SQL)](../../t-sql/functions/is-srvrolemember-transact-sql.md).  
  
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
 [Функция IS_SRVROLEMEMBER (Transact-SQL)](../../t-sql/functions/is-srvrolemember-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Функции безопасности &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
