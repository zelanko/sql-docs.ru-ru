---
title: sys. allocation_units (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c996a258ae9f0dacec09fc58b3f433e620b6d663
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82822115"
---
# <a name="sysallocation_units-transact-sql"></a>sys.allocation_units (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Содержит одну строку для каждой единицы распределения в базе данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|allocation_unit_id|**bigint**|Идентификатор единицы распределения. Уникален в базе данных.|  
|тип|**tinyint**|Тип единицы распределения:<br /><br /> 0 = удаленная;<br /><br /> 1 = внутристрочные данные (все типы данных, за исключением типов данных LOB);<br /><br /> 2 = данные больших объектов (LOB) (**Text**, **ntext**, **Image**, **XML**, типы больших значений и определяемые пользователем типы данных CLR)<br /><br /> 3 = превышающие размер страницы данные строки.|  
|type_desc|**nvarchar(60)**|Описание типа единицы распределения:<br /><br /> **РЫВАЕТ**<br /><br /> **IN_ROW_DATA**<br /><br /> **LOB_DATA**<br /><br /> **ROW_OVERFLOW_DATA**|  
|container_id|**bigint**|Идентификатор контейнера хранения, связанного с единицей распределения.<br /><br /> Если значение type = 1 или 3, то идентификатор container_id = sys.partitions.hobt_id.<br /><br /> Если тип type равен 2, то идентификатор container_id = sys.partitions.partition_id.<br /><br /> 0 = единица распределения помечена для отложенного удаления|  
|data_space_id|**int**|Идентификатор файловой группы, в которой находится эта единица распределения.|  
|total_pages|**bigint**|Общее количество страниц, выделенное или зарезервированное единицей распределения.|  
|used_pages|**bigint**|Общее количество используемых страниц.|  
|data_pages|**bigint**|Количество страниц, включающих:<br /><br /> In-row data<br /><br /> LOB data<br /><br /> Row-overflow data<br /><br /> <br /><br /> Обратите внимание, что возвращаемое значение исключает страницы внутреннего индекса и страницы управления выделением.|  
  
> [!NOTE]  
>  При удалении или перестройке больших индексов либо удалении или усечении больших таблиц компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] откладывает фактическое освобождение страниц и связанных блокировок до момента фиксации транзакции. Отложенные операции удаления не освобождают выделенное место немедленно. Поэтому значения, возвращаемые представлением каталога sys.allocation_units сразу после удаления или усечения большого объекта, могут не отражать реальный объем доступного места на диске.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [sys. partitions &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [Представления каталога объектов &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
