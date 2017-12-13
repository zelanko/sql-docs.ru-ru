---
title: "Набор строк DMSCHEMA_MINING_STRUCTURES | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DMSCHEMA_MINING_STRUCTURES
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DMSCHEMA_MINING_STRUCTURES rowset
ms.assetid: 6224556b-08a0-496e-bd7c-632c3e833e26
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0c7b170ca376598dba93d1f586ebea2c60f4f101
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="dmschemaminingstructures-rowset"></a>Набор строк DMSCHEMA_MINING_STRUCTURES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Перечисляет сведения о структурах интеллектуального анализа данных в текущем каталоге.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DMSCHEMA_MINING_STRUCTURES** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**STRUCTURE_CATALOG**|**DBTYPE_WSTR**||Имя каталога.|  
|**STRUCTURE_SCHEMA**|**DBTYPE_WSTR**||Неполное имя схемы. Значение**NULL** , если схемы не поддерживаются поставщиком.|  
|**STRUCTURE_NAME**|**DBTYPE_WSTR**||Имя структуры. Этот столбец не может содержать значение **NULL**.|  
|**STRUCTURE_GUID**|**DBTYPE_GUID**||Идентификатор GUID, который однозначно определяет структуру. Значение**NULL** , если не поддерживается поставщиком.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Краткое описание структуры. Значение**NULL** , если со структурой не связано описание.|  
|**STRUCTURE_PROPID**|**DBTYPE_UI4**||Идентификатор свойства структуры. Значение**NULL** , если не поддерживается поставщиком.|  
|**DATE_CREATED**|**DBTYPE_DBTIMESTAMP**||Дата создания структуры. Значение**NULL** , если не предоставляется поставщиком.|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**||Дата последнего изменения структуры. Значение**NULL** , если не предоставляется поставщиком.|  
|**CREATION_STATEMENT**|**DBTYPE_WSTR**||Инструкция, которая использовалась для создания первоначальной модели интеллектуального анализа данных (необязательно).|  
|**IS_POPULATED**|**DBTYPE_BOOL**||Логическое значение, которое указывает, заполнена ли структура.<br /><br /> **VARIANT_TRUE** , если структура заполнена; **VARIANT_FALSE** в противном случае.|  
|**LAST_PROCESSED**|**DBTYPE_DBTIMESTAMP**||Дата последней обработки структуры. Значение**NULL** , если не предоставляется поставщиком.|  
|**HOLDOUT_MAXPERCENT**|**DBTYPE_ UI1**||Заданное пользователем значение, которое указывает максимальную процентную долю входных вариантов, зарезервированных как проверочный набор.<br /><br /> 0 или значение **NULL** указывает на отсутствие ограничения.|  
|**HOLDOUT_MAXCASES**|**DBTYPE_UI8**||Заданное пользователем значение, которое указывает максимальное количество входных вариантов, зарезервированных как проверочный набор.<br /><br /> 0 или значение **NULL** указывает на отсутствие ограничения.|  
|**HOLDOUT_SEED**|**DBTYPE_UI8**||Заданное пользователем значение, которое используется как начальное значение для повторяемого секционирования.<br /><br /> Значение 0 указывает, что в качестве начального значения используется хэш идентификатора структуры интеллектуального анализа данных.|  
|**HOLDOUT_ACTUAL_SIZE**|**DBTYPE_UI8**||Если структура интеллектуального анализа данных обработана, это значение указывает фактический размер проверочного набора данных, выраженный как количество вариантов.<br /><br /> Значение**NULL** указывает, что структура интеллектуального анализа данных не обработана.|  
  
 Набор строк отсортирован по **STRUCTURE_CATALOG**, **STRUCTURE_SCHEMA**, **STRUCTURE_NAME**.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DMSCHEMA_MINING_STRUCTURES** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**STRUCTURE_CATALOG**|**DBTYPE_WSTR**|Необязательно.|  
|**STRUCTURE_SCHEMA**|**DBTYPE_WSTR**|Необязательно.|  
|**STRUCTURE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы интеллектуального анализа данных](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
