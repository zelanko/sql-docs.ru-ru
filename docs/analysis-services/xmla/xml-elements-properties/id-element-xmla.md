---
title: "Элемент ID (XMLA) | Документы Microsoft"
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
apiname: ID Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#ID
- urn:schemas-microsoft-com:xml-analysis#ID
- microsoft.xml.analysis.id
helpviewer_keywords: ID element
ms.assetid: f7d67599-6a70-4455-bfdb-1d127e5eff4e
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 17a86cd00a2c5cd254d9c9752b7decda0ee6b325
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="id-element-xmla"></a>Элемент ID (XML для аналитики)
  Определяет блокировку, на котором выполняется родительский [блокировки](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md) или [Unlock](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Lock> <!-- or Unlock>  
   ...  
   <ID>...</ID>  
   ...  
</Lock>  
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
|Родительские элементы|[Блокировка](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md), [разблокировки](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 **Идентификатор** элемент содержит глобальный уникальный идентификатор (GUID), используемый для идентификации блокировки.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Object &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)   
 [Элемент Mode &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
