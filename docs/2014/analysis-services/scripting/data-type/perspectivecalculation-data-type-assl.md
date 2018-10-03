---
title: Тип данных PerspectiveCalculation (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- PerspectiveCalculation Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PerspectiveCalculation
helpviewer_keywords:
- PerspectiveCalculation data type
ms.assetid: 5a5173d2-c96d-4a55-a35c-0cbfd5b0e599
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1b4f56077a784a26617946dd1179738f838b2db3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126094"
---
# <a name="perspectivecalculation-data-type-assl"></a>Тип данных PerspectiveCalculation (ASSL)
  Определяет тип-примитив, представляющий связь между вычислением и [перспективы](../objects/perspective-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<PerspectiveCalculation>  
      <Name>...</Name>  
   <Type>...</Type>  
   <Annotations>...</Annotations>  
</PerspectiveCalculation>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Заметки](../collections/annotations-element-assl.md), [имя](../properties/name-element-assl.md), [типа](../properties/type-element-perspectivecalculation-assl.md)|  
|Производные элементы|[Вычисление](../objects/calculation-element-assl.md) ([вычисления](../collections/calculations-element-assl.md) коллекцию [перспективы](../objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.PerspectiveCalculation>.  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
