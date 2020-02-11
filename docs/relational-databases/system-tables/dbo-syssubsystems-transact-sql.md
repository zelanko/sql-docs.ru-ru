---
title: dbo. заполнения таблицы syssubsystems (Transact-SQL) | Документация Майкрософт
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
ms.openlocfilehash: 3f06182f06e92ff581dd02c072b63fc10962921a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68069084"
---
# <a name="dbosyssubsystems-transact-sql"></a>dbo.syssubsystems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения обо всех доступных подсистемах учетных записей-посредников агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Таблица **заполнения таблицы syssubsystems** хранится в базе данных **msdb** .  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|Идентификатор подсистемы.|  
|**подсистемы**|**nvarchar (40)**|Имя подсистемы.|  
|**description_id**|**int**|Идентификатор сообщения строки в представлении каталога **sys. messages** , содержащей описание подсистемы.|  
|**subsystem_dll**|**nvarchar(255)**|Расположение подсистемы DLL.|  
|**agent_exe**|**nvarchar(255)**|Полный путь к исполняемым объектам, используемым подсистемой.|  
|**start_entry_point**|**nvarchar (30)**|Функция, которая вызывается при инициализации подсистемы.|  
|**event_entry_point**|**nvarchar (30)**|Функция, которая вызывается при запуске шага подсистемы.|  
|**stop_entry_point**|**nvarchar (30)**|Функция, которая вызывается при завершении работы подсистемы.|  
|**max_worker_threads**|**int**|Максимальное число одновременных шагов для заданной подсистемы.|  
  
## <a name="remarks"></a>Remarks  
 Только члены предопределенной роли сервера **sysadmin** могут обращаться к этой таблице.  
  
## <a name="see-also"></a>См. также:  
 [dbo. сиспроксисубсистем &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [dbo. sysproxies &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)   
 [sys. messages &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)  
  
  
