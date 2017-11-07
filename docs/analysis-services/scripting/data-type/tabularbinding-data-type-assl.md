---
title: "Тип данных TabularBinding (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- TabularBinding Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TabularBinding
helpviewer_keywords:
- TabularBinding data type
ms.assetid: 24587e34-20be-4693-81d8-038a6fc4e8ee
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 17e162327cef0a057d424dfca302316b9307ec92
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="tabularbinding-data-type-assl"></a>Тип данных TabularBinding (ASSL)
  Определяет абстрактный производный тип данных, представляющий привязку к табличному элементу, такому как таблица или измерение куба.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<TabularBinding>  
   <!-- The TabularBinding element has no child elements other than those inherited from Binding -->  
</TabularBinding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Привязки](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
|Производные типы данных|[DSVTableBinding](../../../analysis-services/scripting/data-type/dsvtablebinding-data-type-assl.md), [QueryBinding](../../../analysis-services/scripting/data-type/querybinding-data-type-assl.md), [TableBinding](../../../analysis-services/scripting/data-type/tablebinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|None|  
|Производные элементы|В разделе [привязки](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Дополнительные сведения о **привязки** типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) **привязки** тип и иерархию наследования  **Привязка** типов, в разделе [тип привязки данных &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Обзор привязок данных в ASSL см. в разделе [&#40; источники данных и привязки Многомерные службы SSAS &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.TabularBinding>.  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

