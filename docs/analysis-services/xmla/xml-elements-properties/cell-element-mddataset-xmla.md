---
title: "Ячейки элемент (MDDataSet) (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Cell Element (MDDataSet)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.cell
- http://schemas.microsoft.com/analysisservices/2003/engine#Cell
- urn:schemas-microsoft-com:xml-analysis#Cell
helpviewer_keywords:
- Cell element
ms.assetid: c4ea08a4-f653-4ade-be07-b91eb5b1ef32
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b4d8e85ec05fa6fd8b3c05ee0f27f46b0a28a867
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="cell-element-mddataset-xmla"></a>Элемент Cell (MDDataSet) (XML для аналитики)
  Содержит сведения об одной ячейке, содержащейся в родительском [CellData](../../../analysis-services/xmla/xml-elements-properties/celldata-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CellData>  
   <Cell CellOrdinal="unsignedInt">  
      <!-- Zero or more cell property values -->  
      <!-- or -->  
      <Error>...</Error>  
   </Cell>  
</CellData>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CellData](../../../analysis-services/xmla/xml-elements-properties/celldata-element-xmla.md)|  
|Дочерние элементы|Ноль или более значений свойств ячейки или [ошибки](../../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|Attribute|Описание|  
|---------------|-----------------|  
|CellOrdinal|Требуется **unsignedInt** атрибута. Порядковый номер ячейки в многомерном наборе данных.|  
  
## <a name="remarks"></a>Замечания  
 В родительском объекте **корневой** элемент, **осей** следуют элемент **CellData** элемент, набор **ячейки** элементов, содержащих значения свойств для каждой ячейки, возвращенной в многомерном наборе данных. **Ячейки** элемент содержит **CellOrdinal** атрибут, который указывает отсчитываемый от нуля порядковый номер ячейки в многомерном наборе данных и один элемент для каждого значения свойства ячейки связанное с ячейкой. Каждое значение свойства ячейки в **ячейки** элемент определяется отдельным элементом XML. Значение свойства ячейки имеет данные, содержащиеся в XML-элемента и имя свойства ячейки, как определено в **CellInfo** элемент родительского корневого элемента, соответствует имени XML-элемента.  
  
 Ниже представлен синтаксис записи значения свойства ячейки.  
  
```  
<CellProperty xsi:type="string">value</CellProperty>  
```  
  
 Тип данных для значения свойства ячейки указывается только для свойства ячейки VALUE. Типы данных для других свойств ячейки, определяются определение свойства ячейки, включенные в **CellInfo** элемента. Элемент значения свойства ячейки можно исключить, если задано значение по умолчанию (путем включения **по умолчанию** элемент для определения свойства ячейки, содержащиеся в **CellInfo** элемент) для свойства ячейки или если был указан без значения по умолчанию, а значение свойства ячейки равно null.  
  
## <a name="cell-property-errors"></a>Ошибки свойств ячейки  
 Если свойство ячейки не может быть возвращен из-за ошибки, возникшей в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], такие как ошибки вычисления, которая предотвращает возврат для заданной ячейки, значение **ошибка** содержимое свойства рассматриваемой ячейки замещается элементом. В следующем примере кода XML описывается ошибка свойства ячейки.  
  
```  
<Cell CellOrdinal="0">  
   <Value xsi:type="xsd:double">  
      <Error>  
         <ErrorCode>2148497527</ErrorCode>  
         <Description>Unknown error</Description>  
      </Error>  
   </Value>  
</Cell>  
```  
  
## <a name="calculating-cell-ordinal-values"></a>Вычисление значения порядкового номера ячейки  
 Ссылка на ось для ячейки может быть вычислено на основе **CellOrdinal** значение атрибута. По существу, ячейки нумеруются в наборе данных, как будто набор данных *p*-мерный массив, где *p* — число осей. Адресация ячеек осуществляется по строкам.  
  
 Предположим, в запросе запрашивается четыре меры в столбцах и перекрестное соединение для двух штатов с четырьмя кварталами в строках. В следующем наборе данных, **CellOrdinal** свойство для части результирующего набора данных, отображаются полужирным шрифтом — это набор {9, 10, 11, 13, 14, 15, 17, 18, 19}. Это набор, потому что ячейки нумеруются в строках заказа, начиная с **CellOrdinal** 0 для верхней левой ячейки.  
  
|Состояние|Квартал|Продажи единиц товара|Стоимость хранения|Продажи магазинов|Количество продаж|  
|-----------|-------------|----------------|----------------|-----------------|-----------------|  
|California|К1|16890|14431.09|36175.2|5498|  
||К2|18052|15332.02|38396.75|5915|  
||К3|18370|**15672.83**|**39394.05**|**6014**|  
||К4|21436|**18094.5**|**45201.84**|**7015**|  
|Oregon|К1|19287|**16081.07**|**40170.29**|**6184**|  
||К2|15079|12678.96|31772.88|4799|  
||К3|16940|14273.78|35880.46|5432|  
||К4|16353|13738.68|34453.44|5196|  
|Washington|К1|30114|25240.08|63282.86|9906|  
||К2|29479|24953.25|62496.64|9654|  
||К3|30538|25958.26|64997.38|10007|  
||К4|34235|29172.72|73016.34|11217|  
  
 Применяя формулу, показанную на рисунке, получим, что ось при k = 0 содержит Uk = 4 элемента, а ось при k = 1 содержит Uk = 8 кортежей. P = 2 — число осей в запросе. Если принять ячейку {Калифорния, К3, Стоимость хранения} за S0, начальная сумма будет равна i = 0 до 1. При i = 0 порядковый номер кортежа на оси 0 для столбца {Стоимость хранения} равен 1. При i = 1 порядковый номер кортежа для {Калифорния, К3} равен 2.  
  
 Для я = 0 Ei = 1, поэтому при i = 0 сумма равна 1 * 1 = 1 и для я = 1, сумма равна 2 (порядковый номер кортежа) раз 4 (значение Ei вычисляется как 1 \* 4), или 8. Сумма 1 + 8 равна 9, это порядковый номер для этой ячейки.  
  
## <a name="example"></a>Пример  
 В следующем примере демонстрируется структура **ячейки** значения свойств для каждой ячейки, ячейки элемента, включая VALUE, FORMATTED_VALUE и FORMAT_STRING.  
  
```  
<CellData>  
   <Cell CellOrdinal="0">  
      <Value xsi:type="xsd:double">16890</Value>  
      <FmtValue>16,890.00</FmtValue>  
      <FormatString>Standard</FormatString>  
   </Cell>  
   <Cell CellOrdinal="1">  
      <Value xsi:type="xsd:int">50</Value>  
      <FmtValue>50</FmtValue>  
      <FormatString>Standard</FormatString>  
   </Cell>  
   <Cell CellOrdinal="2">  
      <Value xsi:type="xsd:double">36175.2</Value>  
      <FmtValue>$36,175.20</FmtValue>  
      <FormatString>Currency</FormatString>  
   </Cell>  
</CellData>  
```  
  
## <a name="see-also"></a>См. также:  
 [Тип данных MDDataSet &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

