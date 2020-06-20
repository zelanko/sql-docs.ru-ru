---
title: Задача потока данных | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataflowtask.f1
helpviewer_keywords:
- data flow task [Integration Services]
- performance [Integration Services]
- data flow [Integration Services], performance
- data flow [Integration Services], Data Flow task
- Integration Services, performance
ms.assetid: c27555c4-208c-43c8-b511-a4de2a8a3344
author: janinezhang
ms.author: janinez
ms.openlocfilehash: ff5c519fbe9bf8096807962a939677b3a5d58cc5
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84919611"
---
# <a name="data-flow-task"></a>Задача потока данных
  В состав задачи потока данных входит подсистема обработки потока данных, перемещающая данные между источником и назначением и позволяющая пользователю преобразовывать, очищать и изменять данные в процессе перемещения. Добавление задачи потока данных в поток управления пакета позволяет пакету извлекать, преобразовывать и загружать данные.  
  
 Поток данных включает в себя по меньшей мере один компонент потока данных, но обычно представляет собой набор соединенных между собой компонентов потока данных: источников, извлекающих данные, преобразований, которые изменяют, направляют или создают сводку данных и назначений, загружающих данные.  
  
 Во время выполнения задача потока данных создает план выполнения в соответствии с потоком данных, а подсистема обработки потока данных выполняет этот план. Возможно создание задачи потока данных, не содержащей потока данных, но задача будет выполнена, только если она включает по меньшей мере один поток данных.  
  
 Чтобы выполнить массовую вставку из текстовых файлов в базу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вместо задачи потока данных и самого потока данных можно использовать задачу «Массовая вставка». Однако задача «Массовая вставка» не может преобразовывать данные. Дополнительные сведения см. в статье [Bulk Insert Task](bulk-insert-task.md).  
  
## <a name="multiple-flows"></a>Несколько потоков  
 Задача потока данных может включать несколько потоков данных. Если задача копирует несколько наборов данных и порядок, в котором производится копирование, неважен, может оказаться полезным включить в задачу потока данных несколько потоков данных. Например, можно включить пять потоков данных, каждый из которых копирует данные из неструктурированного файла в другую таблицу измерения хранилища данных со схемой «звезда».  
  
 Однако, если имеется несколько потоков данных в пределах одной задачи потока данных, порядок выполнения определяется подсистемой обработки потока данных. Таким образом, если порядок важен, пакет должен использовать несколько задач потока данных, каждая из которых содержит один поток данных. При этом можно будет задать ограничение очередностью для управления очередностью выполнения задач.  
  
 На следующей диаграмме показана задача потока данных с несколькими потоками данных.  
  
 ![Потоки данных](../media/mw-dts-09.gif "Потоки данных")  
  
## <a name="log-entries"></a>Записи журнала  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] предоставляют несколько событий журнала, которые доступны всем задачам. [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] предоставляют также пользовательские записи журнала. Дополнительные сведения см. в разделах [Ведение журналов в службах Integration Services (SSIS)](../performance/integration-services-ssis-logging.md) и [Пользовательские сообщения для ведения журнала](../custom-messages-for-logging.md). Задача потока данных содержит следующие пользовательские записи журнала.  
  
|Запись журнала|Description|  
|---------------|-----------------|  
|`BufferSizeTuning`|Указывает, что задача потока данных изменила размер буфера. Эта запись журнала описывает причины изменения размера и фиксирует новый временный размер буфера.|  
|`OnPipelinePostEndOfRowset`|Означает, что компонент получил сигнал конца набора строк, который устанавливается при последнем вызове метода `ProcessInput`. Запись делается для каждого компонента в потоке данных, который обрабатывает ввод. Запись включает имя компонента.|  
|`OnPipelinePostPrimeOutput`|Указывает, что компонент завершил последний вызов метода `PrimeOutput`. В зависимости от потока данных, возможно формирование нескольких записей в журнале. Если компонент является источником, эта запись журнала означает, что компонент завершил обработку строк.|  
|`OnPipelinePreEndOfRowset`|Показывает, что компонент уже готов получить сигнал конца набора строк, который устанавливается при последнем вызове метода `ProcessInput`. Запись делается для каждого компонента в потоке данных, который обрабатывает ввод. Запись включает имя компонента.|  
|`OnPipelinePrePrimeOutput`|Показывает, что компонент готов получить свой вызов из метода `PrimeOutput`. В зависимости от потока данных, возможно формирование нескольких записей в журнале.|  
|`OnPipelineRowsSent`|Сообщает количество строк, предоставленных входу компонента с помощью вызова метода `ProcessInput`. Запись журнала включает имя компонента.|  
|`PipelineBufferLeak`|Предоставляет сведения обо всех компонентах, которые удерживают буферы от уничтожения после того, как диспетчер буферов завершил свое выполнение. Если буфер все еще существует, ресурсы буферов не освобождаются и могут вызвать утечку памяти. Запись журнала предоставляет имя компонента и идентификатор буфера.|  
|`PipelineComponentTime`|Сообщает о времени (в миллисекундах), которое компонент тратит на каждый из пяти основных шагов обработки — Validate, PreExecute, PostExecute, ProcessInput и ProcessOutput.|  
|`PipelineExecutionPlan`|Сообщает о плане выполнения потока данных. План выполнения предоставляет сведения о том, как буферы будут отсылаться компонентам. Эти сведения в сочетании с записью журнала PipelineExecutionTrees описывают работу задачи потока данных.|  
|`PipelineExecutionTrees`|Сообщает о дереве выполнения макета в потоке данных. Диспетчер ядра подсистемы обработки потока данных использует деревья для построения плана выполнения потока данных.|  
|`PipelineInitialization`|Предоставляет сведения об инициализации задачи. Эти сведения включают каталоги, используемые для временного хранения данных большого объема типа BLOB, размер буфера по умолчанию и количество строк в буфере. В зависимости от настройки задачи потока данных, возможно формирование нескольких записей в журнале.|  
  
 Эти записи журнала предоставляют достаточные сведения об исполнении задачи потока данных при каждом запуске пакета. Если пакеты запускаются периодически, то можно получить сведения, которые со временем предоставят важные данные предыстории о выполнении задачи, о вопросах, влияющих на производительность, и об объемах обрабатываемых задачей данных.  
  
 Дополнительные сведения о об использовании таких записей журнала для наблюдения и повышения производительности потока данных см. в следующих разделах.  
  
-   [Счетчики производительности](../performance/performance-counters.md)  
  
-   [Возможности для повышения производительности потока данных](../data-flow/data-flow-performance-features.md)  
  
### <a name="sample-messages-from-a-data-flow-task"></a>Образцы сообщений от задачи потока данных  
 В следующей таблице приведен список образцов сообщений для записей журнала в очень простом пакете. Пакет использует источник данных «OLE DB» для извлечения данных из таблицы, преобразование «Сортировка» для сортировки данных и назначение «OLE DB» для записи данных в другую таблицу.  
  
|Запись журнала|Сообщения|  
|---------------|--------------|  
|`BufferSizeTuning`|`Rows in buffer type 0 would cause a buffer size greater than the configured maximum. There will be only 9637 rows in buffers of this type.`<br /><br /> `Rows in buffer type 2 would cause a buffer size greater than the configured maximum. There will be only 9497 rows in buffers of this type.`<br /><br /> `Rows in buffer type 3 would cause a buffer size greater than the configured maximum. There will be only 9497 rows in buffers of this type.`|  
|`OnPipelinePostEndOfRowset`|`A component will be given the end of rowset signal. : 1180 : Sort : 1181 : Sort Input`<br /><br /> `A component will be given the end of rowset signal. : 1291 : OLE DB Destination : 1304 : OLE DB Destination Input`|  
|`OnPipelinePostPrimeOutput`|`A component has returned from its PrimeOutput call. : 1180 : Sort`<br /><br /> `A component has returned from its PrimeOutput call. : 1 : OLE DB Source`|  
|`OnPipelinePreEndOfRowset`|`A component has finished processing all of its rows. : 1180 : Sort : 1181 : Sort Input`<br /><br /> `A component has finished processing all of its rows. : 1291 : OLE DB Destination : 1304 : OLE DB Destination Input`|  
|`OnPipelinePrePrimeOutput`|`PrimeOutput will be called on a component. : 1180 : Sort`<br /><br /> `PrimeOutput will be called on a component. : 1 : OLE DB Source`|  
|`OnPipelineRowsSent`|`Rows were provided to a data flow component as input. :  : 1185 : OLE DB Source Output : 1180 : Sort : 1181 : Sort Input : 76`<br /><br /> `Rows were provided to a data flow component as input. :  : 1308 : Sort Output : 1291 : OLE DB Destination : 1304 : OLE DB Destination Input : 76`|  
|`PipelineComponentTime`|`The component "Calculate LineItemTotalCost" (3522) spent 356 milliseconds in ProcessInput.`<br /><br /> `The component "Sum Quantity and LineItemTotalCost" (3619) spent 79 milliseconds in ProcessInput.`<br /><br /> `The component "Calculate Average Cost" (3662) spent 16 milliseconds in ProcessInput.`<br /><br /> `The component "Sort by ProductID" (3717) spent 125 milliseconds in ProcessInput.`<br /><br /> `The component "Load Data" (3773) spent 0 milliseconds in ProcessInput.`<br /><br /> `The component "Extract Data" (3869) spent 688 milliseconds in PrimeOutput filling buffers on output "OLE DB Source Output" (3879).`<br /><br /> `The component "Sum Quantity and LineItemTotalCost" (3619) spent 141 milliseconds in PrimeOutput filling buffers on output "Aggregate Output 1" (3621).`<br /><br /> `The component "Sort by ProductID" (3717) spent 16 milliseconds in PrimeOutput filling buffers on output "Sort Output" (3719).`|  
|`PipelineExecutionPlan`|`SourceThread0`<br /><br /> `Drives: 1`<br /><br /> `Influences: 1180 1291`<br /><br /> `Output Work List`<br /><br /> `CreatePrimeBuffer of type 1 for output ID 11.`<br /><br /> `SetBufferListener: "WorkThread0" for input ID 1181`<br /><br /> `CreatePrimeBuffer of type 3 for output ID 12.`<br /><br /> `CallPrimeOutput on component "OLE DB Source" (1)`<br /><br /> `End Output Work List`<br /><br /> `End SourceThread0`<br /><br /> `WorkThread0`<br /><br /> `Drives: 1180`<br /><br /> `Influences: 1180 1291`<br /><br /> `Input Work list, input ID 1181 (1 EORs Expected)`<br /><br /> `CallProcessInput on input ID 1181 on component "Sort" (1180) for view type 2`<br /><br /> `End Input Work list for input 1181`<br /><br /> `Output Work List`<br /><br /> `CreatePrimeBuffer of type 4 for output ID 1182.`<br /><br /> `SetBufferListener: "WorkThread1" for input ID 1304`<br /><br /> `CallPrimeOutput on component "Sort" (1180)`<br /><br /> `End Output Work List`<br /><br /> `End WorkThread0`<br /><br /> `WorkThread1`<br /><br /> `Drives: 1291`<br /><br /> `Influences: 1291`<br /><br /> `Input Work list, input ID 1304 (1 EORs Expected)`<br /><br /> `CallProcessInput on input ID 1304 on component "OLE DB Destination" (1291) for view type 5`<br /><br /> `End Input Work list for input 1304`<br /><br /> `Output Work List`<br /><br /> `End Output Work List`<br /><br /> `End WorkThread1`|  
|`PipelineExecutionTrees`|`begin execution tree 0`<br /><br /> `output "OLE DB Source Output" (11)`<br /><br /> `input "Sort Input" (1181)`<br /><br /> `end execution tree 0`<br /><br /> `begin execution tree 1`<br /><br /> `output "OLE DB Source Error Output" (12)`<br /><br /> `end execution tree 1`<br /><br /> `begin execution tree 2`<br /><br /> `output "Sort Output" (1182)`<br /><br /> `input "OLE DB Destination Input" (1304)`<br /><br /> `output "OLE DB Destination Error Output" (1305)`<br /><br /> `end execution tree 2`|  
|`PipelineInitialization`|`No temporary BLOB data storage locations were provided. The buffer manager will consider the directories in the TEMP and TMP environment variables.`<br /><br /> `The default buffer size is 10485760 bytes.`<br /><br /> `Buffers will have 10000 rows by default`<br /><br /> `The data flow will not remove unused components because its RunInOptimizedMode property is set to false.`|  
  
 Многие регистрируемые события оставляют по нескольку записей, а сообщения для некоторых записей журнала содержат сложные данные. Чтобы упростить понимание и взаимодействие содержимого сложных сообщений, можно провести синтаксический анализ текста сообщения. В зависимости от положения журналов можно использовать инструкции Transact-SQL или компонент скрипта для разделения сложного текста по столбцам или преобразования в другие форматы, которые окажутся более удобными.  
  
 Например, следующая таблица содержит сообщение «В качестве входных данных компоненту потока данных были предоставлены строки. :  : 1185 : выход источника OLE DB : 1180 : сортировка : 1181 : вход сортировки : 76", разделенное на столбцы. Сообщение записано событием `OnPipelineRowsSent`, когда строки были отправлены из источника «OLE DB» в преобразование «Сортировка».  
  
|Столбец|Описание|Значение|  
|------------|-----------------|-----------|  
|**PathID**|Значение свойства `ID` пути между источником «OLE DB» и преобразованием «Сортировка».|1185|  
|**PathName**|Значение свойства `Name` пути.|Выход данных источника «OLE DB»|  
|**ComponentID**|Значение свойства `ID` преобразования «Сортировка».|1180|  
|**ComponentName**|Значение свойства `Name` преобразования «Сортировка».|Сортировка|  
|**InputID**|Значение свойства `ID` входных данных для преобразования «Сортировка».|1181|  
|**InputName**|Значение свойства `Name` входных данных для преобразования «Сортировка».|Вход сортировки|  
|**ровссент**|Количество строк, отправленных в качестве входных данных на преобразование «Сортировка».|76|  
  
## <a name="configuration-of-the-data-flow-task"></a>Настройка задачи «Поток данных»  
 Задать свойства можно в окне **Свойства** или программно.  
  
 Дополнительные сведения о настройке этих свойств в окне **Свойства** см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-data-flow-task"></a>Настройка задачи «Поток данных» программными средствами  
 Дополнительные сведения о программном добавлении задачи потока данных к пакету и установке свойств потока данных, см. в следующем разделе:  
  
-   [Добавление задачи потока данных программным образом](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-content"></a>См. также  
 Видеоматериал [Распространитель сбалансированных данных](https://go.microsoft.com/fwlink/?LinkID=226278&clcid=0x409)на узле Technet.microsoft.com (на английском языке).  
  
  
