---
title: Элемент NamingTemplate (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/17/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- NamingTemplate Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- NamingTemplate
helpviewer_keywords:
- NamingTemplate element
ms.assetid: d68d765c-f012-40c1-acd4-32741ee2eadf
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6a3fb4f2adec6480205fdbe4d704a47e63a7aef4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="namingtemplate-element-assl"></a>Элемент NamingTemplate (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет, как именуются уровни в иерархии родители потомки, построенным на основе [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md) родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute>  
   ...  
      <NamingTemplate>...</NamingTemplate>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значение **NamingTemplate** элемент используется только родительскими атрибутами (другими словами, значение [использование](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) элемент **DimensionAttribute** родительского элемента имеет значение *родительского*).  
  
 Если для создания иерархии используется родительский атрибут, уровни иерархии определяются связями «родители-потомки» между элементами, содержащимися в родительском атрибуте. Поэтому, в отличие от других измерений, имена уровней нельзя получать из имен атрибутов, используемых для иерархии.  
  
 Вместо этого для создания имен уровней иерархий «родители-потомки» используется шаблон имен. Элемент **NamingTemplate** , определенный в родительском атрибуте, содержит строковое выражение, используемое для определения имен уровней. Есть два способа определить шаблон имен для родительского атрибута. Можно либо разработать шаблон имен, либо указать список имен.  
  
 Шаблон имен содержит звездочку (`*`) в качестве заполнителя символов для счетчика, значение которого увеличивается и вставляется в имя каждого нового, более глубокого уровня. Например, при использовании шаблона `Level *` создаются имена уровней `Level 01`, `Level 02`, `Level 03`и т. д., если не определен уровень (Все). Если шаблон имен не содержит заполнителя символов, сначала он используется в указанном виде, а затем имена следующих уровней формируются добавлением пробела и номера в конец шаблона. Например, при использовании шаблона `Level` создаются имена уровней `Level`, `Level 01`, `Level 02`и т. д.  
  
 Чтобы использовать специальный набор имен, в качестве значения элемента **NamingTemplate** задается список имен уровней, разделенных точкой с запятой. Каждое имя в списке используется в качестве имени следующего уровня. Если число уровней превышает число имен в списке, то для всех последующих имен уровней в качестве шаблона используется последнее имя в списке, к которому добавляется пробел и порядковый номер, как описано выше. Например, при использовании шаблона `Division;Group;Unit` создаются имена уровней `Division`, `Group`, `Unit`, `Unit 01`, `Unit 02`и т. д. В отличие от этого при использовании шаблона `Division;Group;Unit *` создаются имена уровней `Division`, `Group`, `Unit 03`, `Unit 04`и т. д.  
  
 Каждое имя в списке считается шаблоном, чтобы гарантировать уникальность имен уровней. Например, при использовании шаблона `Manager;Team Lead;Manager;Team Lead;Worker *` создаются имена уровней `Manager`, `Team Lead`, `Manager 01`, `Team Lead 01`, `Worker 05`, `Worker 06`.  
  
 Используйте две звездочки (*), чтобы включить звездочку (\*) символ в имени уровня как часть шаблона именования.  
  
 Элемент, соответствующий родителю параметра **NamingTemplate** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Элемент NamingTemplateTranslations &#40;ASSL&#41;](../../../analysis-services/scripting/collections/namingtemplatetranslations-element-assl.md)   
 [Тип данных DimensionAttribute &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
