---
title: Разработка с помощью XMLA в Analysis Services | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, data mining
- commands [XML for Analysis]
- data mining [XML for Analysis]
- XMLA, data mining
- XML for Analysis, Analysis Services tasks
- XMLA, Analysis Services tasks
ms.assetid: 54445ee7-720c-4683-99a6-e75b3dcca904
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 27b143a9cc5c888c6e464d300d2ccfea114ef9bc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "80380685"
---
# <a name="developing-with-xmla-in-analysis-services"></a>Разработка с использованием XMLA в службах Analysis Services
  XML для аналитики (XMLA) — это XML-протокол, основанный на протоколе SOAP и специально предназначенный для обеспечения унифицированного доступа к данным в любом стандартном многомерном источнике данных, доступном через HTTP-соединение. В службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA является единственным протоколом для связи с клиентскими приложениями. Все клиентские библиотеки, поддерживаемые службами Analysis Services, в конечном итоге формируют запросы и ответы по протоколу XMLA.  
  
 С помощью XMLA разработчик может интегрировать клиентское приложение со службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], не создавая зависимости от платформы .NET Framework и COM-интерфейсов. Требования приложений, в том числе касающиеся размещения на широком диапазоне платформ, можно выполнить с помощью XMLA и HTTP-соединения со службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] полностью соответствуют спецификации XMLA 1.1 и расширяют ее для поддержки описания данных, обработки данных и управления данными. Расширения служб Analysis Services называются языком ASSL. Совместное использование XMLA и ASSL расширяет набор возможностей XMLA. Дополнительные сведения о языке ASSL см. в разделе [Разработка с использованием Analysis Services языка сценариев &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Управление соединениями и сеансами (XMLA)](managing-connections-and-sessions-xmla.md)|Описывает соединение с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и управление сеансами и поддержкой состояния в XML для аналитики.|  
|[Обработка ошибок и предупреждений &#40;XMLA&#41;](handling-errors-and-warnings-xmla.md)|Описывает, каким образом службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] возвращают сведения об ошибках и предупреждениях для методов и команд XML для аналитики.|  
|[Определение и идентификация объектов &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)|Описывает идентификаторы и ссылки объектов, а также их использование в командах XML для аналитики.|  
|[Управление транзакциями &#40;XMLA&#41;](managing-transactions-xmla.md)|Сведения об использовании команд [BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla), [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla)и [RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla) для явного определения и управления транзакцией в текущем сеансе XMLA.|  
|[Отмена команд &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/canceling-commands-xmla.md)|Описание использования команды [Cancel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla)для отмены команд, сеансов и соединений в XMLA.|  
|[Выполнение пакетных операций &#40;XMLA&#41;](performing-batch-operations-xmla.md)|Описывает использование команды [Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) для выполнения нескольких команд XMLA в последовательном или параллельном режиме в пределах одной транзакции или в виде отдельных транзакций с помощью одного метода [EXECUTE](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) XMLA.|  
|[Создание и изменение объектов &#40;XMLA&#41;](creating-and-altering-objects-xmla.md)|Описывает использование команд [CREATE](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla), [ALTER](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)и [Delete](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla) вместе со Analysis Services элементами языка сценариев (ASSL) для определения, изменения или удаления объектов из [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляра.|  
|[Блокировка и разблокировка баз данных &#40;XMLA&#41;](locking-and-unlocking-databases-xmla.md)|Сведения об использовании команд [Lock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) и [Unlock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) для блокировки и разблокировки [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных.|  
|[Обработка объектов (XMLA)](processing-objects-xmla.md)|Описывает использование команды [Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) для обработки [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] объекта.|  
|[Слияние секций &#40;XMLA&#41;](merging-partitions-xmla.md)|Описывает использование команды [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) для слияния секций в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляре.|  
|[Проектирование агрегатов &#40;XMLA&#41;](designing-aggregations-xmla.md)|Описывает использование команды [DesignAggregations](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/designaggregations-element-xmla) в итеративном или пакетном режиме для проектирования агрегатов для статистической схемы в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Резервное копирование, восстановление и синхронизация баз данных (XMLA)](backing-up-restoring-and-synchronizing-databases-xmla.md)|Описывает использование команд [BACKUP](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla) и [RESTORE](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla) для резервного копирования и восстановления [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных из файла резервной копии.<br /><br /> Также описывается использование команды [Synchronize](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla) для синхронизации [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных с существующей базой данных в том же экземпляре или на другом экземпляре.|  
|[Вставка, обновление и удаление элементов &#40;XMLA&#41;](inserting-updating-and-dropping-members-xmla.md)|Описывает использование команд [INSERT](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla), [Update](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)и [Drop](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla) для добавления, изменения или удаления элементов из измерения, доступного для записи.|  
|[Обновление ячеек &#40;XMLA&#41;](updating-cells-xmla.md)|Описывает использование команды [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) для изменения значений ячеек в секции, доступной для записи.|  
|[Управление кэшами &#40;XMLA&#41;](managing-caches-xmla.md)|Сведения об использовании команды [ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) для очистки кэшей [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] объектов.|  
|[Мониторинг трассировок &#40;XMLA&#41;](monitoring-traces-xmla.md)|Описывает использование команды [Subscribe](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/subscribe-element-xmla) для подписки и отслеживания существующей трассировки в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляре служб.|  
  
## <a name="data-mining-with-xmla"></a>Интеллектуальный анализ данных в XML для аналитики  
 Протокол XML для аналитики полностью поддерживает наборы строк схемы интеллектуального анализа данных. Эти наборы строк предоставляют сведения для запроса моделей интеллектуального анализа данных с помощью метода [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) . Дополнительные сведения о наборах строк схемы интеллектуального анализа данных см. в разделе [наборы строк схемы интеллектуального анализа данных](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets) . 
  
 Дополнительные сведения о DMX см. в разделе [расширения интеллектуального анализа данных &#40;Справочник по DMX&#41;](/sql/dmx/data-mining-extensions-dmx-reference).  
  
## <a name="namespace-and-schema"></a>Пространство имен и схема  
  
### <a name="namespace"></a>Пространство имен  
 Схема, определенная в этой спецификации, использует пространство `https://schemas.microsoft.com/AnalysisServices/2003/Engine` имен XML и стандартную аббревиатуру "DDL".  
  
### <a name="schema"></a>схема  
 В основе определения схемы XSD для языка определения объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] лежат определение элементов схемы и иерархии, приведенное в этом разделе.  
  
## <a name="extensibility"></a>Расширение среды  
 Расширяемость схемы языка определения объектов обеспечивается за счет элемента `Annotation`, который включается во все объекты. Этот элемент может содержать любой допустимый код XML из любого пространства имен XML (отличного от целевого пространства имен, определяющего DDL) с соблюдением следующих правил.  
  
-   В XML-коде могут содержаться только элементы.  
  
-   Каждый элемент должен иметь уникальное имя. Рекомендуется, чтобы значение `Name` ссылалось на целевое пространство имен.  
  
 Эти правила налагаются с тем, чтобы можно было предоставлять доступ к содержимому тега `Annotation`, как к набору пар «Имя/Значение», через объекты DSO 9.0.  
  
 Если комментарии и пробелы в теге `Annotation` не были заключены в дочерний элемент, то они могут не сохраниться. Кроме того, все элементы должны быть доступными для чтения и записи; элементы, доступные только для чтения, пропускаются.  
  
 Схема языка определения объектов является закрытой; под этим подразумевается то, что сервер не позволяет производить замену производных типов для элементов, определенных в схеме. Поэтому сервер принимает только набор элементов, определенных в схеме, и не принимает другие элементы или атрибуты. Обнаружение неизвестного элемента вынуждает ядро служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] активизировать ошибку.  
  
## <a name="see-also"></a>См. также:  
 [Разработка с помощью Analysis Services языка сценариев &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Основные сведения об архитектуре Microsoft OLAP](../multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
