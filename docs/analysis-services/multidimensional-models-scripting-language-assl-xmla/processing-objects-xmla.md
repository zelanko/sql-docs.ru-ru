---
title: "Обработка объектов (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
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
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6dfc2fafb76d19ea986b697ec065abec738f4c05
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="processing-objects-xmla"></a>Обработка объектов (XMLA)
  В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], обработка — это шаг или последовательность шагов, которые преобразуют данные в сведения для бизнес-анализа. Характеристики обработки меняются в зависимости от типа объекта, но обработка всегда является составной частью процесса преобразования данных в сведения.  
  
 Процессу [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] объекта, можно использовать [процесс](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) команды. **Процесс** команда может обрабатывать следующие объекты на [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляр:  
  
-   Кубы  
  
-   Базы данных  
  
-   Измерения  
  
-   Группы мер  
  
-   Модели интеллектуального анализа данных  
  
-   Структуры интеллектуального анализа данных  
  
-   Секции  
  
 Для управления обработкой объектов, **процесс** команда имеет различные свойства, которые могут быть установлены. **Процесс** команда имеет свойства, которые управляют: какой объем обработки должен быть выполнен, какие объекты будут обработаны, следует ли использовать ожидания привязок, способ обработки ошибок и как управлять таблицами обратной записи.  
  
## <a name="specifying-processing-options"></a>Указание параметров обработки  
 [Тип](../../analysis-services/xmla/xml-elements-properties/type-element-xmla.md) свойство **процесс** команда задает режим обработки для использования при обработке объекта. Дополнительные сведения об обработке см. в разделе [Настройка параметров обработки (службы Analysis Services)](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
 В следующей таблице перечислены константы для **тип** свойство и различных объектов, которые могут быть обработаны при помощи каждой константы.  
  
|**Тип** значение|Применимые объекты|  
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
  
 Дополнительные сведения об обработке [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] см [обработка многомерной модели &#40; Службы Analysis Services &#41; ](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
## <a name="specifying-objects-to-be-processed"></a>Указание объектов для обработки  
 [Объекта](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) свойство **процесс** команда содержит идентификатор объекта для обработки. Только один объект может быть указано в **процесс** команды, но обработка объекта обрабатываются также все дочерние объекты. Например, при обработке группы мер в кубе обрабатываются все секции для этой группы мер, а при обработке базы данных обрабатываются все объекты, включая кубы, измерения и структуры интеллектуального анализа данных, содержащиеся в базе данных.  
  
 Если задать **ProcessAffectedObjects** атрибут **процесс** команды значение true, все связанные также обрабатываются объекты, вовлеченные в обработку указанного объекта. Например, если измерение выполняется добавочное обновление с помощью *ProcessUpdate* параметр в обработки **процесс** любого раздела, агрегаты которых становятся недействительными из-за членов команды, Добавление или удаление также обрабатываются службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Если **ProcessAffectedObjects** задано значение true. В этом случае одна **процесс** команда может обрабатывать несколько объектов в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляра, но [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] определяет, какие объекты, кроме одного объекта, указанного в **процесс** команда также должны быть обработаны.  
  
 Тем не менее, может обрабатывать несколько объектов, таких как измерения, в то же время с помощью нескольких **процесс** команд в **пакета** команды. Пакетные операции предоставления точнее управлять последовательной или параллельной обработкой объектов в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляр, чем при использовании **ProcessAffectedObjects** атрибута, а также позволяют подстраивать подход к обработке для большего размера [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] баз данных. Дополнительные сведения о выполнении пакетных операций см. в разделе [выполнение пакетных операций &#40; XML для Аналитики &#41; ](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md).  
  
## <a name="specifying-out-of-line-bindings"></a>Указание внешних привязок  
 Если **процесс** команда не содержится в **пакета** команду, можно дополнительно указать out-привязок в [привязки](../../analysis-services/xmla/xml-elements-properties/bindings-element-xmla.md), [источникданных](../../analysis-services/xmla/xml-elements-properties/datasource-element-xmla.md), и [DataSourceView](../../analysis-services/xmla/xml-elements-properties/datasourceview-element-xmla.md) свойства **процесс** для объектов для обработки. Out-привязок — это ссылки на источники данных, представления источников данных и другие объекты, в которых привязка существует только во время выполнения **процесс** команда, и которые переопределяют любые существующие привязки, связанные с обрабатываемых объектов. Если внешние привязки не указаны, используются привязки, связанные в данный момент с обрабатываемыми объектами.  
  
 Внешние привязки используются в следующих ситуациях.  
  
-   В случае постепенной обработки секции, в которой должна быть указана альтернативная таблица фактов или фильтр для существующей таблицы фактов с тем, чтобы строки не засчитывались дважды.  
  
-   Используя задачу потока данных в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для предоставления данных при обработке измерения, модели интеллектуального анализа данных или секции.  
  
 Внешние привязки описаны как часть языка сценариев служб Analysis Services (языка ASSL). Дополнительные сведения о привязках вне строки в языке ASSL см. в разделе [&#40; источники данных и привязки Многомерные службы SSAS &#41; ](../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
### <a name="incrementally-updating-partitions"></a>Добавочное обновление секций  
 Для добавочного обновления уже обработанной секции обычно требуется внешняя привязка, так как привязка, указанная для этой секции, ссылается на данные таблицы фактов, которые уже были статистически обработаны в рамках данной секции. При выполнении добавочного обновления уже обработанной секции с помощью **процесс** команды [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] выполняет следующие действия:  
  
-   Создают временную секцию с такой же структурой, как у секции, добавочное обновление которой необходимо выполнить.  
  
-   Обрабатывают временную секцию, с помощью привязки вне строки, заданной в **процесс** команды.  
  
-   Объединяют временную секцию с существующей выделенной секцией.  
  
 Дополнительные сведения о слиянии секций с помощью XML для аналитики (XMLA) см. в разделе [слияние секций &#40; XML для Аналитики &#41; ](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/merging-partitions-xmla.md).  
  
## <a name="handling-processing-errors"></a>Обработка ошибок  
 [ErrorConfiguration](../../analysis-services/xmla/xml-elements-properties/errorconfiguration-element-xmla.md) свойство **процесс** команда позволяет задать способ обработки ошибок, возникших во время обработки объекта. Например, при обработке измерения службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] обнаруживают повторяющиеся значение в ключевом столбце ключевого атрибута. Поскольку ключи атрибутов должны быть уникальны, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] удаляют повторяющиеся записи. На основе [KeyDuplicate](../../analysis-services/scripting/properties/keyduplicate-element-assl.md) свойство **ErrorConfiguration**, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может:  
  
-   Пропустить ошибку и продолжить обработку измерения.  
  
-   Возвратить сообщение, указывающее, что службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] обнаружили повторяющийся ключ, и продолжить обработку.  
  
 Существует много схожих условий, для которого **ErrorConfiguration** предоставляет параметры во время **процесс** команды.  
  
## <a name="managing-writeback-tables"></a>Управление таблицами обратной записи  
 Если **процесс** команда обнаруживает доступной для записи секции или куба или группы мер для такой секции, которые не полностью обработаны, таблица обратной записи может не существовать для этой секции. [WritebackTableCreation](../../analysis-services/xmla/xml-elements-properties/writebacktablecreation-element-xmla.md) свойство **процесс** команда определяет, является ли [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] должны создавать таблицу обратной записи.  
  
## <a name="examples"></a>Примеры  
  
### <a name="description"></a>Description  
 В следующем примере производится полная обработка образца базы данных [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
### <a name="code"></a>код  
  
```  
<Process xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
  </Object>  
  <Type>ProcessFull</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
### <a name="description"></a>Description  
 Следующий пример осуществляет добавочную обработку **Internet_Sales_2004** секции в **продажи через Интернет** группе мер, **Adventure Works DW** куба в [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] пример [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных. **Процесс** команда состоит в добавлении агрегаты для заказа даты позже 31 декабря 2006 г. в секции с помощью привязки запроса вне строки в **привязки** свойство **процесса**  команду для извлечения строк таблицы фактов, из которого должны быть сформированы агрегаты для добавления в секцию.  
  
### <a name="code"></a>код  
  
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
  
  

