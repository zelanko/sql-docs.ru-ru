---
title: Набор строк DMSCHEMA_MINING_SERVICE_PARAMETERS | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DMSCHEMA_MINING_SERVICE_PARAMETERS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_SERVICE_PARAMETERS rowset
ms.assetid: 5994e66b-84d0-4279-9f50-d92fd829dd83
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 85ee3a7833a0c2bffc95ae21b44295d234ee8d5e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48047962"
---
# <a name="dmschemaminingserviceparameters-rowset"></a>Набор строк DMSCHEMA_MINING_SERVICE_PARAMETERS
  Описывает параметры для алгоритмов на сервере.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DMSCHEMA_MINING_SERVICE_PARAMETERS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`||Имя алгоритма.|  
|`PARAMETER_NAME`|`DBTYPE_WSTR`||Имя параметра.|  
|`PARAMETER_TYPE`|`DBTYPE_WSTR`||Тип параметра.|  
|`IS_REQUIRED`|`DBTYPE_BOOL`||Логическое значение, которое возвращает `TRUE`, если параметр является обязательным.|  
|`PARAMETER_FLAGS`|`DBTYPE_UI4`||Битовая маска, которая описывает характеристики параметра:<br /><br /> -   `DM_PARAMETER_TRAINING` (`0x0000001`) указывает параметр используется для обучения<br />-   `DM_PARAMETER_PREDICTION` (`0x00000002`) указывает, что параметр используется для прогнозирования<br />-   `DM_PARAMETER_CONTENT` (`0x00000003`) указывает, что параметр используется для ограничения содержимого|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Понятное описание параметра.|  
|`DEFAULT_VALUE`|`DBTYPE_WSTR`||Значение параметра по умолчанию. Возвращает значение `NULL`, если значением по умолчанию не является простой тип данных.|  
|`VALUE_ENUMERATION`|`DBTYPE_WSTR`||Перечислитель возможных значений для параметра.|  
|`HELP_FILE`|`DBTYPE_WSTR`||Имя файла, который содержит документацию к этому параметру.|  
|`HELP_CONTEXT`|`DBTYPE_I4`||Идентификатор контекста справки для этой функции.|  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DMSCHEMA_MINING_SERVICE_PARAMETERS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`PARAMETER_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы интеллектуального анализа данных](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
