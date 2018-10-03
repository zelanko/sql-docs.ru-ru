---
title: Элемент MiningModelPermission (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MiningModelPermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningModelPermission
helpviewer_keywords:
- MiningModelPermission element
ms.assetid: 4bd2f7e7-ff0d-404e-96fb-7e2c4eeb91e9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c6bad2b1bda46fcc1437a5f4c967ced8a6c726f0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48113474"
---
# <a name="miningmodelpermission-element-assl"></a>Элемент MiningModelPermission (ASSL)
  Определяет разрешения членов [роли](role-element-assl.md) имеют для отдельного [MiningModel](miningmodel-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningModelPermissions>  
   <MiningModelPermission xsi:type="Permission">  
      <!-- The following elements extend Permission -->  
      <AllowDrillThrough>...</AllowDrillThrough>  
      <AllowBrowsing>...</AllowBrowsing>  
   </MiningModelPermission>  
</MiningModelPermissions>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[Разрешение](../data-type/permission-data-type-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[MiningModelPermissions](../collections/miningmodelpermissions-element-assl.md)|  
|Дочерние элементы|[AllowBrowsing](../properties/allowbrowsing-element-assl.md), [AllowDrillThrough](../properties/allowdrillthrough-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 В [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], вы можете включить детализацию в структурах интеллектуального анализа данных, добавив `AllowDrillthrough` разрешение на [MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md) коллекции. Если `AllowDrillthrough` включен в структуре интеллектуального анализа данных и модели интеллектуального анализа данных, любой член роли, обладающей [элемент AllowDrillThrough &#40;ASSL&#41; ](../properties/allowdrillthrough-element-assl.md) разрешения на модель выполнять запросы к модели интеллектуального анализа данных и возврата столбцы структуры, которые не были включены в модель, используя следующий синтаксис:  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 Поэтому, чтобы защитить конфиденциальные или персональные данные, разрешение `AllowDrillthrough` для модели интеллектуального анализа данных следует предоставлять только при необходимости. Дополнительные сведения см. в разделе [элемент AllowDrillThrough &#40;ASSL&#41;](../properties/allowdrillthrough-element-assl.md).  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.MiningModelPermission>.  
  
## <a name="see-also"></a>См. также  
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
