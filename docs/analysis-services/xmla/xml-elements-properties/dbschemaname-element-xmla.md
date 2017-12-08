---
title: "Элемент DbSchemaName (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DbSchemaName Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DbSchemaName
- microsoft.xml.analysis.dbschemaname
- http://schemas.microsoft.com/analysisservices/2003/engine#DbSchemaName
helpviewer_keywords: DbSchemaName element
ms.assetid: 40ca10c9-7597-48fe-a9d9-ee2c7b84d4d1
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bfa0ae41571fcd04361801e13571f758afbc44cd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="dbschemaname-element-xmla"></a>Элемент DbSchemaName (XML для аналитики)
  Содержит имя схемы, используемой родительским элементом [TableNotification](../../../analysis-services/xmla/xml-elements-properties/tablenotification-element-xmla.md) в таблице, указанной элементом [DbTableName](../../../analysis-services/xmla/xml-elements-properties/dbtablename-element-xmla.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<TableNotification>  
   ...  
   <DbSchemaName>...</DbSchemaName>  
   ...  
</TableNotification>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[TableNotification](../../../analysis-services/xmla/xml-elements-properties/tablenotification-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
