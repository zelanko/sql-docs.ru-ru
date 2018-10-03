---
title: sys.Periods (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 25e66ed3-2270-4c5c-9f5a-2c0f165a57ca
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 58ee2ac11e86481c57da79d84bc75507c273b829
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47702526"
---
# <a name="sysperiods-transact-sql"></a>sys.Periods (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Возвращает строку для каждой таблицы, для которого определены периодов.  
  
|Заголовок столбца|Тип данных|Описание|  
|-------------------|---------------|-----------------|  
|period_type|**sysname**|Название периода|  
|period_type_desc|**tinyint**|Числовое значение, представляющее тип периода:<br /><br /> 1 = период системного времени|  
|object_id|**nvarchar(60)**|Текстовое описание типа столбца:<br /><br /> SYSTEM_TIME_PERIOD|  
|object_id|**int**|Идентификатор таблицы, содержащей столбец period_type|  
|start_column_id|**int**|Идентификатор столбца, который определяет нижнюю границу периода|  
|end_column_id|**int**|Идентификатор столбца, который определяет верхнюю границу периода|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Системные представления &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.system_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-columns-transact-sql.md)   
 [Запросив системный каталог SQL Server часто задаваемые вопросы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Темпоральные таблицы](../../relational-databases/tables/temporal-tables.md)  
  
  
