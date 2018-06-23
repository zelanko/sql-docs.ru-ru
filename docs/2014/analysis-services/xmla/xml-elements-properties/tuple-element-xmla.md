---
title: Элемент Tuple (XML для Аналитики) | Документы Microsoft
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
- Tuple Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.tuple
- urn:schemas-microsoft-com:xml-analysis#Tuple
- http://schemas.microsoft.com/analysisservices/2003/engine#Tuple
helpviewer_keywords:
- Tuple element
ms.assetid: d65aba10-55e1-49c1-81bc-0756c39c0da2
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: fe470d60aa008723034e1bdbf95f3ecf593c8a3a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36110014"
---
# <a name="tuple-element-xmla"></a>Элемент Tuple (XML для аналитики)
  Содержит коллекцию элементов [Member](member-element-xmla.md), содержащихся в родительском элементе [Tuples](tuples-element-xmla.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Tuples>  
   <Tuple>  
      <Member>...</Member>  
   </Tuple>  
   ...  
</Tuples>  
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
|Родительские элементы|[Кортежи](tuples-element-xmla.md)|  
|Дочерние элементы|[Член](member-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Когда клиентское приложение задает `AxisFormat` свойства *TupleFormat*, ось представляется в виде набора кортежей. Каждый элемент `Axis` содержит элемент `Tuples`, представляющий набор кортежей на этой оси. Каждый кортеж представляется с помощью элемента `Tuple`, который содержит элементы `Member` из каждой иерархии на оси.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует структуру `Tuple` элемент, если клиент указывает *TupleFormat* или *CustomFormat* для `AxisFormat` свойства XMLA, даны следующие члены для оси:  
  
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
  
  