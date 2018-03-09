---
title: "sys.filetable_system_defined_objects (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.filetable_system_defined_objects_TSQL
- filetable_system_defined_objects
- filetable_system_defined_objects_TSQL
- sys.filetable_system_defined_objects
dev_langs:
- TSQL
helpviewer_keywords:
- sys.filetable_system_defined_objects catalog view
ms.assetid: 62022e6b-46f6-495f-b14b-53f41e040361
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c3bd6bd8368525c94ce0d999af921c76c2cade96
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sysfiletablesystemdefinedobjects-transact-sql"></a>sys.filetable_system_defined_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает список системных объектов, связанных с таблицами FileTable. Содержит по одной строке для каждого системного объекта.  
  
 При создании FileTable одновременно создаются связанные объекты, такие как ограничения и индексы. Эти объекты нельзя изменять или удалять, они исчезают только после удаления самой таблицы FileTable.  
  
 Дополнительные сведения о таблицах Filetable см. в разделе [FileTables &#40; SQL Server &#41; ](../../relational-databases/blob/filetables-sql-server.md).  
  
|Столбец|Data type|Description|  
|------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта системных объектов, относящихся к FileTable.<br /><br /> Ссылается на объект в **sys.objects**.|  
|**parent_object_id**|**int**|Идентификатор объекта родительской таблицы FileTable.<br /><br /> Ссылается на объект в **sys.objects**.|  
  
## <a name="see-also"></a>См. также:  
 [Создание, изменение и удаление таблиц FileTables](../../relational-databases/blob/create-alter-and-drop-filetables.md)   
 [Управление таблицами FileTable](../../relational-databases/blob/manage-filetables.md)  
  
  
