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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fe4c8864856ef9b324a5f44b4811cfff4e8de218
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831695"
---
# <a name="sp_dbfixedrolepermission-transact-sql"></a>sp_dbfixedrolepermission (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает разрешения предопределенной роли базы данных. **sp_dbfixedrolepermission** возвращает правильные сведения в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] . Изменения в иерархии разрешений, реализованные в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], не отражаются. Дополнительные сведения см. в разделе [роли уровня базы данных](../../relational-databases/security/authentication-access/database-level-roles.md#fixed-database-roles), в которых показан список предопределенных ролей базы данных и соответствующие разрешения.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dbfixedrolepermission [ [ @rolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @rolename = ] 'role'`Имя допустимой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предопределенной роли базы данных. Аргумент *Role* имеет тип **sysname**и значение по умолчанию NULL. Если *роль* не указана, отображаются разрешения для всех предопределенных ролей базы данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**DbFixedRole**|**sysname**|Имя предопределенной роли базы данных|  
|**Разрешение**|**nvarchar (70)**|Разрешения, связанные с **дбфикседроле**|  
  
## <a name="remarks"></a>Remarks  
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
  
 Члены предопределенной роли базы данных **db_owner** имеют разрешения всех других предопределенных ролей базы данных. Чтобы отобразить разрешения для предопределенных ролей сервера, выполните **sp_srvrolepermission**.  
  
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
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_helpdbfixedrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdbfixedrole-transact-sql.md)   
 [sp_srvrolepermission &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-srvrolepermission-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
