---
title: Установка свойств пакета | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, properties
- properties [Integration Services]
- checkpoints [Integration Services]
- execution properties [Integration Services]
- packages [Integration Services], properties
- identification properties [Integration Services]
- passwords [Integration Services]
- SSIS packages, properties
- transaction properties [Integration Services]
- updating package properties
- forced execution value properties [Integration Services]
- security properties [Integration Services]
- version properties [Integration Services]
- SQL Server Integration Services packages, properties
ms.assetid: 13f81c3e-2b18-4f83-b445-a2f4a2c560aa
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ea7f5f06816b6dd4ddf840f63119bebb0ebf80e8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889217"
---
# <a name="set-package-properties"></a>Установка свойств пакета
  При создании пакета в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] с помощью графического интерфейса, который предоставляется службами [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , свойства объекта пакета задаются в окне «Свойства».  
  
 В окне **Свойства** список свойств может быть упорядочен по категориям или в алфавитном порядке. Чтобы упорядочить содержимое окна **Свойства** по категории, нажмите значок «По категории».  
  
 При упорядочении по категории содержимое окна **Свойства** группируется по следующим категориям:  
  
-   [Контрольные точки](#Checkpoints)  
  
-   [Выполнение](#Execution)  
  
-   [Значение параметра «Принудительное выполнение»](#ForcedExecutionValue)  
  
-   [Идентификация](#Identification)  
  
-   [Разное](#Misc)  
  
-   [безопасность](#Security)  
  
-   [Transactions](#Transactions)  
  
-   [Версия](#Version)  
  
 Сведения о дополнительных свойствах пакета, которые нельзя установить в окне **Свойства** , см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.Package>.  
  
### <a name="to-set-package-properties-in-the-properties-window"></a>Установка свойств пакета в окне «Свойства»  
  
-   [Установка свойств переменной пакета](../../2014/integration-services/set-the-properties-of-a-package.md)  
  
## <a name="properties-by-category"></a>Свойства, упорядоченные по категориям  
 В следующих таблицах перечислены свойства пакета, упорядоченные по категориям.  
  
###  <a name="Checkpoints"></a> Контрольные точки  
 Свойства этой категории позволяют перезапускать пакет с точки сбоя в его потоке управления без необходимости перезапуска с самого начала потока управления. Дополнительные сведения см. в разделе [Restart Packages by Using Checkpoints](packages/restart-packages-by-using-checkpoints.md).  
  
|Свойство|Описание|  
|--------------|-----------------|  
|`CheckpointFileName`|Имя файла для записи сведений о контрольных точках, которые позволяют перезапускать пакет. При успешном завершении пакета этот файл удаляется.|  
|`CheckpointUsage`|Определяет, когда пакет может быть перезапущен. Допустимые значения — `Never`, `IfExists` и `Always`. Значение этого свойства по умолчанию равно `Never`, что означает невозможность перезапуска пакета. Дополнительные сведения см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.DTSCheckpointUsage>.|  
|`SaveCheckpoints`|Определяет, записываются ли контрольные точки в файл контрольных точек при запуске пакета. Значение по умолчанию этого свойства равно `False`.|  
  
> [!NOTE]  
>  Параметр `/CheckPointing on` программы dtexec аналогичен свойству пакета `SaveCheckpoints` в значении True и свойству `CheckpointUsage` в значении Always. Дополнительные сведения см. в статье [dtexec Utility](packages/dtexec-utility.md).  
  
###  <a name="Execution"></a> Выполнение  
 Свойства этой категории позволяют настраивать поведение объекта пакета во время выполнения.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|`DelayValidation`|Указывает, откладывается ли проверка пакета до того момента, как он будет запущен. Значение этого свойства по умолчанию — `False`.|  
|**Отключить**|Указывает, отключен ли пакет. Значение по умолчанию этого свойства равно `False`.|  
|`DisableEventHandlers`|Определяет, запускаются ли обработчики событий пакета. Значение по умолчанию этого свойства равно `False`.|  
|`FailPackageOnFailure`|Определяет, происходит ли аварийное завершение пакета в случае ошибки в каком-либо его компоненте. Единственным допустимым значением для этого свойства является значение `False`.|  
|`FailParentOnError`|Определяет, происходит ли аварийное завершение родительского контейнера в случае ошибки в дочернем контейнере. Значение этого свойства по умолчанию равно `False`.|  
|`MaxConcurrentExecutables`|Число исполняемых файлов, которые могут быть параллельно запущены пакетом. Значение этого свойства по умолчанию равно **-1**, что означает отсутствие ограничения.|  
|`MaximumErrorCount`|Максимальное число ошибок, после достижения которого выполнение пакета прекращается. Значение этого свойства по умолчанию равно **1**.|  
|`PackagePriorityClass`|Класс приоритета потока пакета в системе Win32. Допустимые значения — `Default`, `AboveNormal`, `Normal`, `BelowNormal`, `Idle`. Значение по умолчанию этого свойства равно `Default`. Дополнительные сведения см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.DTSPriorityClass>.|  
  
###  <a name="ForcedExecutionValue"></a> Значение параметра «Принудительное выполнение»  
 Свойства этой категории позволяют настраивать значение необязательного выполнения для пакета.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|`ForcedExecutionValue`|Если задано значение ForceExecutionValue `True`, значение, указывающее возвращаемое пакетом значение необязательного выполнения. Значение этого свойства по умолчанию равно **0**.|  
|`ForcedExecutionValueType`|Тип данных свойства ForcedExecutionValue. Значение по умолчанию этого свойства равно `Int32`.|  
|`ForceExecutionValue`|Логическое значение, указывающее, должно ли необязательное значение выполнения для контейнера содержать конкретное значение. Значение по умолчанию этого свойства равно `False`.|  
  
###  <a name="Identification"></a> Идентификация  
 Свойства этой категории содержат такие данные, как уникальный идентификатор и имя пакета.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|`CreationDate`|Дата создания пакета.|  
|`CreatorComputerName`|Имя компьютера, на котором был создан пакет.|  
|`CreatorName`|Имя пользователя, создавшего пакет.|  
|`Description`|Описание функциональных возможностей пакета.|  
|`ID`|Идентификатор GUID пакета, назначаемый ему при создании. Это свойство доступно только для чтения. Чтобы создать новое случайное значение для `ID` выберите  **\<сформировать новый идентификатор >** в раскрывающемся списке.|  
|`Name`|Имя пакета.|  
|`PackageType`|Тип пакета. Допустимые значения — `Default`, `DTSDesigner`, `DTSDesigner100`, `DTSWizard`, `SQLDBMaint` и `SQLReplication`. Значение по умолчанию этого свойства равно `Default`. Дополнительные сведения см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.DTSPackageType>.|  
  
###  <a name="Misc"></a> Разное  
 Свойства этой категории используются для доступа к конфигурациям и выражениям, используемым пакетом, а также для указания сведений о локали и режиме записи в журнал пакета. Дополнительные сведения см. в разделе [Использование выражений свойств в пакетах](expressions/use-property-expressions-in-packages.md).  
  
|Свойство|Описание|  
|--------------|-----------------|  
|`Configurations`|Коллекция конфигураций, используемых пакетом. Нажмите кнопку обзора **(…)** для просмотра и настройки конфигурации пакета.|  
|`Expressions`|Нажмите кнопку обзора **(…)** для создания выражений для свойств пакета.<br /><br /> Примечание. Можно создать выражения свойств для всех свойств пакета, объектную модель, не только свойства, перечисленные в окне «Свойства».<br /><br /> Дополнительные сведения см. в разделе [Использование выражений свойств в пакетах](expressions/use-property-expressions-in-packages.md).<br /><br /> Для просмотра существующих выражений свойств раскройте список `Expressions`. Нажмите кнопку обзора **(…)** в текстовом поле выражения для изменения и вычисления этого выражения.|  
|`ForceExecutionResult`|Результат выполнения пакета. Допустимые значения: `None`, `Success`, `Failure` и `Completion`. Значение по умолчанию этого свойства равно `None`. Дополнительные сведения см. в разделе T:Microsoft.SqlServer.Dts.Runtime.DTSForcedExecResult.|  
|`LocaleId`|Локаль Microsoft Win32. Значение этого свойства по умолчанию равно локали операционной системы на локальном компьютере.|  
|`LoggingMode`|Значение, определяющее для пакета режим записи в журнал. Допустимые значения — `Disabled`, `Enabled` и `UseParentSetting`. Значение по умолчанию этого свойства равно `UseParentSetting`. Дополнительные сведения см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode>.|  
|`OfflineMode`|Указывает, работает ли пакет в режиме «вне сети». Это свойство доступно только для чтения. Это свойство устанавливается на уровне проекта. Обычно конструктор служб [!INCLUDE[ssIS](../includes/ssis-md.md)] пытается подключиться ко всем источникам данных, которые использует пакет, чтобы проверить достоверность метаданных, связанных с источниками и назначениями. Можно установить флажок **Работать вне сети** в меню служб **SSIS** даже перед открытием пакета, чтобы избежать этих попыток подключения и возникающих по этой причине ошибок проверки, если источники данных недоступны. Можно также установить флажок **Работать вне сети** для ускорения работы конструктора и снять его только для проверки пакета.|  
|`SuppressConfigurationWarnings`|Указывает, подавляются ли предупреждения, создаваемые конфигурациями. Значение по умолчанию этого свойства равно `False`.|  
|`UpdateObjects`|Указывает, обновляется ли пакет для использования новых версий содержащихся в нем объектов, когда эти новые версии становятся доступны. Например, если значение этого свойства равно `True`, то пакет, включающий задачу «Массовая вставка», обновляется для использования новой версии этой задачи, доступной в службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Значение по умолчанию этого свойства равно `False`.|  
  
###  <a name="Security"></a> безопасность  
 Свойства этой категории используются для установки уровня защиты пакета. Дополнительные сведения см. в разделе [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md).  
  
|Свойство|Описание|  
|--------------|-----------------|  
|`PackagePassword`|Пароль для уровней защиты пакета (`EncryptSensitiveWithPassword` и `EncryptAllWithPassword`), требующих использование пароля.|  
|`ProtectionLevel`|Уровень защиты пакета. Допустимые значения — `DontSaveSensitive`, `EncryptSensitiveWithUserKey`, `EncryptSensitiveWithPassword`, `EncryptAllWithPassword`, и **ServerStorage**. Значение по умолчанию этого свойства равно `EncryptSensitiveWithUserKey`. Дополнительные сведения см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.DTSProtectionLevel>.|  
  
###  <a name="Transactions"></a> Transactions  
 Свойства этой категории позволяют настраивать уровень изоляции и параметр транзакции для пакета. Дополнительные сведения см. в разделе [Транзакции служб Integration Services](integration-services-transactions.md).  
  
|Свойство|Описание|  
|--------------|-----------------|  
|`IsolationLevel`|Уровень изоляции транзакции пакета.  Значение по умолчанию этого свойства равно `Serializable`. Допустимые значения: <br />`Unspecified`<br />`Chaos`<br />`ReadUncommitted`<br />`ReadCommitted`<br />`RepeatableRead`<br />`Serializable`<br />`Snapshot`.<br /><br /> Система применяет свойство `IsolationLevel` к транзакциям пакета только в случае, если свойство `TransactionOption` имеет значение `Required`.<br /><br /> Значение свойства `IsolationLevel`, запрашиваемое дочерним контейнером, не учитывается, если выполняются следующие условия.<br /><br /> Свойство `TransactionOption` дочернего контейнера имеет значение `Supported`.<br />Дочерний контейнер присоединяется к транзакции родительского контейнера.<br /><br /> Значение свойства `IsolationLevel`, запрашиваемое контейнером, учитывается только в случае, когда контейнер запускает новую транзакцию. Контейнер запускает новую транзакцию, если выполняются следующие условия.<br /><br /> Свойство `TransactionOption` контейнера имеет значение `Required`.<br />Родительский пакет еще не запустил транзакцию.<br /><br /> <br /><br /> Примечание. `Snapshot` Значение `IsolationLevel` свойство несовместимо с пакетными транзакциями. Поэтому нельзя использовать свойство `IsolationLevel` для задания уровня изоляции транзакций пакета `Shapshot`. Для задания транзакциям пакета значения `Snapshot` следует использовать SQL-запрос. Дополнительные сведения см. в разделе [SET TRANSACTION ISOLATION LEVEL (Transact-SQL)](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).<br /><br /> Дополнительные сведения о свойстве `IsolationLevel` см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.IsolationLevel%2A>.|  
|`TransactionOption`|Участие пакета в транзакции. Допустимые значения — `NotSupported`, `Supported`, `Required`. Значение по умолчанию этого свойства равно `Supported`. Дополнительные сведения см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.DTSTransactionOption>.|  
  
###  <a name="Version"></a> Версия  
 Свойства этой категории содержат сведения о версии объекта пакета.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|`VersionBuild`|Номер версии сборки пакета.|  
|`VersionComments`|Примечания к версии пакета.|  
|`VersionGUID`|Идентификатор GUID версии пакета. Это свойство предназначено только для чтения.|  
|`VersionMajor`|Последняя основная версия пакета.|  
|`VersionMinor`|Последняя вспомогательная версия пакета.|  
  
  
