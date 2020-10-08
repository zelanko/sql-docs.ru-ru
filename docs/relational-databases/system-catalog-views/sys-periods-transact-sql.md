---
description: sys. Periods (Transact-SQL)
title: sys. Periods (Transact-SQL) | Документация Майкрософт
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c091649234826080054de942ed96272055a1b595
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2020
ms.locfileid: "91810335"
---
# <a name="sysperiods-transact-sql"></a>sys. Periods (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Возвращает строку для каждой таблицы, для которой были определены периоды.  
  
|Заголовок столбца|Тип данных|Описание|  
|-------------------|---------------|-----------------|  
|name|**sysname**|Имя периода|  
|period_type|**tinyint**|Числовое значение, представляющее тип периода:<br /><br /> 1 = системный период времени|  
|period_type_desc|**nvarchar(60)**|Текстовое описание типа столбца:<br /><br /> SYSTEM_TIME_PERIOD|  
|object_id|**int**|Идентификатор таблицы, содержащей столбец period_type|  
|start_column_id|**int**|Идентификатор столбца, определяющего нижнюю границу периода|  
|end_column_id|**int**|Идентификатор столбца, определяющего границу верхнего периода|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Системные представления &#40;&#41;Transact-SQL ](../../t-sql/language-reference.md)   
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.system_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-columns-transact-sql.md)   
 [Запросы к системному каталогу SQL Server вопросы и ответы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Темпоральные таблицы](../../relational-databases/tables/temporal-tables.md)  
  
