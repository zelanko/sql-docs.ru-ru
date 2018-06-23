---
title: Введите элемент (Binding) (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Type Element (Binding)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: b5f5c485-dc83-4d66-a8d2-e96e96d068f9
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b07c1d781bfdade9228b6c5991b2eb56585cbe85
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096935"
---
# <a name="type-element-binding-assl"></a>Элемент Type (Binding) (ASSL)
  Содержит тип привязки атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AttributeBinding> <!-- or CubeAttributeBinding -->  
   ...  
   <Type>...</Type>  
   ...  
</AttributeBinding>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[AttributeBinding](../data-type/binding-data-type-assl.md), [CubeAttributeBinding](../data-type/cubeattributebinding-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*все*|уровень «Все»|  
|*Key*|Ключи элементов|  
|*Название*|Имя члена|  
|*Value*|Значение элемента|  
|*Перевод*|Переводы элементов|  
|*UnaryOperator*|Унарные операторы|  
|*SkippedLevels*|Пропущенные уровни|  
|*CustomRollup*|Формулы пользовательских сверток|  
|*CustomRollupProperties*|Свойства пользовательских сверток|  
  
 Элементы, соответствующие родителям элемента `Type` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.AttributeBinding> и <xref:Microsoft.AnalysisServices.CubeAttributeBinding>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных Binding &#40;ASSL&#41;](../data-type/binding-data-type-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  