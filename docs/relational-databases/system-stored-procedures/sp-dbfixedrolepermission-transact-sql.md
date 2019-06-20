---
title: sp_dbfixedrolepermission (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbfixedrolepermission
- sp_dbfixedrolepermission_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbfixedrolepermission
ms.assetid: b8c30191-f532-49cd-83f3-c271f63ce572
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 41c84c97027c8bfae82d3ac457c454f6a4d497e6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62724035"
---
# <a name="spdbfixedrolepermission-transact-sql"></a>sp_dbfixedrolepermission (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает разрешения предопределенной роли базы данных. **sp_dbfixedrolepermission** возвращает правильные сведения в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Изменения в иерархии разрешений, реализованные в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], не отражаются. Дополнительные сведения см. в разделе[разрешения &#40;СУБД&#41;](../../relational-databases/security/permissions-database-engine.md).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dbfixedrolepermission [ [ @rolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @rolename = ] 'role'` Имя является допустимым [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предопределенной роли базы данных. *роль* — **sysname**, значение по умолчанию NULL. Если *роли* не указан, отображаются разрешения для всех предопределенных ролей базы данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**DbFixedRole**|**sysname**|Имя предопределенной роли базы данных|  
|**Разрешение**|**nvarchar(70)**|Разрешения, связанные с **DbFixedRole**|  
  
## <a name="remarks"></a>Примечания  
 Для отображения списка предопределенных ролей базы данных выполните процедуру **sp_helpdbfixedrole**. В следующей таблице представлены предопределенные роли базы данных.  
  
|Предопределенная роль базы данных|Описание|  
|-------------------------|-----------------|  
|**db_owner**|Владельцы базы данных|  
|**db_accessadmin**|Администраторы доступа к базе данных|  
|**db_securityadmin**|Администраторы безопасности базы данных|  
|**db_ddladmin**|Администраторы языка определения данных (DDL)|  
|**db_backupoperator**|Операторы резервного копирования базы данных|  
|**db_datareader**|Модули чтения данных из базы данных|  
|**db_datawriter**|Модули записи данных в базу данных|  
|**db_denydatareader**|Модули чтения данных из базы данных, которым отказано в доступе|  
|**db_denydatawriter**|Модули записи данных в базу данных, которым отказано в доступе|  
  
 Членами **db_owner** предопределенной роли базы данных имеют разрешения всех других предопределенных ролей базы данных. Для отображения разрешения для предопределенных ролей сервера выполните процедуру **sp_srvrolepermission**.  
  
 В результирующий набор входят инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)], которые могут быть выполнены, и другие особые действия, которые могут быть выполнены членами роли базы данных.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
 Следующий запрос возвращает разрешения для всех предопределенных ролей базы данных, так как не указывает предопределенную роль базы данных.  
  
```  
EXEC sp_dbfixedrolepermission;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Хранимая процедура sp_addrolemember (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_helpdbfixedrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdbfixedrole-transact-sql.md)   
 [sp_srvrolepermission &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-srvrolepermission-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
