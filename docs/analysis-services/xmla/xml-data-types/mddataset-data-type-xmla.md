---
title: Тип данных MDDataSet (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bd82c473b768d8359c82bd2cf55c1cf27e76ae3f
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="mddataset-data-type-xmla"></a>Тип данных MDDataSet (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет производный тип данных, представляющий многомерные данные, возвращаемые [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) метод.  
  
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
|Производные элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Тип данных **MDDataSet** позволяет получить набор строк (или набор данных), предназначенный для использования в среде OLAP, который требуется для представления данных OLAP на языке XML. Содержимое этого набора строк может изменяться в зависимости от значения **содержимого** и **формат** свойства в [свойства](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md) коллекцию  **Выполнение** метод. Дополнительные сведения о **содержимого** и **формат** свойствах см. [поддерживаемые свойства XMLA &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
 Для получения основных сведений о структурах наборов данных OLE DB для OLAP см. раздел «Сопоставление типов данных MDDataSet для OLE DB» в спецификации «XML для аналитики 1.1». Полный образец определения типа данных **MDDataSet** на языке XSD приведен в документе «Приложение Г. пример типа данных MDDataSet» в спецификации «XML для аналитики 1.1».  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
