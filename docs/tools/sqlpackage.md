---
title: SQLPackage.exe
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 198198e2-7cf4-4a21-bda4-51b36cb4284b
author: pensivebrian
ms.author: broneill
ms.reviewer: alayu; sstein
ms.date: 03/17/2020
ms.openlocfilehash: 1ee42c97fe4e032835ccb2f8a07ea51fe70114ac
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303145"
---
# <a name="sqlpackageexe"></a>SQLPackage.exe

Программа командной строки **SqlPackage.exe** автоматизирует следующие задачи разработки баз данных.  
  
- [Extract](#help-for-the-extract-action): создает файл моментального снимка базы данных (DACPAC) из активной Базы данных SQL Server или SQL Azure.  
  
- [Publish](#publish-parameters-properties-and-sqlcmd-variables): выполняет добавочное обновление схемы базы данных в соответствии со схемой исходного DACPAC-файла. Если база данных не существует на сервере, операция публикации создаст ее. В противном случае обновляется существующая база данных.  
  
- [Export](#export-parameters-and-properties): экспортирует активную базу данных, включая схему базы данных и пользовательские данные, из Базы данных SQL Azure или SQL Server в пакет BACPAC (BACPAC-файл).  
  
- [Import](#import-parameters-and-properties): импортирует данные схемы и таблиц из пакета BACPAC в новую пользовательскую базу данных в экземпляре Базы данных SQL Server или SQL Azure.  
  
- [DeployReport](#deployreport-parameters-and-properties): создает XML-отчет по изменениям, которые должны быть внесены в результате публикации.  
  
- [DriftReport](#driftreport-parameters): создает XML-отчет по изменениям, которые были внесены в зарегистрированную базу данных со времени ее последней регистрации.  
  
- [Script](#script-parameters-and-properties): создает скрипт добавочного обновления на языке Transact-SQL, который обновляет схему целевой базы данных до соответствия схеме базы данных-источника.  
  
Программа командной строки **SqlPackage.exe** позволяет указывать эти действия вместе с соответствующими параметрами и свойствами.  

**[Скачать последнюю версию](sqlpackage-download.md)** . Подробнее см. в [заметках о выпуске](release-notes-sqlpackage.md).
  
## <a name="command-line-syntax"></a>Синтаксис командной строки

Программа **SqlPackage.exe** инициирует действия, заданные с использованием параметров, свойств и переменных SQLCMD, указанных в командной строке.  
  
```
SqlPackage {parameters}{properties}{SQLCMD Variables}  
```

### <a name="usage-examples"></a>Примеры использования

**Создание сравнения баз данных с помощью DACPAC-файлов с выходными данными скрипта SQL**

Сначала создайте DACPAC-файл с последними изменениями базы данных:

```
sqlpackage.exe /TargetFile:"C:\sqlpackageoutput\output_current_version.dacpac" /Action:Extract /SourceServerName:"." /SourceDatabaseName:"Contoso.Database"
 ```
 
Затем создайте DACPAC-файл целевого объекта базы данных (без изменений):

 ```
 sqlpackage.exe /TargetFile:"C:\sqlpackageoutput\output_target.dacpac" /Action:Extract /SourceServerName:"." /SourceDatabaseName:"Contoso.Database"
 ```

Создайте скрипт SQL, который создает различия между двумя DACPAC-файлами:

```
sqlpackage.exe /Action:Script /SourceFile:"C:\sqlpackageoutput\output_current_version.dacpac" /TargetFile:"C:\sqlpackageoutput\output_target.dacpac" /TargetDatabaseName:"Contoso.Database" /OutputPath:"C:\sqlpackageoutput\output.sql"
 ```

### <a name="help-for-the-extract-action"></a>Справка для операции извлечения

|Параметр|Краткая форма|Значение|Описание|
|---|---|---|---|
|**/Action:**|**/a**|Extract|Указывает действие, подлежащее выполнению. |
|**/AccessToken:**|**/at**|{строка}| Указывает маркер доступа для проверки подлинности на основе маркеров. Этот маркер используется при подключении к целевой базе данных. |
|**/Diagnostics:**|**/d**|{True&#124;False}|Указывает, следует ли выводить сведения из журнала диагностики в консоль. Значение по умолчанию — False. |
|**/DiagnosticsFile:**|**/df**|{строка}|Указывает файл, в котором следует вести журнал диагностики. |
|**/MaxParallelism:**|**/mp**|{целое_число}| Задает степень параллелизма для параллельных операций с базой данных. Значение по умолчанию: 8. |
|**/OverwriteFiles:**|**/of**|{True&#124;False}|Указывает, должна ли программа sqlpackage.exe перезаписывать существующие файлы. Задание значения false приводит к тому, что программа sqlpackage.exe прерывает действие при обнаружении существующего файла. Значение по умолчанию равно True. |
|**/Properties:**|**/p**|{имя_свойства}={значение}|Указывает пару "имя-значение" для свойства действия; {имя_свойства}={значение}. Имена свойств действия см. в справке по данным действиям. Например: sqlpackage.exe /Action:Extract /?. |
|**/Quiet:**|**/q**|{True&#124;False}|Указывает, происходит ли подавление подробного отзыва. Значение по умолчанию — False. |
|**/SourceConnectionString:**|**/scs**|{строка}|Указывает допустимую строку подключения SQL Server/Azure для базы данных-источника. Если этот параметр указан, ему будет отдаваться предпочтение перед всеми остальными параметрами источника. |
|**/SourceDatabaseName:**|**/sdn**|{строка}|Определяет имя базы данных-источника. |
|**/SourceEncryptConnection:**|**/sec**|{True&#124;False}|Указывает, следует ли использовать шифрование SQL для соединения с базой данных-источником. |
|**/SourcePassword:**|**/sp**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пароль для доступа к базе данных-источнику. |
|**/SourceServerName:**|**/ssn**|{строка}|Определяет имя сервера, где размещается база данных-источник. |
|**/SourceTimeout:**|**/st**|{целое_число}|Задает время ожидания подключения к базе данных-источнику (в секундах). |
|**/SourceTrustServerCertificate:**|**/stsc**|{True&#124;False}|Определяет, используется ли протокол TLS для шифрования подключения к базе данных-источнику без прохода по цепочке сертификатов для проверки доверия. |
|**/SourceUser:**|**/su**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пользователя SQL Server для доступа к базе данных-источнику. |
|**/TargetFile:**|**/tf**|{строка}| Указывает целевой файл (то есть DACPAC-файл) для использования в качестве целевого объекта действия вместо базы данных. Если используется этот параметр, все остальные параметры целевого объекта будут недействительны. Этот параметр будет недопустимым для действий, которые поддерживают только целевые объекты базы данных.| 
|**/TenantId:**|**/tid**|{строка}|Представляет ИД клиента AAD или доменное имя. Этот параметр необходим для поддержки гостевых или импортированных пользователей AAD, а также учетных записей Майкрософт, например outlook.com, hotmail.com или live.com. Если этот параметр пропущен, будет использоваться ИД клиента по умолчанию для AAD. При этом предполагается, что прошедший проверку подлинности пользователь является собственным пользователем для этого AD. Однако в этом случае все гостевые или импортированные пользователи и (или) учетные записи Майкрософт, размещенные в этой службе AAD, не поддерживаются, и операция завершится ошибкой. <br/> Дополнительные сведения об универсальной проверке подлинности AD DS см. в [этой статье](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/UniversalAuthentication:**|**/ua**|{True&#124;False}|Указывает, следует ли использовать универсальную проверку подлинности. Если задано значение true, протокол интерактивной проверки подлинности активируется с поддержкой MFA. Этот параметр также можно применять для проверки подлинности AAD без MFA, используя интерактивный протокол, где пользователю необходимо ввести имя пользователя и пароль, или встроенную проверку подлинности (учетные данные Windows). Если для элемента /UniversalAuthentication задано значение True, в элементе SourceConnectionString (/scs) не может быть указана проверка подлинности AAD. Если для элемента /UniversalAuthentication задано значение False, в элементе SourceConnectionString (/scs) должна быть указана проверка подлинности AAD. <br/> Дополнительные сведения об универсальной проверке подлинности AD DS см. в [этой статье](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|

### <a name="properties-specific-to-the-extract-action"></a>Свойства, относящиеся к действию извлечения

|Свойство|Значение|Описание|
|---|---|---|
|**/p:**|CommandTimeout=(INT32 '60')|Задает время ожидания команды в секундах при выполнении запросов к SQL Server.|
|**/p:**|DacApplicationDescription=(STRING)|Определяет описание приложения для сохранения в метаданных DACPAC.|
|**/p:**|DacApplicationName=(STRING)|Определяет имя приложения для сохранения в метаданных DACPAC. Значением по умолчанию является имя базы данных.|
|**/p:**|DacMajorVersion=(INT32 '1')|Определяет основную версию для сохранения в метаданных DACPAC.|
|**/p:**|DacMinorVersion=(INT32 '0')|Определяет дополнительный номер версии для сохранения в метаданных DACPAC.|
|**/p:**|DatabaseLockTimeout=(INT32 '60')| Позволяет задать превышение времени ожидания блокировки в секундах для базы данных при выполнении запросов к SQL Server. Для ожидания без ограничений используйте значение "-1".|
|**/p:**|ExtractAllTableData=(BOOLEAN)|Указывает, извлекаются ли данные из всех пользовательских таблиц. Если задано значение true, данные извлекаются из всех пользовательских таблиц и нельзя указать отдельные пользовательские таблицы для извлечения данных. Если задано значение false, укажите одну или несколько пользовательских таблиц для извлечения данных.|
|**/p:**|ExtractApplicationScopedObjectsOnly=(BOOLEAN 'True')|Если задано значение true, то из указанного источника извлекаются только объекты в области приложения. Если задано значение false, то из указанного источника извлекаются все объекты.|
|**/p:**|ExtractReferencedServerScopedElements=(BOOLEAN 'True')|Если задано значение true, извлекаются объекты имени для входа, аудита сервера и учетных данных, на которые ссылаются объекты из базы данных-источника.|
|**/p:**|ExtractUsageProperties=(BOOLEAN)|Указывает, будут ли извлечены свойства использования, такие как количество строк в таблице и размер индекса, из базы данных.|
|**/p:**|IgnoreExtendedProperties=(BOOLEAN)|Указывает, следует ли пропускать расширенные свойства.|
|**/p:**|IgnorePermissions=(BOOLEAN 'True')|Указывает, следует ли не учитывать разрешения.|
|**/p:**|IgnoreUserLoginMappings=(BOOLEAN)|Указывает, будут ли игнорироваться связи между пользователями и именами для входа.|
|**/p:**|LongRunningCommandTimeout=(INT32)| Позволяет задать время ожидания в секундах для длительной команды при выполнении запросов к SQL Server. Для ожидания без ограничений используйте значение "0".|
|**/p:**|Storage=({File&#124;Memory} 'File')|Указывает тип резервного хранилища для модели схемы, используемой во время извлечения.|
|**/p:**|TableData=(STRING)|Указывает таблицу, из которой будут извлечены данные. Укажите имя таблицы со скобками или без скобок. Имя должно быть указано в формате: имя_схемы.идентификатор_таблицы. Этот параметр можно указывать несколько раз.|
|**/p:**| TempDirectoryForTableData=(STRING)|Указывает временный каталог, используемый для буферизации табличных данных перед записью в файл пакета.|
|**/p:**|VerifyExtraction=(BOOLEAN)|Указывает, следует ли проверять извлеченный DACPAC-файл.|

## <a name="publish-parameters-properties-and-sqlcmd-variables"></a>Параметры публикации, свойства и переменные SQLCMD

Операция публикации SqlPackage.exe заключается в добавочном обновлении схемы целевой базы данных в соответствии со структурой базы данных-источника. Публикация пакета развертывания, содержащего пользовательские данные для всех или для некоторых таблиц, помимо схемы будет приводить к обновлению этих табличных данных. Развертывание данных приводит к перезаписи схемы и данных в существующих таблицах целевой базы данных. Развертывание данных не будет изменять существующие схему или данные в целевой базе данных для таблиц, не включенных в пакет развертывания.  

### <a name="help-for-publish-action"></a>Справка по действию публикации

|Параметр|Краткая форма|Значение|Описание|
|---|---|---|---|
|**/Action:**|**/a**|Публикация|Указывает действие, подлежащее выполнению. |
|**/AccessToken:**|**/at**|{строка}| Указывает маркер доступа для проверки подлинности на основе маркеров. Этот маркер используется при подключении к целевой базе данных. |
|**/AzureKeyVaultAuthMethod:**|**/akv**|{Interactive&#124;ClientIdSecret}|Указывает способ проверки подлинности для доступа к Azure Key Vault. |
|**/ClientId:**|**/cid**|{строка}|Указывает идентификатор клиента, который будет использоваться при проверке подлинности в Azure Key Vault при необходимости. |
|**/DeployScriptPath:**|**/dsp**|{строка}|Указывает необязательный путь для вывода скрипта развертывания. В среде Azure при использовании команд TSQL для создания или изменения базы данных master скрипт будет записан по тому же пути, но с именем выходного файла Filename_Master.sql. |
|**/DeployReportPath:**|**/drp**|{строка}|Указывает необязательный путь для вывода XML-файла отчета о развертывании. |
|**/Diagnostics:**|**/d**|{True&#124;False}|Указывает, следует ли выводить сведения из журнала диагностики в консоль. Значение по умолчанию — False. |
|**/DiagnosticsFile:**|**/df**|{строка}|Указывает файл, в котором следует вести журнал диагностики. |
|**/MaxParallelism:**|**/mp**|{целое_число}| Задает степень параллелизма для параллельных операций с базой данных. Значение по умолчанию: 8. |
|**/OverwriteFiles:**|**/of**|{True&#124;False}|Указывает, должна ли программа sqlpackage.exe перезаписывать существующие файлы. Задание значения false приводит к тому, что программа sqlpackage.exe прерывает действие при обнаружении существующего файла. Значение по умолчанию равно True. |
|**/Profile:**|**/pr**|{строка}|Указывает путь к файлу приложения уровня данных профиля публикации. Профиль определяет коллекцию свойств и переменных, которые должны использоваться при формировании выходных данных.|
|**/Properties:**|**/p**|{имя_свойства}={значение}|Указывает пару "имя-значение" для свойства действия; {имя_свойства}={значение}. Имена свойств действия см. в справке по данным действиям. Например, sqlpackage.exe /Action:Publish /?.|
|**/Quiet:**|**/q**|{True&#124;False}|Указывает, происходит ли подавление подробного отзыва. Значение по умолчанию — False.|
|**/Secret:**|**/secr**|{строка}|Указывает секрет клиента, который будет использоваться при проверке подлинности в Azure Key Vault при необходимости. |
|**/SourceConnectionString:**|**/scs**|{строка}|Указывает допустимую строку подключения SQL Server/Azure для базы данных-источника. Если этот параметр указан, ему будет отдаваться предпочтение перед всеми остальными параметрами источника. |
|**/SourceDatabaseName:**|**/sdn**|{строка}|Определяет имя базы данных-источника. |
|**/SourceEncryptConnection:**|**/sec**|{True&#124;False}|Указывает, следует ли использовать шифрование SQL для соединения с базой данных-источником. |
|**/SourceFile:**|**/sf**|{строка}|Указывает имя исходного файла, который должен использоваться в качестве источника действия вместо базы данных. Если используется этот параметр, все остальные параметры источника будут недействительны. |
|**/SourcePassword:**|**/sp**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пароль для доступа к базе данных-источнику. |
|**/SourceServerName:**|**/ssn**|{строка}|Определяет имя сервера, где размещается база данных-источник. |
|**/SourceTimeout:**|**/st**|{целое_число}|Задает время ожидания подключения к базе данных-источнику (в секундах). |
|**/SourceTrustServerCertificate:**|**/stsc**|{True&#124;False}|Определяет, используется ли протокол TLS для шифрования подключения к базе данных-источнику без прохода по цепочке сертификатов для проверки доверия. |
|**/SourceUser:**|**/su**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пользователя SQL Server для доступа к базе данных-источнику. |
|**/TargetConnectionString:**|**/tcs**|{строка}|Указывает допустимую строку подключения SQL Server/Azure для целевой базы данных. Если этот параметр указан, ему будет отдаваться предпочтение перед всеми остальными параметрами целевого объекта. |
|**/TargetDatabaseName:**|**/tdn**|{строка}|Задает переопределение имени для целевой базы данных действия sqlpackage.exe. |
|**/TargetEncryptConnection:**|**/tec**|{True&#124;False}|Определяет, должно ли использоваться шифрование SQL для подключения к целевой базе данных. |
|**/TargetPassword:**|**/tp**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пароль для доступа к целевой базе данных. |
|**/TargetServerName:**|**/tsn**|{строка}|Определяет имя сервера, где размещается целевая база данных. |
|**/TargetTimeout:**|**/tt**|{целое_число}|Задает время ожидания подключения к целевой базе данных (в секундах). Для AAD рекомендуется, чтобы это значение было больше или равно 30 с.|
|**/TargetTrustServerCertificate:**|**/ttsc**|{True&#124;False}|Определяет, используется ли протокол TLS для шифрования подключения к целевой базе данных без прохода по цепочке сертификатов для проверки доверия. |
|**/TargetUser:**|**/tu**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пользователя SQL Server для доступа к целевой базе данных. |
|**/TenantId:**|**/tid**|{строка}|Представляет ИД клиента AAD или доменное имя. Этот параметр необходим для поддержки гостевых или импортированных пользователей AAD, а также учетных записей Майкрософт, например outlook.com, hotmail.com или live.com. Если этот параметр пропущен, будет использоваться ИД клиента по умолчанию для AAD. При этом предполагается, что прошедший проверку подлинности пользователь является собственным пользователем для этого AD. Однако в этом случае все гостевые или импортированные пользователи и (или) учетные записи Майкрософт, размещенные в этой службе AAD, не поддерживаются, и операция завершится ошибкой. <br/> Дополнительные сведения об универсальной проверке подлинности AD DS см. в [этой статье](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/UniversalAuthentication:**|**/ua**|{True&#124;False}|Указывает, следует ли использовать универсальную проверку подлинности. Если задано значение true, протокол интерактивной проверки подлинности активируется с поддержкой MFA. Этот параметр также можно применять для проверки подлинности AAD без MFA, используя интерактивный протокол, где пользователю необходимо ввести имя пользователя и пароль, или встроенную проверку подлинности (учетные данные Windows). Если для элемента /UniversalAuthentication задано значение True, в элементе SourceConnectionString (/scs) не может быть указана проверка подлинности AAD. Если для элемента /UniversalAuthentication задано значение False, в элементе SourceConnectionString (/scs) должна быть указана проверка подлинности AAD. <br/> Дополнительные сведения об универсальной проверке подлинности AD DS см. в [этой статье](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/Variables:**|**/v**|{имя_свойства}={значение}|Указывает пару "имя-значение" для переменной действия; {имя_переменной}={значение}. DACPAC-файл содержит список действительных переменных SQLCMD. Если значения каких-либо переменных не будут указаны, возникнет ошибка. |

### <a name="properties-specific-to-the-publish-action"></a>Свойства, относящиеся к действию публикации

|Свойство|Значение|Описание|
|---|---|---|
|**/p:**|AdditionalDeploymentContributorArguments=(STRING)|Задает дополнительные аргументы участника развертывания для участников развертывания. Это должен быть список значений, разделенных точками с запятой.|
|**/p:**|AdditionalDeploymentContributors=(STRING)|Указывает дополнительных участников развертывания, которые должны выполняться при развертывании пакета DACPAC. Это должен быть список идентификаторов или полных имен участников сборки, разделенных точками с запятой.|
|**/p:**|AdditionalDeploymentContributorPaths=(STRING)| Указывает пути для загрузки дополнительных участников развертывания. Это должен быть список значений, разделенных точками с запятой. | 
|**/p:**|AllowDropBlockingAssemblies=(BOOLEAN)|Это свойство используется развертыванием SQLCLR для удаления блокирующих сборок как часть плана развертывания. По умолчанию все блокирующие сборки/ссылки на сборки блокируют обновление сборки, если ссылка на сборку должна быть удалена.|
|**/p:**|AllowIncompatiblePlatform=(BOOLEAN)|Указывает, пытаться ли выполнить это действие, несмотря на несовместимость платформ SQL Server.|
|**/p:**|AllowUnsafeRowLevelSecurityDataMovement=(BOOLEAN)|Если свойство имеет значение true, блокировка перемещения данных в таблице с безопасностью на уровне строк отключается. Значение по умолчанию — false.|
|**/p:**|BackupDatabaseBeforeChanges=(BOOLEAN)|Создает резервную копию базы данных перед развертыванием любых изменений.|
|**/p:**|BlockOnPossibleDataLoss=(BOOLEAN 'True')|Указывает, что следует завершать эпизод публикации, если есть возможность потери данных в результате операции публикации.|
|**/p:**|BlockWhenDriftDetected=(BOOLEAN 'True')|Указывает, следует ли блокировать обновление базы данных, схема которой больше не соответствует регистрации или регистрация которой удалена.|
|**/p:**|CommandTimeout=(INT32 '60')|Задает время ожидания команды в секундах при выполнении запросов к SQL Server.|
|**/p:**|CommentOutSetVarDeclarations=(BOOLEAN)|Указывает, будет ли объявление переменных SETVAR закомментировано в созданном скрипте публикации. Эту возможность можно выбрать, если планируется задавать значения в командной строке во время публикации с помощью такого средства, как SQLCMD.EXE.|
|**/p:**|CompareUsingTargetCollation=(BOOLEAN)|Этот параметр указывает, как обрабатываются параметры сортировки базы данных во время развертывания. По умолчанию параметры сортировки целевой базы данных обновляются, если они не совпадают с параметрами сортировки, указанными источником. Если задан этот параметр, использоваться будут параметры сортировки целевой базы данных (или сервера).|
|**/p:**|CreateNewDatabase=(BOOLEAN)|Указывает, обновляется ли целевая база данных, или ее нужно удалить и создать заново при публикации базы данных.|
|**/p:**|DatabaseEdition=({Basic&#124;Standard&#124;Premium&#124;DataWarehouse&#124;GeneralPurpose&#124;BusinessCritical&#124;Hyperscale&#124;Default} 'Default')|Определяет выпуск Базы данных SQL Azure.|
|**/p:**|DatabaseLockTimeout=(INT32 '60')|Позволяет задать превышение времени ожидания блокировки в секундах для базы данных при выполнении запросов к SQL Server. Для ожидания без ограничений используйте значение "-1".|
|**/p:**|DatabaseMaximumSize=(INT32)|Определяет максимальный размер в ГБ для базы данных SQL Azure.|
|**/p:**|DatabaseServiceObjective=(STRING)|Определяет уровень производительности для базы данных SQL Azure, например "P0" или "S1".|
|**/p:**|DeployDatabaseInSingleUserMode=(BOOLEAN)|Если указано значение true, то перед развертыванием база данных переводится в однопользовательский режим.|
|**/p:**|DisableAndReenableDdlTriggers=(BOOLEAN 'True')|Указывает, следует ли отключить триггеры языка описания данных DDL в начале процесса публикации и включить их в конце.|
|**/p:**|DoNotAlterChangeDataCaptureObjects=(BOOLEAN 'True')|Если указано значение true, объекты отслеживания измененных данных не меняются.|
|**/p:**|DoNotAlterReplicatedObjects=(BOOLEAN 'True')|Указывает, определяются ли во время проверки реплицируемые объекты.|
|**/p:**|DoNotDropObjectType=(STRING)|Тип объекта, который нельзя удалять, если элемент DropObjectsNotInSource имеет значение true. Допустимые имена типов объектов: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.|
|**/p:**|DoNotDropObjectTypes=(STRING)|Список типов объектов (разделенных точками с запятой), которые не следует удалять, если параметр DropObjectsNotInSource имеет значение true. Допустимые имена типов объектов: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.|
|**/p:**|DropConstraintsNotInSource=(BOOLEAN 'True')|Указывает, будут ли ограничения, которые не существуют в моментальном снимке базы данных (DACPAC), удалены из целевой базы данных при выполнении публикации.|
|**/p:**|DropDmlTriggersNotInSource=(BOOLEAN 'True')|Указывает, будут ли триггеры DML, которые не существуют в моментальном снимке базы данных (DACPAC), удалены из целевой базы данных при выполнении публикации.|
|**/p:**|DropExtendedPropertiesNotInSource=(BOOLEAN 'True')|Указывает, будут ли при выполнении публикации в базе данных удалены расширенные свойства, которые не существуют в моментальном снимке базы данных (DACPAC).|
|**/p:**|DropIndexesNotInSource=(BOOLEAN 'True')|Указывает, будут ли индексы, которые не существуют в моментальном снимке базы данных (DACPAC), удалены из целевой базы данных при выполнении публикации.|
|**/p:**|DropObjectsNotInSource=(BOOLEAN)|Указывает, будут ли объекты, которые отсутствуют в моментальном снимке базы данных (DACPAC), удалены из целевой базы данных при выполнении публикации. Это значение имеет приоритет над элементом DropExtendedProperties.|
|**/p:**|DropPermissionsNotInSource=(BOOLEAN)|Указывает, будут ли разрешения, которые не существуют в моментальном снимке базы данных (DACPAC), удалены из целевой базы данных при выполнении публикации обновлений.|
|**/p:**|DropRoleMembersNotInSource=(BOOLEAN)|Указывает, будут ли члены ролей, которые не определены в моментальном снимке базы данных (DACPAC), удалены из целевой базы данных при выполнении публикации обновлений.|
|**/p:**|DropStatisticsNotInSource=(BOOLEAN 'True')|Указывает, будет ли статистика, которая отсутствует в файле моментального снимка базы данных (DACPAC), удалена из целевой базы данных при публикации в базе данных.|
|**/p:**|ExcludeObjectType=(STRING)|Тип объекта, который должен игнорироваться во время развертывания. Допустимые имена типов объектов: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.|
|**/p:**|ExcludeObjectTypes=(STRING)|Список типов объектов, разделенных точками с запятой, которые должны игнорироваться во время развертывания. Допустимые имена типов объектов: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.|
|**/p:**|GenerateSmartDefaults=(BOOLEAN)|Автоматически определяет значение по умолчанию при обновлении таблицы, содержащей данные со столбцом, который не допускает значения NULL.|
|**/p:**|IgnoreAnsiNulls=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в параметре ANSI NULLS при публикации в базе данных.|
|**/p:**|IgnoreAuthorizer=(BOOLEAN)|Определяет, пропускаются или обновляются различия в Authorizer при публикации в базе данных.|
|**/p:**|IgnoreColumnCollation=(BOOLEAN)|Определяет, пропускаются или обновляются различия в параметрах сортировки столбцов при публикации в базе данных.|
|**/p:**|IgnoreColumnOrder=(BOOLEAN)|Указывает, следует ли игнорировать или обновлять различия в порядке столбцов таблицы при публикации в базе данных.|
|**/p:**|IgnoreComments=(BOOLEAN)|Определяет, пропускаются или обновляются различия в комментариях при публикации в базе данных.|
|**/p:**|IgnoreCryptographicProviderFilePath=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в пути к файлам для поставщика служб шифрования при публикации в базе данных.|
|**/p:**|IgnoreDdlTriggerOrder=(BOOLEAN)|Определяет, пропускаются или обновляются различия в порядке триггеров для языка описания данных DDL при публикации в базе данных или на сервере.|
|**/p:**|IgnoreDdlTriggerState=(BOOLEAN)|Определяет, пропускаются или обновляются различия в состоянии (включен-выключен) триггеров языка описания данных DDL при публикации в базе данных.|
|**/p:**|IgnoreDefaultSchema=(BOOLEAN)|Определяет, пропускаются или обновляются различия в схеме по умолчанию при публикации в базе данных.|
|**/p:**|IgnoreDmlTriggerOrder=(BOOLEAN)|Определяет, пропускаются или обновляются различия в порядке триггеров языка обработки данных DML при публикации в базе данных.|
|**/p:**|IgnoreDmlTriggerState=(BOOLEAN)|Определяет, пропускаются или обновляются различия в состоянии (включен–выключен) триггеров DML при публикации в базе данных.|
|**/p:**|IgnoreExtendedProperties=(BOOLEAN)|Определяет, пропускаются или обновляются различия в расширенных свойствах при публикации в базе данных.|
|**/p:**|IgnoreFileAndLogFilePath=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в путях к файлам и файлам журнала при публикации в базе данных.|
|**/p:**|IgnoreFilegroupPlacement=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в размещении объектов в файловых группах FILEGROUP при публикации в базе данных.|
|**/p:**|IgnoreFileSize=(BOOLEAN 'True')|Определяет, создается ли предупреждение о различиях в размерах файлов при публикации в базе данных.|
|**/p:**|IgnoreFillFactor=(BOOLEAN 'True')|Определяет, создается ли предупреждение о различиях в коэффициенте заполнения для хранилища индексов при публикации в базе данных.|
|**/p:**|IgnoreFullTextCatalogFilePath=(BOOLEAN 'True')|Определяет, создается ли предупреждение о различиях в пути к файлам для полнотекстового каталога при публикации в базе данных.|
|**/p:**|IgnoreIdentitySeed=(BOOLEAN)|Определяет, пропускаются или обновляются различия в начальном значении для столбца идентификаторов при публикации обновлений в базе данных.|
|**/p:**|IgnoreIncrement=(BOOLEAN)|Определяет, пропускаются или обновляются различия в шаге приращения для столбца идентификаторов при публикации в базе данных.|
|**/p:**|IgnoreIndexOptions=(BOOLEAN)|Определяет, пропускаются или обновляются различия в параметрах индексов при публикации в базе данных.|
|**/p:**|IgnoreIndexPadding=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в заполнении индекса при публикации в базе данных.|
|**/p:**|IgnoreKeywordCasing=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в регистре ключевых слов при публикации в базе данных.|
|**/p:**|IgnoreLockHintsOnIndexes=(BOOLEAN)|Указывает, следует пропускать или обновлять различия в указаниях блокировки для индексов во время публикации в базе данных.|
|**/p:**|IgnoreLoginSids=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в идентификаторе безопасности (SID) при публикации в базе данных.|
|**/p:**|IgnoreNotForReplication=(BOOLEAN)|Определяет, пропускаются или обновляются параметры "не для репликации" при публикации в базе данных.|
|**/p:**|IgnoreObjectPlacementOnPartitionScheme=(BOOLEAN 'True')|Определяет, пропускается или обновляется размещение объекта в схеме секционирования при публикации в базе данных.|
|**/p:**|IgnorePartitionSchemes=(BOOLEAN)|Определяет, пропускаются или обновляются различия в функциях и схемах секционирования при публикации в базе данных.|
|**/p:**|IgnorePermissions=(BOOLEAN)|Определяет, пропускаются или обновляются различия в разрешениях при публикации в базе данных.|
|**/p:**|IgnoreQuotedIdentifiers=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в параметре нестандартных идентификаторов при публикации в базе данных.|
|**/p:**|IgnoreRoleMembership=(BOOLEAN)|Указывает, следует пропускать или обновлять различия в членстве в роли имен входа во время публикации в базе данных.|
|**/p:**|IgnoreRouteLifetime=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в продолжительности периода, в течение которого SQL Server хранит маршрут в таблице маршрутизации, при публикации в базе данных.|
|**/p:**|IgnoreSemicolonBetweenStatements=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в точках с запятой между инструкциями T-SQL при публикации в базе данных.|
|**/p:**|IgnoreTableOptions=(BOOLEAN)|Определяет, пропускаются или обновляются различия в параметрах таблиц при публикации в базе данных.|
|**/p:**|IgnoreTablePartitionOptions=(BOOLEAN)|Определяет, пропускаются или обновляются различия в параметрах секций таблиц при публикации в базе данных.  Этот параметр применяется только к базам данных пула SQL Azure Synapse Analytics (хранилища данных).|
|**/p:**|IgnoreUserSettingsObjects=(BOOLEAN)|Определяет, пропускаются или обновляются различия в объектах параметров пользователя при публикации в базе данных.|
|**/p:**|IgnoreWhitespace=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в пробелах при публикации в базе данных.|
|**/p:**|IgnoreWithNocheckOnCheckConstraints=(BOOLEAN)|Определяет, пропускаются или обновляются различия в значении предложения WITH NOCHECK для проверочных ограничений при публикации.|
|**/p:**|IgnoreWithNocheckOnForeignKeys=(BOOLEAN)|Определяет, пропускаются или обновляются различия в значении предложения WITH NOCHECK для внешних ключей при публикации в базе данных.|
|**/p:**|IncludeCompositeObjects=(BOOLEAN)|Включить все составные элементы в единую операцию публикации.|
|**/p:**|IncludeTransactionalScripts=(BOOLEAN)|Определяет, будут ли по возможности использоваться инструкции транзакций при публикации в базе данных.|
|**/p:**|LongRunningCommandTimeout=(INT32)|Позволяет задать время ожидания в секундах для длительной команды при выполнении запросов к SQL Server. Для ожидания без ограничений используйте значение "0".|
|**/p:**|NoAlterStatementsToChangeClrTypes=(BOOLEAN)|Указывает, что при публикации (при наличии различий) вместо выполнения инструкции ALTER ASSEMBLY сборка всегда должна удаляться и создаваться повторно.|
|**/p:**|PopulateFilesOnFileGroups=(BOOLEAN 'True')|Указывает, создается ли файл при создании файловой группы FileGroup в целевой базе данных.|
|**/p:**|RegisterDataTierApplication=(BOOLEAN)|Указывает, регистрируется ли схема на сервере базы данных.|
|**/p:**|RunDeploymentPlanExecutors=(BOOLEAN)|Указывает, должны ли выполняться участники DeploymentPlanExecutor при выполнении других операций.|
|**/p:**|ScriptDatabaseCollation=(BOOLEAN)|Определяет, пропускаются или обновляются различия в параметрах сортировки базы данных при публикации в базе данных.|
|**/p:**|ScriptDatabaseCompatibility=(BOOLEAN)|Определяет, пропускаются или обновляются различия в уровне совместимости базы данных при публикации в базе данных.|
|**/p:**|ScriptDatabaseOptions=(BOOLEAN 'True')|Определяет, будут ли свойства целевой базы данных задаваться или обновляться в рамках действия публикации.|
|**/p:**|ScriptDeployStateChecks=(BOOLEAN)|Определяет, создаются ли инструкции в скрипте публикации, чтобы проверить соответствие имен базы данных и сервера с именами, указанными в проекте базы данных.|
|**/p:**|ScriptFileSize=(BOOLEAN)|Определяет, указывается ли размер при добавлении файла в файловую группу.|
|**/p:**|ScriptNewConstraintValidation=(BOOLEAN 'True')|В конце публикации все ограничения будут проверяться как один набор, избегая ошибок данных, вызванных ограничением проверки или внешнего ключа в середине публикации. Если этот параметр имеет значение False, ограничения публикуются без проверки соответствующих данных.|
|**/p:**|ScriptRefreshModule=(BOOLEAN 'True')|Включать инструкции обновления в конец скрипта публикации.|
|**/p:**|Storage=({File&#124;Memory})|Указывает, как сохраняются элементы при построении модели базы данных. Для обеспечения высокой производительности по умолчанию используется значение InMemory. Для больших баз данных требуется хранилище с использованием файлов.|
|**/p:**|TreatVerificationErrorsAsWarnings=(BOOLEAN)|Указывает, должны ли ошибки, обнаруженные во время проверки публикации, обрабатываться как предупреждения. Проверка выполняется применительно к сформированному плану развертывания перед его выполнением применительно к целевой базе данных. Проверка плана выявляет такие проблемы, как потеря объектов, существующих только в целевой базе данных (например, индексов), которые должны быть удалены в процессе внесения изменений. Кроме того, она выявляет ситуации, когда зависимости (например, таблицы или представления) существуют в результате наличия ссылок на составной проект, но отсутствуют в целевой базе данных. Это можно сделать, чтобы получить полный список всех проблем, вместо завершения действия публикации при первой ошибке.
|**/p:**|UnmodifiableObjectWarnings=(BOOLEAN 'True')|Указывает, следует ли формировать предупреждения, если обнаружены различия в объектах, которые не могут быть изменены (например, если отличаются размеры или пути файлов).|
|**/p:**|VerifyCollationCompatibility=(BOOLEAN 'True')|Указывает, проверяется ли совместимость параметров сортировки.|
|**/p:**|VerifyDeployment=(BOOLEAN 'True')|Указывает, следует ли выполнять проверки перед началом публикации, останавливаемой при возникновении проблем, которые могут заблокировать успешную публикацию. Например, публикация может остановиться в случае, если во время публикации возникли ошибки, связанные с тем, что внешние ключи в целевой базе данных не существуют в проекте базы данных.|
|

### <a name="sqlcmd-variables"></a>Переменные SQLCMD

В следующей таблице описан формат параметра, который позволит переопределить значение команды SQL (**sqlcmd**) значением переменной, заданной при публикации. Значения переменных, заданные в командной строке, переопределяют другие значения, присвоенные переменной (например, в профиле публикации).  
  
|Параметр|По умолчанию|Описание|  
|-------------|-----------|---------------|  
|**/Variables:{PropertyName}={Value}**||Указывает пару "имя-значение" для переменной действия; {имя_переменной}={значение}. DACPAC-файл содержит список действительных переменных SQLCMD. Если значения каких-либо переменных не будут указаны, возникнет ошибка.|  
  
## <a name="export-parameters-and-properties"></a>Параметры и свойства экспорта

Действие экспорта SqlPackage.exe экспортирует активную базу данных из SQL Server или Базы данных SQL Azure в пакет BACPAC (BACPAC-файл). По умолчанию данные для всех таблиц будут включены в BACPAC-файл. При необходимости можно указать только подмножество таблиц, для которых следует выполнить экспорт данных. Проверка для действия Export обеспечивает совместимость базы данных SQL Azure со всей целевой базой данных, даже если для экспорта указано подмножество таблиц.  
  
### <a name="help-for-export-action"></a>Справка по действию экспорта

|Параметр|Краткая форма|Значение|Описание|
|---|---|---|---|
|**/Action:**|**/a**|Экспорт|Указывает действие, подлежащее выполнению. |
|**/AccessToken:**|**/at**|{строка}| Указывает маркер доступа для проверки подлинности на основе маркеров. Этот маркер используется при подключении к целевой базе данных. |
|**/Diagnostics:**|**/d**|{True&#124;False}|Указывает, следует ли выводить сведения из журнала диагностики в консоль. Значение по умолчанию — False. |
|**/DiagnosticsFile:**|**/df**|{строка}|Указывает файл, в котором следует вести журнал диагностики. |
|**/MaxParallelism:**|**/mp**|{целое_число}| Задает степень параллелизма для параллельных операций с базой данных. Значение по умолчанию: 8. |
|**/OverwriteFiles:**|**/of**|{True&#124;False}|Указывает, должна ли программа sqlpackage.exe перезаписывать существующие файлы. Задание значения false приводит к тому, что программа sqlpackage.exe прерывает действие при обнаружении существующего файла. Значение по умолчанию равно True. |
|**/Properties:**|**/p**|{имя_свойства}={значение}|Указывает пару "имя-значение" для свойства действия; {имя_свойства}={значение}. Имена свойств действия см. в справке по данным действиям. Например: sqlpackage.exe /Action:Export /?.|
|**/Quiet:**|**/q**|{True&#124;False}|Указывает, происходит ли подавление подробного отзыва. Значение по умолчанию — False.|
|**/SourceConnectionString:**|**/scs**|{строка}|Указывает допустимую строку подключения SQL Server/Azure для базы данных-источника. Если этот параметр указан, ему будет отдаваться предпочтение перед всеми остальными параметрами источника. |
|**/SourceDatabaseName:**|**/sdn**|{строка}|Определяет имя базы данных-источника. |
|**/SourceEncryptConnection:**|**/sec**|{True&#124;False}|Указывает, следует ли использовать шифрование SQL для соединения с базой данных-источником. |
|**/SourcePassword:**|**/sp**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пароль для доступа к базе данных-источнику. |
|**/SourceServerName:**|**/ssn**|{строка}|Определяет имя сервера, где размещается база данных-источник. |
|**/SourceTimeout:**|**/st**|{целое_число}|Задает время ожидания подключения к базе данных-источнику (в секундах). |
|**/SourceTrustServerCertificate:**|**/stsc**|{True&#124;False}|Определяет, используется ли протокол TLS для шифрования подключения к базе данных-источнику без прохода по цепочке сертификатов для проверки доверия. |
|**/SourceUser:**|**/su**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пользователя SQL Server для доступа к базе данных-источнику. |
|**/TargetFile:**|**/tf**|{строка}| Указывает целевой файл (то есть DACPAC-файл) для использования в качестве целевого объекта действия вместо базы данных. Если используется этот параметр, все остальные параметры целевого объекта будут недействительны. Этот параметр будет недопустимым для действий, которые поддерживают только целевые объекты базы данных.|
|**/TenantId:**|**/tid**|{строка}|Представляет ИД клиента AAD или доменное имя. Этот параметр необходим для поддержки гостевых или импортированных пользователей AAD, а также учетных записей Майкрософт, например outlook.com, hotmail.com или live.com. Если этот параметр пропущен, будет использоваться ИД клиента по умолчанию для AAD. При этом предполагается, что прошедший проверку подлинности пользователь является собственным пользователем для этого AD. Однако в этом случае все гостевые или импортированные пользователи и (или) учетные записи Майкрософт, размещенные в этой службе AAD, не поддерживаются, и операция завершится ошибкой. <br/> Дополнительные сведения об универсальной проверке подлинности AD DS см. в [этой статье](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/UniversalAuthentication:**|**/ua**|{True&#124;False}|Указывает, следует ли использовать универсальную проверку подлинности. Если задано значение true, протокол интерактивной проверки подлинности активируется с поддержкой MFA. Этот параметр также можно применять для проверки подлинности AAD без MFA, используя интерактивный протокол, где пользователю необходимо ввести имя пользователя и пароль, или встроенную проверку подлинности (учетные данные Windows). Если для элемента /UniversalAuthentication задано значение True, в элементе SourceConnectionString (/scs) не может быть указана проверка подлинности AAD. Если для элемента /UniversalAuthentication задано значение False, в элементе SourceConnectionString (/scs) должна быть указана проверка подлинности AAD. <br/> Дополнительные сведения об универсальной проверке подлинности AD DS см. в [этой статье](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|

### <a name="properties-specific-to-the-export-action"></a>Свойства, относящиеся к действию экспорта

|Свойство|Значение|Описание|
|---|---|---|
|**/p:**|CommandTimeout=(INT32 '60')|Задает время ожидания команды в секундах при выполнении запросов к SQL Server.|
|**/p:**|DatabaseLockTimeout=(INT32 '60')| Позволяет задать превышение времени ожидания блокировки в секундах для базы данных при выполнении запросов к SQL Server. Для ожидания без ограничений используйте значение "-1".|
|**/p:**|LongRunningCommandTimeout=(INT32)| Позволяет задать время ожидания в секундах для длительной команды при выполнении запросов к SQL Server. Для ожидания без ограничений используйте значение "0".|
|**/p:**|Storage=({File&#124;Memory} 'File')|Указывает тип резервного хранилища для модели схемы, используемой во время извлечения.|
|**/p:**|TableData=(STRING)|Указывает таблицу, из которой будут извлечены данные. Укажите имя таблицы со скобками или без скобок. Имя должно быть указано в формате: имя_схемы.идентификатор_таблицы. Этот параметр можно указывать несколько раз.|
|**/p:**|TempDirectoryForTableData=(STRING)|Указывает временный каталог, используемый для буферизации табличных данных перед записью в файл пакета.|
|**/p:**|TargetEngineVersion=({Default&#124;Latest&#124;V11&#124;V12} 'Latest')|Указывает предполагаемую версию целевой подсистемы. Это влияет на разрешение объектов, поддерживаемых серверами базы данных SQL Azure с возможностями версии 12, например оптимизированные для памяти таблицы в созданном BACPAC-элементе.|
|**/p:**|VerifyFullTextDocumentTypesSupported=(BOOLEAN)|Указывает, следует ли проверять поддерживаемые типы полнотекстовых документов для базы данных SQL Microsoft Azure версии 12.|
  
## <a name="import-parameters-and-properties"></a>Параметры и свойства импорта

Действие импорта SqlPackage.exe импортирует схему и данные таблицы из BACPAC-файла пакета BACPAC в новую или пустую базу данных в SQL Server или Базе данных SQL Azure. Во время операции импорта в существующую базу данных в целевой базе данных не могут находиться никакие определяемые пользователем объекты схемы.  
  
### <a name="help-for-command-actions"></a>Справка по действиям команд

|Параметр|Краткая форма|Значение|Описание|
|---|---|---|---|
|**/Action:**|**/a**|Импорт|Указывает действие, подлежащее выполнению. |
|**/AccessToken:**|**/at**|{строка}| Указывает маркер доступа для проверки подлинности на основе маркеров. Этот маркер используется при подключении к целевой базе данных. |
|**/Diagnostics:**|**/d**|{True&#124;False}|Указывает, следует ли выводить сведения из журнала диагностики в консоль. Значение по умолчанию — False. |
|**/DiagnosticsFile:**|**/df**|{строка}|Указывает файл, в котором следует вести журнал диагностики. |
|**/MaxParallelism:**|**/mp**|{целое_число}| Задает степень параллелизма для параллельных операций с базой данных. Значение по умолчанию: 8. |
|**/Properties:**|**/p**|{имя_свойства}={значение}|Указывает пару "имя-значение" для свойства действия; {имя_свойства}={значение}. Имена свойств действия см. в справке по данным действиям. Например: sqlpackage.exe /Action:Import /?.|
|**/Quiet:**|**/q**|{True&#124;False}|Указывает, происходит ли подавление подробного отзыва. Значение по умолчанию — False.|
|**/SourceFile:**|**/sf**|{строка}|Указывает имя исходного файла, который должен использоваться в качестве источника действия. Если используется этот параметр, все остальные параметры источника будут недействительны. |
|**/TargetConnectionString:**|**/tcs**|{строка}|Указывает допустимую строку подключения SQL Server/Azure для целевой базы данных. Если этот параметр указан, ему будет отдаваться предпочтение перед всеми остальными параметрами целевого объекта. |
|**/TargetDatabaseName:**|**/tdn**|{строка}|Задает переопределение имени для целевой базы данных действия sqlpackage.exe. |
|**/TargetEncryptConnection:**|**/tec**|{True&#124;False}|Определяет, должно ли использоваться шифрование SQL для подключения к целевой базе данных. |
|**/TargetPassword:**|**/tp**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пароль для доступа к целевой базе данных. |
|**/TargetServerName:**|**/tsn**|{строка}|Определяет имя сервера, где размещается целевая база данных. |
|**/TargetTimeout:**|**/tt**|{целое_число}|Задает время ожидания подключения к целевой базе данных (в секундах). Для AAD рекомендуется, чтобы это значение было больше или равно 30 с.|
|**/TargetTrustServerCertificate:**|**/ttsc**|{True&#124;False}|Определяет, используется ли протокол TLS для шифрования подключения к целевой базе данных без прохода по цепочке сертификатов для проверки доверия. |
|**/TargetUser:**|**/tu**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пользователя SQL Server для доступа к целевой базе данных. |
|**/TenantId:**|**/tid**|{строка}|Представляет ИД клиента AAD или доменное имя. Этот параметр необходим для поддержки гостевых или импортированных пользователей AAD, а также учетных записей Майкрософт, например outlook.com, hotmail.com или live.com. Если этот параметр пропущен, будет использоваться ИД клиента по умолчанию для AAD. При этом предполагается, что прошедший проверку подлинности пользователь является собственным пользователем для этого AD. Однако в этом случае все гостевые или импортированные пользователи и (или) учетные записи Майкрософт, размещенные в этой службе AAD, не поддерживаются, и операция завершится ошибкой. <br/> Дополнительные сведения об универсальной проверке подлинности AD DS см. в [этой статье](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/UniversalAuthentication:**|**/ua**|{True&#124;False}|Указывает, следует ли использовать универсальную проверку подлинности. Если задано значение true, протокол интерактивной проверки подлинности активируется с поддержкой MFA. Этот параметр также можно применять для проверки подлинности AAD без MFA, используя интерактивный протокол, где пользователю необходимо ввести имя пользователя и пароль, или встроенную проверку подлинности (учетные данные Windows). Если для элемента /UniversalAuthentication задано значение True, в элементе SourceConnectionString (/scs) не может быть указана проверка подлинности AAD. Если для элемента /UniversalAuthentication задано значение False, в элементе SourceConnectionString (/scs) должна быть указана проверка подлинности AAD. <br/> Дополнительные сведения об универсальной проверке подлинности AD DS см. в [этой статье](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|

Свойства, относящиеся к действию импорта:

|Свойство|Значение|Описание|
|---|---|---|
|**/p:**|CommandTimeout=(INT32 '60')|Задает время ожидания команды в секундах при выполнении запросов к SQL Server.|
|**/p:**|DatabaseEdition=({Basic&#124;Standard&#124;Premium&#124;DataWarehouse&#124;GeneralPurpose&#124;BusinessCritical&#124;Hyperscale&#124;Default} 'Default')|Определяет выпуск Базы данных SQL Azure.|
|**/p:**|DatabaseLockTimeout=(INT32 '60')| Позволяет задать превышение времени ожидания блокировки в секундах для базы данных при выполнении запросов к SQL Server. Для ожидания без ограничений используйте значение "-1".|
|**/p:**|DatabaseMaximumSize=(INT32)|Определяет максимальный размер в ГБ для базы данных SQL Azure.|
|**/p:**|DatabaseServiceObjective=(STRING)|Определяет уровень производительности для базы данных SQL Azure, например "P0" или "S1".|
|**/p:**|ImportContributorArguments=(STRING)|Указывает аргументы для участников развертывания. Это должен быть список значений, разделенных точками с запятой.|
|**/p:**|ImportContributors=(STRING)|Указывает участников развертывания, которые должны выполняться при импорте пакета BACPAC. Это должен быть список идентификаторов или полных имен участников сборки, разделенных точками с запятой.|
|**/p:**|ImportContributorPaths=(STRING)|Указывает пути для загрузки дополнительных участников развертывания. Это должен быть список значений, разделенных точками с запятой. |
|**/p:**|LongRunningCommandTimeout=(INT32)| Позволяет задать время ожидания в секундах для длительной команды при выполнении запросов к SQL Server. Для ожидания без ограничений используйте значение "0".|
|**/p:**|Storage=({File&#124;Memory})|Указывает, как сохраняются элементы при построении модели базы данных. Для обеспечения высокой производительности по умолчанию используется значение InMemory. Для больших баз данных требуется хранилище с использованием файлов.|
  
## <a name="deployreport-parameters-and-properties"></a>Параметры и свойства DeployReport

Действие с отчетом программы **SqlPackage.exe** создает XML-отчет по изменениям, которые должны быть внесены в результате публикации.  
  
### <a name="help-for-deployreport-action"></a>Справка по действию DeployReport

|Параметр|Краткая форма|Значение|Описание|
|---|---|---|---|
|**/Action:**|**/a**|DeployReport|Указывает действие, подлежащее выполнению. |
|**/AccessToken:**|**/at**|{строка}| Указывает маркер доступа для проверки подлинности на основе маркеров. Этот маркер используется при подключении к целевой базе данных. |
|**/Diagnostics:**|**/d**|{True&#124;False}|Указывает, следует ли выводить сведения из журнала диагностики в консоль. Значение по умолчанию — False. |
|**/DiagnosticsFile:**|**/df**|{строка}|Указывает файл, в котором следует вести журнал диагностики. |
|**/MaxParallelism:**|**/mp**|{целое_число}| Задает степень параллелизма для параллельных операций с базой данных. Значение по умолчанию: 8. |
|**/OutputPath:**|**/op**|{строка}|Указывает путь, по которому формируются выходные файлы. |
|**/OverwriteFiles:**|**/of**|{True&#124;False}|Указывает, должна ли программа sqlpackage.exe перезаписывать существующие файлы. Задание значения false приводит к тому, что программа sqlpackage.exe прерывает действие при обнаружении существующего файла. Значение по умолчанию равно True. |
|**/Profile:**|**/pr**|{строка}|Указывает путь к файлу приложения уровня данных профиля публикации. Профиль определяет коллекцию свойств и переменных, которые должны использоваться при формировании выходных данных. |
|**/Properties:**|**/p**|{имя_свойства}={значение}|Указывает пару "имя-значение" для свойства действия; {имя_свойства}={значение}. Имена свойств действия см. в справке по данным действиям. Например: sqlpackage.exe /Action:DeployReport /?. |
|**/Quiet:**|**/q**|{True&#124;False}|Указывает, происходит ли подавление подробного отзыва. Значение по умолчанию — False. |
|**/SourceConnectionString:**|**/scs**|{строка}|Указывает допустимую строку подключения SQL Server/Azure для базы данных-источника. Если этот параметр указан, ему будет отдаваться предпочтение перед всеми остальными параметрами источника. |
|**/SourceDatabaseName:**|**/sdn**|{строка}|Определяет имя базы данных-источника. |
|**/SourceEncryptConnection:**|**/sec**|{True&#124;False}|Указывает, следует ли использовать шифрование SQL для соединения с базой данных-источником. |
|**/SourceFile:**|**/sf**|{строка}|Указывает имя исходного файла, который должен использоваться в качестве источника действия вместо базы данных. Если используется этот параметр, все остальные параметры источника будут недействительны. |
|**/SourcePassword:**|**/sp**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пароль для доступа к базе данных-источнику. |
|**/SourceServerName:**|**/ssn**|{строка}|Определяет имя сервера, где размещается база данных-источник. |
|**/SourceTimeout:**|**/st**|{целое_число}|Задает время ожидания подключения к базе данных-источнику (в секундах). |
|**/SourceTrustServerCertificate:**|**/stsc**|{True&#124;False}|Определяет, используется ли протокол TLS для шифрования подключения к базе данных-источнику без прохода по цепочке сертификатов для проверки доверия. |
|**/SourceUser:**|**/su**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пользователя SQL Server для доступа к базе данных-источнику. |
|**/TargetConnectionString:**|**/tcs**|{строка}|Указывает допустимую строку подключения SQL Server/Azure для целевой базы данных. Если этот параметр указан, ему будет отдаваться предпочтение перед всеми остальными параметрами целевого объекта. |
|**/TargetDatabaseName:**|**/tdn**|{строка}|Задает переопределение имени для целевой базы данных действия sqlpackage.exe. |
|**/TargetEncryptConnection:**|**/tec**|{True&#124;False}|Определяет, должно ли использоваться шифрование SQL для подключения к целевой базе данных. |
|**/TargetFile:**|**/tf**|{строка}|Указывает целевой файл (то есть DACPAC-файл) для использования в качестве целевого объекта действия вместо базы данных. Если используется этот параметр, все остальные параметры целевого объекта будут недействительны. Этот параметр будет недопустимым для действий, которые поддерживают только целевые объекты базы данных.|
|**/TargetPassword:**|**/tp**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пароль для доступа к целевой базе данных. |
|**/TargetServerName:**|**/tsn**|{строка}|Определяет имя сервера, где размещается целевая база данных. |
|**/TargetTimeout:**|**/tt**|{целое_число}|Задает время ожидания подключения к целевой базе данных (в секундах). Для AAD рекомендуется, чтобы это значение было больше или равно 30 с.|
|**/TargetTrustServerCertificate:**|**/ttsc**|{True&#124;False}|Определяет, используется ли протокол TLS для шифрования подключения к целевой базе данных без прохода по цепочке сертификатов для проверки доверия. |
|**/TargetUser:**|**/tu**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пользователя SQL Server для доступа к целевой базе данных. |
|**/TenantId:**|**/tid**|{строка}|Представляет ИД клиента AAD или доменное имя. Этот параметр необходим для поддержки гостевых или импортированных пользователей AAD, а также учетных записей Майкрософт, например outlook.com, hotmail.com или live.com. Если этот параметр пропущен, будет использоваться ИД клиента по умолчанию для AAD. При этом предполагается, что прошедший проверку подлинности пользователь является собственным пользователем для этого AD. Однако в этом случае все гостевые или импортированные пользователи и (или) учетные записи Майкрософт, размещенные в этой службе AAD, не поддерживаются, и операция завершится ошибкой. <br/> Дополнительные сведения об универсальной проверке подлинности AD DS см. в [этой статье](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/UniversalAuthentication:**|**/ua**|{True&#124;False}|Указывает, следует ли использовать универсальную проверку подлинности. Если задано значение true, протокол интерактивной проверки подлинности активируется с поддержкой MFA. Этот параметр также можно применять для проверки подлинности AAD без MFA, используя интерактивный протокол, где пользователю необходимо ввести имя пользователя и пароль, или встроенную проверку подлинности (учетные данные Windows). Если для элемента /UniversalAuthentication задано значение True, в элементе SourceConnectionString (/scs) не может быть указана проверка подлинности AAD. Если для элемента /UniversalAuthentication задано значение False, в элементе SourceConnectionString (/scs) должна быть указана проверка подлинности AAD. <br/> Дополнительные сведения об универсальной проверке подлинности AD DS см. в [этой статье](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/Variables:**|**/v**|{имя_свойства}={значение}|Указывает пару "имя-значение" для переменной действия; {имя_переменной}={значение}. DACPAC-файл содержит список действительных переменных SQLCMD. Если значения каких-либо переменных не будут указаны, возникнет ошибка. |

## <a name="properties-specific-to-the-deployreport-action"></a>Свойства, относящиеся к действию DeployReport

|Свойство|Значение|Описание|
|---|---|---|
|**/p:**|AdditionalDeploymentContributorArguments=(STRING)|Задает дополнительные аргументы участника развертывания для участников развертывания. Это должен быть список значений, разделенных точками с запятой.|
|**/p:**|AdditionalDeploymentContributors=(STRING)|Указывает дополнительных участников развертывания, которые должны выполняться при развертывании пакета DACPAC. Это должен быть список идентификаторов или полных имен участников сборки, разделенных точками с запятой.|
|**/p:**|AdditionalDeploymentContributorPaths=(STRING)| Указывает пути для загрузки дополнительных участников развертывания. Это должен быть список значений, разделенных точками с запятой. | 
|**/p:**|AllowDropBlocking Assemblies=(BOOLEAN)|Это свойство используется развертыванием SQLCLR для удаления блокирующих сборок как часть плана развертывания. По умолчанию все блокирующие сборки/ссылки на сборки блокируют обновление сборки, если ссылка на сборку должна быть удалена.|
|**/p:**|AllowIncompatiblePlatform=(BOOLEAN)|Указывает, пытаться ли выполнить это действие, несмотря на несовместимость платформ SQL Server.|
|**/p:**|AllowUnsafeRowLevelSecurityDataMovement=(BOOLEAN)|Если свойство имеет значение true, блокировка перемещения данных в таблице с безопасностью на уровне строк отключается. Значение по умолчанию — false.|
|**/p:**|BackupDatabaseBeforeChanges=(BOOLEAN)|Создает резервную копию базы данных перед развертыванием любых изменений.|
|**/p:**|BlockOnPossibleDataLoss=(BOOLEAN 'True')|Указывает, что следует завершать эпизод публикации, если есть возможность потери данных в результате операции публикации.|
|**/p:**|BlockWhenDriftDetected=(BOOLEAN 'True')|Указывает, следует ли блокировать обновление базы данных, схема которой больше не соответствует регистрации или регистрация которой удалена. |
|**/p:**|CommandTimeout=(INT32 '60')|Задает время ожидания команды в секундах при выполнении запросов к SQL Server. |
|**/p:**|CommentOutSetVarDeclarations=(BOOLEAN)|Указывает, будет ли объявление переменных SETVAR закомментировано в созданном скрипте публикации. Эту возможность можно выбрать, если планируется задавать значения в командной строке во время публикации с помощью такого средства, как SQLCMD.EXE. |
|**/p:**|CompareUsingTargetCollation=(BOOLEAN)|Этот параметр указывает, как обрабатываются параметры сортировки базы данных во время развертывания. По умолчанию параметры сортировки целевой базы данных обновляются, если они не совпадают с параметрами сортировки, указанными источником. Если задан этот параметр, использоваться будут параметры сортировки целевой базы данных (или сервера). |
|**/p:**|CreateNewDatabase=(BOOLEAN)|Указывает, обновляется ли целевая база данных, или ее нужно удалить и создать заново при публикации базы данных. |
|**/p:**|DatabaseEdition=({Basic&#124;Standard&#124;Premium&#124;DataWarehouse&#124;GeneralPurpose&#124;BusinessCritical&#124;Hyperscale&#124;Default} 'Default')|Определяет выпуск Базы данных SQL Azure.|
|**/p:**|DatabaseLockTimeout=(INT32 '60')| Позволяет задать превышение времени ожидания блокировки в секундах для базы данных при выполнении запросов к SQL Server. Для ожидания без ограничений используйте значение "-1".|
|**/p:**|DatabaseMaximumSize=(INT32)|Определяет максимальный размер в ГБ для базы данных SQL Azure.|
|**/p:**|DatabaseServiceObjective=(STRING)|Определяет уровень производительности для базы данных SQL Azure, например "P0" или "S1". |
|**/p:**|DeployDatabaseInSingleUserMode=(BOOLEAN)|Если указано значение true, то перед развертыванием база данных переводится в однопользовательский режим. |
|**/p:**|DisableAndReenableDdlTriggers=(BOOLEAN 'True')| Указывает, следует ли отключить триггеры языка описания данных DDL в начале процесса публикации и включить их в конце.|
|**/p:**|DoNotAlterChangeDataCaptureObjects=(BOOLEAN 'True')|Если указано значение true, объекты отслеживания измененных данных не меняются.|
|**/p:**|DoNotAlterReplicatedObjects=(BOOLEAN 'True')|Указывает, определяются ли во время проверки реплицируемые объекты.|
|**/p:**|DoNotDropObjectType=(STRING)|Тип объекта, который нельзя удалять, если элемент DropObjectsNotInSource имеет значение true. Допустимые имена типов объектов: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers. |
|**/p:**|DoNotDropObjectTypes=(STRING)|Список типов объектов (разделенных точками с запятой), которые не следует удалять, если параметр DropObjectsNotInSource имеет значение true. Допустимые имена типов объектов: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.|
|**/p:**|DropConstraintsNotInSource=(BOOLEAN 'True')|Указывает, будут ли ограничения, которые не существуют в моментальном снимке базы данных (DACPAC), удалены из целевой базы данных при выполнении публикации.|
|**/p:**|DropDmlTriggersNotInSource=(BOOLEAN 'True')|Указывает, будут ли триггеры DML, которые не существуют в моментальном снимке базы данных (DACPAC), удалены из целевой базы данных при выполнении публикации.|
|**/p:**|DropExtendedPropertiesNotInSource=(BOOLEAN 'True')|Указывает, будут ли при выполнении публикации в базе данных удалены расширенные свойства, которые не существуют в моментальном снимке базы данных (DACPAC).|
|**/p:**|DropIndexesNotInSource=(BOOLEAN 'True')|Указывает, будут ли индексы, которые не существуют в моментальном снимке базы данных (DACPAC), удалены из целевой базы данных при выполнении публикации.|
|**/p:**|DropObjectsNotInSource=(BOOLEAN)|Указывает, будут ли объекты, которые отсутствуют в моментальном снимке базы данных (DACPAC), удалены из целевой базы данных при выполнении публикации. Это значение имеет приоритет над элементом DropExtendedProperties.|
|**/p:**|DropPermissionsNotInSource=(BOOLEAN)|Указывает, будут ли разрешения, которые не существуют в моментальном снимке базы данных (DACPAC), удалены из целевой базы данных при выполнении публикации обновлений.|
|**/p:**|DropRoleMembersNotInSource=(BOOLEAN)|Указывает, будут ли члены ролей, которые не определены в моментальном снимке базы данных (DACPAC), удалены из целевой базы данных при выполнении публикации обновлений.|
|**/p:**|DropStatisticsNotInSource=(BOOLEAN 'True')|Указывает, будет ли статистика, которая отсутствует в файле моментального снимка базы данных (DACPAC), удалена из целевой базы данных при публикации в базе данных.|
|**/p:**|ExcludeObjectType=(STRING)|Тип объекта, который должен игнорироваться во время развертывания. Допустимые имена типов объектов: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.|
|**/p:**|ExcludeObjectTypes=(STRING)|Список типов объектов, разделенных точками с запятой, которые должны игнорироваться во время развертывания. Допустимые имена типов объектов: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.|
|**/p:**|GenerateSmartDefaults=(BOOLEAN)|Автоматически определяет значение по умолчанию при обновлении таблицы, содержащей данные со столбцом, который не допускает значения NULL.|
|**/p:**|IgnoreAnsiNulls=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в параметре ANSI NULLS при публикации в базе данных.|
|**/p:**|IgnoreAuthorizer=(BOOLEAN)|Определяет, пропускаются или обновляются различия в Authorizer при публикации в базе данных.|
|**/p:**|IgnoreColumnCollation=(BOOLEAN)|Определяет, пропускаются или обновляются различия в параметрах сортировки столбцов при публикации в базе данных.|
|**/p:**|IgnoreColumnOrder=(BOOLEAN)|Указывает, следует ли игнорировать или обновлять различия в порядке столбцов таблицы при публикации в базе данных.|
|**/p:**|IgnoreComments=(BOOLEAN)|Определяет, пропускаются или обновляются различия в комментариях при публикации в базе данных.|
|**/p:**|IgnoreCryptographicProviderFilePath=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в пути к файлам для поставщика служб шифрования при публикации в базе данных.|
|**/p:**|IgnoreDdlTriggerOrder=(BOOLEAN)|Определяет, пропускаются или обновляются различия в порядке триггеров для языка описания данных DDL при публикации в базе данных или на сервере.|
|**/p:**|IgnoreDdlTriggerState=(BOOLEAN)|Определяет, пропускаются или обновляются различия в состоянии (включен-выключен) триггеров языка описания данных DDL при публикации в базе данных.|
|**/p:**|IgnoreDefaultSchema=(BOOLEAN)|Определяет, пропускаются или обновляются различия в схеме по умолчанию при публикации в базе данных. |
|**/p:**|IgnoreDmlTriggerOrder=(BOOLEAN)|Определяет, пропускаются или обновляются различия в порядке триггеров языка обработки данных DML при публикации в базе данных.| 
|**/p:**|IgnoreDmlTriggerState=(BOOLEAN)|Определяет, пропускаются или обновляются различия в состоянии (включен–выключен) триггеров DML при публикации в базе данных. |
|**/p:**|IgnoreExtendedProperties=(BOOLEAN)|Определяет, пропускаются или обновляются различия в расширенных свойствах при публикации в базе данных. |
|**/p:**|IgnoreFileAndLogFilePath=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в путях к файлам и файлам журнала при публикации в базе данных. |
|**/p:**|IgnoreFilegroupPlacement=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в размещении объектов в файловых группах FILEGROUP при публикации в базе данных.| 
|**/p:**|IgnoreFileSize=(BOOLEAN 'True')|Определяет, создается ли предупреждение о различиях в размерах файлов при публикации в базе данных. |
|**/p:**|IgnoreFillFactor=(BOOLEAN 'True')|Определяет, создается ли предупреждение о различиях в коэффициенте заполнения для хранилища индексов при публикации в базе данных.|
|**/p:**|IgnoreFullTextCatalogFilePath=(BOOLEAN 'True')|Определяет, создается ли предупреждение о различиях в пути к файлам для полнотекстового каталога при публикации в базе данных.| 
|**/p:**|IgnoreIdentitySeed=(BOOLEAN)|Определяет, пропускаются или обновляются различия в начальном значении для столбца идентификаторов при публикации обновлений в базе данных. |
|**/p:**|IgnoreIncrement=(BOOLEAN)|Определяет, пропускаются или обновляются различия в шаге приращения для столбца идентификаторов при публикации в базе данных. |
|**/p:**|IgnoreIndexOptions=(BOOLEAN)|Определяет, пропускаются или обновляются различия в параметрах индексов при публикации в базе данных. |
|**/p:**|IgnoreIndexPadding=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в заполнении индекса при публикации в базе данных. |
|**/p:**|IgnoreKeywordCasing=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в регистре ключевых слов при публикации в базе данных. |
|**/p:**|IgnoreLockHintsOnIndexes=(BOOLEAN)|Указывает, следует пропускать или обновлять различия в указаниях блокировки для индексов во время публикации в базе данных. |
|**/p:**|IgnoreLoginSids=(BOOLEAN 'True')| Определяет, пропускаются или обновляются различия в идентификаторе безопасности (SID) при публикации в базе данных.| 
|**/p:**|IgnoreNotForReplication=(BOOLEAN)|Определяет, пропускаются или обновляются параметры "не для репликации" при публикации в базе данных. |
|**/p:**|IgnoreObjectPlacementOnPartitionScheme=(BOOLEAN 'True')|Определяет, пропускается или обновляется размещение объекта в схеме секционирования при публикации в базе данных.|
 |**/p:**|IgnorePartitionSchemes=(BOOLEAN)|Определяет, пропускаются или обновляются различия в функциях и схемах секционирования при публикации в базе данных.|
|**/p:**|IgnorePermissions=(BOOLEAN)|Определяет, пропускаются или обновляются различия в разрешениях при публикации в базе данных. |
|**/p:**|IgnoreQuotedIdentifiers=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в параметре нестандартных идентификаторов при публикации в базе данных. |
|**/p:**|IgnoreRoleMembership=(BOOLEAN)|Указывает, следует пропускать или обновлять различия в членстве в роли имен входа во время публикации в базе данных. |
|**/p:**|IgnoreRouteLifetime=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в продолжительности периода, в течение которого SQL Server сохраняет маршрут в таблице маршрутизации, при публикации в базе данных.|
|**/p:**|IgnoreSemicolonBetweenStatements=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в точках с запятой между инструкциями T-SQL при публикации в базе данных.| 
|**/p:**|IgnoreTableOptions=(BOOLEAN)|Определяет, пропускаются или обновляются различия в параметрах таблиц при публикации в базе данных.| 
|**/p:**|IgnoreTablePartitionOptions=(BOOLEAN)|Определяет, пропускаются или обновляются различия в параметрах секций таблиц при публикации в базе данных.  Этот параметр применяется только к базам данных хранилищ данных Azure Synapse Analytics.|
|**/p:**|IgnoreUserSettingsObjects=(BOOLEAN)|Определяет, пропускаются или обновляются различия в объектах параметров пользователя при публикации в базе данных.|
|**/p:**|IgnoreWhitespace=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в пробелах при публикации в базе данных. |
|**/p:**|IgnoreWithNocheckOnCheckConstraints=(BOOLEAN)|Определяет, пропускаются или обновляются различия в значении предложения WITH NOCHECK для проверочных ограничений при публикации в базе данных.| 
|**/p:**|IgnoreWithNocheckOnForeignKeys=(BOOLEAN)|Определяет, пропускаются или обновляются различия в значении предложения WITH NOCHECK для внешних ключей при публикации в базе данных.| 
|**/p:**|IncludeCompositeObjects=(BOOLEAN)|Включить все составные элементы в единую операцию публикации.|
|**/p:**|IncludeTransactionalScripts=(BOOLEAN)|Определяет, будут ли по возможности использоваться инструкции транзакций при публикации в базе данных.|
|**/p:**|LongRunningCommandTimeout=(INT32)| Позволяет задать время ожидания в секундах для длительной команды при выполнении запросов к SQL Server. Для ожидания без ограничений используйте значение "0".|
|**/p:**|NoAlterStatementsToChangeClrTypes=(BOOLEAN)|Указывает, что при публикации (при наличии различий) вместо выполнения инструкции ALTER ASSEMBLY сборка всегда должна удаляться и создаваться повторно. |
|**/p:**|PopulateFilesOnFileGroups=(BOOLEAN 'True')|Указывает, создается ли файл при создании файловой группы FileGroup в целевой базе данных. |
|**/p:**|RegisterDataTierApplication=(BOOLEAN)|Указывает, регистрируется ли схема на сервере базы данных. 
|**/p:**|RunDeploymentPlanExecutors=(BOOLEAN)|Указывает, должны ли выполняться участники DeploymentPlanExecutor при выполнении других операций.|
|**/p:**|ScriptDatabaseCollation=(BOOLEAN)|Определяет, пропускаются или обновляются различия в параметрах сортировки базы данных при публикации в базе данных. |
|**/p:**|ScriptDatabaseCompatibility=(BOOLEAN)|Определяет, пропускаются или обновляются различия в уровне совместимости базы данных при публикации в базе данных. |
|**/p:**|ScriptDatabaseOptions=(BOOLEAN 'True')|Определяет, будут ли свойства целевой базы данных задаваться или обновляться в рамках действия публикации. |
|**/p:**|ScriptDeployStateChecks=(BOOLEAN)|Определяет, создаются ли инструкции в скрипте публикации, чтобы проверить соответствие имен базы данных и сервера с именами, указанными в проекте базы данных.|
|**/p:**|ScriptFileSize=(BOOLEAN)|Определяет, указывается ли размер при добавлении файла в файловую группу. |
|**/p:**|ScriptNewConstraintValidation=(BOOLEAN 'True')|В конце публикации все ограничения будут проверяться как один набор, избегая ошибок данных, вызванных ограничением проверки или внешнего ключа в середине публикации. Если этот параметр имеет значение False, ограничения публикуются без проверки соответствующих данных.|
|**/p:**|ScriptRefreshModule=(BOOLEAN 'True')|Включать инструкции обновления в конец скрипта публикации.|
|**/p:**|Storage=({File&#124;Memory})|Указывает, как сохраняются элементы при построении модели базы данных. Для обеспечения высокой производительности по умолчанию используется значение InMemory. Для больших баз данных требуется хранилище с использованием файлов.|
|**/p:**|TreatVerificationErrorsAsWarnings=(BOOLEAN)|Указывает, должны ли ошибки, обнаруженные во время проверки публикации, обрабатываться как предупреждения. Проверка выполняется применительно к сформированному плану развертывания перед его выполнением применительно к целевой базе данных. Проверка плана выявляет такие проблемы, как потеря объектов, существующих только в целевой базе данных (например, индексов), которые должны быть удалены в процессе внесения изменений. Кроме того, она выявляет ситуации, когда зависимости (например, таблицы или представления) существуют в результате наличия ссылок на составной проект, но отсутствуют в целевой базе данных. Это можно сделать, чтобы получить полный список всех проблем, вместо завершения действия публикации при первой ошибке. |
|**/p:**|UnmodifiableObjectWarnings=(BOOLEAN 'True')|Указывает, следует ли формировать предупреждения, если обнаружены различия в объектах, которые не могут быть изменены (например, если отличаются размеры или пути файлов).| 
|**/p:**|VerifyCollationCompatibility=(BOOLEAN 'True')|Указывает, проверяется ли совместимость параметров сортировки.| 
|**/p:**|VerifyDeployment=(BOOLEAN 'True')|Указывает, следует ли выполнять проверки перед началом публикации, останавливаемой при возникновении проблем, которые могут заблокировать успешную публикацию. Например, публикация может остановиться в случае, если во время публикации возникли ошибки, связанные с тем, что внешние ключи в целевой базе данных не существуют в проекте базы данных. |
  
## <a name="driftreport-parameters"></a>Параметры DriftReport

Действие с отчетом **SqlPackage.exe** создает XML-отчет по изменениям, которые были внесены в зарегистрированную базу данных со времени ее последней регистрации.  
  
### <a name="help-for-driftreport-action"></a>Справка по действию DriftReport

|Параметр|Краткая форма|Значение|Описание|
|---|---|---|---|
|**/Action:**|**/a**|DriftReport|Указывает действие, подлежащее выполнению. |
|**/AccessToken:**|**/at**|{строка}| Указывает маркер доступа для проверки подлинности на основе маркеров. Этот маркер используется при подключении к целевой базе данных. |
|**/Diagnostics:**|**/d**|{True&#124;False}|Указывает, следует ли выводить сведения из журнала диагностики в консоль. Значение по умолчанию — False. |
|**/DiagnosticsFile:**|**/df**|{строка}|Указывает файл, в котором следует вести журнал диагностики. |
|**/MaxParallelism:**|**/mp**|{целое_число}| Задает степень параллелизма для параллельных операций с базой данных. Значение по умолчанию: 8. |
|**/OutputPath:**|**/op**|{строка}|Указывает путь, по которому формируются выходные файлы. |
|**/OverwriteFiles:**|**/of**|{True&#124;False}|Указывает, должна ли программа sqlpackage.exe перезаписывать существующие файлы. Задание значения false приводит к тому, что программа sqlpackage.exe прерывает действие при обнаружении существующего файла. Значение по умолчанию равно True. |
|**/Quiet:**|**/q**|{True&#124;False}|Указывает, происходит ли подавление подробного отзыва. Значение по умолчанию — False.|
|**/TargetConnectionString:**|**/tcs**|{строка}|Указывает допустимую строку подключения SQL Server/Azure для целевой базы данных. Если этот параметр указан, ему будет отдаваться предпочтение перед всеми остальными параметрами целевого объекта. |
|**/TargetDatabaseName:**|**/tdn**|{строка}|Задает переопределение имени для целевой базы данных действия sqlpackage.exe. |
|**/TargetEncryptConnection:**|**/tec**|{True&#124;False}|Определяет, должно ли использоваться шифрование SQL для подключения к целевой базе данных. |
|**/TargetPassword:**|**/tp**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пароль для доступа к целевой базе данных. |
|**/TargetServerName:**|**/tsn**|{строка}|Определяет имя сервера, где размещается целевая база данных. |
|**/TargetTimeout:**|**/tt**|{целое_число}|Задает время ожидания подключения к целевой базе данных (в секундах). Для AAD рекомендуется, чтобы это значение было больше или равно 30 с.|
|**/TargetTrustServerCertificate:**|**/ttsc**|{True&#124;False}|Определяет, используется ли протокол TLS для шифрования подключения к целевой базе данных без прохода по цепочке сертификатов для проверки доверия. |
|**/TargetUser:**|**/tu**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пользователя SQL Server для доступа к целевой базе данных. |
|**/TenantId:**|**/tid**|{строка}|Представляет ИД клиента AAD или доменное имя. Этот параметр необходим для поддержки гостевых или импортированных пользователей AAD, а также учетных записей Майкрософт, например outlook.com, hotmail.com или live.com. Если этот параметр пропущен, будет использоваться ИД клиента по умолчанию для AAD. При этом предполагается, что прошедший проверку подлинности пользователь является собственным пользователем для этого AD. Однако в этом случае все гостевые или импортированные пользователи и (или) учетные записи Майкрософт, размещенные в этой службе AAD, не поддерживаются, и операция завершится ошибкой. <br/> Дополнительные сведения об универсальной проверке подлинности AD DS см. в [этой статье](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/UniversalAuthentication:**|**/ua**|{True&#124;False}|Указывает, следует ли использовать универсальную проверку подлинности. Если задано значение true, протокол интерактивной проверки подлинности активируется с поддержкой MFA. Этот параметр также можно применять для проверки подлинности AAD без MFA, используя интерактивный протокол, где пользователю необходимо ввести имя пользователя и пароль, или встроенную проверку подлинности (учетные данные Windows). Если для элемента /UniversalAuthentication задано значение True, в элементе SourceConnectionString (/scs) не может быть указана проверка подлинности AAD. Если для элемента /UniversalAuthentication задано значение False, в элементе SourceConnectionString (/scs) должна быть указана проверка подлинности AAD. <br/> Дополнительные сведения об универсальной проверке подлинности AD DS см. в [этой статье](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|

## <a name="script-parameters-and-properties"></a>Параметры и свойства скрипта

Действие скрипта **SqlPackage.exe** создает скрипт добавочного обновления на языке Transact-SQL для обновления схемы целевой базы данных до соответствия схеме базы данных-источника.  
  
### <a name="help-for-the-script-action"></a>Справка по действию скрипта

|Параметр|Краткая форма|Значение|Описание|
|---|---|---|---|
|**/Action:**|**/a**|Скрипт|Указывает действие, подлежащее выполнению. |
|**/AccessToken:**|**/at**|{строка}| Указывает маркер доступа для проверки подлинности на основе маркеров. Этот маркер используется при подключении к целевой базе данных. |
|**/DeployScriptPath:**|**/dsp**|{строка}|Указывает необязательный путь для вывода скрипта развертывания. В среде Azure при использовании команд TSQL для создания или изменения базы данных master скрипт будет записан по тому же пути, но с именем выходного файла Filename_Master.sql. |
|**/DeployReportPath:**|**/drp**|{строка}|Указывает необязательный путь для вывода XML-файла отчета о развертывании. |
|**/Diagnostics:**|**/d**|{True&#124;False}|Указывает, следует ли выводить сведения из журнала диагностики в консоль. Значение по умолчанию — False. |
|**/DiagnosticsFile:**|**/df**|{строка}|Указывает файл, в котором следует вести журнал диагностики. |
|**/MaxParallelism:**|**/mp**|{целое_число}| Задает степень параллелизма для параллельных операций с базой данных. Значение по умолчанию: 8. |
|**/OutputPath:**|**/op**|{строка}|Указывает путь, по которому формируются выходные файлы. |
|**/OverwriteFiles:**|**/of**|{True&#124;False}|Указывает, должна ли программа sqlpackage.exe перезаписывать существующие файлы. Задание значения false приводит к тому, что программа sqlpackage.exe прерывает действие при обнаружении существующего файла. Значение по умолчанию равно True. |
|**/Profile:**|**/pr**|{строка}|Указывает путь к файлу приложения уровня данных профиля публикации. Профиль определяет коллекцию свойств и переменных, которые должны использоваться при формировании выходных данных.|
|**/Properties:**|**/p**|{имя_свойства}={значение}|Указывает пару "имя-значение" для свойства действия; {имя_свойства}={значение}. Имена свойств действия см. в справке по данным действиям. Например: sqlpackage.exe /Action:Script /?.|
|**/Quiet:**|**/q**|{True&#124;False}|Указывает, происходит ли подавление подробного отзыва. Значение по умолчанию — False.|
|**/SourceConnectionString:**|**/scs**|{строка}|Указывает допустимую строку подключения SQL Server/Azure для базы данных-источника. Если этот параметр указан, ему будет отдаваться предпочтение перед всеми остальными параметрами источника. |
|**/SourceDatabaseName:**|**/sdn**|{строка}|Определяет имя базы данных-источника. |
|**/SourceEncryptConnection:**|**/sec**|{True&#124;False}|Указывает, следует ли использовать шифрование SQL для соединения с базой данных-источником. |
|**/SourceFile:**|**/sf**|{строка}|Указывает имя исходного файла, который должен использоваться в качестве источника действия. Если используется этот параметр, все остальные параметры источника будут недействительны. |
|**/SourcePassword:**|**/sp**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пароль для доступа к базе данных-источнику. |
|**/SourceServerName:**|**/ssn**|{строка}|Определяет имя сервера, где размещается база данных-источник. |
|**/SourceTimeout:**|**/st**|{целое_число}|Задает время ожидания подключения к базе данных-источнику (в секундах). |
|**/SourceTrustServerCertificate:**|**/stsc**|{True&#124;False}|Определяет, используется ли протокол TLS для шифрования подключения к базе данных-источнику без прохода по цепочке сертификатов для проверки доверия. |
|**/SourceUser:**|**/su**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пользователя SQL Server для доступа к базе данных-источнику. |
|**/TargetConnectionString:**|**/tcs**|{строка}|Указывает допустимую строку подключения SQL Server/Azure для целевой базы данных. Если этот параметр указан, ему будет отдаваться предпочтение перед всеми остальными параметрами целевого объекта. |
|**/TargetDatabaseName:**|**/tdn**|{строка}|Задает переопределение имени для целевой базы данных действия sqlpackage.exe. |
|**/TargetEncryptConnection:**|**/tec**|{True&#124;False}|Определяет, должно ли использоваться шифрование SQL для подключения к целевой базе данных. |
|**/TargetFile:**|**/tf**|{строка}| Указывает целевой файл (то есть DACPAC-файл) для использования в качестве целевого объекта действия вместо базы данных. Если используется этот параметр, все остальные параметры целевого объекта будут недействительны. Этот параметр будет недопустимым для действий, которые поддерживают только целевые объекты базы данных.|
|**/TargetPassword:**|**/tp**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пароль для доступа к целевой базе данных. |
|**/TargetServerName:**|**/tsn**|{строка}|Определяет имя сервера, где размещается целевая база данных. |
|**/TargetTimeout:**|**/tt**|{целое_число}|Задает время ожидания подключения к целевой базе данных (в секундах). Для AAD рекомендуется, чтобы это значение было больше или равно 30 с.|
|**/TargetTrustServerCertificate:**|**/ttsc**|{True&#124;False}|Определяет, используется ли протокол TLS для шифрования подключения к целевой базе данных без прохода по цепочке сертификатов для проверки доверия. |
|**/TargetUser:**|**/tu**|{строка}|В сценариях с проверкой подлинности SQL Server — определяет пользователя SQL Server для доступа к целевой базе данных. |
|**/TenantId:**|**/tid**|{строка}|Представляет ИД клиента AAD или доменное имя. Этот параметр необходим для поддержки гостевых или импортированных пользователей AAD, а также учетных записей Майкрософт, например outlook.com, hotmail.com или live.com. Если этот параметр пропущен, будет использоваться ИД клиента по умолчанию для AAD. При этом предполагается, что прошедший проверку подлинности пользователь является собственным пользователем для этого AD. Однако в этом случае все гостевые или импортированные пользователи и (или) учетные записи Майкрософт, размещенные в этой службе AAD, не поддерживаются, и операция завершится ошибкой. <br/> Дополнительные сведения об универсальной проверке подлинности AD DS см. в [этой статье](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/UniversalAuthentication:**|**/ua**|{True&#124;False}|Указывает, следует ли использовать универсальную проверку подлинности. Если задано значение true, протокол интерактивной проверки подлинности активируется с поддержкой MFA. Этот параметр также можно применять для проверки подлинности AAD без MFA, используя интерактивный протокол, где пользователю необходимо ввести имя пользователя и пароль, или встроенную проверку подлинности (учетные данные Windows). Если для элемента /UniversalAuthentication задано значение True, в элементе SourceConnectionString (/scs) не может быть указана проверка подлинности AAD. Если для элемента /UniversalAuthentication задано значение False, в элементе SourceConnectionString (/scs) должна быть указана проверка подлинности AAD. <br/> Дополнительные сведения об универсальной проверке подлинности AD DS см. в [этой статье](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/Variables:**|**/v**|{имя_свойства}={значение}|Указывает пару "имя-значение" для переменной действия; {имя_переменной}={значение}. DACPAC-файл содержит список действительных переменных SQLCMD. Если значения каких-либо переменных не будут указаны, возникнет ошибка. |

### <a name="properties-specific-to-the-script-action"></a>Свойства, относящиеся к действию скрипта

|Свойство|Значение|Описание|
|---|---|---|
|**/p:**|AdditionalDeploymentContributorArguments=(STRING)|Задает дополнительные аргументы участника развертывания для участников развертывания. Это должен быть список значений, разделенных точками с запятой.
|**/p:**|AdditionalDeploymentContributors=(STRING)|Указывает дополнительных участников развертывания, которые должны выполняться при развертывании пакета DACPAC. Это должен быть список идентификаторов или полных имен участников сборки, разделенных точками с запятой.
|**/p:**|AdditionalDeploymentContributorPaths=(STRING)| Указывает пути для загрузки дополнительных участников развертывания. Это должен быть список значений, разделенных точками с запятой. | 
|**/p:**|AllowDropBlockingAssemblies=(BOOLEAN)|Это свойство используется развертыванием SQLCLR для удаления блокирующих сборок как часть плана развертывания. По умолчанию все блокирующие сборки/ссылки на сборки блокируют обновление сборки, если ссылка на сборку должна быть удалена.
|**/p:**|AllowIncompatiblePlatform=(BOOLEAN)|Указывает, пытаться ли выполнить это действие, несмотря на несовместимость платформ SQL Server.
|**/p:**|AllowUnsafeRowLevelSecurityDataMovement=(BOOLEAN)|Если свойство имеет значение true, блокировка перемещения данных в таблице с безопасностью на уровне строк отключается. Значение по умолчанию — false.
|**/p:**|BackupDatabaseBeforeChanges=(BOOLEAN)|Создает резервную копию базы данных перед развертыванием любых изменений.
|**/p:**|BlockOnPossibleDataLoss=(BOOLEAN 'True')|Указывает, что следует завершать эпизод публикации, если есть возможность потери данных в результате операции публикации.
|**/p:**|BlockWhenDriftDetected=(BOOLEAN 'True')|Указывает, следует ли блокировать обновление базы данных, схема которой больше не соответствует регистрации или регистрация которой удалена.
|**/p:**|CommandTimeout=(INT32 '60')|Задает время ожидания команды в секундах при выполнении запросов к SQL Server.
|**/p:**|CommentOutSetVarDeclarations=(BOOLEAN)|Указывает, будет ли объявление переменных SETVAR закомментировано в созданном скрипте публикации. Эту возможность можно выбрать, если планируется задавать значения в командной строке во время публикации с помощью такого средства, как SQLCMD.EXE.
|**/p:**|CompareUsingTargetCollation=(BOOLEAN)|Этот параметр указывает, как обрабатываются параметры сортировки базы данных во время развертывания. По умолчанию параметры сортировки целевой базы данных обновляются, если они не совпадают с параметрами сортировки, указанными источником. Если задан этот параметр, использоваться будут параметры сортировки целевой базы данных (или сервера).|
|**/p:**|CreateNewDatabase=(BOOLEAN)|Указывает, обновляется ли целевая база данных, или ее нужно удалить и создать заново при публикации базы данных.
|**/p:**|DatabaseEdition=({Basic&#124;Standard&#124;Premium&#124;DataWarehouse&#124;GeneralPurpose&#124;BusinessCritical&#124;Hyperscale&#124;Default} 'Default')|Определяет выпуск Базы данных SQL Azure.|
|**/p:**|DatabaseLockTimeout=(INT32 '60')| Позволяет задать превышение времени ожидания блокировки в секундах для базы данных при выполнении запросов к SQL Server. Для ожидания без ограничений используйте значение "-1".|
|**/p:**|DatabaseMaximumSize=(INT32)|Определяет максимальный размер в ГБ для базы данных SQL Azure.
|**/p:**|DatabaseServiceObjective=(STRING)|Определяет уровень производительности для базы данных SQL Azure, например "P0" или "S1".
|**/p:**|DeployDatabaseInSingleUserMode=(BOOLEAN)|Если указано значение true, то перед развертыванием база данных переводится в однопользовательский режим.
|**/p:**|DisableAndReenableDdlTriggers=(BOOLEAN 'True')| Указывает, следует ли отключить триггеры языка описания данных DDL в начале процесса публикации и включить их в конце.|
|**/p:**|DoNotAlterChangeDataCaptureObjects=(BOOLEAN 'True')|Если указано значение true, объекты отслеживания измененных данных не меняются.
|**/p:**|DoNotAlterReplicatedObjects=(BOOLEAN 'True')|Указывает, определяются ли во время проверки реплицируемые объекты.
|**/p:**|DoNotDropObjectType=(STRING)|Тип объекта, который нельзя удалять, если элемент DropObjectsNotInSource имеет значение true. Допустимые имена типов объектов: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.
|**/p:**|DoNotDropObjectTypes=(STRING)|Список типов объектов (разделенных точками с запятой), которые не следует удалять, если параметр DropObjectsNotInSource имеет значение true. Допустимые имена типов объектов: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.
|**/p:**|DropConstraintsNotInSource=(BOOLEAN 'True')|Указывает, будут ли ограничения, которые не существуют в моментальном снимке базы данных (файл DACPAC), удалены из конечной базы данных при публикации.|
|**/p:**|DropDmlTriggersNotInSource=(BOOLEAN 'True')|Указывает, будут ли триггеры DML, которые не существуют в моментальном снимке базы данных (файл DACPAC), удалены из конечной базы данных при публикации.|
|**/p:**|DropExtendedPropertiesNotInSource=(BOOLEAN 'True')|Указывает, будут ли при выполнении публикации в базе данных удалены расширенные свойства, которые не существуют в моментальном снимке базы данных (DACPAC).|
|**/p:**|DropIndexesNotInSource=(BOOLEAN 'True')|Указывает, будут ли индексы, которые не существуют в моментальном снимке базы данных (файл DACPAC), удалены из конечной базы данных при публикации.|
|**/p:**|DropObjectsNotInSource=(BOOLEAN)|Указывает, будут ли объекты, которые не существуют в моментальном снимке базы данных (файл DACPAC), удалены из конечной базы данных при публикации. Это значение имеет приоритет над элементом DropExtendedProperties.|
|**/p:**|DropPermissionsNotInSource=(BOOLEAN)|Указывает, будут ли разрешения, которые не существуют в моментальном снимке базы данных (DACPAC), удалены из целевой базы данных при выполнении публикации обновлений.|
|**/p:**|DropRoleMembersNotInSource=(BOOLEAN)|Указывает, будут ли члены ролей, которые не определены в моментальном снимке базы данных (DACPAC), удалены из целевой базы данных при выполнении публикации обновлений.|
|**/p:**|DropStatisticsNotInSource=(BOOLEAN 'True')|Указывает, будет ли статистика, которая отсутствует в файле моментального снимка базы данных (DACPAC), удалена из конечной базы данных при публикации.|
|**/p:**|ExcludeObjectType=(STRING)|Тип объекта, который должен игнорироваться во время развертывания. Допустимые имена типов объектов: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.
|**/p:**|ExcludeObjectTypes=(STRING)|Список типов объектов, разделенных точками с запятой, которые должны игнорироваться во время развертывания. Допустимые имена типов объектов: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.
|**/p:**|GenerateSmartDefaults=(BOOLEAN)|Автоматически определяет значение по умолчанию при обновлении таблицы, содержащей данные со столбцом, который не допускает значения NULL.
|**/p:**|IgnoreAnsiNulls=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в параметре ANSI NULLS при публикации в базе данных.
|**/p:**|IgnoreAuthorizer=(BOOLEAN)|Определяет, пропускаются или обновляются различия в Authorizer при публикации в базе данных.
|**/p:**|IgnoreColumnCollation=(BOOLEAN)|Определяет, пропускаются или обновляются различия в параметрах сортировки столбцов при публикации в базе данных.
|**/p:**|IgnoreColumnOrder=(BOOLEAN)|Указывает, следует ли игнорировать или обновлять различия в порядке столбцов таблицы при публикации в базе данных.|
|**/p:**|IgnoreComments=(BOOLEAN)|Определяет, пропускаются или обновляются различия в комментариях при публикации в базе данных.
|**/p:**|IgnoreCryptographicProviderFilePath=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в пути к файлам для поставщика служб шифрования при публикации в базе данных.
|**/p:**|IgnoreDdlTriggerOrder=(BOOLEAN)|Определяет, пропускаются или обновляются различия в порядке триггеров для языка описания данных DDL при публикации в базе данных или на сервере.|
|**/p:**|IgnoreDdlTriggerState=(BOOLEAN)|Определяет, пропускаются или обновляются различия в состоянии (включен-выключен) триггеров языка описания данных DDL при публикации в базе данных.|
|**/p:**|IgnoreDefaultSchema=(BOOLEAN)|Определяет, пропускаются или обновляются различия в схеме по умолчанию при публикации в базе данных.|
|**/p:**|IgnoreDmlTriggerOrder=(BOOLEAN)|Определяет, пропускаются или обновляются различия в порядке триггеров языка обработки данных DML при публикации в базе данных.|
|**/p:**|IgnoreDmlTriggerState=(BOOLEAN)|Определяет, пропускаются или обновляются различия в состоянии (включен–выключен) триггеров DML при публикации в базе данных.|
|**/p:**|IgnoreExtendedProperties=(BOOLEAN)|Определяет, пропускаются или обновляются различия в расширенных свойствах при публикации в базе данных.|
|**/p:**|IgnoreFileAndLogFilePath=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в путях к файлам и файлам журнала при публикации в базе данных.|
|**/p:**|IgnoreFilegroupPlacement=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в размещении объектов в файловых группах FILEGROUP при публикации в базе данных.|
|**/p:**|IgnoreFileSize=(BOOLEAN 'True')|Определяет, создается ли предупреждение о различиях в размерах файлов при публикации в базе данных.|
|**/p:**|IgnoreFillFactor=(BOOLEAN 'True')|Определяет, создается ли предупреждение о различиях в коэффициенте заполнения для хранилища индексов при публикации.|
|**/p:**|IgnoreFullTextCatalogFilePath=(BOOLEAN 'True')|Указывает, создается ли предупреждение о различиях в пути к файлам для полнотекстового объекта при публикации в базе данных.|
|**/p:**|IgnoreIdentitySeed=(BOOLEAN)|Определяет, пропускаются или обновляются различия в начальном значении для столбца идентификаторов при публикации обновлений в базе данных.|
|**/p:**|IgnoreIncrement=(BOOLEAN)|Определяет, пропускаются или обновляются различия в шаге приращения для столбца идентификаторов при публикации в базе данных.|
|**/p:**|IgnoreIndexOptions=(BOOLEAN)|Определяет, пропускаются или обновляются различия в параметрах индексов при публикации в базе данных.|
|**/p:**|IgnoreIndexPadding=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в заполнении индекса при публикации в базе данных.|
|**/p:**|IgnoreKeywordCasing=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в регистре ключевых слов при публикации в базе данных.|
|**/p:**|IgnoreLockHintsOnIndexes=(BOOLEAN)|Указывает, следует пропускать или обновлять различия в указаниях блокировки для индексов во время публикации в базе данных.|
|**/p:**|IgnoreLoginSids=(BOOLEAN 'True')| Определяет, пропускаются или обновляются различия в идентификаторе безопасности (SID) при публикации в базе данных.|
|**/p:**|IgnoreNotForReplication=(BOOLEAN)|Определяет, пропускаются или обновляются параметры "не для репликации" при публикации в базе данных.|
|**/p:**|IgnoreObjectPlacementOnPartitionScheme=(BOOLEAN 'True')|Определяет, пропускается или обновляется размещение объекта в схеме секционирования при публикации в базе данных.|
|**/p:**|IgnorePartitionSchemes=(BOOLEAN)|Определяет, пропускаются или обновляются различия в функциях и схемах секционирования при публикации в базе данных.|
|**/p:**|IgnorePermissions=(BOOLEAN)|Определяет, пропускаются или обновляются различия в разрешениях при публикации в базе данных.|
|**/p:**|IgnoreQuotedIdentifiers=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в параметре нестандартных идентификаторов при публикации в базе данных.|
|**/p:**|IgnoreRoleMembership=(BOOLEAN)|Указывает, следует пропускать или обновлять различия в членстве в роли имен входа во время публикации в базе данных.|
|**/p:**|IgnoreRouteLifetime=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в продолжительности периода, в течение которого SQL Server хранит маршрут в таблице маршрутизации, при публикации в базе данных.|
|**/p:**|IgnoreSemicolonBetweenStatements=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в точках с запятой между инструкциями T-SQL при публикации в базе данных.|
|**/p:**|IgnoreTableOptions=(BOOLEAN)|Определяет, пропускаются или обновляются различия в параметрах таблиц при публикации в базе данных.|
|**/p:**|IgnoreTablePartitionOptions=(BOOLEAN)|Определяет, пропускаются или обновляются различия в параметрах секций таблиц при публикации в базе данных.  Этот параметр применяется только к базам данных хранилищ данных Azure Synapse Analytics.|
|**/p:**|IgnoreUserSettingsObjects=(BOOLEAN)|Определяет, пропускаются или обновляются различия в объектах параметров пользователя при публикации в базе данных.|
|**/p:**|IgnoreWhitespace=(BOOLEAN 'True')|Определяет, пропускаются или обновляются различия в пробелах при публикации в базе данных.|
|**/p:**|IgnoreWithNocheckOnCheckConstraints=(BOOLEAN)|Определяет, пропускаются или обновляются различия в значении предложения WITH NOCHECK для проверочных ограничений при публикации.|
|**/p:**|IgnoreWithNocheckOnForeignKeys=(BOOLEAN)|Определяет, пропускаются или обновляются различия в значении предложения WITH NOCHECK для внешних ключей при публикации в базе данных.|
|**/p:**|IncludeCompositeObjects=(BOOLEAN)|Включить все составные элементы в единую операцию публикации.|
|**/p:**|IncludeTransactionalScripts=(BOOLEAN)|Определяет, будут ли по возможности использоваться инструкции транзакций при публикации в базе данных.|
|**/p:**|LongRunningCommandTimeout=(INT32)| Позволяет задать время ожидания в секундах для длительной команды при выполнении запросов к SQL Server. Для ожидания без ограничений используйте значение "0".|
|**/p:**|NoAlterStatementsToChangeClrTypes=(BOOLEAN)|Указывает, что при публикации (при наличии различий) вместо выполнения инструкции ALTER ASSEMBLY сборка всегда должна удаляться и создаваться повторно.|
|**/p:**|PopulateFilesOnFileGroups=(BOOLEAN 'True')|Указывает, создается ли файл при создании файловой группы FileGroup в целевой базе данных.|
|**/p:**|RegisterDataTierApplication=(BOOLEAN)|Указывает, регистрируется ли схема на сервере базы данных.|
|**/p:**|RunDeploymentPlanExecutors=(BOOLEAN)|Указывает, должны ли выполняться участники DeploymentPlanExecutor при выполнении других операций.|
|**/p:**|ScriptDatabaseCollation=(BOOLEAN)|Определяет, пропускаются или обновляются различия в параметрах сортировки базы данных при публикации в базе данных.|
|**/p:**|ScriptDatabaseCompatibility=(BOOLEAN)|Определяет, пропускаются или обновляются различия в уровне совместимости базы данных при публикации в базе данных.|
|**/p:**|ScriptDatabaseOptions=(BOOLEAN 'True')|Определяет, будут ли свойства целевой базы данных задаваться или обновляться в рамках действия публикации.|
|**/p:**|ScriptDeployStateChecks=(BOOLEAN)|Определяет, создаются ли инструкции в скрипте публикации, чтобы проверить соответствие имен базы данных и сервера с именами, указанными в проекте базы данных.|
|**/p:**|ScriptFileSize=(BOOLEAN)|Определяет, указывается ли размер при добавлении файла в файловую группу.|
|**/p:**|ScriptNewConstraintValidation=(BOOLEAN 'True')|В конце публикации все ограничения будут проверяться как один набор, избегая ошибок данных, вызванных ограничением проверки или внешнего ключа в середине публикации. Если этот параметр имеет значение False, ограничения публикуются без проверки соответствующих данных.|
|**/p:**|ScriptRefreshModule=(BOOLEAN 'True')|Включать инструкции обновления в конец скрипта публикации.|
|**/p:**|Storage=({File&#124;Memory})|Указывает, как сохраняются элементы при построении модели базы данных. Для обеспечения высокой производительности по умолчанию используется значение InMemory. Для больших баз данных требуется хранилище с использованием файлов.|
|**/p:**|TreatVerificationErrorsAsWarnings=(BOOLEAN)|Указывает, должны ли ошибки, обнаруженные во время проверки публикации, обрабатываться как предупреждения. Проверка выполняется применительно к сформированному плану развертывания перед его выполнением применительно к целевой базе данных. Проверка плана выявляет такие проблемы, как потеря объектов, существующих только в целевой базе данных (например, индексов), которые должны быть удалены в процессе внесения изменений. Кроме того, она выявляет ситуации, когда зависимости (например, таблицы или представления) существуют в результате наличия ссылок на составной проект, но отсутствуют в целевой базе данных. Это можно сделать, чтобы получить полный список всех проблем, вместо завершения действия публикации при первой ошибке.|
|**/p:**|UnmodifiableObjectWarnings=(BOOLEAN 'True')|Указывает, следует ли формировать предупреждения, если обнаружены различия в объектах, которые не могут быть изменены (например, если отличаются размеры или пути файлов).|
|**/p:**|VerifyCollationCompatibility=(BOOLEAN 'True')|Указывает, проверяется ли совместимость параметров сортировки.
|**/p:**|VerifyDeployment=(BOOLEAN 'True')|Указывает, следует ли выполнять проверки перед началом публикации, останавливаемой при возникновении проблем, которые могут заблокировать успешную публикацию. Например, публикация может остановиться в случае, если во время публикации возникли ошибки, связанные с тем, что внешние ключи в целевой базе данных не существуют в проекте базы данных.|

## <a name="exit-codes"></a>Коды выхода

Команды, возвращающие следующие коды выхода:

- 0 = успешное завершение;
- ненулевое значение = сбой.
