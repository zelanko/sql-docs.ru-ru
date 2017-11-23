---
title: "sys.dm_os_loaded_modules (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_loaded_modules
- dm_os_loaded_modules
- sys.dm_os_loaded_modules_TSQL
- dm_os_loaded_modules_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_loaded_modules dynamic management view
ms.assetid: 56c7743a-b568-4943-bd3b-73c57d9d641c
caps.latest.revision: "20"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3c260b70aca72d90254571bc819dd20704bafbb0
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmosloadedmodules-transact-sql"></a>sys.dm_os_loaded_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по строке для каждого модуля, загруженного в адресное пространство сервера.  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_loaded_modules**.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**base_address**|**varbinary(8)**|Адрес модуля в процессе.|  
|**file_version**|**varchar(23)**|Версия файла. Отображается в следующем формате:<br /><br /> x.x:x.x|  
|**product_version**|**varchar(23)**|Версия продукта. Отображается в следующем формате:<br /><br /> x.x:x.x|  
|**Отладка**|**bit**|1 = Модуль является отладочной версией загруженного модуля.|  
|**Исправлено**|**bit**|1 = Модуль был обновлен.|  
|**Предварительный выпуск**|**bit**|1 = Модуль является предварительной версией загруженного модуля.|  
|**private_build**|**bit**|1 = Модуль является внутренней сборкой загруженного модуля.|  
|**special_build**|**bit**|1 = Модуль является специальной сборкой загруженного модуля.|  
|**язык**|**int**|Язык сведений о версии модуля.|  
|**компании**|**nvarchar(256)**|Имя компании, создавшей модуль.|  
|**Описание**|**nvarchar(256)**|Описание модуля.|  
|**name**|**nvarchar(255)**|Имя модуля. Включает полный путь к модулю.|  
|**pdw_node_id**|**int**|**Применяется к**:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Permissions  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Относящиеся к операционной системе SQL Server динамические административные представления &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
