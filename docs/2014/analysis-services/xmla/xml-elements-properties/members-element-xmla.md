---
title: Элемент Members (XMLA) | Документы Microsoft
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
- Members Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Members
- urn:schemas-microsoft-com:xml-analysis#Members
- microsoft.xml.analysis.members
helpviewer_keywords:
- Members element
ms.assetid: 55f9ec3a-5a41-4b3a-acd6-c07598868c46
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 5d812d0eea48c4f2b54352f61a176462b280071a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188320"
---
# <a name="members-element-xmla"></a>Элемент Members (XML для аналитики)
  Содержит коллекцию [член](member-element-xmla.md) элементов, содержащихся в родительском [CrossProduct](crossproduct-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CrossProduct>  
   <Members Hierarchy="string">  
      <Member>...</Member>  
   </Members>  
   ...  
</CrossProduct>  
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
|Родительские элементы|[CrossProduct](crossproduct-element-xmla.md)|  
|Дочерние элементы|[Член](member-element-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|attribute|Описание|  
|---------------|-----------------|  
|Иерархия|Требуется `String` атрибута. Имя иерархии, которой принадлежат элементы, содержащиеся в элементе `Members`.|  
  
## <a name="remarks"></a>Примечания  
 Когда клиентское приложение задает `AxisFormat` свойства *ClusterFormat*, элементы на каждой оси разделяются на кластеры, в которых каждый кластер представляет перекрестное произведение упорядоченных множеств элементов из каждой иерархии. Каждый элемент `Axis` состоит из одного или нескольких элементов `CrossProduct`. Каждый элемент `CrossProduct` содержит элемент `Members` из каждой иерархии на оси. В элементе `Members`, в свою очередь, содержится по одному элементу `Member` для каждого элемента указанной иерархии, включенной в перекрестное произведение.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует структуру `Members` элемент, если клиент указывает *ClusterFormat* для `AxisFormat` свойства XMLA на оси имеются следующие члены:  
  
||||||  
|-|-|-|-|-|  
|Иерархия `Time`|1999|1999|2000|2001|  
|Иерархия `Category`|Actual|Budget|Budget|Budget|  
|Clusters|Кластер 1|Кластер 1|Кластер 1|Кластер 2|  
  
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
  
  