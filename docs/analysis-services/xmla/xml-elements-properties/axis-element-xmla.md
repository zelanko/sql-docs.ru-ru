---
title: Элемент Axis (XML для Аналитики) | Документы Microsoft
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
- Axis Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.axis
- http://schemas.microsoft.com/analysisservices/2003/engine#Axis
helpviewer_keywords:
- Axis element
ms.assetid: 336895e1-4a57-4b43-9a53-e31569866e6c
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d04a9d7def676122ea3ae64aa5e170b36b4ae5aa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="axis-element-xmla"></a>Элемент Axis (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит набор кортежей, используемых для представления единственной оси в многомерном наборе данных, содержащихся в [осей](../../../analysis-services/xmla/xml-elements-properties/axes-element-xmla.md) элемент, который использует [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) тип данных, возвращенных [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) метод.  
  
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
|Родительские элементы|[Оси](../../../analysis-services/xmla/xml-elements-properties/axes-element-xmla.md)|  
|Дочерние элементы|[CrossProduct](../../../analysis-services/xmla/xml-elements-properties/crossproduct-element-xmla.md) или [кортежей](../../../analysis-services/xmla/xml-elements-properties/tuples-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 Содержимое **оси** элемент изменяется в зависимости от значения **AxisFormat** XMLA-свойства, используемые **Execute** метод.  
  
## <a name="tupleformat"></a>TupleFormat  
 Когда клиентское приложение устанавливает для свойства **AxisFormat** значение *TupleFormat*, ось представляется в виде набора кортежей. Каждый **оси** элемент содержит **кортежей** элемент, представляющий набор кортежей на этой оси. Каждый кортеж представлен с помощью элемента **Tuple**, содержащего элементы **Member** из каждой иерархии оси.  
  
## <a name="clusterformat"></a>ClusterFormat  
 Когда клиентское приложение задает **AxisFormat** свойства *ClusterFormat*, элементы на каждой оси разделяются на кластеры, в которых каждый кластер представляет перекрестное произведение упорядоченных наборов элементов из каждой иерархии. Каждый **оси** элемент состоит из одного или нескольких **CrossProduct** элементов. Каждый **CrossProduct** элемент содержит **члены** элемента каждой иерархии на оси.  
  
## <a name="customformat"></a>CustomFormat  
 Когда клиентское приложение задает **AxisFormat** свойства *CustomFormat*, значение интерпретируется таким же, как *TupleFormat* значение на экземпляре служб Analysis Services.  
  
## <a name="examples"></a>Примеры  
  
### <a name="description"></a>Описание  
 Следующий пример иллюстрирует структуру **оси** элементы, если клиент указывает *TupleFormat* или *CustomFormat* для **AxisFormat**  Свойства XMLA на оси имеются следующие члены:  
  
|||||  
|-|-|-|-|  
|Иерархия **Time**|1999|1999|2000|  
|Иерархия **Category**|Actual|Budget|Budget|  
  
### <a name="code"></a>код  
  
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
 Следующий пример иллюстрирует структуру **оси** элементы, если клиент указывает *ClusterFormat* для **AxisFormat** свойства XMLA, даны следующие члены для оси:  
  
||||||  
|-|-|-|-|-|  
|Иерархия **Time**|1999|1999|2000|2001|  
|Иерархия **Category**|Actual|Budget|Budget|Budget|  
|Clusters|Кластер 1|Кластер 1|Кластер 1|Кластер 2|  
  
### <a name="code"></a>код  
  
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
  
## <a name="see-also"></a>См. также:  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
