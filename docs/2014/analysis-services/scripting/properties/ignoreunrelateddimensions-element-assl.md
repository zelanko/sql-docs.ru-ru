---
title: Элемент IgnoreUnrelatedDimensions (ASSL) | Документация Майкрософт
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
- IgnoreUnrelatedDimensions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- IgnoreUnrelatedDimensions
helpviewer_keywords:
- IgnoreUnrelatedDimensions element
ms.assetid: c7d7a1cd-a8e0-4ae7-9464-a1d2a55a86ab
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c278a3109180dbd058bc7ed8212c7b05782ce3d5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37295466"
---
# <a name="ignoreunrelateddimensions-element-assl"></a>Элемент IgnoreUnrelatedDimensions (ASSL)
  Определяет, будут ли несвязанные измерения принудительно перемещаться на верхний уровень, если элементы измерений, не связанных с группой мер, включаются в запрос.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MeasureGroup>  
   ...  
   <IgnoreUnrelatedDimensions>...</IgnoreUnrelatedDimensions>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Логическое значение|  
|Значение по умолчанию|True|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Группа мер](../objects/group-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Если элемент `IgnoreUnrelatedDimensions` имеет значение `true`, несвязанные измерения принудительно переводятся на верхний уровень; если его значение равно `false`, измерения на верхний уровень принудительно не переводятся. Это свойство похоже на многомерных выражений (MDX) [ValidMeasure](/sql/mdx/validmeasure-mdx) функции.  
  
 Элемент, соответствующий родителю параметра `IgnoreUnrelatedDimensions` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.MeasureGroup>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
