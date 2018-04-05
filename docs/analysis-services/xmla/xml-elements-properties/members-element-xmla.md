---
title: Элемент Members (XMLA) | Документы Microsoft
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
- Members Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Members
- urn:schemas-microsoft-com:xml-analysis#Members
- microsoft.xml.analysis.members
helpviewer_keywords:
- Members element
ms.assetid: 55f9ec3a-5a41-4b3a-acd6-c07598868c46
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 478115a00c7e0f97fcad6e25fc74c1e205bb0a75
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="members-element-xmla"></a>Элемент Members (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Содержит коллекцию [член](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md) элементов, содержащихся в родительском [CrossProduct](../../../analysis-services/xmla/xml-elements-properties/crossproduct-element-xmla.md) элемента.  
  
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
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CrossProduct](../../../analysis-services/xmla/xml-elements-properties/crossproduct-element-xmla.md)|  
|Дочерние элементы|[Член](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|attribute|Description|  
|---------------|-----------------|  
|Иерархия|Обязательный атрибут типа **String** . Имя иерархии, к которому элементы, содержащиеся в **члены** принадлежит элемент.|  
  
## <a name="remarks"></a>Remarks  
 Когда клиентское приложение задает **AxisFormat** свойства *ClusterFormat*, элементы на каждой оси разделяются на кластеры, в которых каждый кластер представляет перекрестное произведение упорядоченных наборов элементов из каждой иерархии. Каждый **оси** элемент состоит из одного или нескольких **CrossProduct** элементов. Каждый **CrossProduct** элемент содержит **члены** элемента каждой иерархии на оси. **Элементы** , в свою очередь, содержит один **член** элемент для каждого элемента указанной иерархии, включенной в перекрестное произведение.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует структуру **элементы** элемент, если клиент указывает *ClusterFormat* для **AxisFormat** свойства XMLA, учитывая следующие элементы для оси:  
  
||||||  
|-|-|-|-|-|  
|Иерархия **Time**|1999|1999|2000|2001|  
|Иерархия **Category**|Actual|Budget|Budget|Budget|  
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
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
