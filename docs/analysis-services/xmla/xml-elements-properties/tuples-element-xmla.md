---
title: Элемент Tuples (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1b149356d30dc390c6779ef165c80c9b967f9044
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="tuples-element-xmla"></a>Элемент Tuples (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит набор [кортежа](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md) объектов для [оси](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md) элемент, который использует [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) тип данных, возвращенных [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) метод.  
  
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
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Оси](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
|Дочерние элементы|[Кортеж](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Когда клиентское приложение устанавливает для свойства **AxisFormat** значение *TupleFormat*, ось представляется в виде набора кортежей. Каждый элемент **Axis** содержит элемент **Tuples**, представляющий набор кортежей на этой оси. Каждый кортеж представлен с помощью элемента **Tuple**, содержащего элементы [Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md) из каждой иерархии оси.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует структуру **кортежей** элемент, если клиент указывает *TupleFormat* или *CustomFormat* для **AxisFormat**  XML для аналитики (XMLA), на оси имеются следующие члены:  
  
|||||  
|-|-|-|-|  
|Иерархия **Time**|1999|1999|2000|  
|Иерархия **Category**|Actual|Budget|Budget|  
  
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
  
## <a name="see-also"></a>См. также:  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
