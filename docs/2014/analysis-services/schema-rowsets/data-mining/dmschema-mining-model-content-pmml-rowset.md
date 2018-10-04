---
title: Набор строк DMSCHEMA_MINING_MODEL_CONTENT_PMML | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DMSCHEMA_MINING_MODEL_CONTENT_PMML
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_MODEL_CONTENT_PMML rowset
ms.assetid: fa05bb08-a955-4c8d-b57f-ffcd82470220
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 23d900676f0a3abf0891a951712dca5d58f65fab
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075344"
---
# <a name="dmschemaminingmodelcontentpmml-rowset"></a>Набор строк DMSCHEMA_MINING_MODEL_CONTENT_PMML
  Возвращает XML-структуру модели интеллектуального анализа данных. Формат XML-строки соответствует стандарту языка разметки прогнозирующих моделей (PMML 2.1).  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DMSCHEMA_MINING_MODEL_CONTENT_PMML` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||Имя каталога, заполненное именем базы данных, элементом которой является модель.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||Неполное имя схемы. Этот столбец не поддерживается службами [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит `NULL`.|  
|`MODEL_NAME`|`DBTYPE_WSTR`||Имя модели. Этот столбец не может содержать значение `NULL`.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`||Тип модели. Строка, зависящая от поставщика. Она может иметь значение `NULL`.|  
|`MODEL_GUID`|`DBTYPE_GUID`||Идентификатор GUID, определяющий модель. Поставщики, не использующие идентификаторы GUID для определения таблиц, возвращают значение `NULL`.|  
|`MODEL_PMML`|`DBTYPE_WSTR`||XML-представление содержимого модели в формате PMML.|  
|`SIZE`|`DBTYPE_UI4`||Число байтов в XML-строке.|  
|`LOCATION`|`DBTYPE_WSTR`||Расположение XML-файла. Представляет собой значение `NULL`, если сведения о расположении недоступны.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DMSCHEMA_MINING_MODEL_CONTENT_PMML` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MODEL_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`|Необязательный параметр.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы интеллектуального анализа данных](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
