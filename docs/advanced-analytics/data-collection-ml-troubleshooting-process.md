---
title: Устранение неполадок при сборе данных для машинного обучения — службы SQL Server машинного обучения
ms.prod: sql
ms.technology: machine-learning
ms.date: 02/28/2019
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a4fdd31cddaba1c46cc14ae6dbdeeb6ad92449da
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/07/2019
ms.locfileid: "57579134"
---
# <a name="troubleshoot-data-collection-for-machine-learning"></a>Устранение неполадок при сборе данных для машинного обучения

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описаны методы сбора данных, которые следует использовать при попытке устранения проблем самостоятельно или с помощью клиента Microsoft поддерживают.

**Применимо к:** Службы R SQL Server 2016, SQL Server 2017 службы машинного обучения (R и Python)

## <a name="sql-server-version-and-edition"></a>Версии и выпуска SQL Server

SQL Server 2016 R Services — это первый выпуск SQL Server для поддержки интеграции R. SQL Server 2016 с пакетом обновления 1 (SP1) включает в себя несколько существенных улучшений, включая возможность выполнения внешних скриптов. Если вы являетесь клиентом SQL Server 2016, следует устанавливать с пакетом обновления 1 или более поздней версии.

SQL Server 2017 добавлена интеграция языка Python. Не удается получить функция интеграции с Python в более ранних выпусках.

Помощь начало выпуска и версии, см. в этой статье перечислены номера сборки для каждого из [версий SQL Server](https://social.technet.microsoft.com/wiki/contents/articles/783.sql-server-versions.aspx#Service_Pack_editions).

Зависимости от выпуска SQL Server, вы используете некоторые машинного обучения функциональность может быть недоступна или ограниченный. Следующий список статей функции машинного обучения в выпусках Enterprise, Developer, Standard и Express.

* [Выпуски и поддерживаемые функции SQL Server](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016)
* [Функции R и Python с версии SQL Server](r/differences-in-r-features-between-editions-of-sql-server.md)

## <a name="r-language-and-tool-versions"></a>Язык и средства версии R

Как правило версию Microsoft R, которая устанавливается при выборе компонент служб r. или компонент служб машинного обучения определяется номером сборки SQL Server. Если обновления или исправления SQL Server, необходимо также обновления или исправления его компонентов R.

Список выпусков, а также ссылки на файлы для загрузки компонентов R, см. в разделе [Установка компонентов машинного обучения без доступа к Интернету](https://docs.microsoft.com/sql/advanced-analytics/r/installing-ml-components-without-internet-access). На компьютерах с доступом в Интернет требуемая версия R определяется и устанавливаются автоматически.

Можно отдельно обновить компоненты R Server из ядра СУБД SQL Server, в процесс, называемый привязки. Поэтому версии R, используемой при выполнении кода R в SQL Server могут отличаться в зависимости от установленной версии SQL Server и ли переноса сервера до последней версии R.

### <a name="determine-the-r-version"></a>Определение версии R

— Это самый простой способ определения версии R для получения свойств среды выполнения, выполнив инструкцию, такую как следующие:

```sql
exec sp_execute_external_script
       @language = N'R'
       , @script = N'
# Transform R version properties to data.frame
OutputDataSet <- data.frame(
  property_name = c("R.version", "Revo.version"),
  property_value = c(R.Version()$version.string, Revo.version$version.string),
  stringsAsFactors = FALSE)
# Retrieve properties like R.home, libPath & default packages
OutputDataSet <- rbind(OutputDataSet, data.frame(
  property_name = c("R.home", "libPaths", "defaultPackages"),
  property_value = c(R.home(), .libPaths(), paste(getOption("defaultPackages"), collapse=", ")),
  stringsAsFactors = FALSE)
)
'
WITH RESULT SETS ((PropertyName nvarchar(100), PropertyValue nvarchar(4000)));

```

> [!TIP]
> Если службы R не работает, попробуйте запустить только часть скрипта R из RGui.

В качестве последнего средства можно открыть файлы на сервере, чтобы определить установленную версию. Чтобы сделать это, найдите файл rlauncher.config для получения расположения среды выполнения R и текущий рабочий каталог. Рекомендуется создать и открыть копию файла, поэтому не случайно изменить какие-либо свойства.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name\MSSQL\Binn\rlauncher.config`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Binn\rlauncher.config`

Чтобы получить версии R и RevoScaleR, откройте командную строку R или откройте RGui, который связан с экземпляром.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64\RGui.exe`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES\bin\x64\RGui.exe`

В консоли R отображаются сведения о версии во время запуска. Например следующая версия представляет конфигурации по умолчанию для SQL Server 2017:

    *Microsoft R Open 3.3.3*

    *The enhanced R distribution from Microsoft*

    *Microsoft packages Copyright (C) 2017 Microsoft*

    *Loading Microsoft R Server packages, version 9.1.0.*

## <a name="python-versions"></a>Версии Python

Существует несколько способов получить версию Python. Самым простым способом является для выполнения этой инструкции в Management Studio или другом средстве запросов SQL:

```sql
-- Get Python runtime properties:
exec sp_execute_external_script
       @language = N'Python'
       , @script = N'
import sys
import pkg_resources
OutputDataSet = pandas.DataFrame(
                    {"property_name": ["Python.home", "Python.version", "Revo.version", "libpaths"],
                    "property_value": [sys.executable[:-10], sys.version, pkg_resources.get_distribution("revoscalepy").version, str(sys.path)]}
)
'
with WITH RESULT SETS (SQL keywords) ((PropertyName nvarchar(100), PropertyValue nvarchar(4000)));
```

Если службы машинного обучения не запущена, можно определить установленную версию Python, просмотрев файл pythonlauncher.config. Рекомендуется создать и открыть копию файла, поэтому не случайно изменить какие-либо свойства.

1. Только для SQL Server 2017: `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog\pythonlauncher.config`
2. Получить значение для **PYTHONHOME**.
3. Получает значение текущего рабочего каталога.

> [!NOTE]
> Если вы установили Python и R в SQL Server 2017, рабочий каталог и пул рабочих учетных записей являются общими для языков R и Python.

## <a name="are-multiple-instances-of-r-or-python-installed"></a>Несколько экземпляров служб R или Python устанавливается?

Установите этот флажок, чтобы узнать, установлена ли более чем одну копию библиотеки R на компьютере. Это дублирование возможно в том случае, если:

* Во время установки выбрать службы R (в базе данных) и R Server (изолированный).
* Вы установите Microsoft R Client, помимо SQL Server.
* Другой набор библиотек R была установлена с помощью инструментов R для Visual Studio, R Studio, Microsoft R Client или другую среду R IDE.
* Компьютер содержит несколько экземпляров SQL Server, а более одного экземпляра использует машинное обучение.

Такие же условия применяются к Python.

Если обнаружится, что устанавливаются несколько библиотек или сред выполнения, убедитесь, что вы получаете только ошибки, связанные с сред выполнения Python или R, которые используются в экземпляре SQL Server.

## <a name="origin-of-errors"></a>Источник ошибки

Ошибки, которое отображается при попытке запуска кода R могут поступать из любого из следующих источников:

* Ядро СУБД SQL Server, включая хранимой процедуры sp_execute_external_script
* SQL Server доверенная панель запуска
* Другие компоненты платформы расширения, включая средства запуска R и Python и вспомогательными процессами
* Поставщиков, таких как Microsoft Open Database Connectivity (ODBC)
* Язык R

При работе со службой в первый раз, может быть трудно определить, какие сообщения получаются из службы. Рекомендуется перехватывать не только текстовое сообщение об ошибке, но контекст, в котором вы видели сообщение. Обратите внимание, клиентское программное обеспечение, вы используете для выполнения машинного обучения кода:

* Вы используете Management Studio? Внешнее приложение?
* Вы используете код R, в удаленный клиент или непосредственно в хранимой процедуре?

## <a name="sql-server-log-files"></a>Файлы журналов SQL Server

Получите последние журнале ОШИБОК SQL Server. Полный набор журналов ошибок состоит из файлов из следующего каталога журнала по умолчанию:

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.SQL2016\MSSQL\Log\ExtensibilityLog`

> [!NOTE]
> Точное имя папки будет зависеть от имени экземпляра.

## <a name="errors-returned-by-spexecuteexternalscript"></a>Ошибки, возвращенные sp_execute_external_script

Получите полный текст ошибки, которые возвращаются, если таковое имеется, при выполнении команды sp_execute_external_script.

Чтобы удалить ошибки R или Python из рассмотрения, можно запустить этот скрипт, который запускает среду выполнения R или Python и передает данные и обратно.

**Для R**

```sql
exec sp_execute_external_script @language =N'R',  
@script=N'OutputDataSet<-InputDataSet',  
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go
```

**Для Python**

```sql
exec sp_execute_external_script @language =N'Python',  
@script=N'OutputDataSet= InputDataSet',  
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go
```

## <a name="errors-generated-by-the-extensibility-framework"></a>Ошибки, создаваемые платформой расширяемости

SQL Server создает отдельные журналы для языковых сред выполнения внешнего скрипта. Эти ошибки не создаются в языке R или Python. Они будут созданы из компонентами расширяемости в SQL Server, включая средства запуска конкретного языка и их вспомогательными процессами.

Эти журналы можно получить из следующих расположений по умолчанию:

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog`

> [!NOTE]
> Точное имя папки отличается в зависимости от имени экземпляра. В зависимости от конфигурации папка может быть на другом диске.

Например следующие сообщения журнала, касающиеся инфраструктуры расширяемости.

* *Сбой LogonUser для пользователя MSSQLSERVER01*
  
  Это может означать, что рабочие учетные записи внешних сценариев нет доступа к экземпляру.

* *Не удалось InitializePhysicalUsersPool*
  
  Это сообщение может означать, что параметры безопасности препятствуют установки создается пул рабочих учетных записей, которые необходимы для выполнения внешних скриптов.

* *Не удалось инициализировать диспетчер контекста безопасности*

* *Не удалось инициализировать диспетчер сеансов вспомогательной*

## <a name="system-events"></a>Системные события

1. Откройте средство просмотра событий Windows и найдите **системное событие** сообщения, содержащие строку в журнале *панель запуска*.
2. Откройте файл ExtLaunchErrorlog и искать строки *ErrorCode*. Ознакомьтесь с сообщением, связанную с ErrorCode.

Например следующие сообщения являются общие системные ошибки, относящиеся к структуре расширяемости SQL Server:

* *Служба панели запуска SQL Server (MSSQLSERVER) не удалось запуститься из-за следующей ошибки:  <text>*

* *Служба не ответила на запрос запуска или управления за отведенное время.*

* *Во время ожидания для службы панели запуска SQL Server (MSSQLSERVER) для подключения истекло время ожидания (120000 миллисекунд).*

## <a name="dump-files"></a>Файлы дампа

Если вы являетесь знаниями об отладке, можно использовать файлы дампа для анализа сбоев в панели запуска.

1. Найдите папку, содержащую журналы установки начальной загрузки для SQL Server. Например в SQL Server 2016 путь по умолчанию был C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log.
2. Откройте папку журнала начальной загрузки, относящиеся к расширяемости.
3. Если вам нужно отправить запрос в службу поддержки, добавьте все содержимое этой папки в ZIP-файл. Например C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log\LOG\ExtensibilityLog.
  
Точное расположение может отличаться в вашей системе, и он может располагаться на любом диске, кроме диска c. Не забудьте получить журналы для экземпляра, где установлен машинного обучения.

## <a name="configuration-settings"></a>Параметры конфигурации

В этом разделе перечислены дополнительные компоненты или поставщиков, которые могут стать источником ошибок при выполнении скриптов R или Python.

### <a name="what-network-protocols-are-available"></a>Какие сетевые протоколы доступны?

Службы машинного обучения требуются следующие сетевые протоколы для внутренней связи между компонентами расширяемости и для взаимодействия с внешними клиентами R или Python.

* Именованные каналы
* TCP/IP

Откройте диспетчер конфигурации SQL Server для определения протокола, установлен ли и, если он установлен, чтобы определить, включена ли она.

### <a name="security-configuration-and-permissions"></a>Настройка безопасности и разрешений

Для рабочих учетных записей:

1. В панели управления откройте **пользователей и групп**и найдите группу, используемый для выполнения внешних скриптов заданий. По умолчанию, данная группа является **SQLRUserGroup**.
2. Убедитесь, что группа существует и что он содержит по крайней мере одна рабочая учетная запись.
3. В SQL Server Management Studio, выберите экземпляр, в которой будет выполняться задания R или Python, выберите **безопасности**, а затем определить, существует ли вход для SQLRUserGroup.
4. Просмотрите разрешения для группы пользователей.

Для отдельных учетных записей пользователей:

1. Определите, поддерживает ли экземпляр смешанного режима проверки подлинности, только имена входа SQL или только проверку подлинности Windows. Этот параметр влияет на R или Python code требования.
2. Для каждого пользователя, который нужно выполнять код R определите необходимый уровень разрешений в каждой базе данных, где объекты будут записаны из R, данные будут доступны или будут созданы объекты.
3. Чтобы включить выполнение сценариев, Создание ролей или добавить пользователей в следующие роли, при необходимости:

   - Все, кроме *db_owner*: Требуется выполнение ЛЮБОГО ВНЕШНЕГО СКРИПТА.
   - *db_datawriter*: Для записи результатов из R или Python.
   - *db_ddladmin*: Для создания новых объектов.
   - *db_datareader*: Для чтения данных, который используется с кодом R или Python.
4. Обратите внимание на то, изменено ли учетные записи запуска по умолчанию при установке SQL Server 2016.
5. Если пользователю нужно установить новые пакеты R или использования пакетов R, установленных другими пользователями, может потребоваться включение управления пакетами в экземпляре, а затем назначить дополнительные разрешения. Дополнительные сведения см. в разделе [включить или отключить управление пакетами R](r/r-package-how-to-enable-or-disable.md).

### <a name="what-folders-are-subject-to-locking-by-antivirus-software"></a>Какие папки используются применяются блокировки, антивирусное программное обеспечение?

Антивирусное программное обеспечение может выполнить блокировку папок, препятствующий установки машинного обучения, функции и выполнение скрипта успешно. Определите, являются ли все папки в дереве SQL Server может быть поиск вирусов.

Тем не менее при установке нескольких служб или компонентов на экземпляре трудно перечислить все возможные папки, которые используются в экземпляре. Например когда добавляются новые функции, новые папки необходимо идентифицировать и исключены.

Кроме того некоторые возможности создавать новые папки динамически во время выполнения. Например таблицы OLTP в памяти, хранимые процедуры и функции создайте новые каталоги во время выполнения. Эти имена папок часто содержат идентификаторы GUID и предсказать невозможно. SQL Server доверенная панель запуска создает новые рабочие каталоги для R и Python скрипты заданий.

Может оказаться невозможным исключение всех папок, необходимые процессу SQL Server и его компонентах, поэтому рекомендуется исключить все дерево каталогов экземпляра SQL Server.

### <a name="is-the-firewall-open-for-sql-server-does-the-instance-support-remote-connections"></a>Открыт брандмауэра для SQL Server? Поддерживает ли экземпляр удаленные соединения?

1. Чтобы определить, поддерживает ли SQL Server удаленные подключения, см. в разделе [Настройка соединения с удаленным сервером](../database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md).

2. Определите, был ли создан правило брандмауэра для SQL Server. По соображениям безопасности при установке по умолчанию не возможно для удаленного клиента R или Python, чтобы соединиться с экземпляром. Дополнительные сведения см. в разделе [Устранение неполадок подключения к SQL Server](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md).

## <a name="see-also"></a>См. также

[Устранение неполадок машинного обучения в SQL Server](machine-learning-troubleshooting-faq.md)
