---
title: "Базы данных элемент (XMLA) | Документы Microsoft"
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
apiname: Database Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.database
- http://schemas.microsoft.com/analysisservices/2003/engine#Database
- urn:schemas-microsoft-com:xml-analysis#Database
helpviewer_keywords: Database element
ms.assetid: 2ded06c4-4eaf-4ccb-a416-41ee51ced8bc
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: cb1d9091dfbeb521c84d1db19fca80b2629f8c63
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="database-element-xmla"></a>Элемент Database (XML для аналитики)
  Определяет базу данных, содержащей измерение, представленное родительским [объекта](../../../analysis-services/xmla/xml-elements-properties/object-element-dimension-xmla.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Object>  
   ...  
   <Database>...</Database>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Объект](../../../analysis-services/xmla/xml-elements-properties/object-element-dimension-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 **Базы данных** элемент представляет собой идентификатор объекта, который содержит имя базы данных служб Analysis Services, которая содержит измерение, представленное **объекта** элемент.  
  
## <a name="see-also"></a>См. также:  
 [Элемент CUBE &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/cube-element-xmla.md)   
 [Элемент измерения &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/dimension-element-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
