---
title: Элемент MemberUniqueNameStyle (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- MemberUniqueNameStyle Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MemberUniqueNameStyle element
ms.assetid: f0771c81-0127-4203-9501-ae4f864730fa
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9e23cd5d4581f5199f5a4d4bc9488ceb9a6c8863
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="memberuniquenamestyle-element-assl"></a>Элемент MemberUniqueNameStyle (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет уникальных имен для элементов иерархий, содержащихся в создаются [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md) элемента.  
  
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
|Значение по умолчанию|*Собственный*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Собственный*|Экземпляр автоматически определяет уникальные имена элементов.|  
|*NamePath*|Экземпляр формирует составное имя, содержащее каждый уровень и заголовок элемента.|  
  
## <a name="remarks"></a>Замечания  
 Элемент, соответствующий родителю параметра **MemberUniqueNameStyle** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>См. также  
 [Элемент CUBE & #40; ASSL & #41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Элемент измерения & #40; ASSL & #41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [Тип данных CubeDimension & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)  
  
  
