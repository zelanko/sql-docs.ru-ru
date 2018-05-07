---
title: dbo.syssubsystems (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dbo.syssubsystems
- syssubsystems
- syssubsystems_TSQL
- dbo.syssubsystems_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syssubsystems system table
ms.assetid: 114b3d55-1ad6-4777-b868-8ef0c86ba596
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: abe7c8fa687a5868bae73b9590ea39a30fc90ee2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="dbosyssubsystems-transact-sql"></a>dbo.syssubsystems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения обо всех доступных подсистемах учетных записей-посредников агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **Syssubsystems** таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|Идентификатор подсистемы.|  
|**Подсистема**|**nvarchar(40)**|Имя подсистемы.|  
|**description_id**|**int**|Идентификатор строки в сообщения **sys.messages** каталога представления, содержащего описание подсистемы.|  
|**subsystem_dll**|**nvarchar(255)**|Расположение подсистемы DLL.|  
|**agent_exe**|**nvarchar(255)**|Полный путь к исполняемым объектам, используемым подсистемой.|  
|**start_entry_point**|**nvarchar(30)**|Функция, которая вызывается при инициализации подсистемы.|  
|**event_entry_point**|**nvarchar(30)**|Функция, которая вызывается при запуске шага подсистемы.|  
|**stop_entry_point**|**nvarchar(30)**|Функция, которая вызывается при завершении работы подсистемы.|  
|**max_worker_threads**|**int**|Максимальное число одновременных шагов для заданной подсистемы.|  
  
## <a name="remarks"></a>Замечания  
 Только члены **sysadmin** предопределенной роли сервера можно получить доступ к этой таблице.  
  
## <a name="see-also"></a>См. также  
 [dbo.sysproxysubsystem &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [dbo.sysproxies &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)   
 [sys.messages &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)  
  
  
