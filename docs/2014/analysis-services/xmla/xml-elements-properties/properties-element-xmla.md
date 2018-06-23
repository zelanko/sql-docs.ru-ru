---
title: Элемент Properties (XMLA) | Документы Microsoft
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
- Properties Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Properties
- microsoft.xml.analysis.properties
- urn:schemas-microsoft-com:xml-analysis#Properties
- Properties
helpviewer_keywords:
- Properties element
ms.assetid: 0b5468e5-bf23-4d22-862f-72e27a9fff2f
caps.latest.revision: 30
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 66accb9aab2c970c1fd09b1e14408b5585269d7f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095093"
---
# <a name="properties-element-xmla"></a>Элемент Properties (XML для аналитики)
  Содержит XML для аналитики (XMLA) свойства, используемые [Discover](../xml-elements-methods-discover.md) и [Execute](../xml-elements-methods-execute.md) методы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Discover> <!-- or Execute -->  
...  
   <Properties>  
      <PropertyList>...</PropertyList>  
   </Properties>  
...  
</Discover>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Обнаружение](../xml-elements-methods-discover.md), [выполнение](../xml-elements-methods-execute.md)|  
|Дочерние элементы|[PropertyList](propertylist-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Элемент `Properties` представляет свойства XMLA, используемые для управления работой методов `Discover` и `Execute`, например для определения сведений, необходимых для соединения с источником данных, указания формата результирующего набора или локали, в которой форматируются данные.  
  
 Доступные свойства и их значения могут быть получены с помощью с типом запроса DISCOVER_PROPERTIES `Discover` метод.  
  
## <a name="example"></a>Пример  
  
```  
<Properties>  
   <PropertyList>  
      <DataSourceInfo>  
         Provider=MSOLAP;Data Source=local;  
      </DataSourceInfo>  
      <Catalog>  
         Foodmart 2000  
      </Catalog>  
      <Format>  
         Multidimensional  
      </Format>  
   </PropertyList>  
</Properties>  
```  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  