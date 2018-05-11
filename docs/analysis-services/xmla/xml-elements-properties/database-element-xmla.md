---
title: Базы данных элемент (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3e9804c9c8f6b4a1fec3617ac5026a9b2e2ce527
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="database-element-xmla"></a>Элемент Database (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет базу данных, содержащей измерение, представленное родительским [объекта](../../../analysis-services/xmla/xml-elements-properties/object-element-dimension-xmla.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Object>  
   ...  
   <Database>...</Database>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Объект](../../../analysis-services/xmla/xml-elements-properties/object-element-dimension-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 **Базы данных** элемент представляет собой идентификатор объекта, который содержит имя базы данных служб Analysis Services, которая содержит измерение, представленное **объекта** элемент.  
  
## <a name="see-also"></a>См. также  
 [Элемент CUBE & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/cube-element-xmla.md)   
 [Элемент измерения & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/dimension-element-xmla.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
