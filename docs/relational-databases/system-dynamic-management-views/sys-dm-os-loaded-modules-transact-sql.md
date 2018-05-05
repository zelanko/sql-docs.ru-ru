---
title: sys.dm_os_loaded_modules (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_loaded_modules
- dm_os_loaded_modules
- sys.dm_os_loaded_modules_TSQL
- dm_os_loaded_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_loaded_modules dynamic management view
ms.assetid: 56c7743a-b568-4943-bd3b-73c57d9d641c
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 29e91f1859eb1dabe8bfa7df42acf594c021679d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmosloadedmodules-transact-sql"></a>sys.dm_os_loaded_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по строке для каждого модуля, загруженного в адресное пространство сервера.  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_loaded_modules**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**base_address**|**varbinary(8)**|Адрес модуля в процессе.|  
|**file_version**|**varchar(23)**|Версия файла. Отображается в следующем формате:<br /><br /> x.x:x.x|  
|**product_version**|**varchar(23)**|Версия продукта. Отображается в следующем формате:<br /><br /> x.x:x.x|  
|**debug**|**бит**|1 = Модуль является отладочной версией загруженного модуля.|  
|**Исправлено**|**бит**|1 = Модуль был обновлен.|  
|**Предварительный выпуск**|**бит**|1 = Модуль является предварительной версией загруженного модуля.|  
|**private_build**|**бит**|1 = Модуль является внутренней сборкой загруженного модуля.|  
|**special_build**|**бит**|1 = Модуль является специальной сборкой загруженного модуля.|  
|**Язык**|**int**|Язык сведений о версии модуля.|  
|**Компании**|**nvarchar(256)**|Имя компании, создавшей модуль.|  
|**Описание**|**nvarchar(256)**|Описание модуля.|  
|**name**|**nvarchar(255)**|Имя модуля. Включает полный путь к модулю.|  
|**pdw_node_id**|**int**|**Область применения**: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
