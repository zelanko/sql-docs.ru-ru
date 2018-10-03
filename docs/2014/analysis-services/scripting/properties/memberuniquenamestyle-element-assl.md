---
title: Элемент MemberUniqueNameStyle (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MemberUniqueNameStyle Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- MemberUniqueNameStyle element
ms.assetid: f0771c81-0127-4203-9501-ae4f864730fa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 204f29e7bfb90894fded974b78cfd136aa39eaeb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133464"
---
# <a name="memberuniquenamestyle-element-assl"></a>Элемент MemberUniqueNameStyle (ASSL)
  Определяет, как уникальные имена создаются для элементов иерархий, содержащихся в [CubeDimension](../data-type/dimension-data-type-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubeDimension>  
   ...  
   <MemberUniqueNameStyle>...</MemberUniqueNameStyle>  
   ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*собственный*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[CubeDimension](../data-type/dimension-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*собственный*|Экземпляр автоматически определяет уникальные имена элементов.|  
|*NamePath*|Экземпляр формирует составное имя, содержащее каждый уровень и заголовок элемента.|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра `MemberUniqueNameStyle` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>См. также  
 [Элемент куба &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Элемент измерения &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [Тип данных CubeDimension &#40;ASSL&#41;](../data-type/dimension-data-type-assl.md)  
  
  
