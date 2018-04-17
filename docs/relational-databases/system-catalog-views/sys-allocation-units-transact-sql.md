---
title: sys.allocation_units (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.allocation_units_TSQL
- sys.allocation_units
- allocation_units_TSQL
- allocation_units
dev_langs:
- TSQL
helpviewer_keywords:
- sys.allocation_units catalog view
ms.assetid: ec9de780-68fd-4551-b70b-2d3ab3709b3e
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 32a9850ab45de9ddd9b32fb7b308584ffadd5c00
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysallocationunits-transact-sql"></a>sys.allocation_units (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Содержит одну строку для каждой единицы распределения в базе данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|allocation_unit_id|**bigint**|Идентификатор единицы распределения. Уникален в базе данных.|  
|Тип|**tinyint**|Тип единицы распределения:<br /><br /> 0 = удаленная;<br /><br /> 1 = внутристрочные данные (все типы данных, за исключением типов данных LOB);<br /><br /> 2 = данные больших объектов (LOB) (**текст**, **ntext**, **изображения**, **xml**, типы больших значений и определяемые пользователем типы среды CLR)<br /><br /> 3 = превышающие размер страницы данные строки.|  
|type_desc|**nvarchar(60)**|Описание типа единицы распределения:<br /><br /> **УДАЛЕНЫ**<br /><br /> **IN_ROW_DATA**<br /><br /> **LOB_DATA**<br /><br /> **ROW_OVERFLOW_DATA**|  
|container_id|**bigint**|Идентификатор контейнера хранения, связанного с единицей распределения.<br /><br /> Если значение type = 1 или 3, то идентификатор container_id = sys.partitions.hobt_id.<br /><br /> Если тип type равен 2, то идентификатор container_id = sys.partitions.partition_id.<br /><br /> 0 = единица распределения помечена для отложенного удаления|  
|data_space_id|**int**|Идентификатор файловой группы, в которой находится эта единица распределения.|  
|total_pages|**bigint**|Общее количество страниц, выделенное или зарезервированное единицей распределения.|  
|used_pages|**bigint**|Общее количество используемых страниц.|  
|data_pages|**bigint**|Количество страниц, включающих:<br /><br /> In-row data<br /><br /> LOB data<br /><br /> Row-overflow data<br /><br /> <br /><br /> Обратите внимание, что возвращаемое значение не содержит внутренние страницы индекса и страницы управления размещением.|  
  
> [!NOTE]  
>  При удалении или перестройке больших индексов либо удалении или усечении больших таблиц компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] откладывает фактическое освобождение страниц и связанных блокировок до момента фиксации транзакции. Отложенные операции удаления не освобождают выделенное место немедленно. Поэтому значения, возвращаемые представлением каталога sys.allocation_units сразу после удаления или усечения большого объекта, могут не отражать реальный объем доступного места на диске.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public** . Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [sys.partitions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
