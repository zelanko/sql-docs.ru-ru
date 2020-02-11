---
title: dbo. sysproxies (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysproxies_TSQL
- sysproxies_TSQL
- dbo.sysproxies
- sysproxies
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxies system table
ms.assetid: a73da875-be22-45fc-b5e2-ea7ebd48e2d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1dd486757a912d8f0364f55570a368292cf39ab7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67984903"
---
# <a name="dbosysproxies-transact-sql"></a>dbo.sysproxies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Определяет атрибуты учетной записи-посредника агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта таблица хранится в базе данных **msdb** .  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|Идентификатор учетной записи-посредника.|  
|**name**|**имеет sysname**|Имя учетной записи-посредника.|  
|**credential_id**|**int**|Идентификатор учетных данных, используемых учетной записью-посредником.|  
|**доступной**|**tinyint**|Состояние учетной записи-посредника:<br /><br /> **0** = отключено. **1** = включено.|  
|**nописание**|**nvarchar(512)**|Описание, введенное пользователем при создании учетной записи-посредника.|  
|**user_sid**|**varbinary (85)**|*Security_identifier* Microsoft Windows для пользователя или группы, связанных с учетными данными прокси-сервера.|  
|**credential_date_created**|**datetime**|Дата и время создания учетных данных.|  
  
## <a name="remarks"></a>Remarks  
 Только члены предопределенной роли сервера **sysadmin** могут обращаться к таблице **sysproxies** .  
  
## <a name="see-also"></a>См. также:  
 [dbo. сиспроксилогин &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxylogin-transact-sql.md)   
 [dbo. сиспроксисубсистем &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [dbo. заполнения таблицы syssubsystems &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-syssubsystems-transact-sql.md)  
  
  
