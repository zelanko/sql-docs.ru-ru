---
title: "Оси элемент (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Axes Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- Axes
- http://schemas.microsoft.com/analysisservices/2003/engine#Axes
- microsoft.xml.analysis.axes
- urn:schemas-microsoft-com:xml-analysis#Axes
helpviewer_keywords: Axes element
ms.assetid: 2005d06a-f8a2-4b4f-8c0d-2f7f73eb6f5c
caps.latest.revision: "21"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 949574c5719b09dceb8dd1fa6f252d097b014237
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="axes-element-xmla"></a>Элемент Axes (XML для аналитики)
  Содержит коллекцию [оси](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md) элементов, представляющих данные оси, содержащиеся в [корневой](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) элемент, который использует [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) тип данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">  
   ...  
   <Axes>  
      <Axis>...</Axis>  
   </Axes>  
   ...  
</root>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Любой|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[корень](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|Дочерние элементы|[Axis](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 В разделе **осей** элемент, **оси** элементы перечислены в порядке их появления в наборе данных, начиная с нуля. **AxisFormat** определяет параметр свойства XMLA как **оси** должны быть отформатированы элементы. Дополнительные сведения о **AxisFormat** свойство, в разделе [поддерживаемые свойства XMLA &#40; XML для Аналитики &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
 Ось представляет набор кортежей, в котором все кортежи набора имеют одну и ту же размерность. Набор может быть представлен с помощью разных способов, позволяющих достичь разных преимуществ. Например, следующий набор из четырех кортежей может быть представлен в виде коллекций двумерных кортежей или декартова произведения двух одномерных наборов.  
  
|1999|1999|2000|2000|  
|----------|----------|----------|----------|  
|Actual|Budget|Actual|Budget|  
  
 Этот набор кортежей может быть представлен также, как коллекция двумерных кортежей:  
  
```  
{ ( 1999, Actual ), ( 1999, Budget ), ( 2000, Actual ), ( 2000, Budget ) }  
```  
  
 Этот набор кортежей может быть представлен, как декартово произведение двух одномерных наборов:  
  
```  
{ 1999, 2000 } x { Actual, Budget }  
```  
  
 Первое представление, в котором используются двумерные кортежи, является более простым с точки зрения использования клиентских инструментов. А во втором представлении, основанном на декартовом произведении одномерных наборов, используется меньше пространства и сохраняется многомерный характер набора.  
  
 В следующей таблице перечислены операции, которые могут использоваться для определения и описания характеристик структуры и членов оси.  
  
|Операция|Description|  
|---------------|-----------------|  
|Член|Наименьшая единица измерения на оси, представляющая элемент в иерархии измерений.|  
|Члены|Коллекция **член** объекты из той же иерархии измерений.|  
|Кортеж|Коллекция элементов из разных иерархий измерений.|  
|Кортежи|Коллекция **кортежа** объектов одинаковой размерности.|  
|Union|Объединение наборов.|  
|CrossJoin|Декартово произведение наборов.|  
  
 В этих операциях производится преобразование двумерных кортежей и декартова произведения одномерных наборов следующим образом.  
  
## <a name="two-dimensional-tuples"></a>Двумерные кортежи  
  
```  
Tuples (  
   Tuple( Member(1999), Member(Actual) ),  
   Tuple( Member(1999), Member(Budget) ),  
   Tuple( Member(2000), Member(Actual) ),  
   Tuple( Member(2000), Member(Budget) )  
```  
  
## <a name="cartesian-product-of-one-dimensional-sets"></a>Декартово произведение одномерных наборов  
  
```  
CrossProduct (  
   Members( Member(1999), Member(2000) ),  
   Members( Member(Actual), Member(Budget) )  
```  
  
 Клиент может использовать **AxisFormat** свойство для затребования конкретного представления.  
  
## <a name="see-also"></a>См. также:  
 [Тип данных MDDataSet &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
