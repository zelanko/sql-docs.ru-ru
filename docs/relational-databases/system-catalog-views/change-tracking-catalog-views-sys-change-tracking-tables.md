---
description: Отслеживание изменений представлений каталога sys.change_tracking_tables
title: sys.change_tracking_tables (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- change_tracking_tables_TSQL
- sys.change_tracking_tables
- change_tracking_tables
- sys.change_tracking_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- change tracking [SQL Server], sys.change_tracking_tables
- sys.change_tracking_tables
ms.assetid: 97ec69b6-0d49-4d98-82f0-d3e77ba1ad2b
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1837ce515f31a0a8c98c2c63b0ef4ab853bad19a
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97475245"
---
# <a name="change-tracking-catalog-views---syschange_tracking_tables"></a>Отслеживание изменений представлений каталога sys.change_tracking_tables
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает по одной строке для каждой таблицы в текущей базе данных, для которой включено отслеживание изменений.  
   
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Идентификатор таблицы, для которой ведется журнал изменений. Ведение журнала изменений для таблицы возможно даже в случае, если отслеживание изменений отключено.<br /><br /> Идентификатор таблицы уникален в пределах базы данных.|  
|is_track_columns_updated_on|**bit**|Текущее состояние отслеживания изменений для таблицы:<br /><br /> 0 = выключен.<br /><br /> 1 = включен;|  
|begin_version|**bigint**|Версия базы данных, с которой началось отслеживание изменений для таблицы. Эта версия обычно указывает, когда было включено отслеживание изменений, однако это значение сбрасывается при усечении таблицы.|  
|cleanup_version|**bigint**|Версия, вплоть до которой при очистке могли быть удалены данные отслеживания изменений.|  
|min_valid_version|**bigint**|Минимально допустимая версия данных отслеживания изменений, доступная для таблицы.<br /><br /> При получении изменений из таблицы, связанной с данной строкой, значение last_sync_version должно быть больше либо равно версии, указанной в этом столбце. Дополнительные сведения см. в разделе [CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md).|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [CHANGE_TRACKING_MIN_VALID_VERSION (Transact-SQL)](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)   
 [Отслеживание изменений представления каталога &#40;&#41;Transact-SQL ](./catalog-views-transact-sql.md)   
 [Отслеживание измененных данных (SQL Server)](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
