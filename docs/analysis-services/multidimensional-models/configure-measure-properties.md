---
title: "Настройка свойств мер | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "аддитивность [службы Analysis Services]"
  - "ID, свойство"
  - "ErrorConfiguration, свойство"
  - "AggregateFunction, свойство"
  - "DisplayFolder, свойство"
  - "IgnoreUnrelatedDimensions, свойство"
  - "FormatString, свойство"
  - "Description, свойство"
  - "полуаддитивные"
  - "свойства [службы Analysis Services], группы мер"
  - "агрегатные функции [службы Analysis Services]"
  - "DataType, свойство"
  - "ProcessingMode, свойство"
  - "MeasureExpression, свойство"
  - "AggregationPrefix, свойство"
  - "Visible, свойство"
  - "свойства [службы Analysis Services], меры"
  - "StorageLocation, свойство"
  - "StorageMode, свойство"
  - "форматы [службы Analysis Services], меры"
  - "Source, свойство"
  - "агрегаты [службы Analysis Services], меры"
  - "меры [службы Analysis Services], свойства"
  - "неаддитивные [службы Analysis Services]"
  - "Name, свойство"
  - "меры [службы Analysis Services], форматы отображения"
  - "ProcessingPriority, свойство"
  - "группы мер [службы Analysis Services], свойства"
  - "Type, свойство"
  - "ProactiveCaching, свойство"
ms.assetid: e9031078-c4f5-4986-b0c9-4d064b622ab7
caps.latest.revision: 50
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 50
---
# Настройка свойств мер
  Меры имеют свойства, позволяющие определять и управлять их работой и отображением для пользователей.  
  
 Свойства в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] можно задать при создании или изменении куба или меры. Можно также задать их программным способом с помощью многомерных выражений или объектов AMO. Дополнительные сведения см. в разделах [Создание мер и групп мер в многомерных моделях](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md), [Инструкция CREATE MEMBER (многомерные выражения)](../Topic/CREATE%20MEMBER%20Statement%20\(MDX\).md) и [Программирование основных объектов AMO OLAP](../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-olap-basic-objects.md).  
  
## Свойства мер  
 Меры наследуют определенные свойства у группы мер, элементами которых они являются, если только эти свойства не переопределены на уровне мер. Свойства мер определяют статистическое вычисление, тип данных, отображаемые для пользователей имена, папку отображения, строку форматирования, выражения меры, базовые исходные столбцы и видимость для пользователей.  
  
|Свойство|Определение|  
|--------------|----------------|  
|**AggregateFunction**|Обязательный. Определяет, как выполняется статистическое вычисление мер. **Sum** — это агрегирование по умолчанию. Описание каждой функции см. в разделе [Use Aggregate Functions](../../analysis-services/multidimensional-models/use-aggregate-functions.md) .|  
|**DataType**|Обязательный. Указывает тип данных столбца базовой таблицы фактов, к которым привязана мера. Это значение наследуется из исходного столбца по умолчанию.|  
|**Description**|Содержит описание меры, которое может быть видно в клиентских приложениях.|  
|**DisplayFolder**|Указывает папку отображения, в которой будет представлена мера при подключении пользователя к кубу. Если куб содержит множество мер, папки отображения позволяют разбить их по категориям мер, упростив доступ к ним.|  
|**FormatString**|Можно выбрать формат, используемый для отображения значений меры пользователям, используя свойство **FormatString** меры.<br /><br /> Список форматов отображения представлен в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], но можно указать множество дополнительных форматов, не содержащихся в этом списке. Можно указать любой именованный или определенный пользователем формат, допустимый в языке Microsoft Visual Basic.|  
|**Идентификатор**|Обязательный. Отображает уникальный идентификатор (ID) меры. Это свойство предназначено только для чтения.|  
|**MeasureExpression**|Указывает ограниченное многомерное выражение, определяющее значение меры. Выражение вычисляется на конечном уровне до агрегирования и позволяет получить взвешенное значение. Например, конвертация валют, где объем продаж взвешен с учетом обменного курса.|  
|**Название**|Обязательный. Имя меры.|  
|**Source**|Обязательный. Столбец в представлении источника данных, к которому привязана мера. См. раздел [Источники данных и привязки (многомерные службы SSAS)](../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).|  
|**Visible**|Определяет видимость меры в клиентских приложениях.|  
  
## См. также  
 [Настройка свойств группы мер](../../analysis-services/multidimensional-models/configure-measure-group-properties.md)   
 [Изменение мер](../../analysis-services/modifying-measures.md)  
  
  