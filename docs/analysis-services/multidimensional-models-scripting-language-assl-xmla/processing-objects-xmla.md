---
title: Обработка объектов (XMLA) | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 59a581f7e70f3fc1afd7eb7c1eaf4751d32719d0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63261661"
---
# <a name="processing-objects-xmla"></a>Обработка объектов (XMLA)
  В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], обработка — это шаг или последовательность шагов, которые преобразуют данные в сведения для бизнес-анализа. Характеристики обработки меняются в зависимости от типа объекта, но обработка всегда является составной частью процесса преобразования данных в сведения.  
  
 К процессу [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] объекта, можно использовать [процесс](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) команды. **Процесс** команда может обрабатывать следующие объекты на [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляр:  
  
-   Кубы  
  
-   Базы данных  
  
-   Измерения  
  
-   Группы мер  
  
-   Модели интеллектуального анализа данных  
  
-   Структуры интеллектуального анализа данных  
  
-   Секции  
  
 Для управления обработкой объектов, **процесс** команда имеет различные свойства, которые могут быть установлены. **Процесс** команда имеет свойства, которые управляют: какой объем обработки должен быть выполнен, какие объекты будут обработаны, следует ли использовать out-привязок, способ обработки ошибок и как управлять таблицами обратной записи.  
  
## <a name="specifying-processing-options"></a>Указание параметров обработки  
 [Тип](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla) свойство **процесс** команда указывает параметр обработки для использования при обработке объекта. Дополнительные сведения об обработке см. в разделе [Настройка параметров обработки (службы Analysis Services)](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
 В следующей таблице перечислены константы для **тип** свойства, а также различных объектов, которые могут быть обработаны при помощи каждой константы.  
  
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
  
 Дополнительные сведения об обработке [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] объектов, см. в разделе [обработка многомерной модели &#40;служб Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
## <a name="specifying-objects-to-be-processed"></a>Указание объектов для обработки  
 [Объект](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) свойство **процесс** команда содержит идентификатор объекта, который должен быть обработан. Можно указать только один объект в **процесс** команды, однако при его обработке обрабатываются также все дочерние объекты. Например, при обработке группы мер в кубе обрабатываются все секции для этой группы мер, а при обработке базы данных обрабатываются все объекты, включая кубы, измерения и структуры интеллектуального анализа данных, содержащиеся в базе данных.  
  
 Если задать **ProcessAffectedObjects** атрибут **процесс** команды значение true, все связанные также обработки объекта, вовлеченные в обработку указанного объекта. Например, если осуществляется добавочное обновление измерения с помощью *ProcessUpdate* параметр в обработки **процесс** любой секции, агрегаты которых становятся недействительными из-за членов команды, добавлять или удалять, также обрабатываются службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Если **ProcessAffectedObjects** задано значение true. В этом случае одна **процесс** команда может обрабатывать несколько объектов в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляра, но [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] определяет, какие объекты, кроме одного объекта, указанного в **процесс** команда также должен быть обработан.  
  
 Тем не менее, может обрабатывать несколько объектов, таких как измерения, в то же время, с помощью нескольких **процесс** команды в **пакета** команды. Пакетные операции позволяют точнее управлять последовательной или параллельной обработки объектов на [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляра, чем при использовании **ProcessAffectedObjects** атрибута, а также позволяют подстраивать подход к обработке для большего размера [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] баз данных. Дополнительные сведения о выполнении пакетных операций, см. в разделе [выполнение пакетных операций &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md).  
  
## <a name="specifying-out-of-line-bindings"></a>Указание внешних привязок  
 Если **процесс** команды не содержится **пакета** команду, при необходимости можно указать вне строки привязок в [привязки](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla), [источникаданных](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasource-element-xmla), и [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) свойства **процесс** команду для объектов для обработки. Out-привязок — это ссылки на источники данных, представления источников данных и другие объекты, в которых привязка существует только во время выполнения **процесс** команды и которые переопределяют любые существующие привязки, связанные с обрабатываемых объектов. Если внешние привязки не указаны, используются привязки, связанные в данный момент с обрабатываемыми объектами.  
  
 Внешние привязки используются в следующих ситуациях.  
  
-   В случае постепенной обработки секции, в которой должна быть указана альтернативная таблица фактов или фильтр для существующей таблицы фактов с тем, чтобы строки не засчитывались дважды.  
  
-   С помощью задачи потока данных в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для предоставления данных при обработке измерения, модели интеллектуального анализа данных или секции.  
  
 Внешние привязки описаны как часть языка сценариев служб Analysis Services (языка ASSL). Дополнительные сведения о привязках вне строки в языке ASSL см. в разделе [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
### <a name="incrementally-updating-partitions"></a>Добавочное обновление секций  
 Для добавочного обновления уже обработанной секции обычно требуется внешняя привязка, так как привязка, указанная для этой секции, ссылается на данные таблицы фактов, которые уже были статистически обработаны в рамках данной секции. При выполнении добавочного обновления уже обработанной секции с помощью **процесс** команде [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] выполняет следующие действия:  
  
-   Создают временную секцию с такой же структурой, как у секции, добавочное обновление которой необходимо выполнить.  
  
-   Обрабатывают временную секцию, с помощью привязки вне строки, указанной в **процесс** команды.  
  
-   Объединяют временную секцию с существующей выделенной секцией.  
  
 Дополнительные сведения о слиянии секций с помощью XML для аналитики (XMLA) см. в разделе [слияние секций &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/merging-partitions-xmla.md).  
  
## <a name="handling-processing-errors"></a>Обработка ошибок  
 [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) свойство **процесс** команда позволяет задать способ обработки ошибок, возникших при обработке объекта. Например, при обработке измерения службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] обнаруживают повторяющиеся значение в ключевом столбце ключевого атрибута. Поскольку ключи атрибутов должны быть уникальны, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] удаляют повторяющиеся записи. На основе [KeyDuplicate](https://docs.microsoft.com/bi-reference/assl/properties/keyduplicate-element-assl) свойство **ErrorConfiguration**, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может:  
  
-   Пропустить ошибку и продолжить обработку измерения.  
  
-   Возвратить сообщение, указывающее, что службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] обнаружили повторяющийся ключ, и продолжить обработку.  
  
 Существует много схожих условий, для которого **ErrorConfiguration** предоставляет параметры во время **процесс** команды.  
  
## <a name="managing-writeback-tables"></a>Управление таблицами обратной записи  
 Если **процесс** команда обнаруживает секции, доступные для записи или куба или группы мер для такой секции, который не является полностью обработаны, таблица обратной записи может не существовать для этой секции. [WritebackTableCreation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/writebacktablecreation-element-xmla) свойство **процесс** команда определяет ли [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] необходимо создать таблицу обратной записи.  
  
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
 В следующем примере **Internet_Sales_2004** раздел в **Интернет-продажи** группе мер **Adventure Works DW** куба в [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] пример [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных. **Процесс** команда добавляет агрегаты для заказа даты позже 31 декабря 2006 г. в раздел при помощи привязки запроса вне строки в **привязки** свойство **процесса**  команду, чтобы получить строки таблицы фактов, из которого должны быть сформированы агрегаты для добавления в секцию.  
  
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
  
  
