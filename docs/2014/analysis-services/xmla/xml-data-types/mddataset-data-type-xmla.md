---
title: Тип данных MDDataSet (XML для Аналитики) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDDataSet Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#MDDataSet
- MDDataSet
- urn:schemas-microsoft-com:xml-analysis#MDDataSet
helpviewer_keywords:
- MDDataSet data type
ms.assetid: 1a7e0092-f9f0-4ae5-ba27-ad1d8ebe8cb9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6d9208c800800032a2e79d58239132c5152b51b5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124204"
---
# <a name="mddataset-data-type-xmla"></a>Тип данных MDDataSet (XML для аналитики)
  Определяет производный тип данных, представляющий многомерные данные, возвращаемые [Execute](../xml-elements-methods-execute.md) метод.  
  
 **Пространство имен** urn:schemas-microsoft-com:xml-analysis:mddataset  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <!-- The following elements extend Resultset -->  
   <!-- Optional schema elements -->  
   <OlapInfo>...</OlapInfo>  
   <Axes>...</Axes>  
   <CellData>...</CellData>  
</root>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Результирующий набор](resultset-data-type-xmla.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Оси](../xml-elements-properties/axes-element-xmla.md), [CellData](../xml-elements-properties/celldata-element-xmla.md), [OlapInfo](../xml-elements-properties/olapinfo-element-xmla.md)|  
|Производные элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Тип данных `MDDataSet` позволяет получить набор строк (или набор данных), предназначенный для использования в среде OLAP, который требуется для представления данных OLAP на языке XML. Содержимое этого набора строк может изменяться в зависимости от значения `Content` и `Format` свойства в [свойства](../xml-elements-properties/properties-element-xmla.md) коллекцию `Execute` метод. Дополнительные сведения о `Content` и `Format` свойства, см. в разделе [поддерживаемые свойства XMLA &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
 Для получения основных сведений о структурах наборов данных OLE DB для OLAP см. раздел «Сопоставление типов данных MDDataSet для OLE DB» в спецификации «XML для аналитики 1.1». Полный XML-схемы определения языка XSD образец `MDDataSet` тип данных, см. «Приложение D: MDDataSet пример» XML для аналитики 1.1.  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML &#40;XML для Аналитики&#41;](xml-data-types-xmla.md)  
  
  
