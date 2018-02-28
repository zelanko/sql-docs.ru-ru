---
title: "sys.syslanguages (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.syslanguages
- sys.syslanguages_TSQL
- syslanguages
- syslanguages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syslanguages system table
- sys.syslanguages compatibility view
ms.assetid: f216d1cd-997c-42f0-a737-abbdfcd88383
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 47eb77543c650a16650680435e5d0db7d395eade
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="syssyslanguages-transact-sql"></a>sys.syslanguages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит одну строку для каждого языка, представленного в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|langid|**smallint**|Уникальный идентификатор языка.|  
|формат даты|**nchar(3)**|Формат представления даты, например DMY.|  
|datefirst|**tinyint**|Первый день недели: 1 — понедельник, 2 — вторник и так далее до 7 — воскресенье.|  
|обновление|**int**|Зарезервировано для системного использования.|  
|имя|**sysname**|Официальное название языка, например Français.|  
|alias|**sysname**|Альтернативное название языка, например French.|  
|months|**nvarchar(372)**|Список полных названий месяцев через запятую в порядке с января до декабря. Каждое название может содержать не более 20 символов.|  
|shortmonths|**nvarchar(132)**|Список сокращенных названий месяцев через запятую в порядке с января до декабря. Название может содержать не более 9 символов.|  
|days|**nvarchar(217)**|Список названий дней недели через запятую в порядке с понедельника до воскресенья. Каждое название может содержать не более 30 символов.|  
|lcid|**int**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Код данной локали в Windows.|  
|msglangid|**smallint**|[!INCLUDE[ssDE](../../includes/ssde-md.md)] Идентификатор группы сообщений.|  
  
 Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] содержит следующие установленные языки.  
  
|Английское название языка|Код языка в Windows|[!INCLUDE[ssDE](../../includes/ssde-md.md)] Идентификатор группы сообщений|  
|---------------------|------------------|-----------------------------------------|  
|Английский|1033|1033|  
|Немецкий|1031|1031|  
|Французский|1036|1036|  
|Японский|1041|1041|  
|Danish|1030|1030|  
|Испанский|3082|3082|  
|Итальянский|1040|1040|  
|Нидерландский|1043|1043|  
|Норвежский|2068|2068|  
|Португальский|2070|2070|  
|Финский|1035|1035|  
|Шведский|1053|1053|  
|Czech|1029|1029|  
|Венгерский|1038|1038|  
|Польский|1045|1045|  
|Румынский|1048|1048|  
|Хорватский|1050|1050|  
|Словацкий|1051|1051|  
|Slovene|1060|1060|  
|Greek|1032|1032|  
|Болгарский|1026|1026|  
|Русский|1049|1049|  
|Турецкий|1055|1055|  
|British English|2057|1033|  
|Эстонский|1061|1061|  
|Латышский|1062|1062|  
|Литовский|1063|1063|  
|Бразильский португальский|1046|1046|  
|Китайский (традиционный)|1028|1028|  
|Корейский|1042|1042|  
|Китайский (упрощенный)|2052|2052|  
|Арабский|1025|1025|  
|Тайский|1054|1054|  
  
## <a name="see-also"></a>См. также  
 [Представления совместимости &#40; Transact-SQL &#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [Сопоставление системных таблиц с системными представлениями &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)  
  
  
