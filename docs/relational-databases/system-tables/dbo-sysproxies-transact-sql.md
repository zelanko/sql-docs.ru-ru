---
title: "dbo.sysproxies (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.sysproxies_TSQL
- sysproxies_TSQL
- dbo.sysproxies
- sysproxies
dev_langs: TSQL
helpviewer_keywords: sysproxies system table
ms.assetid: a73da875-be22-45fc-b5e2-ea7ebd48e2d6
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b28fdf8c7cee40fa088ee0d7634e4ea17aba91c8
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysproxies-transact-sql"></a>dbo.sysproxies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Определяет атрибуты учетной записи-посредника агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|Идентификатор учетной записи-посредника.|  
|**name**|**sysname**|Имя учетной записи-посредника.|  
|**credential_id**|**int**|Идентификатор учетных данных, используемых учетной записью-посредником.|  
|**включен**|**tinyint**|Состояние учетной записи-посредника:<br /><br /> **0** = отключено. **1** = включен.|  
|**Описание**|**nvarchar(512)**|Описание, введенное пользователем при создании учетной записи-посредника.|  
|**user_sid**|**varbinary(85)**|Microsoft Windows *security_identifier* пользователя или группы, связанные с учетными данными прокси-сервера.|  
|**credential_date_created**|**datetime**|Дата и время создания учетных данных.|  
  
## <a name="remarks"></a>Замечания  
 Только члены **sysadmin** предопределенной роли сервера можно получить доступ к **sysproxies** таблицы.  
  
## <a name="see-also"></a>См. также:  
 [dbo.sysproxylogin &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-sysproxylogin-transact-sql.md)   
 [dbo.sysproxysubsystem &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [dbo.syssubsystems &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-syssubsystems-transact-sql.md)  
  
  
