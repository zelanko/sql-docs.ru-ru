---
title: Элемент CrossProduct (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CrossProduct Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#CrossProduct
- microsoft.xml.analysis.crossproduct
- urn:schemas-microsoft-com:xml-analysis#CrossProduct
helpviewer_keywords:
- CrossProduct element
ms.assetid: a9a1584e-d2dd-45db-a918-d694c20d8189
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0612d741cc6aa04d2564f7100179d3d1881b9e5b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055225"
---
# <a name="crossproduct-element-xmla"></a>Элемент CrossProduct (XML для аналитики)
  Содержит перекрестное произведение упорядоченных множеств элементов из каждой иерархии для [оси](axis-element-xmla.md) элемент, использующий [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) тип данных, возвращенных [Execute](../xml-elements-methods-execute.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Axis>  
   ...  
   <CrossProduct Size="integer">  
      <Members>...</Members>  
   </CrossProduct>  
   ...  
</Axis>  
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
|Родительские элементы|[Axis](axis-element-xmla.md)|  
|Дочерние элементы|[Члены](members-element-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|attribute|Описание|  
|---------------|-----------------|  
|Размер|Требуется `Integer` атрибута. Определяет число кортежей, содержащихся в векторном произведении, представленном элементом `CrossProduct`.|  
  
## <a name="remarks"></a>Примечания  
 Когда клиентское приложение устанавливает `AxisFormat` свойства *ClusterFormat*, элементы на каждой оси разделяются на кластеры, в которых каждый кластер представляет перекрестное произведение упорядоченных множеств элементов из каждой иерархии. Каждый кластер представляется элементом `CrossProduct`. Каждый элемент `CrossProduct` содержит элемент `Members` из каждой иерархии на оси. Элемент `CrossProduct` может содержать элементы из одной иерархии.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует структуру `CrossProduct` элемент, если клиент указывает *ClusterFormat* для `AxisFormat` XMLA-свойства, на оси имеются следующие члены:  
  
||||||  
|-|-|-|-|-|  
|Иерархия `Time`|1999|1999|2000|2001|  
|Иерархия `Category`|Actual|Budget|Budget|Budget|  
|Clusters|Кластер 1|Кластер 1|Кластер 1|Кластер 2|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <CrossProduct Size="4">  
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
      <CrossProduct Size="1">  
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
  
  
