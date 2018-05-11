---
title: Тип данных ResultSet (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 68843bb4e08e1383b6df88a0f8f776a8ebab77a3
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="resultset-data-type-xmla"></a>Тип данных Resultset (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет абстрактный примитивный тип данных, представляющий данные, возвращенные из [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) или [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) вызова метода.  
  
 **Пространство имен** urn:schemas-microsoft-com:xml-analysis:resultset  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Resultset>  
   <Exception>...</Exception>  
   <Messages>...</Messages>  
</Resultset>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md), [olapxmla_EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md), [набора строк](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Исключение](../../../analysis-services/xmla/xml-elements-properties/exception-element-xmla.md), [сообщения](../../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)|  
|Производные элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Тип данных **Resultset** представляет собой описывающий сам себя результирующий набор XML, который может включать и схему, и данные, в зависимости от типа возвращаемых данных.  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
