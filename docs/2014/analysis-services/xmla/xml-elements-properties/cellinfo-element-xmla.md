---
title: Элемент CellInfo (XML для Аналитики) | Документы Microsoft
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
- CellInfo Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cellinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#CellInfo
- urn:schemas-microsoft-com:xml-analysis#CellInfo
helpviewer_keywords:
- CellInfo element
ms.assetid: 8b6420f1-e9a7-4975-b580-1439fa11f5ca
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 803640fe83ccc3137b4597b8c1b78850abeb55c1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36110228"
---
# <a name="cellinfo-element-xmla"></a>Элемент CellInfo (XML для аналитики)
  Представляет метаданные ячейки, содержащиеся в родительском [OlapInfo](olapinfo-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<OlapInfo>  
   ...  
   <CellInfo>  
      <!-- One or more cell property definitions -->  
   </CellInfo>  
   ...  
</OlapInfo>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[OlapInfo](olapinfo-element-xmla.md)|  
|Дочерние элементы|Одно или несколько определений свойств ячейки|  
  
## <a name="remarks"></a>Примечания  
 Элемент `CellInfo` содержит коллекцию свойств ячеек, которые используются для ячеек, включенных в многомерный набор данных, возвращаемый элементом `root`, использующим тип данных `MDDataSet`. Каждое свойство ячейки в элементе `CellInfo` определяется отдельным XML-элементом, обладающим атрибутами `name` и `type`. Атрибут `name` свойства ячейки соответствует имени свойства ячейки OLE DB для OLAP, представленной XML-элементом. Атрибут `type` представляет тип данных XML свойства ячейки. Имя XML-элемента используется для идентификации значения свойства ячейки у ячеек, которые содержатся в элементе `CellData` элемента `root`.  
  
 Следующий синтаксис описывает определение свойства ячейки:  
  
```  
<CellPropertyDefinition name="string" type"string" />  
```  
  
 Доступные свойства и их значения могут быть получены с помощью с типом запроса DISCOVER_PROPERTIES `Discover` метод. Для перечисления свойств в элементе `PropertyList` не требуется определенного порядка.  
  
 По желанию поставщик может указать значения по умолчанию для отдельных элементов или для свойств ячеек в разделе `AxisInfo` или `CellInfo`. Значения по умолчанию могут быть малополезны в случае, если свойство всегда или почти всегда имеет одно и то же значение. Чтобы указать значение по умолчанию для свойства`Default` элемента может быть указана как дочерний элемент одного из элементов определения свойства ячейки. В том случае, если в результате отсутствует элемент или свойство ячейки, вместо него будет использовано значение по умолчанию, заданное для этого свойства ячейки.  
  
## <a name="example"></a>Пример  
 В следующем примере показывается, как свойства ячеек VALUE, FORMATTED_VALUE и FORMAT_STRING представлены в элементе `CellInfo`.  
  
```  
<OlapInfo>  
   ...  
      <CellInfo>  
         <Value name="VALUE"></Value>  
         <FmtValue name="FORMATTED_VALUE"></FmtValue>  
         <FormatString name="FORMAT_STRING"></FormatString>  
      </CellInfo>  
</OlapInfo>  
```  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  