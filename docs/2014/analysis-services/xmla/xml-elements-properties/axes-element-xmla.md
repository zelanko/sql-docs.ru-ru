---
title: Осей элемент (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Axes Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Axes
- http://schemas.microsoft.com/analysisservices/2003/engine#Axes
- microsoft.xml.analysis.axes
- urn:schemas-microsoft-com:xml-analysis#Axes
helpviewer_keywords:
- Axes element
ms.assetid: 2005d06a-f8a2-4b4f-8c0d-2f7f73eb6f5c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bdb5aa48dd3a65f99b424274fdb89b3aee8c9591
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48094914"
---
# <a name="axes-element-xmla"></a>Элемент Axes (XML для аналитики)
  Содержит коллекцию [оси](axis-element-xmla.md) элементов, представляющих данные оси, содержащиеся в [корневой](root-element-xmla.md) элемент, использующий [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) тип данных.  
  
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
|Родительские элементы|[Корневой](root-element-xmla.md)|  
|Дочерние элементы|[Axis](axis-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 В элементе `Axes` элементы `Axis` перечисляются в том порядке, в котором они появляются в наборе данных, начиная с нуля. Параметр свойства XMLA `AxisFormat` определяет, как должны быть отформатированы элементы `Axis`. Дополнительные сведения о `AxisFormat` свойство, см. в разделе [поддерживаемые свойства XMLA &#40;XMLA&#41;](propertylist-element-supported-xmla-properties.md).  
  
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
  
|Операция|Описание|  
|---------------|-----------------|  
|Член|Наименьшая единица измерения на оси, представляющая элемент в иерархии измерений.|  
|Члены|Коллекция объектов `Member` из одной и той же иерархии измерений.|  
|Кортеж|Коллекция элементов из разных иерархий измерений.|  
|Кортежи|Коллекция объектов `Tuple` с одной и той же размерностью.|  
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
  
 Свойство `AxisFormat` может использоваться клиентом для затребования конкретного представления.  
  
## <a name="see-also"></a>См. также  
 [Тип данных MDDataSet &#40;XML для Аналитики&#41;](../xml-data-types/mddataset-data-type-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
