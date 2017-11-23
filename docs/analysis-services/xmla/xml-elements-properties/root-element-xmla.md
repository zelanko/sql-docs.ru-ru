---
title: "корневой элемент (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
apiname: Root Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#root
- urn:schemas-microsoft-com:xml-analysis#root
- microsoft.xml.analysis.root
helpviewer_keywords: root element
ms.assetid: ecd9d6e8-b16c-4d62-9a87-107c413a0056
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 71a112a9cbf086175eb7c11e628fb423add2f62d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="root-element-xmla"></a>Элемент root (XML для аналитики)
  Содержит результат, возвращаемый методом [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метода или команду XML для аналитики (XMLA) выполняется с помощью [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<return> <!-- or results-->  
   ...  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">...</root> <!-- for Execute method only -->  
   <!-- or -->  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">...</root>  
   <!-- or -->  
   <root xmlns= xmlns="urn:schemas-microsoft-com:xml-analysis:empty">...</root>  
   ...  
</return>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|См. в следующей таблице.|  
|Значение по умолчанию|None|  
|Количество элементов|1-N: обязательный элемент, который может встречаться несколько раз.|  
  
|Предок|Тип данных|  
|--------------|---------------|  
|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)|[Набор строк](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md), [olapxmla_EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|  
|[ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md), [строк](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md), [olapxmla_EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[результаты](../../../analysis-services/xmla/xml-elements-properties/results-element-xmla.md), [возврата](../../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 **Корневой** элемент содержит данные, возвращаемые в любом [DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md) элемент, возвращаемый один **Discover** вызова метода, или в [ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md) элемент, возвращаемый в отдельной команде XMLA, выполненной при единственном **Execute** вызова метода.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
