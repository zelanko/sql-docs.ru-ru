---
title: "Объекты ASSL и характеристики объектов | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- reference exceptions [Analysis Services Scripting Language]
- ASSL, objects
- inheritance [Analysis Services Scripting Language]
- localized names [Analysis Services Scripting Language]
- objects [Analysis Services Scripting Language]
- names [Analysis Services Scripting Language]
- Analysis Services Scripting Language, objects
- expansion [Analysis Services Scripting Language]
ms.assetid: 6e5c28b5-c0bc-4ccd-82e5-e174bbb71386
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 54c1e299952f042587389631e3220eb241ea598e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="assl-objects-and-object-characteristics"></a>Объекты ASSL и характеристики объектов
  В языке ASSL объекты следуют специальным рекомендациям в отношении групп объектов, наследования, именования, расширения и обработки.  
  
## <a name="object-groups"></a>Группы объектов  
 Все [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] объекты имеют XML-представление. Объекты разделены на две группы.  
  
 **Основные объекты.**  
 Основные объекты можно создавать, изменять и удалять независимо. К основным объектам относятся следующие:  
  
-   Серверы  
  
-   Базы данных  
  
-   Измерения  
  
-   Кубы  
  
-   Группы мер  
  
-   Секции  
  
-   Перспективы  
  
-   Модели интеллектуального анализа данных  
  
-   Роли  
  
-   Команды, связанные с сервером или базой данных  
  
-   Источники данных  
  
 Для отслеживания истории и состояния у основных объектов предусмотрены следующие свойства:  
  
-   **CreatedTimestamp**  
  
-   **LastSchemaUpdate**  
  
-   **LastProcessed** (при необходимости)  
  
> [!NOTE]  
>  Отнесение объекта к основным влияет на то, как этот объект рассматривается в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], а также на то, как он обрабатывается в языке определения объектов. Однако такая классификация не гарантирует, что средства управления и разработки служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] разрешат независимое создание, изменение или удаление этих объектов.  
  
 **Второстепенные объекты**  
 Создавать, изменять или удалять второстепенные объекты можно только в рамках создания, изменения или удаления родительского основного объекта. К второстепенным объектам относятся следующие:  
  
-   Иерархии и уровни  
  
-   Атрибуты  
  
-   Меры  
  
-   Столбцы модели интеллектуального анализа данных  
  
-   Команды, связанные с кубом  
  
-   Aggregations  
  
## <a name="object-expansion"></a>Раскрытие объектов  
 **ObjectExpansion** ограниченного использования программ можно использовать для управления степенью раскрытия XML языка ASSL, возвращаемого сервером. Параметры этого ограничения приведены в следующей таблице.  
  
|Значение перечисления|Разрешено для \<Alter >|Description|  
|-----------------------|---------------------------|-----------------|  
|*ReferenceOnly*|нет|Возвращает только имя, идентификатор и отметку времени для запрошенного объекта, а также рекурсивно для всех содержащихся в нем основных объектов.|  
|*ObjectProperties*|да|Раскрывает запрошенные объект и содержащиеся в нем второстепенные объекты, но не возвращает содержащиеся в нем основные объекты.|  
|*ExpandObject*|нет|Аналогичен параметру *ObjectProperties*, но также возвращает имя, идентификатор и отметку времени для вложенных основных объектов.|  
|*ExpandFull*|да|Полностью раскрывает запрошенный объект и, рекурсивно, все содержащиеся в нем объекты.|  
  
 В этом разделе справки ASSL описывается *ExpandFull* представление. Все остальные **ObjectExpansion** уровни являются производными от этого уровня.  
  
## <a name="object-processing"></a>Обработка объектов  
 ASSL есть элементы, доступные только для чтения и свойства (например, **LastProcessed**), которые можно считывать из [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр, но которые пропускаются при подаче на экземпляр командных скриптов. Службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] не учитывают измененные значения для элементов, которые доступны только для чтения, не выдавая при этом предупреждений или сообщений об ошибке.  
  
 Службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] также пропускают несоответствующие свойства, не формируя при этом ошибок проверки правильности. Например, допустим, что элемент Х должен присутствовать, только если элемент Y имеет определенное значение. Экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] не учитывает элемент X вместо проверки правильности этого элемента по значению элемента Y.  
  
  

