---
title: Тип данных PerspectiveMeasureGroup (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- PerspectiveMeasureGroup Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PerspectiveMeasureGroup
helpviewer_keywords:
- PerspectiveMeasureGroup data type
ms.assetid: 5927120d-f30e-4f87-8523-6d17012817d7
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bc1978c2ae733b07071c7c95d3fd232c207d2853
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191893"
---
# <a name="perspectivemeasuregroup-data-type-assl"></a>Тип данных PerspectiveMeasureGroup (ASSL)
  Определяет тип-примитив, представляющий сведения о группе мер в [перспективы](../objects/perspective-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<PerspectiveMeasureGroup>  
   <MeasureGroupID>...</MeasureGroupID>  
   <Measures>...</Measures>  
   <Annotations>...</Annotations>  
</PerspectiveMeasureGroup>  
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
|Дочерние элементы|[Заметки](../collections/annotations-element-assl.md), [MeasureGroupID](../properties/id-element-assl.md), [меры](../collections/measures-element-assl.md)|  
|Производные элементы|[Группа мер](../objects/group-element-assl.md) ([MeasureGroups](../collections/groups-element-assl.md) коллекцию [перспективы](../objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 Структура группы мер в перспективе совпадает со структурой группы мер в базовом кубе.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.PerspectiveMeasureGroup>.  
  
## <a name="see-also"></a>См. также  
 [Службы Analysis Services сценариев типы данных XML в &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  