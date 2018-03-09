---
title: "sys.dm_xe_packages (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_xe_packages_TSQL
- sys.dm_xe_packages_TSQL
- dm_xe_packages
- sys.dm_xe_packages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_packages dynamic management view
- extended events [SQL Server], views
ms.assetid: 2e5ecbe9-3ea8-45e6-a161-e31671a03e1d
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d33b1703f517fbedb746d1a0185e960764603ff5
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmxepackages-transact-sql"></a>sys.dm_xe_packages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит список всех пакетов, зарегистрированных подсистемой расширенных событий.  
  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|имя|**nvarchar(60)**|Имя пакета. Это описание берется из самого пакета. Не допускает значение NULL.|  
|guid|**uniqueidentifier**|Идентификатор GUID пакета. Не допускает значение NULL.|  
|description|**nvarchar(256)**|Описание пакета. descriptionis задать автором пакета и не допускает значения NULL.|  
|capabilities|**int**|Битовая карта, описывающая возможности этого пакета. Допускает значение NULL.|  
|capabilities_desc|**nvarchar(256)**|Список всех возможностей, допустимых для этого пакета. Допускает значение NULL.|  
|module_guid|**uniqueidentifier**|Идентификатор GUID модуля, содержащегося в пакете. Не допускает значение NULL.|  
|module_address|**varbinary(8)**|Базовый адрес, по которому загружается модуль, содержащийся в пакете. Один модуль может занимать несколько пакетов. Не допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="remarks"></a>Remarks  
 Пакеты, зарегистрированные подсистемой расширенных событий, содержат события; действия, которые могут быть выполнены в ответ на событие; цели как для синхронной, так и асинхронной обработки данных события.  
  
 Эти пакеты могут быть динамически загружены в адресное пространство процесса. Во время загрузки пакета он регистрирует все объекты, предоставляемые подсистеме расширенных событий.  
  
## <a name="relationship-cardinalities"></a>Количество элементов связей  
  
||||  
|-|-|-|  
|От|Чтобы|Связь|  
|sys.dm_xe_packages.module_address|sys.dm_os_loaded_modules.base_address|Многие к одному|  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

