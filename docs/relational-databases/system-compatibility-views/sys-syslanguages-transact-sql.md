---
title: sys. syslanguages (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bc152b8241b775f9fd686f8a31363cb4fca39de4
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874871"
---
# <a name="syssyslanguages-transact-sql"></a>sys.syslanguages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит одну строку для каждого языка, представленного в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|langid|**smallint**|Уникальный идентификатор языка.|  
|формат даты|**nchar (3)**|Формат представления даты, например DMY.|  
|datefirst|**tinyint**|Первый день недели: 1 для Понедельник, 2 для вторника и так далее до 7 для воскресенья.|  
|обновление|**int**|Зарезервировано для системного использования.|  
|name|**sysname**|Официальное название языка, например Franзais.|  
|alias|**sysname**|Альтернативное название языка, например French.|  
|months|**nvarchar (372)**|Список полных названий месяцев через запятую в порядке с января до декабря. Каждое название может содержать не более 20 символов.|  
|shortmonths|**nvarchar (132)**|Список сокращенных названий месяцев через запятую в порядке с января до декабря. Название может содержать не более 9 символов.|  
|days|**nvarchar (217)**|Список названий дней недели через запятую в порядке с понедельника до воскресенья. Каждое название может содержать не более 30 символов.|  
|lcid|**int**|Код локали языка в [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.|  
|msglangid|**smallint**|Идентификатор группы сообщений компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
  
 Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] содержит следующие установленные языки.  
  
|Английское название языка|Код языка в Windows|Идентификатор группы сообщений компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]|  
|---------------------|------------------|-----------------------------------------|  
|English|1033|1033|  
|German|1031|1031|  
|French|1036|1036|  
|Japanese|1041|1041|  
|Датский|1030|1030|  
|Spanish|3082|3082|  
|Italian|1040|1040|  
|Dutch|1043|1043|  
|Норвежский|2068|2068|  
|Португальский|2070|2070|  
|Финский|1035|1035|  
|Swedish|1053|1053|  
|Czech|1029|1029|  
|Венгерский|1038|1038|  
|Polish|1045|1045|  
|Romanian|1048|1048|  
|Croatian|1050|1050|  
|Slovak|1051|1051|  
|Slovene|1060|1060|  
|Greek|1032|1032|  
|Bulgarian|1026|1026|  
|Russian|1049|1049|  
|Turkish|1055|1055|  
|British English|2057|1033|  
|Эстонский|1061|1061|  
|Latvian|1062|1062|  
|Lithuanian|1063|1063|  
|Portuguese (Brazil)|1046|1046|  
|Traditional Chinese|1028|1028|  
|Korean|1042|1042|  
|Simplified Chinese|2052|2052|  
|Arabic|1025|1025|  
|Thai|1054|1054|  
  
## <a name="see-also"></a>См. также статью  
 [Представления &#40;совместимости Transact-SQL&#41; ](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [Сопоставление системных таблиц с системными &#40;представлениями TRANSACT-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)  
  
  
