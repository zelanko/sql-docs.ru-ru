---
title: Настройка свойств мер | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- additivity [Analysis Services]
- ID property
- ErrorConfiguration property
- AggregateFunction property
- DisplayFolder property
- IgnoreUnrelatedDimensions property
- FormatString property
- Description property
- semiadditive
- properties [Analysis Services], measure groups
- aggregate functions [Analysis Services]
- DataType property
- ProcessingMode property
- MeasureExpression property
- AggregationPrefix property
- Visible property
- properties [Analysis Services], measures
- StorageLocation property
- StorageMode property
- formats [Analysis Services], measures
- Source property
- aggregations [Analysis Services], measures
- measures [Analysis Services], properties
- nonadditive [Analysis Services]
- Name property
- measures [Analysis Services], display formats
- ProcessingPriority property
- measure groups [Analysis Services], properties
- Type property
- ProactiveCaching property
ms.assetid: e9031078-c4f5-4986-b0c9-4d064b622ab7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9303e3d2ddfa53560b900b92bc75763d44c7f87e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48177724"
---
# <a name="configure-measure-properties"></a>Настройка свойств мер
  Меры имеют свойства, позволяющие определять и управлять их работой и отображением для пользователей.  
  
 Свойства в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] можно задать при создании или изменении куба или меры. Можно также задать их программным способом с помощью многомерных выражений или объектов AMO. Дополнительные сведения см. в разделах [Создание мер и групп мер в многомерных моделях](create-measures-and-measure-groups-in-multidimensional-models.md), [Инструкция CREATE MEMBER (многомерные выражения)](/sql/mdx/mdx-data-definition-create-member) и [Программирование основных объектов AMO OLAP](analysis-management-objects/programming-amo-olap-basic-objects.md).  
  
## <a name="measure-properties"></a>Свойства мер  
 Меры наследуют определенные свойства у группы мер, элементами которых они являются, если только эти свойства не переопределены на уровне мер. Свойства мер определяют статистическое вычисление, тип данных, отображаемые для пользователей имена, папку отображения, строку форматирования, выражения меры, базовые исходные столбцы и видимость для пользователей.  
  
|Свойство|Определение|  
|--------------|----------------|  
|`AggregateFunction`|Обязательный. Определяет, как выполняется статистическое вычисление мер. `Sum` — Это агрегирование по умолчанию. Описание каждой функции см. в разделе [Use Aggregate Functions](use-aggregate-functions.md) .|  
|`DataType`|Обязательный. Указывает тип данных столбца базовой таблицы фактов, к которым привязана мера. Это значение наследуется из исходного столбца по умолчанию.|  
|`Description`|Содержит описание меры, которое может быть видно в клиентских приложениях.|  
|`DisplayFolder`|Указывает папку отображения, в которой будет представлена мера при подключении пользователя к кубу. Если куб содержит множество мер, папки отображения позволяют разбить их по категориям мер, упростив доступ к ним.|  
|`FormatString`|Можно выбрать формат, который используется для отображения значений меры пользователям с помощью `FormatString` свойства меры.<br /><br /> Список форматов отображения представлен в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], но можно указать множество дополнительных форматов, не содержащихся в этом списке. Можно указать любой именованный или определенный пользователем формат, допустимый в языке Microsoft Visual Basic.|  
|`ID`|Обязательный. Отображает уникальный идентификатор (ID) меры. Это свойство доступно только для чтения.|  
|`MeasureExpression`|Указывает ограниченное многомерное выражение, определяющее значение меры. Выражение вычисляется на конечном уровне до агрегирования и позволяет получить взвешенное значение. Например, конвертация валют, где объем продаж взвешен с учетом обменного курса.|  
|`Name`|Обязательный. Имя меры.|  
|`Source`|Обязательный. Столбец в представлении источника данных, к которому привязана мера. См. раздел [Источники данных и привязки (многомерные службы SSAS)](data-sources-and-bindings-ssas-multidimensional.md).|  
|`Visible`|Определяет видимость меры в клиентских приложениях.|  
  
## <a name="see-also"></a>См. также  
 [Настройка свойств группы мер](configure-measure-group-properties.md)   
 [Изменение мер](../lesson-3-1-modifying-measures.md)  
  
  
