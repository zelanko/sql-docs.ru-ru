---
title: Разработка с использованием XMLA в службах Analysis Services | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 99ccf53ab36d68ab0b03fa042d08e00d65703228
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63265088"
---
# <a name="developing-with-xmla-in-analysis-services"></a>Разработка с использованием XMLA в службах Analysis Services
  XML для аналитики (XMLA) — это XML-протокол, основанный на протоколе SOAP и специально предназначенный для обеспечения унифицированного доступа к данным в любом стандартном многомерном источнике данных, доступном через HTTP-соединение. В службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA является единственным протоколом для связи с клиентскими приложениями. Все клиентские библиотеки, поддерживаемые службами Analysis Services, в конечном итоге формируют запросы и ответы по протоколу XMLA.  
  
 С помощью XMLA разработчик может интегрировать клиентское приложение со службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], не создавая зависимости от платформы .NET Framework и COM-интерфейсов. Требования приложений, в том числе касающиеся размещения на широком диапазоне платформ, можно выполнить с помощью XMLA и HTTP-соединения со службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] полностью соответствуют спецификации XMLA 1.1 и расширяют ее для поддержки описания данных, обработки данных и управления данными. Расширения служб Analysis Services называются языком ASSL. Совместное использование XMLA и ASSL расширяет набор возможностей XMLA. Дополнительные сведения о ASSL см. в разделе [разработка с использованием язык сценариев служб Analysis Services &#40;ASSL&#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Управление соединениями и сеансами &#40;XML для Аналитики&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)|Описывает соединение с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и управление сеансами и поддержкой состояния в XML для аналитики.|  
|[Обработка ошибок и предупреждений &#40;XML для Аналитики&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/handling-errors-and-warnings-xmla.md)|Описывает, каким образом службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] возвращают сведения об ошибках и предупреждениях для методов и команд XML для аналитики.|  
|[Определение и идентификация объектов &#40;XML для Аналитики&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/defining-and-identifying-objects-xmla.md)|Описывает идентификаторы и ссылки объектов, а также их использование в командах XML для аналитики.|  
|[Управление транзакциями &#40;XML для Аналитики&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-transactions-xmla.md)|Подробное описание использования [BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla), [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla), и [RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla) команды, чтобы явным образом определять и управлять ими транзакцию в текущем XML для Аналитики сеанс.|  
|[Отмена команд &#40;XML для Аналитики&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/canceling-commands-xmla.md)|Описывает использование [отменить](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla)команду для отмены команд, сеансов и соединений в XML для Аналитики.|  
|[Выполнение пакетных операций &#40;XML для Аналитики&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md)|Описывает использование [пакета](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) команду для запуска нескольких XML для Аналитики команды, последовательно или параллельно, как в той же транзакции, так и отдельные транзакции, при помощи только одного [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) метод.|  
|[Создание и изменение объектов &#40;XML для Аналитики&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/creating-and-altering-objects-xmla.md)|Описывает использование [создать](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla), [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla), и [удалить](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla) команды, а также элементы языка сценариев служб Analysis Services (ASSL) для определения, изменения или удаления объекты из [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляра.|  
|[Блокировка и снятие блокировки баз данных &#40;XML для Аналитики&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/locking-and-unlocking-databases-xmla.md)|Подробное описание использования [блокировки](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) и [Unlock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) команды, чтобы блокировать и разблокировать [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных.|  
|[Обработка объектов (XMLA)](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/processing-objects-xmla.md)|Описывает использование [процесс](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) команду к процессу [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] объекта.|  
|[Слияние секций &#40;XML для Аналитики&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/merging-partitions-xmla.md)|Описывает использование [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) команды для слияния секций в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляра.|  
|[Проектирование агрегатов &#40;XML для Аналитики&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/designing-aggregations-xmla.md)|Описывает использование [DesignAggregations](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/designaggregations-element-xmla) команды, в последовательном или пакетном режиме для проектирования агрегатов для статистических схем в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Резервное копирование, восстановление и синхронизация баз данных (XMLA)](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)|Описывает использование [резервного копирования](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla) и [восстановить](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla) команды для резервного копирования и восстановления [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных из файла резервной копии.<br /><br /> Также описывается использование [Synchronize](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla) команду, чтобы синхронизировать [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных с помощью существующей базы данных в одном экземпляре или на другом экземпляре.|  
|[Вставка, обновление и удаление элементов &#40;XML для Аналитики&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md)|Описывает использование [вставить](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla), [обновление](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla), и [Drop](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla) команды, чтобы добавить, изменить или удалить элементы из измерения, доступного для записи.|  
|[Обновление ячеек &#40;XML для Аналитики&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md)|Описывает использование [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) команду, чтобы изменить значения ячеек в секции, доступные для записи.|  
|[Управление кэшами &#40;XML для Аналитики&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-caches-xmla.md)|Подробное описание использования [ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) команду, чтобы очистить кэш [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] объектов.|  
|[Наблюдение за трассировками &#40;XML для Аналитики&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/monitoring-traces-xmla.md)|Описывает использование [Subscribe](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/subscribe-element-xmla) команду, чтобы подписаться на и наблюдения за существующей трассировки на [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляра.|  
  
## <a name="data-mining-with-xmla"></a>Интеллектуальный анализ данных в XML для аналитики  
 Протокол XML для аналитики полностью поддерживает наборы строк схемы интеллектуального анализа данных. Эти наборы строк содержат сведения для выполнения запросов к модели интеллектуального анализа данных с использованием [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) метод. Дополнительные сведения о наборах строк схемы интеллектуального анализа данных см. в разделе [наборы строк схемы интеллектуального анализа данных](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets)  
  
 Дополнительные сведения о расширениях интеллектуального анализа данных, см. в разделе [расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; ссылку](../../dmx/data-mining-extensions-dmx-reference.md).  
  
## <a name="namespace-and-schema"></a>Пространство имен и схема  
  
### <a name="namespace"></a>Пространство имен  
 Схемы, определенной в данной спецификации использует пространство имен XML `http://schemas.microsoft.com/AnalysisServices/2003/Engine` и стандартное сокращение «DDL».  
  
### <a name="schema"></a>схема  
 В основе определения схемы XSD для языка определения объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] лежат определение элементов схемы и иерархии, приведенное в этом разделе.  
  
## <a name="extensibility"></a>Расширение среды  
 Расширяемость схемы языка определения объектов обеспечивается с помощью параметра **заметки** элемент, который включается во все объекты. Этот элемент может содержать любой допустимый код XML из любого пространства имен XML (отличного от целевого пространства имен, определяющего DDL) с соблюдением следующих правил.  
  
-   В XML-коде могут содержаться только элементы.  
  
-   Каждый элемент должен иметь уникальное имя. Рекомендуется значение **имя** ссылаются на целевое пространство имен.  
  
 Эти правила применяются, чтобы содержимое **заметки** тега может быть предоставлен как набор пар "имя-значение" через принятия решений поддержки объектов DSO 9.0.  
  
 Комментарии и пробелы в **заметки** тег, который не заключаются в дочерний элемент не будет сохранен. Кроме того, все элементы должны быть доступными для чтения и записи; элементы, доступные только для чтения, пропускаются.  
  
 Схема языка определения объектов является закрытой; под этим подразумевается то, что сервер не позволяет производить замену производных типов для элементов, определенных в схеме. Поэтому сервер принимает только набор элементов, определенных в схеме, и не принимает другие элементы или атрибуты. Обнаружение неизвестного элемента вынуждает ядро служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] активизировать ошибку.  
  
## <a name="see-also"></a>См. также  
 [Разработка на языке ASSL (язык ASSL)](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Основные сведения об архитектуре Microsoft OLAP](../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
