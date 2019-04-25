---
title: dbo.syssubsystems (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d685f5e8837feebffeeeade95697f4f3bfea4c81
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62470504"
---
# <a name="dbosyssubsystems-transact-sql"></a>dbo.syssubsystems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения обо всех доступных подсистемах учетных записей-посредников агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **Syssubsystems** таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|Идентификатор подсистемы.|  
|**подсистемы**|**nvarchar(40)**|Имя подсистемы.|  
|**description_id**|**int**|Идентификатор строки в сообщения **sys.messages** каталога представления, содержащего описание подсистемы.|  
|**subsystem_dll**|**nvarchar(255)**|Расположение подсистемы DLL.|  
|**agent_exe**|**nvarchar(255)**|Полный путь к исполняемым объектам, используемым подсистемой.|  
|**start_entry_point**|**nvarchar(30)**|Функция, которая вызывается при инициализации подсистемы.|  
|**event_entry_point**|**nvarchar(30)**|Функция, которая вызывается при запуске шага подсистемы.|  
|**stop_entry_point**|**nvarchar(30)**|Функция, которая вызывается при завершении работы подсистемы.|  
|**max_worker_threads**|**int**|Максимальное число одновременных шагов для заданной подсистемы.|  
  
## <a name="remarks"></a>Примечания  
 Только члены **sysadmin** предопределенной роли сервера можно получить доступ к этой таблице.  
  
## <a name="see-also"></a>См. также  
 [dbo.sysproxysubsystem &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [dbo.sysproxies &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)   
 [sys.messages &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)  
  
  
