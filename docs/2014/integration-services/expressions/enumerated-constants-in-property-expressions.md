---
title: Перечислимые константы в выражениях свойств | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], expressions
- dynamic properties
- updating package properties
- enumerated constants [Integration Services]
- property expressions [Integration Services]
ms.assetid: a4418315-38e2-4ad3-8784-576163b25d6f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b22e25ad9053ed4da0187035cff00ff7e3ca70af
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62898902"
---
# <a name="enumerated-constants-in-property-expressions"></a>Констант-перечислителей в выражениях свойств
  Если выражения свойств включают в себя значения из списка элементов-перечислителей, эти выражения должны использовать числовое значение элементов-перечислителей вместо понятного имени элемента. Например, если выражение устанавливает свойство `LoggingMode`, необходимо использовать числовое значение 2 вместо понятного имени «Запрещено».  
  
 Этот раздел приводит список числовых значений, эквивалентных понятным именам перечислителей, элементы которых, как правило, используются в выражениях свойств. Объектная модель служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] включает много дополнительных перечислителей, которые используются при программировании объектной модели для программного построения пакетов или при создании кода элементов пользовательских пакетов, таких как задачи и компоненты потоков данных.  
  
 В дополнение к пользовательским свойствам пакетов и объектов пакетов окно свойств в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] включает набор свойств, которые доступны пакетам, задачам, контейнерам последовательности, «цикл по элементам» и «цикл по каждому элементу». Общие свойства, которые задаются значениями из перечислителей`ForceExecutionResult`, `LoggingMode` `IsolationLevel` `Transaction Option`перечислены в разделе Общие свойства.  
  
 Ниже приведены сведения о перечислителях-константах.  
  
 [Пакет](#Package)  
  
 [Перечислители контейнера «цикл по каждому элементу»](#Foreach)  
  
 [Задачи](#Tasks)  
  
 [Задачи плана обслуживания](#MaintenancePlanTasks)  
  
 [Общие свойства](#CommonProperties)  
  
##  <a name="package"></a><a name="Package"></a> Пакет  
 В следующих таблицах приводятся списки понятных имен и эквивалентных числовых значений для свойств пакетов, которые устанавливаются с использованием значений перечислителей.  
  
 `PackageType`свойство задается с помощью значений из `DTSPackageType` перечисления.  
  
|Понятное имя в перечислении DTSPackageType|Числовое значение|  
|-------------------------------------|-------------------|  
|По умолчанию|0|  
|DTSWizard|1|  
|DTSDesigner|2|  
|SQLReplication|3|  
|DTSDesigner100|5|  
|SQLDBMaint|6|  
  
 `CheckpointUsage`свойство задается с помощью значений из `DTSCheckpointUsage` перечисления.  
  
|Понятное имя в перечислении DTSCheckpointUsage|Числовое значение|  
|-----------------------------------------|-------------------|  
|Никогда|0|  
|IfExists|1|  
|Всегда|2|  
  
 `PackagePriorityClass`свойство задается с помощью значений из `DTSPriorityClass` перечисления.  
  
|Понятное имя в перечислении DTSPriorityClass|Числовое значение|  
|---------------------------------------|-------------------|  
|По умолчанию|0|  
|AboveNormal|1|  
|Нормальный|2|  
|BelowNormal|3|  
|Бездействие|4|  
  
 `ProtectionLevel`свойство задается с помощью значений из `DTSProtectionLevel` перечисления.  
  
|Понятное имя в перечислении DTSProtectionLevel|Числовое значение|  
|-----------------------------------------|-------------------|  
|DontSaveSensitive|0|  
|EncryptSensitiveWithUserKey|1|  
|EncryptSensitiveWithPassword|2|  
|EncryptAllWithPassword|3|  
|EncryptAllWithUserKey|4|  
|ServerStorage|5|  
  
##  <a name="precedence-constraints"></a><a name="PrecedenceConstraints"></a> Управление очередностью  
 `EvalOp`свойство задается с помощью значений из `DTSPrecedenceEvalOp` перечисления.  
  
|Понятное имя в перечислении DTSPrecedenceEvalOp|Числовое значение|  
|------------------------------------------|-------------------|  
|Выражение|1|  
|Ограничение|2|  
|ExpressionAndConstraint|3|  
|ExpressionOrConstraint|4|  
  
 `Value`свойство задается с помощью значений из `DTSExecResult` перечисления.  
  
|Понятное имя|Числовое значение|  
|-------------------|-------------------|  
|Успешно|0|  
|Failure|1|  
|Completion|2|  
|Отменено|3|  
  
##  <a name="foreach-loop-enumerators"></a><a name="Foreach"></a> Перечислители контейнера «цикл по каждому элементу»  
 Контейнер «цикл по каждому элементу» включает в себя набор перечислителей со свойствами, которые могут быть установлены с помощью выражений свойств.  
  
### <a name="foreach-ado-enumerator"></a>Перечислитель ADO по каждой строке  
 `Type`свойство задается с помощью значений из `ADOEnumerationType` перечисления.  
  
|Понятное имя в перечислении ADOEnumerationType|Числовое значение|  
|-----------------------------------------|-------------------|  
|EnumerateTables|0|  
|EnumerateAllRows|1|  
|EnumerateRowsInFirstTable|2|  
  
### <a name="foreach-nodelist-enumerator"></a>Перечислитель по набору узлов  
 `SourceDocumentType`свойства `InnerXPathStringSourceType`, и **OuterXPathStringSourceType** задаются с помощью значений из `SourceType` перечисления.  
  
|Понятное имя в перечислении SourceType|Числовое значение|  
|---------------------------------|-------------------|  
|FileConnection|0|  
|Переменная|1|  
|DirectInput|2|  
  
 `EnumerationType`свойство задается с помощью значений из `EnumerationType` перечисления.  
  
|Понятное имя в перечислении EnumerationType|Числовое значение|  
|--------------------------------------|-------------------|  
|Navigator|0|  
|Узел|1|  
|NodeText|2|  
|ElementCollection|3|  
  
 `InnerElementType`свойство задается с помощью значений из `InnerElementType` перечисления.  
  
|Понятное имя в перечислении InnerElementType|Числовое значение|  
|---------------------------------------|-------------------|  
|Navigator|0|  
|Узел|1|  
|NodeText|2|  
  
##  <a name="tasks"></a><a name="Tasks"></a> Задачи  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] включают в себя многочисленные задачи со свойствами, которые можно устанавливать с помощью выражений свойств.  
  
### <a name="analysis-services-execute-ddl-task"></a>Задача «Выполнение инструкции DDL служб Analysis Services»  
 `SourceType`свойство задается с помощью значений из `DDLSourceType` перечисления.  
  
|Понятное имя в DDLSourceType|Числовое значение|  
|------------------------------------|-------------------|  
|DirectInput|0|  
|FileConnection|1|  
|Переменная|2|  
  
### <a name="bulk-insert-task"></a>задача «Массовая вставка»  
 `DataFileType`свойство задается с помощью значений из `DTSBulkInsert_DataFileType` перечисления.  
  
|Понятное имя в перечислении DTSBulkInsert_DataFileType|Числовое значение|  
|--------------------------------------------------|-------------------|  
|DTSBulkInsert_DataFileType_Char|0|  
|DTSBulkInsert_DataFileType_Native|1|  
|DTSBulkInsert_DataFileType_WideChar|2|  
|DTSBulkInsert_DataFileType_WideNative|3|  
  
### <a name="execute-sql-task"></a>Задача "Выполнение SQL"  
 `ResultSetType`свойство задается с помощью значений из `ResultSetType` перечисления.  
  
|Понятное имя в перечислении ResultSetType|Числовое значение|  
|------------------------------------|-------------------|  
|ResultSetType_None|1|  
|ResultSetType_SingleRow|2|  
|ResultSetType_Rowset|3|  
|ResultSetType_XML|4|  
  
 `SqlStatementSourceType`свойство задается с помощью значений из `SqlStatementSourceType` перечисления.  
  
|Понятное имя в перечислении SqlStatementSourceType|Числовое значение|  
|---------------------------------------------|-------------------|  
|DirectInput|1|  
|FileConnection|2|  
|Переменная|3|  
  
### <a name="file-system-task"></a>Задача "Файловая система"  
 `Operation`свойство задается с помощью значений из `DTSFileSystemOperation` перечисления.  
  
|Понятное имя в перечислении DTSFileSystemOperation|Числовое значение|  
|---------------------------------------------|-------------------|  
|CopyFile|0|  
|MoveFile|1|  
|DeleteFile|2|  
|RenameFile|3|  
|SetAttributes|4|  
|CreateDirectory|5|  
|CopyDirectory|6|  
|MoveDirectory|7|  
|DeleteDirectory|8|  
|DeleteDirectoryContent|9|  
  
 `Attributes`свойство задается с помощью значений из `DTSFileSystemAttributes` перечисления.  
  
|Понятное имя в перечислении DTSFileSystemAttributes|Числовое значение|  
|----------------------------------------------|-------------------|  
|Нормальный|0|  
|Архив|1|  
|Скрытый|2|  
|ReadOnly|4|  
|Система|8|  
  
### <a name="ftp-task"></a>Задача «FTP»  
 `Operation`свойство задается с помощью значений из `DTSFTPOp` перечисления.  
  
|Понятное имя в перечислении DTSFTPOp|Числовое значение|  
|-------------------------------|-------------------|  
|Send|0|  
|Receive|1|  
|DeleteLocal|2|  
|DeleteRemote|3|  
|MakeDirLocal|4|  
|MakeDirRemote|5|  
|RemoveDirLocal|6|  
|RemoveDirRemote|7|  
  
### <a name="message-queue-task"></a>Message Queue Task  
 `MessageType`свойство задается с помощью значений из `MQMessageType` перечисления.  
  
|Понятное имя в перечислении MQMessageType|Числовое значение|  
|------------------------------------|-------------------|  
|DTSMQMessageType_String|0|  
|DTSMQMessageType_DataFile|1|  
|DTSMQMessageType_Variables|2|  
|DTSMQMessagType_StringMessageToVariable|3|  
  
 `StringCompareType`свойство задается с помощью значений из `MQStringMessageCompare` перечисления.  
  
|Понятное имя в перечислении MQStringMessageCompare|Числовое значение|  
|---------------------------------------------|-------------------|  
|DTSMQStringMessageCompare_None|0|  
|DTSMQStringMessageCompare_Exact|1|  
|DTSMQStringMessageCompare_IgnoreCase|2|  
|DTSMQStringMessageCompare_Contains|3|  
  
 `TaskType`свойство задается с помощью значений из `MQType` перечисления.  
  
|Понятное имя в перечислении MQType|Числовое значение|  
|-----------------------------|-------------------|  
|DTSMQType_Sender|0|  
|DTSMQType_Receiver|1|  
  
### <a name="send-mail-task"></a>Задача «Отправка почты»  
 `MessageSourceType`свойство задается с помощью значений из `SendMailMessageSourceType` перечисления.  
  
|Понятное имя в перечислении SendMailMessageSourceType|Числовое значение|  
|------------------------------------------------|-------------------|  
|DirectInput|0|  
|FileConnection|1|  
|Переменная|2|  
  
 `Priority`свойство задается с помощью значений из `MailPriority` перечисления.  
  
|Понятное имя в перечислении MailPriority|Числовое значение|  
|-----------------------------------|-------------------|  
|Высокий|1|  
|Нормальный|3|  
|Низкий|5|  
  
### <a name="transfer-database-task"></a>Задача «Передача базы данных»  
 `Action`свойство задается с помощью значений из `TransferAction` перечисления.  
  
|Понятное имя в перечислении TransferAction|Числовое значение|  
|-------------------------------------|-------------------|  
|Копировать|0|  
|Переместить|1|  
  
 `Method`свойство задается с помощью значений из `TransferMethod` перечисления.  
  
|Понятное имя в перечислении TransferMethod|Числовое значение|  
|-------------------------------------|-------------------|  
|DatabaseOffline|0|  
|DatabaseOnline|1|  
  
### <a name="transfer-error-messages-task"></a>Задача «Передача сообщений об ошибках»  
 `IfObjectExists`свойство задается с помощью значений из `IfObjectExists` перечисления.  
  
|Понятное имя в перечислении IfObjectExists|Числовое значение|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Overwrite|1|  
|Skip|2|  
  
### <a name="transfer-jobs-task"></a>Задача «Передача заданий»  
 `IfObjectExists`свойство задается с помощью значений из `IfObjectExists` перечисления.  
  
|Понятное имя в перечислении IfObjectExists|Числовое значение|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Overwrite|1|  
|Skip|2|  
  
### <a name="transfer-logins-task"></a>Задача «Передача имен входа»  
 `IfObjectExists`свойство задается с помощью значений из `IfObjectExists` перечисления.  
  
|Понятное имя в перечислении IfObjectExists|Числовое значение|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Overwrite|1|  
|Skip|2|  
  
 `LoginsToTransfer`свойство задается с помощью значений из `LoginsToTransfer` перечисления.  
  
|Понятное имя в перечислении LoginsToTransfer|Числовое значение|  
|---------------------------------------|-------------------|  
|AllLogins|0|  
|SelectedLogins|1|  
|AllLoginsFromSelectedDatabases|2|  
  
### <a name="transfer-master-stored-procedures-task"></a>Задача «Передача главных хранимых процедур»  
 `IfObjectExists`свойство задается с помощью значений из `IfObjectExists` перечисления.  
  
|Понятное имя в перечислении IfObjectExists|Числовое значение|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Overwrite|1|  
|Skip|2|  
  
### <a name="transfer-sql-server-objects-task"></a>Задача «Передача объектов SQL Server»  
 `ExistingData`свойство задается с помощью значений из `ExistingData` перечисления.  
  
|Понятное имя в перечислении ExistingData|Числовое значение|  
|-----------------------------------|-------------------|  
|Заменить|0|  
|Append|1|  
  
### <a name="web-service-task"></a>Задача «Веб-служба»  
 `OutputType`свойство задается с помощью значений из `DTSOutputType` перечисления.  
  
|Понятное имя в перечислении DTSOutputType|Числовое значение|  
|------------------------------------|-------------------|  
|Файл|0|  
|Переменная|1|  
  
### <a name="wmi-data-reader-task"></a>Задача «Модуль чтения данных WMI»  
 `OverwriteDestination`свойство задается с помощью значений из `OverwriteDestination` перечисления.  
  
|Понятное имя в перечислении OverwriteDestination|Числовое значение|  
|-------------------------------------------|-------------------|  
|OverwriteDestination|0|  
|AppendToDestination|1|  
|KeepOriginal|2|  
  
 `OutputType`свойство задается с помощью значений из `OutputType` перечисления.  
  
|Понятное имя в перечислении OutputType|Числовое значение|  
|---------------------------------|-------------------|  
|DataTable|0|  
|PropertyValue|1|  
|PropertyNameAndValue|2|  
  
 `DestinationType`свойство задается с помощью значений из `DestinationType` перечисления.  
  
|Понятное имя в перечислении DestinationType|Числовое значение|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|Переменная|1|  
  
 `WqlQuerySourceType`свойство задается с помощью значений из `QuerySourceType` перечисления.  
  
|Понятное имя в перечислении QuerySourceType|Числовое значение|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|DirectInput|1|  
|Переменная|2|  
  
 `ActionAtEvent` Свойство "НАБЛЮДАТЕЛЬ событий WMI" задается с помощью значений `ActionAtEvent` из перечисления.  
  
|Понятное имя в перечислении ActionAtEvent|Числовое значение|  
|------------------------------------|-------------------|  
|LogTheEventAndFireDTSEvent|0|  
|LogTheEvent|1|  
  
 `ActionAtTimeout`свойство задается с помощью значений из `ActionAtTimeout` перечисления.  
  
|Понятное имя в перечислении ActionAtTimeout|Числовое значение|  
|--------------------------------------|-------------------|  
|LogTimeoutAndFireDTSEvent|0|  
|LogTimeout|1|  
  
 `AfterEvent`свойство задается с помощью значений из `AfterEvent` перечисления.  
  
|Понятное имя в перечислении AfterEvent|Числовое значение|  
|---------------------------------|-------------------|  
|ReturnWithSuccess|0|  
|ReturnWithFailure|1|  
|WatchfortheEventAgain|2|  
  
 `AfterTimeout`свойство задается с помощью значений из `AfterTimeout` перечисления.  
  
|Понятное имя в перечислении AfterTimeout|Числовое значение|  
|-----------------------------------|-------------------|  
|ReturnWithSuccess|0|  
|ReturnWithFailure|1|  
|WatchfortheEventAgain|2|  
  
 `WqlQuerySourceType`свойство задается с помощью значений из `QuerySourceType` перечисления.  
  
|Понятное имя в перечислении QuerySourceType|Числовое значение|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|DirectInput|1|  
|Переменная|2|  
  
### <a name="xml-task"></a>Задача «XML»  
 `OperationType`свойство задается с помощью значений из `DTSXMLOperation` перечисления.  
  
|Понятное имя в перечислении DTSXMLOperation|Числовое значение|  
|--------------------------------------|-------------------|  
|Проверить|0|  
|XSLT|1|  
|XPATH|2|  
|Объединить|3|  
|Поиск различий|4|  
|Обновление|5|  
  
 `SourceType`свойства `SecondOperandType`, и `XPathSourceType` задаются с помощью значений из `DTSXMLSourceType` перечисления.  
  
|Понятное имя в перечислении DTSXMLSourceType|Числовое значение|  
|---------------------------------------|-------------------|  
|FileConnection|0|  
|Переменная|1|  
|DirectInput|2|  
  
 `DestinationType`свойства и **диффграмдестинатионтипе** задаются с помощью значений из `DTSXMLSaveResultTo` перечисления.  
  
|Понятное имя в перечислении DTSXMLSaveResultTo|Числовое значение|  
|-----------------------------------------|-------------------|  
|FileConnection|0|  
|Переменная|1|  
  
 `ValidationType`свойство задается с помощью значений из `DTSXMLValidationType` перечисления.  
  
|Понятное имя в перечислении DTSXMLValidationType|Числовое значение|  
|-------------------------------------------|-------------------|  
|DTD|0|  
|XSD|1|  
  
 `XPathOperation`свойство задается с помощью значений из `DTSXMLXPathOperation` перечисления.  
  
|Понятное имя в перечислении DTSXMLXPathOperation|Числовое значение|  
|-------------------------------------------|-------------------|  
|Ознакомительная версия|0|  
|Значения|1|  
|NodeList|2|  
  
 `DiffOptions`свойство задается с помощью значений из `DTSXMLDiffOptions` перечисления. Параметры в этом перечислителе взаимно не исключаемы. Чтобы использовать несколько параметров, предоставьте список параметров с разделителями-запятыми.  
  
|Понятное имя в перечислении DTSXMLDiffOptions|Числовое значение|  
|----------------------------------------|-------------------|  
|None|0|  
|IgnoreChildOrder|1|  
|IgnoreComments|2|  
|IgnorePI|4|  
|IgnoreWhitespace|8|  
|IgnoreNamespaces|16|  
|IgnorePrefixes|32|  
|IgnoreXmlDecl|64|  
|IgnoreDtd|128|  
  
 `DiffAlgorithm`свойство задается с помощью значений из `DTSXMLDiffAlgorithm` перечисления.  
  
|Понятное имя в перечислении DTSXMLDiffAlgorithm|Числовое значение|  
|------------------------------------------|-------------------|  
|Auto|0|  
|быстрый;|1|  
|Точный|2|  
  
##  <a name="maintenance-plan-tasks"></a><a name="MaintenancePlanTasks"></a> Задачи плана обслуживания  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] включают в себя набор задач, выполняющих задачи SQL Server для использования в планах обслуживания, и пакеты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживают работу с этими задачами программным путем, а документация по программированию не включает в себя API-документацию для этих задач и их перечислителей.  
  
### <a name="all-maintenance-tasks"></a>Все задачи плана обслуживания  
 Все задачи плана обслуживания для установки указанных свойств используют следующие перечисления.  
  
 `DatabaseSelectionType`свойство задается с помощью значений из `DatabaseSelection` перечисления.  
  
|Понятное имя в перечислении DatabaseSelection|Числовое значение|  
|----------------------------------------|-------------------|  
|None|0|  
|All|1|  
|Система|2|  
|Пользователь|3|  
|Specific|4|  
  
 `TableSelectionType`свойство задается с помощью значений из `TableSelection` перечисления.  
  
|Понятное имя в перечислении TableSelection|Числовое значение|  
|-------------------------------------|-------------------|  
|None|0|  
|All|1|  
|Specific|2|  
  
 `ObjectTypeSelection`свойство задается с помощью значений из `ObjectType` перечисления.  
  
|Понятное имя в перечислении ObjectType|Числовое значение|  
|---------------------------------|-------------------|  
|Таблица|0|  
|Представление|1|  
|TableView|2|  
  
### <a name="back-up-database-task"></a>Задача «Создание резервной копии базы данных»  
 `DestinationCreationType`свойство задается с помощью значений из `DestinationType` перечисления.  
  
|Понятное имя в перечислении DestinationType|Числовое значение|  
|--------------------------------------|-------------------|  
|Auto|0|  
|Вручную|1|  
  
 `ExistingBackupsAction`свойство задается с помощью значений из `ActionForExistingBackups` перечисления.  
  
|Понятное имя в перечислении ActionForExistingBackups|Числовое значение|  
|-----------------------------------------------|-------------------|  
|Append|0|  
|Overwrite|1|  
  
 `BackupAction`свойство задается с помощью значений из `BackupTaskType` перечисления. Это свойство работает совместно со свойством `BackupIsIncremental` для определения типа резервной копии, которую создает задача.  
  
|Понятное имя в перечислении BackupTaskType|Числовое значение|  
|-------------------------------------|-------------------|  
|База данных|0|  
|Файлы|1|  
|Журнал|2|  
  
 `BackupDevice`свойство задается с помощью значений из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перечисления управляющих объектов ( `DeviceType` SMO).  
  
|Понятное имя в перечислении DeviceType|Числовое значение|  
|---------------------------------|-------------------|  
|LogicalDevice|0|  
|Лента|1|  
|Файл|2|  
|Pipe|3|  
|VirtualDevice|4|  
  
### <a name="maintenance-cleanup-task"></a>задача «Очистка после обслуживания»  
 `FileTypeSelected`свойство задается с помощью значений из `FileType` перечисления.  
  
|Понятное имя в перечислении FileType|Числовое значение|  
|-------------------------------|-------------------|  
|FileBackup|0|  
|FileReport|1|  
  
 `OlderThanTimeUnitType`свойство задается с помощью значений из `TimeUnitType` перечисления.  
  
|Понятное имя в перечислении TimeUnitType|Числовое значение|  
|-----------------------------------|-------------------|  
|День|0|  
|Неделя|1|  
|Месяц|2|  
|Год|3|  
  
### <a name="update-statistics-task"></a>Задача «Обновление статистики»  
 `UpdateType`свойство задается с помощью значений из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перечисления управляющих объектов ( `StatisticsTarget` SMO).  
  
|Понятное имя в перечислении StatisticsTarget|Числовое значение|  
|---------------------------------------|-------------------|  
|Столбец|1|  
|Индекс|2|  
|All|3|  
  
##  <a name="common-properties"></a><a name="CommonProperties"></a> Общие свойства  
 Пакеты, задачи, а также контейнеры последовательности, «цикл по каждому элементу» и «цикл по элементам» могут использовать следующие перечисления для задания специфических свойств.  
  
 `ForceExecutionResult`свойство задается с помощью значений из `DTSForcedExecResult` перечисления.  
  
|Понятное имя в перечислении DTSForcedExecResult|Числовое значение|  
|------------------------------------------|-------------------|  
|None|-1|  
|Успешно|0|  
|Failure|1|  
|Completion|2|  
  
 `IsolationLevel`свойство задается перечислением .NET Framework `IsolationLevel` . Дополнительные сведения см. в документации по библиотеке классов платформы .NET Framework в [Библиотеке MSDN](https://go.microsoft.com/fwlink?LinkId=17313).  
  
 `LoggingMode`свойство задается с помощью значений из `DTSLoggingMode` перечисления.  
  
|Понятное имя в перечислении DTSLoggingMode|Числовое значение|  
|-------------------------------------|-------------------|  
|UseParentSetting|0|  
|Активировано|1|  
|Выключено|2|  
  
 `TransactionOption`свойство задается с помощью значений из `DTSTransactionOption` перечисления.  
  
|Понятное имя в перечислении DTSTransactionOption|Числовое значение|  
|-------------------------------------------|-------------------|  
|NotSupported|0|  
|Поддерживается|1|  
|Обязательно|2|  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Добавление или изменение выражение свойства](add-or-change-a-property-expression.md)  
  
## <a name="see-also"></a>См. также:  
 [Использование выражений свойств в пакетах](use-property-expressions-in-packages.md)   
 [Пакеты служб Integration Services (SSIS)](../integration-services-ssis-packages.md)   
 [Контейнеры служб Integration Services](../control-flow/integration-services-containers.md)   
 [Задачи служб Integration Services](../control-flow/integration-services-tasks.md)   
 [Управление очередностью](../control-flow/precedence-constraints.md)  
  
  
