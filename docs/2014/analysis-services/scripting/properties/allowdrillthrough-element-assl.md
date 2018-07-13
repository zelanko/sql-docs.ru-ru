---
title: Элемент AllowDrillThrough (язык ASSL) | Документация Майкрософт
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
- AllowDrillThrough Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AllowDrillThrough
helpviewer_keywords:
- AllowDrillThrough element
ms.assetid: 53c9e4a3-a376-447d-a13f-80d845cc9789
caps.latest.revision: 51
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f98b16569c3a7f4ab136be291d7bfd45698b5b11
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37178871"
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
|Тип данных и длина|Логическое значение|  
|Значение по умолчанию|`False`|  
|Количество элементов|0—1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Элемент MiningModel](../objects/miningmodel-element-assl.md), [MiningModelPermission](../objects/miningmodelpermission-element-assl.md), [MiningStructurePermission](../objects/miningstructurepermission-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элементы, соответствующие родителям элемента `AllowDrillThrough` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningModelPermission> и <xref:Microsoft.AnalysisServices.MiningStructurePermission>.  
  
## <a name="drillthrough-on-mining-structures"></a>Детализация структур интеллектуального анализа данных  
 В [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], можно определить `AllowDrillthrough` разрешения для структуры интеллектуального анализа данных, а также моделей интеллектуального анализа данных. При назначении роли этого разрешения любой член этой роли может выполнять запросы к модели интеллектуального анализа данных и возвращать столбцы структуры, которые не были включены в модель. Например, вы создали модель, которая использует только следующие столбцы: ключ клиента, доход клиента и покупки клиента. Если включить детализацию модели, пользователи могут возвратить информацию из других столбцов структуры интеллектуального анализа данных, таких как адреса электронной почты или имена клиентов.  
  
 Таким образом, чтобы защитить конфиденциальные данные, необходимо соблюдать осторожность при добавлении столбцов в структуру интеллектуального анализа данных. Кроме того, предоставлять структуре разрешение `AllowDrillthrough` нужно только при необходимости.  
  
 Чтобы выполнить детализацию столбцов структуры, можно использовать запросы в одной из следующих форм.  
  
 `SELECT * FROM <structure>.CASES`  
  
 или диспетчер конфигурации служб  
  
 `SELECT StructureColumn('<structure-column-name>') FROM <model>.CASES`  
  
## <a name="see-also"></a>См. также  
 [Элемент Role &#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
