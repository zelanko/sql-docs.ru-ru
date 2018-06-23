---
title: Тип данных UserDefinedGroupBinding (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- UserDefinedGroupBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- UserDefinedGroupBinding
helpviewer_keywords:
- UserDefinedGroupBinding data type
ms.assetid: 70149929-0ff7-4a67-84bf-e94908ae7611
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 8ebbc22ff9a9ff2d38e36b53d5e1e2e382739ca0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192111"
---
# <a name="userdefinedgroupbinding-data-type-assl"></a>Тип данных UserDefinedGroupBinding (ASSL)
  Определяет производный тип данных, представляющий определенное пользователем группирование для атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<UserDefinedGroupBinding>  
   <!-- The following elements extend Binding -->  
      <AttributeID>...</AttributeID>  
      <Groups>...</Groups>  
</UserDefinedGroupBinding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Привязки](binding-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[AttributeID](../properties/id-element-assl.md), [групп](../collections/groups-element-assl.md)|  
|Производные элементы|В разделе [привязки](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 `UserDefinedGroupBinding` автоматически рассматривается как [AttributeBinding](attributebinding-data-type-assl.md), чей [тип](../properties/type-element-binding-assl.md) задан равным *все*.  
  
 Дополнительные сведения о `Binding` типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) `Binding` тип и иерархию наследования `Binding` типов, в разделе [тип привязки данных &#40;ASSL &#41;](binding-data-type-assl.md).  
  
 Обзор привязок данных в ASSL см. в разделе [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.UserDefinedGroupBinding>.  
  
## <a name="see-also"></a>См. также  
 [Службы Analysis Services сценариев типы данных XML в &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  