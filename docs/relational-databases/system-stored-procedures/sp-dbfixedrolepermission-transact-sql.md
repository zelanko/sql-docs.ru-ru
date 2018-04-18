---
title: sp_dbfixedrolepermission (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_dbfixedrolepermission
- sp_dbfixedrolepermission_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbfixedrolepermission
ms.assetid: b8c30191-f532-49cd-83f3-c271f63ce572
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 02ae10dc752b2122f2d7d86319b336bf5be3bc9f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spdbfixedrolepermission-transact-sql"></a>sp_dbfixedrolepermission (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает разрешения предопределенной роли базы данных. **sp_dbfixedrolepermission** возвращает правильные сведения в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Изменения в иерархии разрешений, реализованные в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], не отражаются. Дополнительные сведения см. в разделе[разрешений &#40;СУБД&#41;](../../relational-databases/security/permissions-database-engine.md).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dbfixedrolepermission [ [ @rolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@rolename =** ] **"***роль***"**  
 Имя допустимой предопределенной роли базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *роль* — **sysname**, значение по умолчанию NULL. Если *роли* не указан, отображаются разрешения для всех предопределенных ролей базы данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**DbFixedRole**|**sysname**|Имя предопределенной роли базы данных|  
|**Разрешение**|**nvarchar(70)**|Разрешения, связанные с **DbFixedRole**|  
  
## <a name="remarks"></a>Замечания  
 Чтобы отобразить список предопределенных ролей базы данных, выполните **sp_helpdbfixedrole**. В следующей таблице представлены предопределенные роли базы данных.  
  
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
  
 Члены **db_owner** предопределенной роли базы данных имеют разрешения всех других предопределенных ролей базы данных. Для отображения разрешений предопределенных ролей сервера, выполните **sp_srvrolepermission**.  
  
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
 [sp_droprolemember & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_helpdbfixedrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdbfixedrole-transact-sql.md)   
 [sp_srvrolepermission &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-srvrolepermission-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
