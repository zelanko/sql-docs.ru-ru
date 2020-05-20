---
title: sys. time_zone_info (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.time_zone_info
- sys.time_zone_info_TSQL
- time_zone_info
- time_zone_info_TSQL
helpviewer_keywords:
- sys.time_zone_info system table
ms.assetid: 3f51a9a4-75f8-4a11-9552-8bf6118b68da
author: CarlRabeler
ms.author: carlrab
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0475dc1666af92e141610e56200a881798b3774b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82821333"
---
# <a name="systime_zone_info-transact-sql"></a>sys. time_zone_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Возвращает сведения о поддерживаемых часовых поясах. Все часовые пояса, установленные на компьютере, хранятся в следующем кусте реестра:  
`KEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones`.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя часового пояса в стандартном формате Windows. Например, Central **. Австралия (зима** ) или **Центральноевропейское время**(зима).|  
|**current_utc_offset**|**nvarchar (12)**|Текущее смещение до UTC. Например, **+ 01:00** или **-07:00**.|  
|**is_currently_dst**|**bit**|Значение true, если в настоящее время выполняется наблюдение за летним временем.|  
  
## <a name="see-also"></a>См. также  
 [GETUTCDATE &#40;Transact-SQL&#41;](../../t-sql/functions/getutcdate-transact-sql.md)   
 [НА&#41;часового пояса &#40;Transact-SQL](../../t-sql/queries/at-time-zone-transact-sql.md)   
 [Типы данных и функции даты и времени &#40;языке Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [Представления каталога конфигурации на уровне сервера &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)  
