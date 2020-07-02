---
title: sys. filetable_system_defined_objects (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0232a635267dc97f53f67309fb59d06651d918ce
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786438"
---
# <a name="sysfiletable_system_defined_objects-transact-sql"></a>sys.filetable_system_defined_objects (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отображает список системных объектов, связанных с таблицами FileTable. Содержит по одной строке для каждого системного объекта.  
  
 При создании FileTable одновременно создаются связанные объекты, такие как ограничения и индексы. Эти объекты нельзя изменять или удалять, они исчезают только после удаления самой таблицы FileTable.  
  
 Дополнительные сведения о таблицах FileTable см. в разделе [Таблицы FileTable (SQL Server)](../../relational-databases/blob/filetables-sql-server.md).  
  
|Столбец|Тип данных|Описание|  
|------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта системных объектов, относящихся к FileTable.<br /><br /> Ссылается на объект в **представлении sys. Objects**.|  
|**parent_object_id**|**int**|Идентификатор объекта родительской таблицы FileTable.<br /><br /> Ссылается на объект в **представлении sys. Objects**.|  
  
## <a name="see-also"></a>См. также  
 [Создание, изменение и удаление таблиц FileTables](../../relational-databases/blob/create-alter-and-drop-filetables.md)   
 [Управление таблицами FileTable](../../relational-databases/blob/manage-filetables.md)  
  
  
