---
title: Тип данных CubeHierarchy (ASSL) | Документы Microsoft
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
- CubeHierarchy Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeHierarchy
helpviewer_keywords:
- CubeHierarchy data type
ms.assetid: cd633409-0c14-4dd9-97cc-3d30e25df24f
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 48176b4096b7fa7ba8e1847750410be0f65da552
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180137"
---
# <a name="cubehierarchy-data-type-assl"></a>Тип данных CubeHierarchy (язык ASSL)
  Определяет тип-примитив, представляющий сведения об [иерархии](../objects/hierarchy-element-assl.md) элемент в [куба](../objects/cube-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<CubeHierarchy>   <HierarchyID>...</HierarchyID>   <Name>...</Name>   <OptimizedState>...</OptimizedState>   <Visible>...</Visible>   <Enabled>...</Enabled>   <Annotations>...</Annotations></CubeHierarchy>  
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
|Дочерние элементы|[Заметки](../collections/annotations-element-assl.md), [включен](../properties/enabled-element-assl.md), [HierarchyID](../properties/id-element-assl.md), [имя](../properties/name-element-assl.md), [OptimizedState](../properties/state-element-assl.md), [видимыми](../properties/visible-element-assl.md)|  
|Производные элементы|[Иерархия](../objects/hierarchy-element-assl.md) ([иерархий](../collections/hierarchies-element-assl.md) коллекцию [CubeDimension](dimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 Этот тип данных не имеет ограничений и может использоваться в любом из режимов развертывания: 0 (многомерный и интеллектуальный анализ данных), 1 (SharePoint) и 2 (табличный).  
  
 В [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)], *включено* не может быть присвоено свойству `False` для *CubeHierarchy*.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.CubeHierarchy>.  
  
## <a name="see-also"></a>См. также  
 [Метод Discover &#40;XML для Аналитики&#41;](../../xmla/xml-elements-methods-discover.md)   
 [Службы Analysis Services сценариев типы данных XML в &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  