---
title: Элемент AllowDrillThrough (ASSL) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0e4897c2e0fdc7ade56a6067b8e24dbaa1bf7d2f
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="allowdrillthrough-element-assl"></a>Элемент AllowDrillThrough (язык ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
## <a name="remarks"></a>Примечания  
 Элементы, соответствующие родителям элемента **AllowDrillThrough** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningModelPermission>, и <xref:Microsoft.AnalysisServices.MiningStructurePermission>.  
  
## <a name="drillthrough-on-mining-structures"></a>Детализация структур интеллектуального анализа данных  
 В [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], можно определить **AllowDrillthrough** разрешения для структуры интеллектуального анализа данных, а также моделей интеллектуального анализа данных. При назначении роли этого разрешения любой член этой роли может выполнять запросы к модели интеллектуального анализа данных и возвращать столбцы структуры, которые не были включены в модель. Например, вы создали модель, которая использует только следующие столбцы: ключ клиента, доход клиента и покупки клиента. Если включить детализацию модели, пользователи могут возвратить информацию из других столбцов структуры интеллектуального анализа данных, таких как адреса электронной почты или имена клиентов.  
  
 Таким образом, чтобы защитить конфиденциальные данные, необходимо соблюдать осторожность при добавлении столбцов в структуру интеллектуального анализа данных. Кроме того, предоставлять структуре разрешение **AllowDrillthrough** нужно только при необходимости.  
  
 Чтобы выполнить детализацию столбцов структуры, можно использовать запросы в одной из следующих форм.  
  
 `SELECT * FROM <structure>.CASES`  
  
 либо  
  
 `SELECT StructureColumn('<structure-column-name>') FROM <model>.CASES`  
  
## <a name="see-also"></a>См. также  
 [Элемент Role & #40; ASSL & #41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
