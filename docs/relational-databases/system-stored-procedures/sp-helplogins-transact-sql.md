---
title: sp_helplogins (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helplogins_TSQL
- sp_helplogins
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplogins
ms.assetid: f9ad3767-5b9f-420d-8922-b637811404f7
author: stevestein
ms.author: sstein
ms.openlocfilehash: b4c3d6ded5d85e5d38556792aaa7ea71dd9f42fa
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68122453"
---
# <a name="sp_helplogins-transact-sql"></a>sp_helplogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет данные об именах учетных записей и соответствующих пользователях в каждой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helplogins [ [ @LoginNamePattern = ] 'login' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @LoginNamePattern = ] 'login'`Имя входа. Аргумент *login* имеет тип **sysname** и значение по умолчанию NULL. *имя входа* должно существовать, если оно указано. Если параметр *Login* не указан, возвращаются сведения обо всех именах входа.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Первый отчет содержит данные о каждой заданной учетной записи, как показано в следующей таблице.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|Имя входа.|  
|**ТРАНСЛЯЦИЮ**|**varbinary(85)**|Идентификатор защиты имени входа (SID).|  
|**DefDBName**|**sysname**|База данных по умолчанию, которую использует **LoginName** при соединении с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**DefLangName**|**sysname**|Язык по умолчанию, используемый в **LoginName**.|  
|**Auser**|**char (5)**|Yes = **LoginName** имеет связанное имя пользователя в базе данных.<br /><br /> No = **LoginName** не имеет связанного имени пользователя.|  
|**ARemote**|**char (7)**|Yes = **LoginName** имеет связанное удаленное имя входа.<br /><br /> No = **LoginName** не имеет связанного имени входа.|  
  
 Второй отчет содержит данные о пользователях, сопоставленных с каждым из имен входа, а также ролях, членом которых является каждое имя входа, как показано в следующей таблице.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|Имя входа.|  
|**DBName**|**sysname**|База данных по умолчанию, которую использует **LoginName** при соединении с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Имен**|**sysname**|Учетная запись пользователя, сопоставленная с **LoginName** в параметре **dbname**, а роли, в которые находится **LoginName** , являются членами в параметре **dbname**.|  
|**UserOrAlias**|**char (8)**|MemberOf = **имя пользователя** является ролью.<br /><br /> Пользователь = **username** является учетной записью пользователя.|  
  
## <a name="remarks"></a>Remarks  
 Перед удалением имени входа используйте **sp_helplogins** , чтобы указать учетные записи пользователей, сопоставленные с именем входа.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли сервера **администратора** .  
  
 Чтобы определить все учетные записи пользователей, сопоставленные с данным именем входа, **sp_helplogins** должны проверить все базы данных в сервере. Однако для каждой базы данных на сервере должно выполняться как минимум одно из следующих условий.  
  
-   Пользователь, который исполняет **sp_helplogins** , имеет разрешение на доступ к базе данных.  
  
-   Учетная запись **гостевого** пользователя включена в базе данных.  
  
 Если **sp_helplogins** не может получить доступ к базе данных, **sp_helplogins** возвратит столько сведений, сколько может и выводит сообщение об ошибке 15622.  
  
## <a name="examples"></a>Примеры  
 Следующий пример выдает данные об имени входа `John`.  
  
```  
EXEC sp_helplogins 'John';  
GO  
  
LoginName SID                        DefDBName DefLangName AUser ARemote   
--------- -------------------------- --------- ----------- ----- -------   
John      0x23B348613497D11190C100C  master    us_english  yes   no  
  
(1 row(s) affected)  
  
LoginName   DBName   UserName   UserOrAlias   
---------   ------   --------   -----------   
John        pubs     John       User          
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_helpdb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helpuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
