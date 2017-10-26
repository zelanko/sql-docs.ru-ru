---
title: "Элемент AllowDrillThrough (ASSL) | Документы Microsoft"
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
- AllowDrillThrough Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AllowDrillThrough
helpviewer_keywords:
- AllowDrillThrough element
ms.assetid: 53c9e4a3-a376-447d-a13f-80d845cc9789
caps.latest.revision: 51
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5b0b2212ec86f1bb0c5a95fbf9f23768b36bb133
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="allowdrillthrough-element-assl"></a>Элемент AllowDrillThrough (язык ASSL)
  Определяет, разрешена ли детализация для родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningModel> <!-- or MiningModelPermission -->  
<!-- or MiningStructurePermission -->   ...  
   <AllowDrillThrough>...</AllowDrillThrough>  
   ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Boolean|  
|Значение по умолчанию|**False**|  
|Количество элементов|0—1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Элемент MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md), [MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md), [MiningStructurePermission](../../../analysis-services/scripting/objects/miningstructurepermission-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элементы, соответствующие родителям элемента **AllowDrillThrough** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningModelPermission>, и <xref:Microsoft.AnalysisServices.MiningStructurePermission>.  
  
## <a name="drillthrough-on-mining-structures"></a>Детализация структур интеллектуального анализа данных  
 В [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], можно определить **AllowDrillthrough** разрешения для структуры интеллектуального анализа данных, а также моделей интеллектуального анализа данных. При назначении роли этого разрешения любой член этой роли может выполнять запросы к модели интеллектуального анализа данных и возвращать столбцы структуры, которые не были включены в модель. Например, вы создали модель, которая использует только следующие столбцы: ключ клиента, доход клиента и покупки клиента. Если включить детализацию модели, пользователи могут возвратить информацию из других столбцов структуры интеллектуального анализа данных, таких как адреса электронной почты или имена клиентов.  
  
 Таким образом, чтобы защитить конфиденциальные данные, необходимо соблюдать осторожность при добавлении столбцов в структуру интеллектуального анализа данных. Кроме того, предоставлять структуре разрешение **AllowDrillthrough** нужно только при необходимости.  
  
 Чтобы выполнить детализацию столбцов структуры, можно использовать запросы в одной из следующих форм.  
  
 `SELECT * FROM <structure>.CASES`  
  
 либо  
  
 `SELECT StructureColumn('<structure-column-name>') FROM <model>.CASES`  
  
## <a name="see-also"></a>См. также:  
 [Элемент Role &#40; ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

