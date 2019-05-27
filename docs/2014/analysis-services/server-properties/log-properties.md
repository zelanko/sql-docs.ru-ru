---
title: Вход свойства | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- QueryLogFileSize property
- QueryLogTableName property
- TraceBackgroundDistributionPeriod property
- TraceMaxRowsetSize property
- NullKeyConvertedToUnknown property
- CrashReportsFolder property
- TraceDefinitionFile property
- SQLDumperFlagsOn property
- KeyErrorLimit property
- SnapshotDefinitionFile property
- MinidumpErrorList property
- ErrorLogFileName property
- KeyDuplicate property
- IgnoreDataTruncation property
- logs [Analysis Services]
- Enabled property
- FileSizeMB property
- TraceFileWriteTrailerPeriod property
- TraceQueryResponseTextChunkSize property
- File property
- FileBufferSize property
- TraceRowsetBackgroundFlushPeriod property
- ErrorLogFileSize property
- TraceRequestParameters property
- KeyErrorLimitAction property
- CreateQueryLogTable property
- LogDir property
- TraceBackgroundFlushPeriod property
- TraceFileBufferSize property
- SQLDumperFlagsOff property
- QueryLogConnectionString property
- KeyNotFound property
- KeyErrorLogFile property
- TraceReportFQDN property
- KeyErrorAction property
- QueryLogFileName property
- MessageLogs property
- MiniDumpFlagsOn property
- SnapshotFrequencySec property
- QueryLogSampling property
- CreateAndSendCrashReports property
- LogDurationSec property
ms.assetid: 33fd90ee-cead-48f0-8ff9-9b458994c766
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 81653d9b93a7dc8ec71a88e70cee8b2d68f33a8e
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66068918"
---
# <a name="log-properties"></a>Свойства журнала
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают свойства сервера журналов, список которых приведен в следующих таблицах. Дополнительные сведения о дополнительных свойствах сервера и об их настройке см. в разделе [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
## <a name="general"></a>Общие  
 `File`  
 Строковое свойство, идентифицирующее имя файла журнала сервера. Данное свойство применяется только в том случае, когда для ведения журнала используется дисковый файл, а не таблица базы данных (настройка по умолчанию).  
  
 Значение этого свойства по умолчанию равно msmdsrv.log.  
  
 `FileBufferSize`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MessageLogs`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="error-log"></a>Журнал ошибок  
 Эти свойства можно задать на уровне экземпляра сервера, чтобы изменить значения по умолчанию для конфигурации обработки ошибок, которые применяются в других средствах и конструкторах. См. в разделе [конфигурации ошибок для кубов, секций и обработка измерения &#40;службы SSAS — многомерные&#41; ](../multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md) и <xref:Microsoft.AnalysisServices.MiningStructure.ErrorConfiguration%2A> Дополнительные сведения.  
  
 **ErrorLog\ErrorLogFileName**  
 Свойство, используемое в качестве значения по умолчанию во время выполнения операции обработки сервером.  
  
 **ErrorLog\ErrorLogFileSize**  
 Свойство, используемое в качестве значения по умолчанию во время выполнения операции обработки сервером.  
  
 **ErrorLog\KeyErrorAction**  
 Задает действие, которое выполняет сервер при возникновении ошибки `KeyNotFound`. Допустимые действия для этой ошибки:  
  
-   `ConvertToUnknown` указывает, что сервер должен выделить ключевое значение ошибки неизвестному элементу.  
  
-   `DiscardRecord` указывает, что сервер должен исключить запись.  
  
 **ErrorLog\KeyErrorLogFile**  
 Это определяемое пользователем имя файла должно иметь расширение LOG и находиться в папке, для которой учетная запись службы имеет разрешения на чтение и запись. Файл журнала будет содержать только ошибки, возникшие во время обработки. Для сбора более подробной информации воспользуйтесь средством «черный ящик».  
  
 **ErrorLog\KeyErrorLimit**  
 Максимальное число ошибок целостности данных, допустимых для сервера, прежде чем он остановит обработку. Значение -1 указывает, что предел не установлен. Значение по умолчанию — 0, т. е. обработка останавливается при первой ошибке. Также можно задать целое число.  
  
 **ErrorLog\KeyErrorLimitAction**  
 Определяет действие, которое выполняет сервер, когда количество ошибок ключа достигает верхней границы. Допустимые ответы к данному действию:  
  
-   `StopProcessing` предписывает серверу остановить обработку при достижении предельного количества ошибок.  
  
-   `StopLogging` предписывает серверу остановить регистрацию ошибок при достижении предельного количества ошибок, но продолжить обработку.  
  
 **ErrorLog\ LogErrorTypes\KeyNotFound**  
 Задает действие, которое выполняет сервер при возникновении ошибки `KeyNotFound`. Допустимые действия для этой ошибки:  
  
-   `IgnoreError` указывает, что сервер должен продолжить обработку, не записывая ошибку в журнал и не учитывая ее при подсчете предельного количества ошибок ключа. Пропуск данной ошибки просто разрешает продолжение обработки без увеличения количества ошибок и вывода ошибки на экран или в файл журнала. Рассматриваемая запись имеет нарушение целостности данных и не может быть добавлена в базу данных. Запись или будет пропущена, или будет добавлена в неизвестный элемент, что определяется свойством `KeyErrorAction`.  
  
-   `ReportAndContinue` предписывает серверу зарегистрировать ошибку в журнале, учесть ее при подсчете предельного количества ошибок ключа и продолжить обработку. Запись, вызвавшая ошибку, пропускается или преобразуется в неизвестный элемент.  
  
-   `ReportAndStop` предписывает серверу немедленно прервать обработку и зарегистрировать ошибку в журнале вне зависимости от предельного количества ошибок ключа. Запись, вызвавшая ошибку, пропускается или преобразуется в неизвестный элемент.  
  
 **ErrorLog\ LogErrorTypes\KeyDuplicate**  
 Определяет действие, выполняемое сервером при обнаружении повторяющегося ключа. Допустимые значения: `IgnoreError`, чтобы продолжить обработку, как будто ошибки не было, `ReportAndContinue` для регистрации ошибки и продолжения обработки и `ReportAndStop` для регистрации ошибки и немедленного прерывания обработки, даже если количество ошибок ниже предельного количества ошибок.  
  
 **ErrorLog\ LogErrorTypes\NullKeyConvertedToUnknown**  
 Указывает действие, выполняемое сервером, когда ключ NULL преобразован в неизвестный элемент. Допустимые значения: `IgnoreError`, чтобы продолжить обработку, как будто ошибки не было, `ReportAndContinue` для регистрации ошибки и продолжения обработки и `ReportAndStop` для регистрации ошибки и немедленного прерывания обработки, даже если количество ошибок ниже предельного количества ошибок.  
  
 **ErrorLog\ LogErrorTypes\NullKeyNotAllowed**  
 Указывает действие, выполняемое сервером, когда для `NullProcessing` задается значение `Error` (в атрибуте измерения). Если значение NULL недопустимо для данного атрибута, возникает ошибка. Это свойство конфигурации по обработке ошибок формирует следующий шаг — сообщить об ошибке и продолжить обработку до тех пор, пока не будет достигнуто предельное количество ошибок. Допустимые значения: `IgnoreError`, чтобы продолжить обработку, как будто ошибки не было, `ReportAndContinue` для регистрации ошибки и продолжения обработки и `ReportAndStop` для регистрации ошибки и немедленного прерывания обработки, даже если количество ошибок ниже предельного количества ошибок.  
  
 **ErrorLog\ LogErrorTypes\CalculationError**  
 Свойство, используемое в качестве значения по умолчанию во время выполнения операции обработки сервером.  
  
 **ErrorLog\IgnoreDataTruncation**  
 Свойство, используемое в качестве значения по умолчанию во время выполнения операции обработки сервером.  
  
## <a name="exception"></a>Исключение  
 **Exception\CreateAndSendCrashReports**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Exception\CrashReportsFolder**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Exception\SQLDumperFlagsOn**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Exception\SQLDumperFlagsOff**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Exception\MiniDumpFlagsOn**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Exception\MinidumpErrorList**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="flight-recorder"></a>«Черный ящик»  
 **FlightRecorder\Enabled**  
 Логическое свойство, указывающее, используется ли функция «черного ящика».  
  
 **FlightRecorder\FileSizeMB**  
 Свойство с 32-разрядным целочисленным значением со знаком, определяющее размер (в мегабайтах) дискового файла «черного ящика».  
  
 **FlightRecorder\LogDurationSec**  
 Свойство с 32-разрядным целочисленным значением со знаком, определяющее частоту (в секундах), с которой «черный ящик» переключается на файл продолжения.  
  
 **FlightRecorder\SnapshotDefinitionFile**  
 Строковое свойство, определяющее имя файла определения моментального снимка, содержащего команды обнаружения, выдаваемые серверу при создании моментального снимка.  
  
 Значением по умолчанию для этого свойства является пустая строка, что соответствует имени файла FlightRecorderSnapshotDef.xml.  
  
 **FlightRecorder\SnapshotFrequencySec**  
 Свойство с 32-разрядным целочисленным значением со знаком, определяющее частоту (в секундах) моментальных снимков.  
  
 **FlightRecorder\TraceDefinitionFile**  
 Строковое свойство, задающее имя файла определения трассировки «черного ящика».  
  
 Значением по умолчанию для этого свойства является пустая строка, что по умолчанию соответствует файлу FlightRecorderTraceDef.xml.  
  
## <a name="query-log"></a>Журнал запросов  
 **Применимо к:** Только многомерный режим сервера  
  
 **QueryLog\QueryLogFileName**  
 Строковое свойство, задающее имя файла журнала запросов. Данное свойство применяется только в том случае, когда для ведения журнала используется дисковый файл, а не таблица базы данных (настройка по умолчанию).  
  
 **QueryLog\QueryLogSampling**  
 Свойство с 32-разрядным целочисленным значением со знаком, задающее частоту выборки журнала запросов.  
  
 Значение этого свойства по умолчанию равно 10, что означает, что в журнал заносится 1 из каждых 10 серверных запросов.  
  
 **QueryLog\QueryLogFileSize**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **QueryLog\QueryLogConnectionString**  
 Строковое свойство, задающее соединение с базой данных журнала запросов.  
  
 **QueryLog\QueryLogTableName**  
 Строковое свойство, задающее имя таблицы журнала запросов.  
  
 Значение этого свойства по умолчанию равно OlapQueryLog.  
  
 **QueryLog\CreateQueryLogTable**  
 Логическое свойство, задающее необходимость создания таблицы журнала запросов.  
  
 Значение этого свойства по умолчанию равно false, что указывает на то, что сервер не будет автоматически создавать таблицу журнала и не будет записывать в журнал события запросов.  
  
> [!NOTE]  
>  Дополнительные сведения о настройке журнала запросов см. в разделе [записи операций в службах Analysis Services](../instances/log-operations-in-analysis-services.md).  
  
## <a name="trace"></a>Trace  
 **Trace\TraceBackgroundDistributionPeriod**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Trace\TraceBackgroundFlushPeriod**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Trace\TraceFileBufferSize**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Trace\TraceFileWriteTrailerPeriod**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Trace\TraceMaxRowsetSize**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Trace\TraceProtocolTraffic**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Trace\TraceQueryResponseTextChunkSize**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Trace\TraceReportFQDN**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Trace\TraceRequestParameters**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Trace\TraceRowsetBackgroundFlushPeriod**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Настройка свойств сервера в службах Analysis Services](server-properties-in-analysis-services.md)   
 [Определение режима работы сервера экземпляра служб Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
