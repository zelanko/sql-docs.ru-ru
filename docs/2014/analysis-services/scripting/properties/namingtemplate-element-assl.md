---
title: Элемент NamingTemplate (ASSL) | Документация Майкрософт
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
- NamingTemplate Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NamingTemplate
helpviewer_keywords:
- NamingTemplate element
ms.assetid: d68d765c-f012-40c1-acd4-32741ee2eadf
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8ba346be8664cf26992143c15789684c503fdf2a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37300844"
---
# <a name="namingtemplate-element-assl"></a>Элемент NamingTemplate (ASSL)
  Определяет, как именуются уровни в иерархии родители потомки, созданный из [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) родительского элемента.  
  
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
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значение `NamingTemplate` элемент используется только родительскими атрибутами (другими словами, значение [использования](usage-element-dimensionattribute-assl.md) элемент `DimensionAttribute` родительского элемента имеет значение *родительского*).  
  
 Если для создания иерархии используется родительский атрибут, уровни иерархии определяются связями «родители-потомки» между элементами, содержащимися в родительском атрибуте. Поэтому, в отличие от других измерений, имена уровней нельзя получать из имен атрибутов, используемых для иерархии.  
  
 Вместо этого для создания имен уровней иерархий «родители-потомки» используется шаблон имен. Элемент `NamingTemplate`, определенный в родительском атрибуте, содержит строковое выражение, используемое для определения имен уровней. Есть два способа определить шаблон имен для родительского атрибута. Можно либо разработать шаблон имен, либо указать список имен.  
  
 Шаблон имен содержит звездочку (`*`) в качестве заполнителя символов для счетчика, значение которого увеличивается и вставляется в имя каждого нового, более глубокого уровня. Например, при использовании шаблона `Level *` создаются имена уровней `Level 01`, `Level 02`, `Level 03`и т. д., если не определен уровень (Все). Если шаблон имен не содержит заполнителя символов, сначала он используется в указанном виде, а затем имена следующих уровней формируются добавлением пробела и номера в конец шаблона. Например, при использовании шаблона `Level` создаются имена уровней `Level`, `Level 01`, `Level 02`и т. д.  
  
 Чтобы использовать специальный набор имен, в качестве значения элемента `NamingTemplate` задается список имен уровней, разделенных точкой с запятой. Каждое имя в списке используется в качестве имени следующего уровня. Если число уровней превышает число имен в списке, то для всех последующих имен уровней в качестве шаблона используется последнее имя в списке, к которому добавляется пробел и порядковый номер, как описано выше. Например, при использовании шаблона `Division;Group;Unit` создаются имена уровней `Division`, `Group`, `Unit`, `Unit 01`, `Unit 02`и т. д. В отличие от этого при использовании шаблона `Division;Group;Unit *` создаются имена уровней `Division`, `Group`, `Unit 03`, `Unit 04`и т. д.  
  
 Каждое имя в списке считается шаблоном, чтобы гарантировать уникальность имен уровней. Например, при использовании шаблона `Manager;Team Lead;Manager;Team Lead;Worker *` создаются имена уровней `Manager`, `Team Lead`, `Manager 01`, `Team Lead 01`, `Worker 05`, `Worker 06`.  
  
 Используйте две звездочки (*), чтобы включить звездочку (\*) символ в имени уровня как часть шаблона именования.  
  
 Элемент, соответствующий родителю параметра `NamingTemplate` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Элемент NamingTemplateTranslations &#40;ASSL&#41;](../collections/translations-element-assl.md)   
 [Тип данных DimensionAttribute &#40;ASSL&#41;](../data-type/dimensionattribute-data-type-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
