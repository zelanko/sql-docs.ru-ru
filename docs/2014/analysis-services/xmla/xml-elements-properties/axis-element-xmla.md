---
title: Элемент Axis (XMLA) | Документация Майкрософт
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
- Axis Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.axis
- http://schemas.microsoft.com/analysisservices/2003/engine#Axis
helpviewer_keywords:
- Axis element
ms.assetid: 336895e1-4a57-4b43-9a53-e31569866e6c
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e3e68903dc828f4b14ac60892d1b6fc2baed2f30
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37263230"
---
# <a name="axis-element-xmla"></a>Элемент Axis (XML для аналитики)
  Содержит набор кортежей, используемых для представления единственной оси в многомерном наборе данных, содержащихся в [осей](axes-element-xmla.md) элемент, использующий [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) тип данных, возвращенных [Execute](../xml-elements-methods-execute.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Axes>  
   ...  
   <Axis> <!-- when AxisFormat XMLA property is set to ClusterFormat -->  
      <CrossProduct>...</CrossProduct>  
   </Axis>  
   <Axis> <!-- when AxisFormat XMLA property is set to TupleFormat or CustomFormat -->  
      <Tuples>...</Tuples>  
   </Axis>  
   ...  
</Axes>  
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
|Родительские элементы|[Оси](axes-element-xmla.md)|  
|Дочерние элементы|[CrossProduct](crossproduct-element-xmla.md) или [кортежей](tuples-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Содержимое элемента `Axis` изменяется в зависимости от значения свойства XMLA `AxisFormat`, используемого методом `Execute`.  
  
## <a name="tupleformat"></a>TupleFormat  
 Когда клиентское приложение устанавливает `AxisFormat` свойства *TupleFormat*, ось представляется в виде набора кортежей. Каждый элемент `Axis` содержит элемент `Tuples`, который представляет множество кортежей на этой оси. Каждый кортеж представляется с помощью элемента `Tuple`, который содержит элементы `Member` из каждой иерархии на оси.  
  
## <a name="clusterformat"></a>ClusterFormat  
 Когда клиентское приложение устанавливает `AxisFormat` свойства *ClusterFormat*, элементы на каждой оси разделяются на кластеры, в которых каждый кластер представляет перекрестное произведение упорядоченных множеств элементов из каждой иерархии. Каждый элемент `Axis` состоит из одного или нескольких элементов `CrossProduct`. Каждый элемент `CrossProduct` содержит элемент `Members` из каждой иерархии на оси.  
  
## <a name="customformat"></a>CustomFormat  
 Когда клиентское приложение устанавливает `AxisFormat` свойства *CustomFormat*, значение обрабатывается так же, как *TupleFormat* значение на экземпляре служб Analysis Services.  
  
## <a name="examples"></a>Примеры  
  
### <a name="description"></a>Описание  
 Следующий пример иллюстрирует структуру `Axis` элементов, если клиент указывает *TupleFormat* или *CustomFormat* для `AxisFormat` свойство XMLA, даны следующие члены для оси:  
  
|||||  
|-|-|-|-|  
|Иерархия `Time`|1999|1999|2000|  
|Иерархия `Category`|Actual|Budget|Budget|  
  
### <a name="code"></a>Код  
  
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
  
### <a name="description"></a>Описание  
 Следующий пример иллюстрирует структуру `Axis` элементов, если клиент указывает *ClusterFormat* для `AxisFormat` XMLA-свойства, на оси имеются следующие члены:  
  
||||||  
|-|-|-|-|-|  
|Иерархия `Time`|1999|1999|2000|2001|  
|Иерархия `Category`|Actual|Budget|Budget|Budget|  
|Clusters|Кластер 1|Кластер 1|Кластер 1|Кластер 2|  
  
### <a name="code"></a>Код  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <CrossProduct Size = "4">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
      <CrossProduct Size = "1">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[2001]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
