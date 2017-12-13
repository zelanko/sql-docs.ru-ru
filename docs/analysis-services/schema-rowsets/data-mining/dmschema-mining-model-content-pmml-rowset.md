---
title: "Набор строк DMSCHEMA_MINING_MODEL_CONTENT_PMML | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
apiname: DMSCHEMA_MINING_MODEL_CONTENT_PMML
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DMSCHEMA_MINING_MODEL_CONTENT_PMML rowset
ms.assetid: fa05bb08-a955-4c8d-b57f-ffcd82470220
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5aedcf454ac340ceff2862728e29b676b9d00893
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="dmschemaminingmodelcontentpmml-rowset"></a>Набор строк DMSCHEMA_MINING_MODEL_CONTENT_PMML
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Возвращает XML-структуру модели интеллектуального анализа данных. Формат XML-строки соответствует стандарту языка разметки прогнозирующих моделей (PMML 2.1).  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DMSCHEMA_MINING_MODEL_CONTENT_PMML** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**||Имя каталога, заполненное именем базы данных, элементом которой является модель.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**||Неполное имя схемы. Этот столбец не поддерживается [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **NULL**.|  
|**MODEL_NAME**|**DBTYPE_WSTR**||Имя модели. Этот столбец не может содержать значение **NULL**.|  
|**MODEL_TYPE**|**DBTYPE_WSTR**||Тип модели. Строка, зависящая от поставщика. Она может иметь значение **NULL**.|  
|**MODEL_GUID**|**DBTYPE_GUID**||Идентификатор GUID, определяющий модель. Поставщики, не использующие идентификаторы GUID для определения таблиц, возвращают значение **NULL**.|  
|**MODEL_PMML**|**DBTYPE_WSTR**||XML-представление содержимого модели в формате PMML.|  
|**РАЗМЕР**|**DBTYPE_UI4**||Число байтов в XML-строке.|  
|**РАСПОЛОЖЕНИЕ**|**DBTYPE_WSTR**||Расположение XML-файла. Представляет собой значение **NULL** , если сведения о расположении недоступны.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DMSCHEMA_MINING_MODEL_CONTENT_PMML** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|Необязательно.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|Необязательно.|  
|**MODEL_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**MODEL_TYPE**|**DBTYPE_WSTR**|Необязательно.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы интеллектуального анализа данных](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
