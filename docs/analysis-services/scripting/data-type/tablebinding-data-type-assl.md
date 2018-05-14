---
title: Тип данных TableBinding (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 80055d443f0a08b7cc957d5fa26d458178d3a1f6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="tablebinding-data-type-assl"></a>Тип данных TableBinding (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Производные элементы|См. раздел [Binding](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Примечания  
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
  
 Дополнительные сведения о **привязки** типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) типа **привязки** и иерархию наследования **привязки** типов, в разделе [тип данных привязки &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Обзор привязок данных в ASSL см. в разделе [& #40; источники данных и привязки Многомерные службы SSAS & #41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.TableBinding>.  
  
## <a name="see-also"></a>См. также  
 [Тип привязки данных & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)   
 [Источники данных и привязки &#40;многомерные службы SSAS&#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Службы Analysis Services сценариев типы данных XML в & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
