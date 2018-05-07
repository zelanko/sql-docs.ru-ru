---
title: Набор строк DMSCHEMA_MINING_SERVICE_PARAMETERS | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: caaee84cfe87aba1e5c5f2c52a46264838a63411
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="dmschemaminingserviceparameters-rowset"></a>Набор строк DMSCHEMA_MINING_SERVICE_PARAMETERS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Описывает параметры для алгоритмов на сервере.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DMSCHEMA_MINING_SERVICE_PARAMETERS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Описание|  
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
  
  
