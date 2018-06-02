---
title: Элемент CellInfo (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3ada531d33baf7007d08ac8a719fca2bf8f1b2e4
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34574256"
---
# <a name="cellinfo-element-xmla"></a>Элемент CellInfo (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Представляет метаданные ячейки, содержащиеся в родительском [OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md) элемента.  
  
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
|Родительские элементы|[OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md)|  
|Дочерние элементы|Одно или несколько определений свойств ячейки|  
  
## <a name="remarks"></a>Примечания  
 **CellInfo** элемент содержит коллекцию свойств ячейки для ячеек, включенных в многомерный набор данных, возвращаемый **корневой** элемента с помощью **MDDataSet**тип данных. Каждое свойство ячейки в **CellInfo** отдельным элементом XML, каждый из которых определяется элемент **имя** атрибута и **тип** атрибута. **Имя** свойства ячейки соответствует атрибуту имя OLE DB для OLAP свойства ячейки, представленного элементом XML и **тип** атрибут представляет тип данных XML, ячейки свойство. Имя XML-элемента используется для идентификации значения свойства ячейки у ячеек, содержащихся в **CellData** элемент **корневой** элемента.  
  
 Следующий синтаксис описывает определение свойства ячейки:  
  
```  
<CellPropertyDefinition name="string" type"string" />  
```  
  
 Доступные свойства и их значения можно получить, используя метод **Discover** с типом запроса DISCOVER_PROPERTIES. Для перечисления свойств в элементе **PropertyList** не требуется определенного порядка.  
  
 Поставщик можно дополнительно указать значения по умолчанию для отдельных свойств элемента или ячейки в **AxisInfo** или **CellInfo** раздела. Значения по умолчанию могут быть малополезны в случае, если свойство всегда или почти всегда имеет одно и то же значение. Чтобы указать значение по умолчанию для свойства**по умолчанию** элемент может быть указана как дочерний элемент одного из элементов определения свойства ячейки. В том случае, если в результате отсутствует элемент или свойство ячейки, вместо него будет использовано значение по умолчанию, заданное для этого свойства ячейки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как свойства ячейки VALUE, FORMATTED_VALUE и FORMAT_STRING представлены в **CellInfo** элемента.  
  
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
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
