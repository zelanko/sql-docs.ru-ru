---
title: Общие свойства | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- external metadata column properties [Integration Services]
- output properties [Integration Services]
- data types [Integration Services], properties
- input properties [Integration Services]
- component properties [Integration Services]
ms.assetid: 51973502-5cc6-4125-9fce-e60fa1b7b796
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 77bb61af021bb7499f6656d2fd604f4bdc06bfeb
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84922115"
---
# <a name="common-properties"></a>Общие свойства
  Объекты потока данных в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] объектной модели имеют общие свойства и пользовательские свойства на уровнях компонент, вход и выход, а также входные и выходные столбцы. Многие свойства имеют значения, доступные только для чтения и присваиваемые подсистемой обработки потока данных на этапе выполнения.  
  
 Этот раздел содержит список и описание пользовательских свойств объектов потоков данных.  
  
-   [Components](#components)  
  
-   [Входа](#inputs)  
  
-   [Входные столбцы](#inputcolumns)  
  
-   [Выходные](#outputs)  
  
-   [Выходные столбцы](#outputcolumns)  
  
 Дополнительные сведения о пользовательских свойствах см. в следующих разделах.  
  
-   [Пользовательские свойства ADO NET](data-flow/ado-net-custom-properties.md)  
  
-   [Пользовательские свойства задач управления CDC](control-flow/cdc-control-task-custom-properties.md)  
  
-   [Пользовательские свойства источника «CDC»](data-flow/cdc-source-custom-properties.md)  
  
-   [Пользовательские свойства назначения «Обучение модели интеллектуального анализа данных»](data-flow/data-mining-model-training-destination-custom-properties.md)  
  
-   [Пользовательские свойства назначения «Модуль чтения данных»](data-flow/datareader-destination-custom-properties.md)  
  
-   [Пользовательские свойства назначения «Обработка измерений»](data-flow/dimension-processing-destination-custom-properies.md)  
  
-   [Пользовательские свойства Excel](data-flow/excel-custom-properties.md)  
  
-   [Пользовательские свойства неструктурированного файла](data-flow/flat-file-custom-properties.md)  
  
-   [Пользовательские свойства назначений ODBC](data-flow/odbc-destination-custom-properties.md)  
  
-   [Пользовательские свойства источника «ODBC»](data-flow/odbc-source-custom-properties.md)  
  
-   [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md)Пользовательские свойства OLE DB  
  
-   [Пользовательские свойства назначения «Обработка секций»](data-flow/partition-processing-destination-custom-properties.md)  
  
-   [Пользовательские свойства необработанного файла](data-flow/raw-file-custom-properties.md)  
  
-   [Пользовательские свойства назначения «Набор записей»](data-flow/recordset-destination-custom-properties.md)  
  
-   [Пользовательские свойства назначения «SQL Server Compact Edition»](data-flow/sql-server-compact-edition-destination-custom-properties.md)  
  
-   [Пользовательские свойства назначения «SQL Server»](data-flow/sql-server-destination-custom-properties.md)  
  
-   [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md)  
  
-   [Пользовательские свойства источника «XML»](data-flow/xml-source-custom-properties.md)  
  
##  <a name="component-properties"></a><a name="components"></a>Свойства компонента  
 В объектной модели служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] компонент потока данных реализует интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>.  
  
 В следующей таблице показаны свойства компонентов потока данных. Некоторые свойства имеют значения, доступные только для чтения и присваиваемые подсистемой обработки потока данных на этапе выполнения.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|ComponentClassID|Строка|Идентификатор CLSID компонента.|  
|ContactInfo|Строка|Контактные данные разработчика компонента.|  
|Описание|Строка|Описание компонента потока данных. Значением по умолчанию для этого свойства является имя компонента потока данных.|  
|ID|Целое число|Значение, являющееся уникальным идентификатором данного экземпляра компонента.|  
|IdentificationString|Строка|Идентифицирует компонент.|  
|IsDefaultLocale|Логическое|Указывает, используется ли компонентом локаль задачи потока данных, которой она принадлежит.|  
|LocaleID|Целое число|Локаль, используемая компонентом потока данных при запуске пакета. Все локали Windows доступны для использования компонентами потока данных.|  
|Название|Строка|Имя компонента потока данных.|  
|PipelineVersion|Целое число|Версия задачи потока данных, в которой должен выполняться компонент.|  
|UsesDispositions|Логическое|Указывает, имеет ли компонент вывод ошибок на выходе.|  
|ValidateExternalMetadata|Логическое|Указывает, проверены ли метаданные внешних столбцов. Значение по умолчанию этого свойства равно `True`.|  
|Версия|Целое число|Версия компонента.|  
  
##  <a name="input-properties"></a><a name="inputs"></a>Входные свойства  
 В объектной модели служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] преобразования и назначения имеют входы. Вход компонента потока данных реализует интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>.  
  
 В следующей таблице показаны свойства входов компонентов в потоке данных. Некоторые свойства имеют значения, доступные только для чтения и присваиваемые подсистемой обработки потока данных на этапе выполнения.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|Описание|Строка|Описание входа.|  
|ErrorOrTruncationOperation|Строка|Дополнительная строка, указывающая типы ошибок или типы усечения, которые могут происходить при обработке строки.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Значение, указывающее порядок обработки ошибок. Допустимые значения — `Fail component`, `Ignore failure` и `Redirect row`.|  
|HasSideEffects|Логическое|Указывает, можно ли удалить компонент из плана выполнения потока данных, если он не присоединен к нисходящему компоненту и когда `RunInOptimizedMode` имеет значение `true` .|  
|ID|Целое число|Значение, уникально определяющее вход.|  
|IdentificationString|Строка|Строка, определяющая вход.|  
|IsSorted|Логическое|Указывает, сортируются ли данные на входе.|  
|Название|Строка|Имя входа.|  
|SourceLocale|Целое число|Идентификатор локали данных входа.|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Значение, определяющее, как компонент обрабатывает усечения, происходящие при обработке строк. . Допустимые значения — `Fail component`, `Ignore failure` и `Redirect row`.|  
  
 Назначения и некоторые преобразования не поддерживают вывод ошибок на выходе, а свойства ErrorRowDisposition и TruncationRowDisposition этих компонентов доступны только для чтения.  
  
###  <a name="input-column-properties"></a><a name="inputcolumns"></a>Свойства входного столбца  
 В объектной модели служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] вход содержит коллекцию входных столбцов. Входной столбец компонента потока данных реализует интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInputColumn100>.  
  
 В следующей таблице показаны свойства входных столбцов компонентов потока данных. Некоторые свойства имеют значения, доступные только для чтения и присваиваемые подсистемой обработки потока данных на этапе выполнения.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|ComparisonFlags|Целое число|Набор флагов, задающий правила сравнения столбцов, имеющих символьный тип данных. Дополнительные сведения см. в статье [Comparing String Data](data-flow/comparing-string-data.md).|  
|Описание|Строка|Описывает входной столбец.|  
|ErrorOrTruncationOperation|Строка|Дополнительная строка, указывающая типы ошибок или типы усечения, которые могут происходить при обработке строки.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Значение, указывающее порядок обработки ошибок. Допустимые значения — `Fail component`, `Ignore failure` и `Redirect row`.|  
|ExternalMetadataColumnID|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100>|Идентификатор столбца внешних метаданных, присвоенный входному столбцу.|  
|ID|Целое число|Значение, уникально определяющее входной столбец.|  
|IdentificationString|Строка|Строка, определяющая входной столбец.|  
|LineageID|Целое число|Идентификатор восходящего столбца.|  
|Название|Строка|Имя входного столбца.|  
|SortKeyPosition|Целое число|Значение указывает, является ли столбец отсортированным, порядок его сортировки и последовательность, в которой отсортированы несколько столбцов. Значение **0** указывает на то, что столбец не отсортирован.  Дополнительные сведения см. в разделе [Сортировка данных для преобразований "Слияние" и "Соединение слиянием"](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Значение, определяющее, как компонент обрабатывает усечения, происходящие при обработке строк. Допустимые значения — `Fail component`, `Ignore failure` и `Redirect row`.|  
|UpstreamComponentName|Строка|Имя компонента восходящего потока данных.|  
|UsageType|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSUsageType>|Значение, определяющее, как входной столбец используется компонентом.|  
  
 Входной столбец также использует свойства типа данных, описанные в разделе "Свойства типа данных".  
  
##  <a name="output-properties"></a><a name="outputs"></a>Свойства вывода  
 В объектной модели служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] источники и назначения имеют выходы. Выход компонента потока данных реализует интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>.  
  
 В следующей таблице показаны свойства выходов компонентов в потоке данных. Некоторые свойства имеют значения, доступные только для чтения и присваиваемые подсистемой обработки потока данных на этапе выполнения.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|DeleteOutputOnPathDetached|Логическое|Определяет, удаляет ли подсистема обработки потока данных выход при отключении от пути.|  
|Описание|Строка|Описывает выход.|  
|ErrorOrTruncationOperation|Строка|Дополнительная строка, указывающая типы ошибок или типы усечения, которые могут происходить при обработке строки.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Значение, указывающее порядок обработки ошибок. Допустимые значения — `Fail component`, `Ignore failure` и `Redirect row`.|  
|ExclusionGroup|Целое число|Значение, определяющее группу взаимоисключающих выводов.|  
|HasSideEffects|Логическое|Указывает, можно ли удалять компонент из плана выполнения потока данных, если он не присоединен к компоненту восходящего потока данных, а свойство `RunInOptimizedMode` установлено в `true`.|  
|ID|Целое число|Значение, уникально определяющее выход.|  
|IdentificationString|Строка|Строка, определяющая выход.|  
|IsErrorOut|Логическое|Указывает, используется ли выход для вывода ошибок.|  
|IsSorted|Логическое|Указывает, отсортирован ли выход. Значение по умолчанию — `False`.<br /><br /> Важно. Установка значения свойства в не сортирует ** \* данные. \* \* \* ** `IsSorted` `True` Это свойство только указывает компонентам нисходящего потока, что данные раньше были отсортированы. Дополнительные сведения см. в разделе [Сортировка данных для преобразований "Слияние" и "Соединение слиянием"](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).|  
|Название|Строка|Имя выхода.|  
|SynchronousInputID|Целое число|Идентификатор синхронного с выходом входа.|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Значение, определяющее, как компонент обрабатывает усечения, происходящие при обработке строк. Допустимые значения — `Fail component`, `Ignore failure` и `Redirect row`.|  
  
###  <a name="output-column-properties"></a><a name="outputcolumns"></a>Свойства выходного столбца  
 В объектной модели служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] выход содержит коллекцию выходных столбцов. Выходной столбец компонента потока данных реализует интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100>.  
  
 В следующей таблице показаны свойства выходных столбцов компонентов потока данных. Некоторые свойства имеют значения, доступные только для чтения и присваиваемые подсистемой обработки потока данных на этапе выполнения.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|ComparisonFlags|Целое число|Набор флагов, задающий правила сравнения столбцов, имеющих символьный тип данных. Дополнительные сведения см. в статье [Comparing String Data](data-flow/comparing-string-data.md).|  
|Описание|Строка|Описывает выходной столбец.|  
|ErrorOrTruncationOperation|Строка|Дополнительная строка, указывающая типы ошибок или типы усечения, которые могут происходить при обработке строки.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Значение, указывающее порядок обработки ошибок. Допустимые значения — `Fail component`, `Ignore failure` и `Redirect row`. Значение по умолчанию — `Fail component`.|  
|ExternalMetadataColumnID|Целое число|Идентификатор столбца внешних метаданных, присвоенный входному столбцу.|  
|ID|Целое число|Значение, уникально определяющее выходной столбец.|  
|IdentificationString|Строка|Строка, определяющая выходной столбец.|  
|LineageID|Целое число|Идентификатор выходного столбца. Компоненты нисходящего потока данных ссылаются на столбец при помощи этого значения.|  
|Название|Строка|Имя выходного столбца.|  
|SortKeyPosition|Целое число|Значение указывает, является ли столбец отсортированным, порядок его сортировки и последовательность, в которой отсортированы несколько столбцов. Значение **0** указывает на то, что столбец не отсортирован. Дополнительные сведения см. в разделе [Сортировка данных для преобразований "Слияние" и "Соединение слиянием"](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).|  
|SpecialFlags|Целое число|Значение, содержащее специальные флаги выходного столбца.|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Значение, определяющее, как компонент обрабатывает усечения, происходящие при обработке строк. Допустимые значения — `Fail component`, `Ignore failure` и `Redirect row`. Значение по умолчанию — `Fail component`.|  
  
 Выходные столбцы также содержат набор свойств типа данных.  
  
## <a name="external-metadata-column-properties"></a>Свойства столбца внешних метаданных  
 В объектной модели служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] выходы и входы могут содержать коллекцию столбцов внешних метаданных. Столбец внешних метаданных компонента потока данных реализует интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100>.  
  
 В следующей таблице показаны свойства столбцов внешних метаданных компонентов потока данных. Некоторые свойства имеют значения, доступные только для чтения и присваиваемые подсистемой обработки потока данных на этапе выполнения.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|Описание|Строка|Описывает внешний столбец.|  
|ID|Целое число|Значение, уникально определяющее столбец.|  
|IdentificationString|Строка|Строка, определяющая столбец.|  
|Название|Строка|Имя внешнего столбца.|  
  
 Столбцы внешних метаданных также содержат набор свойств типа данных.  
  
## <a name="data-type-properties"></a>Свойства типа данных  
 Выходные столбцы и столбцы внешних метаданных также содержат набор свойств типа данных. В зависимости от типа данных столбца, свойства могут быть доступны либо для чтения и для записи, либо только для чтения.  
  
 В следующей таблице описываются свойства типов данных внешних столбцов и столбцов внешних метаданных.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|CodePage|Целое число|Определяет кодовую страницу данных строки, записанных не в Юникоде.|  
|DataType|Integer (перечисление)|Тип данных столбца служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Дополнительные сведения см. в разделе [типы данных Integration Services](data-flow/integration-services-data-types.md).|  
|Длина|Целое число|Длина столбца, измеренная в символах.|  
|Точность|Целое число|Точность числового столбца.|  
|Масштабирование|Целое число|Масштаб числового столбца.|  
  
## <a name="see-also"></a>См. также:  
 [Поток данных](data-flow/data-flow.md)   
 [Пользовательские свойства преобразования](data-flow/transformations/transformation-custom-properties.md)   
 [Свойства пути](../../2014/integration-services/path-properties.md)   
 [Свойства потока данных, которые можно задавать с помощью выражений](../../2014/integration-services/data-flow-properties-that-can-be-set-by-using-expressions.md)  
  
  
