---
title: "Тип данных MDDataSet (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MDDataSet Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#MDDataSet
- MDDataSet
- urn:schemas-microsoft-com:xml-analysis#MDDataSet
helpviewer_keywords: MDDataSet data type
ms.assetid: 1a7e0092-f9f0-4ae5-ba27-ad1d8ebe8cb9
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5fe67716b8c818e5a5784ea6599b1a045e7f8a44
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="mddataset-data-type-xmla"></a>Тип данных MDDataSet (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Определяет производный тип данных, представляющий многомерные данные, возвращаемые [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) метод.  
  
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
|Базовые типы данных|[Результирующий набор](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Оси](../../../analysis-services/xmla/xml-elements-properties/axes-element-xmla.md), [CellData](../../../analysis-services/xmla/xml-elements-properties/celldata-element-xmla.md), [OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md)|  
|Производные элементы|Нет|  
  
## <a name="remarks"></a>Замечания  
 Тип данных **MDDataSet** позволяет получить набор строк (или набор данных), предназначенный для использования в среде OLAP, который требуется для представления данных OLAP на языке XML. Содержимое этого набора строк может изменяться в зависимости от значения **содержимого** и **формат** свойства в [свойства](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md) коллекцию  **Выполнение** метод. Дополнительные сведения о **содержимого** и **формат** см [поддерживаемые свойства XMLA &#40; XML для Аналитики &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
 Для получения основных сведений о структурах наборов данных OLE DB для OLAP см. раздел «Сопоставление типов данных MDDataSet для OLE DB» в спецификации «XML для аналитики 1.1». Полный образец определения типа данных **MDDataSet** на языке XSD приведен в документе «Приложение Г. пример типа данных MDDataSet» в спецификации «XML для аналитики 1.1».  
  
## <a name="see-also"></a>См. также:  
 [Типы данных XML &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
