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
ms.openlocfilehash: 6613c4e94ce8c802e45fe003ac73e51b3f38072b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68032807"
---
# <a name="sp_srvrolepermission-transact-sql"></a>sp_srvrolepermission (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
|Значение|Description|  
|-----------|-----------------|  
|**sysadmin**|Системные администраторы|  
|**администратора**|Администраторы безопасности.|  
|**serveradmin**|Администраторы сервера|  
|**setupadmin**|Администраторы установки.|  
|**processadmin**|Администраторы процесса.|  
|**diskadmin**|Администраторы диска.|  
|**создателя**|Создатели баз данных|  
|**bulkadmin**|Имеющие разрешение на выполнение инструкции BULK INSERT.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**ServerRole**|**имеет sysname**|Имя предопределенной роли сервера|  
|**Разрешение**|**имеет sysname**|Разрешение, связанное с **serverRole**|  
  
## <a name="remarks"></a>Remarks  
 Перечисляемые разрешения включают допустимые к выполнению инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)], а также другие специальные действия, которые могут выполняться членами предопределенных ролей сервера. Чтобы отобразить список предопределенных ролей сервера, выполните **sp_helpsrvrole**.  
  
 Предопределенной роли сервера **sysadmin** предоставлены разрешения всех других предопределенных ролей сервера.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли **Public** .  
  
## <a name="examples"></a>Примеры  
 Следующий запрос возвращает разрешения, связанные с предопределенной ролью сервера `sysadmin`.  
  
```  
EXEC sp_srvrolepermission 'sysadmin';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpsrvrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrole-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
