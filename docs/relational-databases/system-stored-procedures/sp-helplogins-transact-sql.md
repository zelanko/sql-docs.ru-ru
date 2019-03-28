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
manager: craigg
ms.openlocfilehash: 3461d6f80bb1ac693cca78954e5165fb7f012436
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58529746"
---
# <a name="sphelplogins-transact-sql"></a>sp_helplogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет данные об именах учетных записей и соответствующих пользователях в каждой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helplogins [ [ @LoginNamePattern = ] 'login' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @LoginNamePattern = ] 'login'` — Имя входа. Аргумент *login* имеет тип **sysname** и значение по умолчанию NULL. *Имя входа* должен существовать, если задано. Если *входа* является не указан, возвращаются сведения обо всех имен входа.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Первый отчет содержит данные о каждой заданной учетной записи, как показано в следующей таблице.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|Имя входа.|  
|**SID**|**varbinary(85)**|Идентификатор защиты имени входа (SID).|  
|**DefDBName**|**sysname**|По умолчанию базы данных, которые **LoginName** при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**DefLangName**|**sysname**|Язык, используемый по умолчанию **LoginName**.|  
|**Auser**|**char(5)**|Yes = **LoginName** имеет связанное имя пользователя в базе данных.<br /><br /> Нет = **LoginName** не имеет связанного имени пользователя.|  
|**Возможность**|**char(7)**|Yes = **LoginName** имеет связанного имени для удаленного входа.<br /><br /> Нет = **LoginName** не имеет связанного имени для входа.|  
  
 Второй отчет содержит данные о пользователях, сопоставленных с каждым из имен входа, а также ролях, членом которых является каждое имя входа, как показано в следующей таблице.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|Имя входа.|  
|**DBName**|**sysname**|По умолчанию базы данных, которые **LoginName** при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**UserName**|**sysname**|Учетная запись пользователя, **LoginName** сопоставляется в **DBName**и роли, **LoginName** входит в **DBName**.|  
|**UserOrAlias**|**char(8)**|MemberOf = **UserName** — это роль.<br /><br /> Пользователь = **UserName** является учетной записью пользователя.|  
  
## <a name="remarks"></a>Примечания  
 Прежде чем удалить имя входа, используйте **sp_helplogins** для идентификации учетных записей пользователей, сопоставленных с именем входа.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **securityadmin** предопределенной роли сервера.  
  
 Для определения всех учетных записей, сопоставленных с данным именем входа, **sp_helplogins** необходимо проверить все базы данных на сервере. Однако для каждой базы данных на сервере должно выполняться как минимум одно из следующих условий.  
  
-   Пользователь, выполняющий **sp_helplogins** имеет разрешение на доступ к базе данных.  
  
-   **Гостевой** учетной записи пользователя включена в базе данных.  
  
 Если **sp_helplogins** не может получить доступ к базе данных, **sp_helplogins** возвратит столько информации, сколько возможно и сообщение об ошибке 15622.  
  
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
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_helpdb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helpuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
