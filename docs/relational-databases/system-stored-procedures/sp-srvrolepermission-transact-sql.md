---
title: sp_srvrolepermission (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_srvrolepermission_TSQL
- sp_srvrolepermission
dev_langs:
- TSQL
helpviewer_keywords:
- sp_srvrolepermission
ms.assetid: 5709667f-e3e4-48a2-93ec-af5e22a2ac58
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 930b5ae195ab917faf5425bd2084314a633318b3
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893037"
---
# <a name="sp_srvrolepermission-transact-sql"></a>sp_srvrolepermission (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отображает разрешения предопределенной роли сервера.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_srvrolepermission [ [ @srvrolename = ] 'role']  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @srvrolename = ] 'role'`Имя предопределенной роли сервера, для которой возвращаются разрешения. Аргумент *Role* имеет тип **sysname**и значение по умолчанию NULL. Если роль не указана, возвращаются разрешения для всех предопределенных ролей сервера. *роль* может иметь одно из следующих значений.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|**sysadmin**|Системные администраторы|  
|**securityadmin**|Администраторы безопасности.|  
|**serveradmin**|Администраторы сервера.|  
|**setupadmin**|Администраторы установки.|  
|**processadmin**|Администраторы процесса.|  
|**diskadmin**|Администраторы диска.|  
|**dbcreator**|Создатели баз данных.|  
|**bulkadmin**|Имеющие разрешение на выполнение инструкции BULK INSERT.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**ServerRole**|**sysname**|Имя предопределенной роли сервера|  
|**Разрешение**|**sysname**|Разрешение, связанное с **serverRole**|  
  
## <a name="remarks"></a>Комментарии  
 Перечисляемые разрешения включают допустимые к выполнению инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)], а также другие специальные действия, которые могут выполняться членами предопределенных ролей сервера. Чтобы отобразить список предопределенных ролей сервера, выполните **sp_helpsrvrole**.  
  
 Предопределенной роли сервера **sysadmin** предоставлены разрешения всех других предопределенных ролей сервера.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
 Следующий запрос возвращает разрешения, связанные с предопределенной ролью сервера `sysadmin`.  
  
```  
EXEC sp_srvrolepermission 'sysadmin';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpsrvrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrole-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
