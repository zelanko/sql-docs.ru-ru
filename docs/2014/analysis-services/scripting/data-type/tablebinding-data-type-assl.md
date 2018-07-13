---
title: Тип данных TableBinding (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- TableBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TableBinding
helpviewer_keywords:
- TableBinding data type
ms.assetid: 3195dca4-82bf-46b7-a31f-5383586e3573
caps.latest.revision: 39
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 475044a0bcad3c90ffaffa71eeeb6735a37f96c7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220254"
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
|Базовые типы данных|[TabularBinding](binding-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[DataSourceID](../properties/id-element-assl.md), [DbSchemaName](../properties/name-element-assl.md), [DbTableName](../properties/dbtablename-element-assl.md)|  
|Производные элементы|См. в разделе [привязки](binding-data-type-assl.md)|  
  
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
  
 Расчетное выражение все еще применяется, даже если в выражении используются уточненные имена таблиц (например Sales.Qty). То же остается верным, если вместо этого таблица заменяется некоторым запросом «SELECT…». Приведенное выше предложение FROM принимает вид «FROM SELECT... As Sales».  
  
 Дополнительные сведения о `Binding` типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) типа `Binding` и иерархию наследования `Binding` типов, см. в разделе [типа привязки данных &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Обзор привязки данных в языке ASSL, см. в разделе [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.TableBinding>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных Binding &#40;ASSL&#41;](binding-data-type-assl.md)   
 [Источники данных и привязки &#40;многомерные службы SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
