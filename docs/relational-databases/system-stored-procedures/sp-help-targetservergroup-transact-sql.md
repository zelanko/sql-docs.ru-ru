---
title: sp_help_targetservergroup (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_targetservergroup_TSQL
- sp_help_targetservergroup
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_targetservergroup
ms.assetid: ec3a4a68-b591-431c-9518-053ede522d0c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fcb699741435bace786241ac01a57ad66dd5631d
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528866"
---
# <a name="sphelptargetservergroup-transact-sql"></a>sp_help_targetservergroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Перечисляет все целевые серверы в указанной группе. Если группа не указана, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает сведения обо всех группах целевых серверов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_targetservergroup  
    [ [ @name = ] 'name' ]  
```  
  
## <a name="argument"></a>Аргумент  
`[ @name = ] 'name'` — Имя группы целевых серверов, для которой возвращаются сведения. *имя* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**servergroup_id**|**int**|Идентификационный номер серверной группы|  
|**name**|**sysname**|Имя группы серверов.|  
  
## <a name="permissions"></a>Разрешения  
 Разрешения для выполнения этой процедуры по умолчанию **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-information-for-all-target-server-groups"></a>A. Вывод сведений обо всех группах целевых серверов  
 В этом примере выводятся сведения обо всех целевых серверных группах.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_targetservergroup ;  
GO  
```  
  
### <a name="b-listing-information-for-a-specific-target-server-group"></a>Б. Вывод сведений об определенной группе целевых серверов  
 В этом примере выводятся сведения о целевой серверной группе `Servers Maintaining Customer Information`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_targetservergroup   
    N'Servers Maintaining Customer Information' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_targetservergroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql.md)   
 [sp_delete_targetservergroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql.md)   
 [sp_update_targetservergroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
