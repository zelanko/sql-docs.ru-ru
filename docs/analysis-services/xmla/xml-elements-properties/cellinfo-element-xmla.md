---
title: Элемент CellInfo (XML для Аналитики) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- CellInfo Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.cellinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#CellInfo
- urn:schemas-microsoft-com:xml-analysis#CellInfo
helpviewer_keywords:
- CellInfo element
ms.assetid: 8b6420f1-e9a7-4975-b580-1439fa11f5ca
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2ea1b5a95a79e8142eb9ee2d2ccadcbc6ac03949
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
## <a name="remarks"></a>Замечания  
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
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
