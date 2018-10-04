---
title: Тип данных CubeHierarchy (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ba39d031f8760a82232f4f276c46d04101cc6438
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48209653"
---
# <a name="cubehierarchy-data-type-assl"></a>Тип данных CubeHierarchy (язык ASSL)
  Определяет тип-примитив, представляющий сведения об [иерархии](../objects/hierarchy-element-assl.md) элемент в [куба](../objects/cube-element-assl.md) элемент.  
  
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
|Дочерние элементы|[Заметки](../collections/annotations-element-assl.md), [включена](../properties/enabled-element-assl.md), [HierarchyID](../properties/id-element-assl.md), [имя](../properties/name-element-assl.md), [OptimizedState](../properties/state-element-assl.md), [видимым](../properties/visible-element-assl.md)|  
|Производные элементы|[Иерархия](../objects/hierarchy-element-assl.md) ([иерархий](../collections/hierarchies-element-assl.md) коллекцию [CubeDimension](dimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 Этот тип данных не имеет ограничений и может использоваться в любом из режимов развертывания: 0 (многомерный и интеллектуальный анализ данных), 1 (SharePoint) и 2 (табличный).  
  
 В [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)], *включено* не может быть присвоено свойству `False` для *CubeHierarchy*.  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.CubeHierarchy>.  
  
## <a name="see-also"></a>См. также  
 [Метод Discover &#40;XML для Аналитики&#41;](../../xmla/xml-elements-methods-discover.md)   
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
