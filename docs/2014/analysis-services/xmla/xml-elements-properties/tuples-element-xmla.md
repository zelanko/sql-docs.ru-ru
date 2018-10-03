---
title: Элемент Tuples (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Tuples Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Tuples
- microsoft.xml.analysis.tuples
- urn:schemas-microsoft-com:xml-analysis#Tuples
helpviewer_keywords:
- Tuples element
ms.assetid: 5494bbaa-c1aa-43fa-b3e0-83befb2bccdd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 36f29edb149ab6a5c7c22dfe87c4d630289f29cd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128024"
---
# <a name="tuples-element-xmla"></a>Элемент Tuples (XML для аналитики)
  Содержит набор [кортежа](tuple-element-xmla.md) объектов для [оси](axis-element-xmla.md) элемент, использующий [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) тип данных, возвращенных [Execute](../xml-elements-methods-execute.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Axis>  
   ...  
   <Tuples>  
      <Tuple>...</Tuple>  
   </Tuples>  
   ...  
</Axis>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Axis](axis-element-xmla.md)|  
|Дочерние элементы|[кортеж](tuple-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Когда клиентское приложение устанавливает `AxisFormat` свойства *TupleFormat*, ось представляется в виде набора кортежей. Каждый элемент `Axis` содержит элемент `Tuples`, представляющий набор кортежей на этой оси. Каждый кортеж представлен с помощью `Tuple` элемент, содержащий [член](member-element-xmla.md) элементы из каждой иерархии на оси.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует структуру `Tuples` элемент, если клиент указывает *TupleFormat* или *CustomFormat* для `AxisFormat` XML для аналитики (XMLA), на оси имеются следующие члены:  
  
|||||  
|-|-|-|-|  
|Иерархия `Time`|1999|1999|2000|  
|Иерархия `Category`|Actual|Budget|Budget|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <Tuples>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
      </Tuples>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
