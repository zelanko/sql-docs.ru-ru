---
title: "Элемент UnknownMember (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- UnknownMember Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- UnknownMember
helpviewer_keywords:
- UnknownMember element
ms.assetid: 5558961e-e3c6-4f4e-817d-5b12b0734c03
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5da9cdc237512a47a27b21691864b3da523ce70a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="unknownmember-element-assl"></a>Элемент UnknownMember (ASSL)
  Показывает, видим ли неизвестный элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Dimension>  
      ...  
   <UnknownMember>...</UnknownMember>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*None*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Отображается*|Неизвестный элемент существует и отображается.|  
|*Скрытые*|Неизвестный элемент существует, но не отображается.|  
|*None*|Неизвестный элемент не используется.|  
  
 Перечисление, соответствующее разрешенным значениям для **UnknownMember** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.UnknownMemberBehavior>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент UnknownMemberName &#40; ASSL &#41;](../../../analysis-services/scripting/properties/unknownmembername-element-assl.md)   
 [Элемент UnknownMemberTranslation &#40; ASSL &#41;](../../../analysis-services/scripting/objects/unknownmembertranslation-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

