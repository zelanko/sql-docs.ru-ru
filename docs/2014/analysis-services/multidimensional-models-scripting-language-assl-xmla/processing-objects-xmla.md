---
title: Обработка объектов (XMLA) | Документы Microsoft
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
helpviewer_keywords:
- errors [XML for Analysis]
- objects [XML for Analysis]
- XML for Analysis, objects
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
- writeback [Analysis Services], XML for Analysis
- out-of-line bindings
- processing objects [XML for Analysis]
- XMLA, objects
ms.assetid: a65b3249-303d-49c6-98af-6ac6eed11a03
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b4bb32d561a140746fb7b64dc9f9181f23306da9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193466"
---
# <a name="processing-objects-xmla"></a>Обработка объектов (XMLA)
  В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], обработка — это шаг или последовательность шагов, которые преобразуют данные в сведения для бизнес-анализа. Характеристики обработки меняются в зависимости от типа объекта, но обработка всегда является составной частью процесса преобразования данных в сведения.  
  
 Процессу [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] объекта, можно использовать [процесс](../xmla/xml-elements-commands/process-element-xmla.md) команды. Команда `Process` в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может обрабатывать следующие объекты:  
  
-   Кубы  
  
-   Базы данных  
  
-   Измерения  
  
-   Группы мер  
  
-   Модели интеллектуального анализа данных  
  
-   Структуры интеллектуального анализа данных  
  
-   Секции  
  
 Чтобы можно было управлять обработкой объектов, в команде `Process` предусмотрены различные свойства, которые можно задавать. Команда `Process` имеет свойства, которые определяют, какой объем обработки должен быть выполнен, какие объекты должны быть обработаны, будут ли использоваться внешние привязки, а также способ обработки ошибок и управления таблицами обратной записи.  
  
## <a name="specifying-processing-options"></a>Указание параметров обработки  
 [Тип](../xmla/xml-elements-properties/type-element-xmla.md) свойство `Process` команда задает режим обработки для использования при обработке объекта. Дополнительные сведения об обработке см. в разделе [Настройка параметров обработки (службы Analysis Services)](../multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
 В следующей таблице приведены константы для свойства `Type`, а также различные объекты, которые можно обрабатывать при помощи каждой константы.  
  
|Значение `Type`|Применимые объекты|  
|--------------------|------------------------|  
|*ProcessFull*|Куб, база данных, измерение, группа мер, модель интеллектуального анализа данных, структура интеллектуального анализа данных, секция|  
|*ProcessAdd*|Измерение, секция|  
|*ProcessUpdate*|Измерение|  
|*ProcessIndexes*|Измерение, куб, группа мер, секция|  
|*ProcessData*|Измерение, куб, группа мер, секция|  
|*ProcessDefault*|Куб, база данных, измерение, группа мер, модель интеллектуального анализа данных, структура интеллектуального анализа данных, секция|  
|*ProcessClear*|Куб, база данных, измерение, группа мер, модель интеллектуального анализа данных, структура интеллектуального анализа данных, секция|  
|*ProcessStructure*|Куб, структура интеллектуального анализа данных|  
|*ProcessClearStructureOnly*|Структура интеллектуального анализа данных|  
|*ProcessScriptCache*|Cube|  
  
 Дополнительные сведения об обработке [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] объектов, в разделе [многомерной модели обработки объекта](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
## <a name="specifying-objects-to-be-processed"></a>Указание объектов для обработки  
 [Объекта](../xmla/xml-elements-properties/object-element-xmla.md) свойство `Process` команда содержит идентификатор объекта для обработки. В команде `Process` можно указать только один объект, однако при его обработке обрабатываются также все дочерние объекты. Например, при обработке группы мер в кубе обрабатываются все секции для этой группы мер, а при обработке базы данных обрабатываются все объекты, включая кубы, измерения и структуры интеллектуального анализа данных, содержащиеся в базе данных.  
  
 Если атрибуту `ProcessAffectedObjects` команды `Process` задать значение TRUE, то все связанные объекты, вовлеченные в обработку указанного объекта, также будут обработаны. Например, если измерение выполняется добавочное обновление с помощью *ProcessUpdate* параметр в обработки `Process` команды также является любой секции, агрегаты которых становятся недействительными из-за членов, добавляемых или удаляемых обрабатываемые [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Если `ProcessAffectedObjects` задано значение true. В этом случае одна команда `Process` позволяет обрабатывать несколько объектов в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], но службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] определяют, какие объекты также должны обрабатываться, кроме одного объекта, указанного в команде `Process`.  
  
 Однако можно обрабатывать одновременно несколько объектов, например измерений, при помощи нескольких команд `Process` в составе команды `Batch`. Пакетные операции позволяют точнее управлять последовательной или параллельной обработкой объектов в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], чем при использовании атрибута `ProcessAffectedObjects`, а также позволяют подстраивать подход к обработке применительно к более крупным базам данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Дополнительные сведения о выполнении пакетных операций см. в разделе [выполнение пакетных операций &#40;XMLA&#41;](performing-batch-operations-xmla.md).  
  
## <a name="specifying-out-of-line-bindings"></a>Указание внешних привязок  
 Если `Process` команда не содержится в `Batch` команду, можно дополнительно указать out-привязок в [привязки](../xmla/xml-elements-properties/bindings-element-xmla.md), [DataSource](../xmla/xml-elements-properties/source-element-xmla.md), и [DataSourceView ](../xmla/xml-elements-properties/datasourceview-element-xmla.md) свойства `Process` для объектов для обработки. Внешние привязки — это ссылки на источники данных, представления источников данных и другие объекты, в которых привязка существует только во время выполнения команды `Process` и которые переопределяют любые существующие привязки, связанные с обрабатываемыми объектами. Если внешние привязки не указаны, используются привязки, связанные в данный момент с обрабатываемыми объектами.  
  
 Внешние привязки используются в следующих ситуациях.  
  
-   В случае постепенной обработки секции, в которой должна быть указана альтернативная таблица фактов или фильтр для существующей таблицы фактов с тем, чтобы строки не засчитывались дважды.  
  
-   Используя задачу потока данных в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для предоставления данных при обработке измерения, модели интеллектуального анализа данных или секции.  
  
 Внешние привязки описаны как часть языка сценариев служб Analysis Services (языка ASSL). Дополнительные сведения о привязках вне строки в языке ASSL см. в разделе [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
### <a name="incrementally-updating-partitions"></a>Добавочное обновление секций  
 Для добавочного обновления уже обработанной секции обычно требуется внешняя привязка, так как привязка, указанная для этой секции, ссылается на данные таблицы фактов, которые уже были статистически обработаны в рамках данной секции. При выполнении добавочного обновления уже обработанной секции с помощью команды `Process` службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] выполняют следующие действия.  
  
-   Создают временную секцию с такой же структурой, как у секции, добавочное обновление которой необходимо выполнить.  
  
-   Обрабатывают временную секцию при помощи внешней привязки, указанной в команде `Process`.  
  
-   Объединяют временную секцию с существующей выделенной секцией.  
  
 Дополнительные сведения о слиянии секций с помощью XML для аналитики (XMLA) см. в разделе [слияние секций &#40;XMLA&#41;](merging-partitions-xmla.md).  
  
## <a name="handling-processing-errors"></a>Обработка ошибок  
 [ErrorConfiguration](../xmla/xml-elements-properties/errorconfiguration-element-xmla.md) свойство `Process` команда позволяет задать способ обработки ошибок, возникших во время обработки объекта. Например, при обработке измерения службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] обнаруживают повторяющиеся значение в ключевом столбце ключевого атрибута. Поскольку ключи атрибутов должны быть уникальны, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] удаляют повторяющиеся записи. На основе [KeyDuplicate](../scripting/properties/keyduplicate-element-assl.md) свойство `ErrorConfiguration`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может:  
  
-   Пропустить ошибку и продолжить обработку измерения.  
  
-   Возвратить сообщение, указывающее, что службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] обнаружили повторяющийся ключ, и продолжить обработку.  
  
 Существует много схожих условий, для которых предусмотрены параметры свойства `ErrorConfiguration` при выполнении команды `Process`.  
  
## <a name="managing-writeback-tables"></a>Управление таблицами обратной записи  
 Если команда `Process` обнаруживает секцию, доступную для записи, куб или группу мер для такой секции, которые еще не полностью обработаны, для этой секции может еще не существовать таблица обратной записи. [WritebackTableCreation](../xmla/xml-elements-properties/writebacktablecreation-element-xmla.md) свойство `Process` команда определяет, является ли [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] должны создавать таблицу обратной записи.  
  
## <a name="examples"></a>Примеры  
  
### <a name="description"></a>Описание  
 В следующем примере производится полная обработка образца базы данных [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
### <a name="code"></a>Код  
  
```  
<Process xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
  </Object>  
  <Type>ProcessFull</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
### <a name="description"></a>Описание  
 Следующий пример осуществляет добавочную обработку **Internet_Sales_2004** секции в **продажи через Интернет** группе мер, **Adventure Works DW** куба в [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] пример [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных. `Process` Команда состоит в добавлении агрегаты для заказа даты позже 31 декабря 2006 г. в секции с помощью привязки запроса вне строки в `Bindings` свойство `Process` команду для извлечения строк таблицы фактов для создания агрегаты для добавления в секцию.  
  
### <a name="code"></a>Код  
  
```  
<Process ProcessAffectedObjects="true" xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2006</PartitionID>  
  </Object>  
  <Bindings>  
    <Binding>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2006</PartitionID>  
      <Source xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="QueryBinding">  
        <DataSourceID>Adventure Works DW</DataSourceID>  
        <QueryDefinition>  
          SELECT  
            [dbo].[FactInternetSales].[ProductKey],  
            [dbo].[FactInternetSales].[OrderDateKey],  
            [dbo].[FactInternetSales].[DueDateKey],  
            [dbo].[FactInternetSales].[ShipDateKey],   
            [dbo].[FactInternetSales].[CustomerKey],   
            [dbo].[FactInternetSales].[PromotionKey],  
            [dbo].[FactInternetSales].[CurrencyKey],  
            [dbo].[FactInternetSales].[SalesTerritoryKey],  
            [dbo].[FactInternetSales].[SalesOrderNumber],  
            [dbo].[FactInternetSales].[SalesOrderLineNumber],  
            [dbo].[FactInternetSales].[RevisionNumber],  
            [dbo].[FactInternetSales].[OrderQuantity],  
            [dbo].[FactInternetSales].[UnitPrice],  
            [dbo].[FactInternetSales].[ExtendedAmount],  
            [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
            [dbo].[FactInternetSales].[DiscountAmount],  
            [dbo].[FactInternetSales].[ProductStandardCost],  
            [dbo].[FactInternetSales].[TotalProductCost],  
            [dbo].[FactInternetSales].[SalesAmount],  
            [dbo].[FactInternetSales].[TaxAmt],  
            [dbo].[FactInternetSales].[Freight],  
            [dbo].[FactInternetSales].[CarrierTrackingNumber],  
            [dbo].[FactInternetSales].[CustomerPONumber]  
          FROM [dbo].[FactInternetSales]  
          WHERE OrderDateKey > '1280'  
        </QueryDefinition>  
      </Source>  
    </Binding>  
  </Bindings>  
  <Type>ProcessAdd</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
  