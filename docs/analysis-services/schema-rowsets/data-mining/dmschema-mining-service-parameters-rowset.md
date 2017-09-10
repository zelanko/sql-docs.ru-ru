---
title: "Набор строк DMSCHEMA_MINING_SERVICE_PARAMETERS | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DMSCHEMA_MINING_SERVICE_PARAMETERS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DMSCHEMA_MINING_SERVICE_PARAMETERS rowset
ms.assetid: 5994e66b-84d0-4279-9f50-d92fd829dd83
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e867952dac5e49b5f563ba7a9aed29eef3564d1a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="dmschemaminingserviceparameters-rowset"></a>Набор строк DMSCHEMA_MINING_SERVICE_PARAMETERS
  Описывает параметры для алгоритмов на сервере.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DMSCHEMA_MINING_SERVICE_PARAMETERS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Description|  
|-----------------|--------------------|-----------------|  
|**ПАРАМЕТРЫ SERVICE_NAME**|**DBTYPE_WSTR**|Имя алгоритма.|  
|**ИМЯ_ПАРАМЕТРА**|**DBTYPE_WSTR**|Имя параметра.|  
|**ТИП_ПАРАМЕТРА**|**DBTYPE_WSTR**|Тип параметра.|  
|**IS_REQUIRED**|**DBTYPE_BOOL**|Логическое значение, которое возвращает **TRUE** , если параметр является обязательным.|  
|**PARAMETER_FLAGS**|**DBTYPE_UI4**|Битовая маска, которая описывает характеристики параметра:<br /><br /> **DM_PARAMETER_TRAINING** (**0x0000001**) указывает, что параметр используется для обучения;<br /><br /> **DM_PARAMETER_PREDICTION** (**0x00000002**) указывает, что параметр используется для прогнозирования;<br /><br /> **DM_PARAMETER_CONTENT** (**0x00000003**) указывает, что параметр используется для ограничения содержимого.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Понятное описание параметра.|  
|**ЗНАЧЕНИЕ ПО УМОЛЧАНИЮ**|**DBTYPE_WSTR**|Значение параметра по умолчанию. Возвращает значение **NULL** , если значением по умолчанию не является простой тип данных.|  
|**VALUE_ENUMERATION**|**DBTYPE_WSTR**|Перечислитель возможных значений для параметра.|  
|**HELP_FILE**|**DBTYPE_WSTR**|Имя файла, который содержит документацию к этому параметру.|  
|**HELP_CONTEXT**|**DBTYPE_I4**|Идентификатор контекста справки для этой функции.|  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DMSCHEMA_MINING_SERVICE_PARAMETERS** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**ПАРАМЕТРЫ SERVICE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**ИМЯ_ПАРАМЕТРА**|**DBTYPE_WSTR**|Необязательно.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы интеллектуального анализа данных](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
