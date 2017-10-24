---
title: "Тип данных TableBinding (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- TableBinding Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TableBinding
helpviewer_keywords:
- TableBinding data type
ms.assetid: 3195dca4-82bf-46b7-a31f-5383586e3573
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 680587b7bd9154cf8f32ecbebe34e68c39e4c04a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="tablebinding-data-type-assl"></a>Тип данных TableBinding (ASSL)
  Определяет производный тип данных, представляющий привязку к таблице.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<TableBinding>  
   <!-- The following elements extend TabularBinding -->  
   <DataSourceID>...</DataSourceID>  
   <DbTableName>...</DbTableName>  
   <DbSchemaName>...</DbSchemaName>  
</TableBinding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[TabularBinding](../../../analysis-services/scripting/data-type/tabularbinding-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[DataSourceID](../../../analysis-services/scripting/properties/datasourceid-element-assl.md), [DbSchemaName](../../../analysis-services/scripting/properties/dbschemaname-element-assl.md), [DbTableName](../../../analysis-services/scripting/properties/dbtablename-element-assl.md)|  
|Производные элементы|В разделе [привязки](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Следует учитывать, что применение ссылок на другие таблицы в выражении фильтра, включенном в подзапрос выборки, может привести к снижению производительности доступа к некоторым источникам данных. Но конструктор может получить полный контроль над выражением SQL, определив именованный запрос в представлении источника данных, а затем ссылаясь на него.  
  
 Этот метод определения связываний для секции не зависит от того, как используются секционированные таблицы в представлении источника данных.  
  
 В качестве примера рассмотрим группу мер, в которой по умолчанию используется таблица Sales со столбцами Date, Product ID, Qty, Price и Amount (вычисляемыми в представлении источника данных). После этого в секции Sales97 можно использовать таблицу Sales97 с фильтром «Year(Sales.Date) = 97».  
  
 При этом запрос по существу имеет вид:  
  
```  
SELECT Date, Product ID, Qty, Price, Qty * Price AS Amount   
   FROM Sales97 As Sales  
   WHERE Year(Sales.Date) = 97  
```  
  
 Расчетное выражение все еще применяется, даже если в выражении используются уточненные имена таблиц (например Sales.Qty). То же самое происходит, если вместо таблицы были заменяется некоторым запросом «SELECT...» Предложение FROM выше стал бы «FROM SELECT... As Sales».  
  
 Дополнительные сведения о **привязки** типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) типа **привязки** и иерархию наследования **привязки** типов, в разделе [тип привязки данных &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Обзор привязок данных в ASSL см. в разделе [&#40; источники данных и привязки Многомерные службы SSAS &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.TableBinding>.  
  
## <a name="see-also"></a>См. также:  
 [Тип привязки данных &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)   
 [Источники данных и привязки &#40; Многомерные службы SSAS &#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

