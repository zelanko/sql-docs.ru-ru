---
title: "Набор строк DMSCHEMA_MINING_MODEL_XML | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DMSCHEMA_MINING_MODEL_XML
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DMSCHEMA_MINING_MODEL_XML rowset
ms.assetid: f58b00e9-3f72-4cff-b448-21a9fb529772
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0d508a1bc916d75ff33e5aba19c6306a547af8fb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="dmschemaminingmodelxml-rowset"></a>Набор строк DMSCHEMA_MINING_MODEL_XML
  Возвращает XML-структуру модели интеллектуального анализа данных. Формат XML-строки соответствует стандарту языка разметки прогнозирующих моделей (PMML 2.1).  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DMSCHEMA_MINING_MODEL_XML** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**||Имя каталога. Заполняется именем базы данных, элементом которой является модель.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**||Неполное имя схемы. Этот столбец не поддерживается [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **NULL**.|  
|**MODEL_NAME**|**DBTYPE_WSTR**||Имя модели. Этот столбец не может содержать значение **NULL**.|  
|**MODEL_TYPE**|**DBTYPE_WSTR**||Тип модели. Строка, зависящая от поставщика. Она может иметь значение **NULL**.|  
|**MODEL_GUID**|**DBTYPE_GUID**||Идентификатор GUID, определяющий модель. Поставщики, не использующие идентификаторы GUID для определения таблиц, возвращают значение **NULL**.|  
|**MODEL_PMML**|**DBTYPE_WSTR**||XML-представление содержимого модели в формате PMML.|  
|**РАЗМЕР**|**DBTYPE_UI4**||Число байтов в XML-строке.|  
|**РАСПОЛОЖЕНИЕ**|**DBTYPE_WSTR**||Расположение XML-файла. Содержит значение **NULL** , если физический файл не используется для хранения.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк DMSCHEMA_MINING_MODEL_XML может быть ограничен столбцами, приведенными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**MODEL_CATALOG**|**DBTYPE_W**STR|Необязательно.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|Необязательно.|  
|**MODEL_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**MODEL_TYPE**|**DBTYPE_WSTR**|Необязательно.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы интеллектуального анализа данных](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  

