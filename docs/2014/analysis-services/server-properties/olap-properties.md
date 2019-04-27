---
title: Свойства OLAP | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- AggregationPerfLog property
- DefaultPageSizeForProp property
- UseSinglePassForDimSecurityAutoExist property
- DeepCompressValue property
- CacheRowsetRows property
- Income property
- AggregationNewAlgo property
- MemoryAdjustFactor property
- DimensionLatencyAccuracy property
- InitialBonus property
- DefaultPageSizeForDataHeader property
- MaxCPUUsage property
- DistinctBuffer property
- PartitionLatencyAccuracy property
- MaxRetries property
- UseDataCacheRegistryMultiplyKey property
- ConvertDeletedToUnknown property
- DatabaseConnectionPoolMax property
- DataFileInitEnabled property
- DefaultPageSizeForHash property
- MaxRolapOrConditions property
- UseDataCacheFreeLastPageMemory property
- OLAP [Analysis Services], properties
- MapHandleAlgorithm property
- IndexBuildEnabled property
- MaxObjectsInParallel property
- IgnoreNullRolapRows property
- DimensionPropertyCacheSize property
- DefaultRefreshInterval property
- CheckDistinctRecordSortOrder property
- BufferMemoryLimit property
- EnableTableGrouping property
- ExpressNonEmptyUseEnabled property
- CopyLinkedDataCacheAndRegistry property
- UseDataSlice property
- MemoryLimitErrorEnabled property
- Enabled property
- EnableRolapOptimization property
- DatabaseConnectionPoolTimeout property
- UseDataCacheRegistryHashTable property
- AggregationsBuildEnabled property
- Tax property
- DatabaseConnectionPoolGeneralTimeout property
- DefaultPageSizeForString property
- DatabaseConnectionPoolConnectTimeout property
- MinimumBalance property
- OptimizeSchema property
- UseCalculationCacheRegistry property
- MaxTableDepth property
- DataSliceInitEnabled property
- PrefetchLowerGranularities property
- UseVBANet property
- BufferRecordLimit property
- DefaultPageSizeForIndexHeader property
- MaximumBalance property
- CalculationCacheRegistryMaxIterations property
- DefaultDrillthroughMaxRows property
- IndexBuildThreshold property
- UseDataCacheRegistry property
- MemoryAdjustConst property
- ApplyIntersect property
- IndexFileInitEnabled property
- CacheRowsetToDisk property
- DataCacheRegistryMaxIterations property
- AllowSEFiltering property
- ForceMultiPass property
- ApplySubtract property
- IndexUseEnabled property
- AggregationsUseEnabled property
- DataPlacementOptimization property
- UseMaterializedIterators property
- CacheRecordLimit property
- ROLAPDimensionProcessingEffort property
- DefaultPageSizeForIndex property
- EnableRolapDimQueryTableGrouping property
- DimensionPropertyKeyCache property
- SleepIntervalSecs property
- DefaultPageSizeForData property
- MapFormatMask property
- CalculationEvaluationPolicy property
- AggregationMemoryLimitMin property
- RecordsReportGranularity property
- MemoryLimit property
- AggregationMemoryLimitMax property
ms.assetid: 06eb0d78-96c0-42ff-b759-f4c794597c8d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e89743de546afbc331259dbe3ff18a0344a4e420
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62746726"
---
# <a name="olap-properties"></a>Свойства OLAP
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают перечисленные в следующих таблицах свойства сервера OLAP. Дополнительные сведения о дополнительных свойствах сервера и об их настройке см. в разделе [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **Применимо к:** Только многомерный режим сервера  
  
## <a name="memory"></a>Память  
 `DefaultPageSizeForData`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DefaultPageSizeForDataHeader`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DefaultPageSizeForIndex`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DefaultPageSizeForIndexHeader`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DefaultPageSizeForString`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DefaultPageSizeForHash`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DefaultPageSizeForProp`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="lazyprocessing"></a>LazyProcessing  
 `Enabled`  
 Логическое свойство, которое указывает, включена ли отложенная обработка агрегатов.  
  
 `SleepIntervalSecs`  
 32-разрядное целочисленное свойство со знаком, которое определяет, с каким периодом (в секундах) сервер проверяет наличие ожидающих задач отложенной обработки.  
  
 `MaxCPUUsage`  
 64-разрядное свойство со значением двойной точности с плавающей запятой, определяющее максимальное использование процессора для отложенной обработки, в процентах. Сервер отслеживает среднюю занятость процессора по моментальным снимкам. Для процесса является нормальным превышать это пороговое значение.  
  
 Значение этого свойства по умолчанию — 0,5, что означает, что на отложенную обработку отводится не более 50 % ресурсов процессора.  
  
 `MaxObjectsInParallel`  
 32-разрядное целочисленное свойство со знаком, которое указывает максимальное число секций, которые могут параллельно проходить отложенную обработку.  
  
 `MaxRetries`  
 32-разрядное целочисленное свойство со знаком, определяющее число неудачных попыток отложенной обработки, после которого возникает ошибка.  
  
## <a name="processplan"></a>ProcessPlan  
 `CacheRowsetRows`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `CacheRowsetToDisk`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DistinctBuffer`  
 32-разрядное целочисленное свойство со знаком, устанавливающее размер внутреннего буфера для различных расчетов. Увеличьте это значение, чтобы ускорить обработку различных расчетов за счет использования дополнительной памяти.  
  
 `EnableRolapDimQueryTableGrouping`  
 Логическое свойство, устанавливающее, включено ли группирование таблиц для измерений ROLAP. Если оно имеет значение True, то при запросе измерений ROLAP во время выполнения происходит одновременный запрос полных таблиц измерений ROLAP в противоположность организации отдельных очередей для каждого атрибута.  
  
 `EnableTableGrouping`  
 Логическое свойство, которое указывает, включено ли группирование таблиц. Если оно имеет значение True, то при обработке измерений происходит одновременный запрос ко всем таблицам измерений в противоположность организации отдельных очередей для каждого атрибута.  
  
 `ForceMultiPass`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MaxTableDepth`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MemoryAdjustConst`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MemoryAdjustFactor`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MemoryLimit`  
 64-разрядное свойство со значением двойной точности с плавающей запятой, определяющее максимальный размер памяти, выделяемой на обработку, в процентах от физической памяти.  
  
 Значение этого свойства по умолчанию — 65, что означает, что на обработку измерений и кубов может быть выделено до 65 % физической памяти.  
  
 `MemoryLimitErrorEnabled`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `OptimizeSchema`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="proactivecaching"></a>ProactiveCaching  
 `DefaultRefreshInterval`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DimensionLatencyAccuracy`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `PartitionLatencyAccuracy`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="process"></a>Процесс  
 `AggregationMemoryLimitMax`  
 64-разрядное свойство со значением двойной точности с плавающей запятой, определяющее максимальный размер памяти, выделяемой на обработку, в процентах от физической памяти.  
  
 Значение этого свойства по умолчанию — 80, что означает, что на обработку агрегатов может быть выделено до 80% физической памяти.  
  
 `AggregationMemoryLimitMin`  
 64-разрядное свойство со значением двойной точности с плавающей запятой, определяющее максимальный размер памяти, выделяемой на обработку, в процентах от физической памяти. Большее значение может ускорить обработку агрегатов за счет использования дополнительной памяти.  
  
 Значение этого свойства по умолчанию — 10, что означает, что на обработку агрегатов будет выделено 10 % физической памяти.  
  
 `AggregationNewAlgo`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `AggregationPerfLog2`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `AggregationsBuildEnabled`  
 Логическое свойство, которое указывает, включено ли построение статистических схем. Этот механизм позволяет испытать построение агрегатов без изменения статистической схемы.  
  
 `BufferMemoryLimit`  
 64-разрядное свойство со знаком, имеющее значение двойной точности с плавающей запятой и определяющее предельный объем памяти буфера обработки в процентах от физической памяти.  
  
 Значение этого свойства по умолчанию — 60, то есть для буфера может использоваться до 60% физической памяти.  
  
 `BufferRecordLimit`  
 32-разрядное целочисленное свойство со знаком, устанавливающее количество записей, которые можно поместить в буфер во время обработки.  
  
 Значение этого свойства по умолчанию — 1 048 576 (записей).  
  
 `CacheRecordLimit`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `CheckDistinctRecordSortOrder`  
 Логическое свойство, которое определяет, поддается ли интерпретации порядок сортировки результатов запроса различных расчетов при обработке секций. Значение True показывает, что порядок сортировки не поддается интерпретации и должен проверяться сервером. При обработке секций с мерами числа различных объектов запросы отправляются SQL в упорядоченном виде. Установите значение false, чтобы ускорить обработку.  
  
 Значение по умолчанию — True, то есть порядок сортировки не поддается интерпретации и должен быть проверен.  
  
 `DatabaseConnectionPoolConnectTimeout`  
 32-разрядное целочисленное свойство со знаком, задающее время ожидания (в секундах) при открытии нового соединения.  
  
 `DatabaseConnectionPoolGeneralTimeout`  
 32-разрядное целочисленное свойство со знаком, задающее время ожидания подключения к базе данных для внешних соединений OLEDB, в секундах.  
  
 `DatabaseConnectionPoolMax`  
 32-разрядное целочисленное свойство со знаком, устанавливающее максимальное количество подключение к базе данных в пуле.  
  
 Значение по умолчанию для этого свойства составляет 50 (соединений).  
  
 `DatabaseConnectionPoolTimeout`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataFileInitEnabled`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataPlacementOptimization`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataSliceInitEnabled`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DeepCompressValue`  
 Логическое свойство, которое применяется к мерам с данными типа Double и указывает, можно ли эти числа сжимать с потерей численной точности. Значение False запрещает сжатие и означает отсутствие потерь точности.  
  
 Значение по умолчанию — True, то есть разрешается сжатие с потерей точности.  
  
 `DimensionPropertyKeyCache`  
 Логическое свойство, которое указывает, будут ли кэшироваться ключи свойств измерения. Если ключи не уникальны, необходимо установить значение True.  
  
 `IndexBuildEnabled`  
 Логическое свойство, которое указывает, будут ли при обработке строиться индексы. Это свойство служит для оценки эффективности и для получения сведений.  
  
 `IndexBuildThreshold`  
 32-разрядное целочисленное свойство со знаком, задающее пороговое количество строк, ниже которого для секций не будут строиться индексы.  
  
 Значение по умолчанию для этого свойства составляет 4096 (строк).  
  
 `IndexFileInitEnabled`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MapFormatMask`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `RecordsReportGranularity`  
 32-разрядное целочисленное свойство со знаком, устанавливающее, как часто сервер записывает события трассировки во время обработки, в строках.  
  
 Значение этого свойства по умолчанию — 1 000, что означает, что событие трассировки записывается в журнал каждые 1 000 строк.  
  
 `ROLAPDimensionProcessingEffort`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="query"></a>Запрос  
 `AggregationsUseEnabled`  
 Логическое свойство, которое определяет, будут ли во время выполнения использоваться хранимые агрегаты. Это свойство позволяет отключить агрегаты без изменения статистической схемы и без повторной обработки в целях оценки производительности и получения сведений.  
  
 Значение этого свойства по умолчанию — True, то есть агрегаты включены.  
  
 `AllowSEFiltering`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `CalculationCacheRegistryMaxIterations`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `CalculationEvaluationPolicy`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ConvertDeletedToUnknown`  
 Логическое свойство, которое указывает, будут ли удаленные элементы измерения преобразованы в неизвестные элементы.  
  
 `CopyLinkedDataCacheAndRegistry`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataCacheRegistryMaxIterations`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DefaultDrillthroughMaxRows`  
 32-разрядное целочисленное свойство со знаком, которое указывает число строк, возвращаемых детализированным запросом.  
  
 Значение по умолчанию для этого свойства составляет 10 000 (строк).  
  
 `DimensionPropertyCacheSize`  
 Подписанное 32-разрядное целочисленное свойство, указывающее объем памяти (в байтах), используемой для сохранения в кэше тех элементов измерения, которые применяются в запросе.  
  
 Значение по умолчанию равно 4 000 000 байт (или 4 МБ) на одну иерархию атрибутов, на один активный запрос. Значение по умолчанию обеспечивает хорошо сбалансированный размер кэша для решений со стандартными иерархиями. Однако измерения с очень большим количеством элементов (которые исчисляются миллионами) или глубокие иерархии работают лучше, если увеличить это значение.  
  
 Последствия увеличение размера кэша.  
  
-   При предоставлении дополнительной памяти для кэша измерения растет стоимость использования памяти. Фактический объем применяемой памяти зависит от выполнения запроса. Не все запросы будут использовать допустимый максимум.  
  
     Обратите внимание, что объем памяти, используемый этими кэшами, считается несжимаемым и учитывается при вычислении значения **TotalMemoryLimit**.  
  
-   Затрагивает все базы данных на сервере. Свойство**DimensionPropertyCachesize** распространяется на весь сервер. Изменение этого свойства влияет на все базы данных, которые работают в этом экземпляре.  
  
 Способ оценки потребностей кэша измерения.  
  
1.  Начните с увеличения размера на значительную величину, чтобы определить, ведет ли увеличение размера кэша измерения к росту производительности. Например, на начальном этапе значение, заданное по умолчанию, можно удвоить.  
  
2.  Если улучшение производительности очевидно, постепенно уменьшайте это значение до тех пор, пока не будет найден баланс между производительностью и использованием памяти.  
  
 `ExpressNonEmptyUseEnabled`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `IgnoreNullRolapRows`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `IndexUseEnabled`  
 Логическое свойство, которое определяет, будут ли во время выполнения использоваться индексы. Это свойство служит для оценки эффективности и получения сведений.  
  
 `MapHandleAlgorithm`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MaxRolapOrConditions`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `UseCalculationCacheRegistry`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `UseDataCacheFreeLastPageMemory`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `UseDataCacheRegistry`  
 Логическое свойство, которое указывает, включен ли реестр кэша данных, где хранятся результаты запросов (но не вычисленные результаты).  
  
 `UseDataCacheRegistryHashTable`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `UseDataCacheRegistryMultiplyKey`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `UseDataSlice`  
 Логическое свойство, которое определяет, использовать ли срезы данных секции во время работы для оптимизации запросов. Это свойство служит для оценки эффективности и для получения сведений.  
  
 `UseMaterializedIterators`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `UseSinglePassForDimSecurityAutoExist`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `UseVBANet`  
 Логическое свойство, которое определяет, использовать ли для пользовательских функций сборку VBA .Net.  
  
 `CalculationPrefetchLocality\ ApplyIntersect`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `CalculationPrefetchLocality\ ApplySubtract`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `CalculationPrefetchLocality\ PrefetchLowerGranularities`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataCache\  CachedPageAlloc\ Income`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataCache\  CachedPageAlloc\ InitialBonus`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataCache\  CachedPageAlloc\ MaximumBalance`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataCache\  CachedPageAlloc\ MinimumBalance`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataCache\  CachedPageAlloc\ Tax`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataCache\CellStore\ Income`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataCache\CellStore\ InitialBonus`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataCache\CellStore\ MaximumBalance`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataCache\CellStore\ MinimumBalance`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataCache\CellStore\ Tax`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataCache\ MemoryModel \ Income`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataCache\ MemoryModel \ InitialBonus`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataCache\ MemoryModel \ MaximumBalance`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataCache\ MemoryModel \ MinimumBalance`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataCache\ MemoryModel\ Tax`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="jobs"></a>Задания  
 `ProcessAggregation\ MemoryModel\ Income`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ProcessAggregation\ MemoryModel\ InitialBonus`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ProcessAggregation\ MemoryModel\ MaximumBalance`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ProcessAggregation\ MemoryModel\ MinimumBalance`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ProcessAggregation\ MemoryModel\ Tax`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ProcessAggregation\ ProcessPartition\ Income`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ProcessAggregation\ ProcessPartition \ InitialBonus`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ProcessAggregation\ ProcessPartition \ MaximumBalance`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ProcessAggregation\ ProcessPartition \ MinimumBalance`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ProcessAggregation\ ProcessPartition \ Tax`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ProcessAggregation\ ProcessProperty\ Income`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ProcessAggregation\ ProcessProperty\ InitialBonus`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ProcessAggregation\ ProcessProperty\ MaximumBalance`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ProcessAggregation\ ProcessProperty\ MinimumBalance`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ProcessAggregation\ ProcessProperty\ Tax`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Настройка свойств сервера в службах Analysis Services](server-properties-in-analysis-services.md)   
 [Определение режима работы сервера экземпляра служб Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
