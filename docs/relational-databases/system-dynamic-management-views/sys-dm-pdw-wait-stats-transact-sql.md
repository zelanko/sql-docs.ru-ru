---
title: sys.dm_pdw_wait_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cfb8d905-c34f-44de-9574-dde81e170916
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: c6ee905e387f0333b26f99b9b73859e273711df7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47852252"
---
# <a name="sysdmpdwwaitstats-transact-sql"></a>sys.dm_pdw_wait_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения, относящиеся к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] состояние операционной системы, связанные с экземпляров, работающих на разных узлах. Список типов ожиданий и их описание см. в разделе [sys.dm_os_wait_stats](http://msdn.microsoft.com/library/ms179984\(v=sql.120\).aspx).  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|**pdw_node_id**|**int**|Идентификатор узла, на который ссылается эта запись.||  
|**wait_name**|**nvarchar(255)**|Имя типа ожидания.||  
|**max_wait_time**|**bigint**|Максимальное время ожидания данного типа ожидания.||  
|**request_count**|**bigint**|Число ожиданий данного типа, которые необработанных ожидания.||  
|**signal_time**|**bigint**|Разница между временем сигнализации ожидающего потока и временем начала его выполнения.||  
|**completed_count**|**bigint**|Общее количество случаев ожидания для этого типа, завершено с момента его последнего перезапуска.||  
|**wait_time**|**bigint**|Общее время ожидания для данного типа в millisecons. Инклюзивное signal_time.||  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [sys.dm_pdw_waits &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)  
  
  
