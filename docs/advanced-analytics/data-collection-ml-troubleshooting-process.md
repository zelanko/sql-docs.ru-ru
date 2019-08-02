---
title: Устранение неполадок сбора данных для машинного обучения
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c7566d9b25b15a334e48380daca6cb81e92f6a2b
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715233"
---
# <a name="troubleshoot-data-collection-for-machine-learning"></a>Устранение неполадок сбора данных для машинного обучения

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье описываются методы сбора данных, которые следует использовать при попытке самостоятельно разрешать проблемы или с помощью службы поддержки пользователей Майкрософт.

## <a name="sql-server-version-and-edition"></a>SQL Server версии и выпуска

SQL Server 2016 R Services — это первый выпуск SQL Server, включающий интегрированную поддержку R. SQL Server 2016 с пакетом обновления 1 (SP1) включает несколько основных усовершенствований, включая возможность запуска внешних сценариев. При использовании SQL Server 2016 рекомендуется установить пакет обновления 1 (SP1) или более поздней версии.

В SQL Server 2017 и более поздних версий установлена интеграция с языком Python. В более ранних выпусках невозможно получить интеграцию возможностей Python.

Сведения о получении выпуска и версий см. в этой статье, где перечислены номера сборок для каждой из [SQL Server версий](https://social.technet.microsoft.com/wiki/contents/articles/783.sql-server-versions.aspx#Service_Pack_editions).

В зависимости от используемого выпуска SQL Server некоторые функции машинного обучения могут быть недоступны или ограничены. В следующих статьях перечислены функции машинного обучения в выпусках Enterprise Edition, Developer, Standard и Express.

* [Выпуски и поддерживаемые функции SQL Server](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016)
* [Возможности R и Python по выпускам SQL Server](r/differences-in-r-features-between-editions-of-sql-server.md)

## <a name="r-language-and-tool-versions"></a>Версии языка и инструментов R

Как правило, версия Microsoft R, устанавливаемая при выборе компонента служб R или Службы машинного обучения, определяется SQL Serverным номером сборки. При обновлении или исправлении SQL Server необходимо также обновить компоненты R или исправить их.

Список выпусков и ссылки на загружаемые компоненты R см. в [статье Установка компонентов машинного обучения без доступа к Интернету](https://docs.microsoft.com/sql/advanced-analytics/r/installing-ml-components-without-internet-access). На компьютерах с доступом к Интернету необходимая версия R определяется и устанавливается автоматически.

Обновить серверные компоненты R Server можно отдельно от ядра СУБД SQL Server в процессе, известном как Binding. Таким образом, версия R, используемая при запуске кода R в SQL Server, может отличаться в зависимости от установленной версии SQL Server и от того, перенесены ли сервер в последнюю версию R.

### <a name="determine-the-r-version"></a>Определение версии R

Самый простой способ определить версию R — получить свойства среды выполнения, выполнив следующую инструкцию:

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
> Если службы R не работают, попробуйте выполнить только часть скрипта R из RGui.

В качестве последнего средства можно открыть файлы на сервере, чтобы определить установленную версию. Для этого необходимо найти файл rlauncher. config, чтобы получить расположение среды выполнения R и текущего рабочего каталога. Рекомендуется создать и открыть копию файла, чтобы случайно не изменить свойства.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name\MSSQL\Binn\rlauncher.config`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Binn\rlauncher.config`

Чтобы получить версии R и RevoScaleR, откройте командную строку R или откройте RGui, связанный с экземпляром.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64\RGui.exe`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES\bin\x64\RGui.exe`

В консоли R отображаются сведения о версии при запуске. Например, следующая версия представляет конфигурацию по умолчанию для SQL Server 2017:

    *Microsoft R Open 3.3.3*

    *The enhanced R distribution from Microsoft*

    *Microsoft packages Copyright (C) 2017 Microsoft*

    *Loading Microsoft R Server packages, version 9.1.0.*

## <a name="python-versions"></a>Версии Python

Существует несколько способов получить версию Python. Самый простой способ — запустить эту инструкцию из Management Studio или любого другого средства SQL-запроса:

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

Если Службы машинного обучения не выполняется, можно определить установленную версию Python, просмотрев файл писонлаунчер. config. Рекомендуется создать и открыть копию файла, чтобы случайно не изменить свойства.

1. Только для SQL Server 2017:`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog\pythonlauncher.config`
2. Получите значение для **писонхоме**.
3. Возвращает значение текущего рабочего каталога.

> [!NOTE]
> Если вы установили Python и R в SQL Server 2017, Рабочий каталог и пул рабочих учетных записей являются общими для языков R и Python.

## <a name="are-multiple-instances-of-r-or-python-installed"></a>Установлены ли несколько экземпляров R или Python?

Проверьте, установлена ли на компьютере более одной копии библиотек R. Это дублирование может произойти в следующих случаях.

* Во время установки вы выбрали обе службы R (в базе данных) и R Server (изолированный).
* Вы устанавливаете Microsoft R Client в дополнение к SQL Server.
* Другой набор библиотек R был установлен с помощью Инструменты R для Visual Studio, R Studio, Microsoft R Client или другой среды R IDE.
* На компьютере размещается несколько экземпляров SQL Server, а в нескольких экземплярах используется машинное обучение.

Те же условия применимы к Python.

Если вы обнаружите, что установлено несколько библиотек или сред выполнения, убедитесь, что вы получаете только ошибки, связанные с средами выполнения Python или R, используемыми экземпляром SQL Server.

## <a name="origin-of-errors"></a>Происхождение ошибок

Ошибки, отображаемые при попытке выполнить код R, могут поступать из любого из следующих источников:

* Ядро СУБД SQL Server, включая хранимую процедуру sp_execute_external_script
* Доверенная панель запуска SQL Server
* Другие компоненты платформы расширяемости, включая запуски R и Python и вспомогательные процессы
* Поставщики, такие как Microsoft Open Database Connectivity (ODBC)
* Язык R

При первой работе со службой может быть трудно определить, какие сообщения исходят от служб. Рекомендуется записывать не только точный текст сообщения, но и контекст, в котором было показано сообщение. Обратите внимание на клиентское программное обеспечение, которое используется для запуска кода машинного обучения.

* Вы используете Management Studio? Внешнее приложение?
* Вы запускаете код R в удаленном клиенте или непосредственно в хранимой процедуре?

## <a name="sql-server-log-files"></a>Файлы журналов SQL Server

Получите последнюю SQL Server ERRORLOG. Полный набор журналов ошибок состоит из файлов из следующего каталога журналов по умолчанию:

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.SQL2016\MSSQL\Log\ExtensibilityLog`

> [!NOTE]
> Точное имя папки различается в зависимости от имени экземпляра.

## <a name="errors-returned-by-spexecuteexternalscript"></a>Ошибки, возвращенные sp_execute_external_script

Получение полного текста ошибок, возвращаемых при выполнении команды sp_execute_external_script, если таковые имеются.

Чтобы устранить проблемы с R или Python, можно выполнить этот скрипт, который запускает среду выполнения R или Python и передает данные назад и вперед.

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

SQL Server создает отдельные журналы для языковых сред выполнения для внешних скриптов. Эти ошибки не создаются языком Python или R. Они создаются из компонентов расширяемости в SQL Server, включая средства запуска для конкретных языков и их вспомогательные процессы.

Эти журналы можно получить из следующих расположений по умолчанию:

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog`

> [!NOTE]
> Точное имя папки различается в зависимости от имени экземпляра. В зависимости от конфигурации папка может находиться на другом диске.

Например, следующие сообщения журнала связаны с платформой расширяемости:

* *Сбой LogonUser для пользователя MSSQLSERVER01*
  
  Это может означать, что рабочие учетные записи, выполняющие внешние скрипты, не могут получить доступ к экземпляру.

* *Сбой Инитиализефисикалусерспул*
  
  Это сообщение может означать, что параметры безопасности не позволяют программе установки создать пул рабочих учетных записей, необходимых для выполнения внешних скриптов.

* *Не удалось инициализировать диспетчер контекста безопасности*

* *Не удалось инициализировать диспетчер сеансов спутниковой связи*

## <a name="system-events"></a>Системные события

1. Откройте Просмотр событий Windows и найдите в журнале **системных событий** сообщения, включающие *панель*запуска строк.
2. Откройте файл Екстлаунчеррорлог и найдите строку *ErrorCode*. Проверьте сообщение, связанное с ErrorCode.

Например, следующие сообщения являются общими системными ошибками, связанными с платформой расширяемости SQL Server:

* *Не удалось запустить службу панель запуска SQL Server (MSSQLSERVER) из-за следующей ошибки:<text>*

* *Служба не ответила на запрос запуска или управления в течение отведенного времени.*

* *Истекло время ожидания (120000 миллисекунд) при ожидании подключения службы панель запуска SQL Server (MSSQLSERVER).*

## <a name="dump-files"></a>Файлы дампа

Если вы осведомлены об отладке, можно использовать файлы дампа для анализа сбоя на панели запуска.

1. Откройте папку, в которой находятся журналы начальной загрузки для SQL Server. Например, в SQL Server 2016 по умолчанию используется путь C:\Program Files\Microsoft SQL Server\130\Setup Бутстрап\лог.
2. Откройте вложенную папку журнала начальной загрузки, относящуюся к расширяемости.
3. Если вам нужно отправить запрос в службу поддержки, добавьте все содержимое этой папки в ZIP-файл. Например, C:\Program Files\Microsoft SQL Server\130\Setup Бутстрап\лог\лог\екстенсибилитилог.
  
Точное расположение может отличаться в вашей системе и может находиться на диске, отличном от диска C. Не забудьте получить журналы для экземпляра, на котором установлено машинное обучение.

## <a name="configuration-settings"></a>Параметры конфигурации

В этом разделе перечислены дополнительные компоненты или поставщики, которые могут быть источником ошибок при выполнении скриптов R или Python.

### <a name="what-network-protocols-are-available"></a>Какие сетевые протоколы доступны?

Службы машинного обучения требуются следующие сетевые протоколы для внутреннего взаимодействия между компонентами расширяемости и для взаимодействия с внешними клиентами R или Python.

* Именованные каналы
* TCP/IP

Откройте диспетчер конфигурации SQL Server, чтобы определить, установлен ли протокол, и, если он установлен, определить, включен ли он.

### <a name="security-configuration-and-permissions"></a>Настройка безопасности и разрешения

Для рабочих учетных записей:

1. На панели управления откройте **Пользователи и группы**и выберите группу, используемую для запуска заданий внешних скриптов. По умолчанию группа — **SQLRUserGroup**.
2. Убедитесь, что группа существует и содержит по крайней мере одну рабочую учетную запись.
3. В SQL Server Management Studio выберите экземпляр, где будут выполняться задания R или Python, выберите **Безопасность**, а затем определите, есть ли вход в систему для SQLRUserGroup.
4. Проверьте разрешения для группы пользователей.

Для учетных записей отдельных пользователей:

1. Определите, поддерживает ли экземпляр проверку подлинности в смешанном режиме, только имена входа SQL или только проверку подлинности Windows. Этот параметр влияет на требования к коду R или Python.
2. Для каждого пользователя, который должен выполнять код R, определите необходимый уровень разрешений на каждой базе данных, где объекты будут записываться из R, будут доступны данные или будут созданы объекты.
3. Чтобы включить выполнение скрипта, создайте роли или добавьте пользователей в следующие роли при необходимости:

   - Все, кроме *db_owner*: Требуется выполнение любого внешнего СКРИПТа.
   - *db_datawriter*: Для записи результатов из R или Python.
   - *db_ddladmin*: Для создания новых объектов.
   - *db_datareader*: Для чтения данных, используемых кодом R или Python.
4. Обратите внимание, изменились ли учетные записи запуска по умолчанию при установке SQL Server 2016.
5. Если пользователю необходимо установить новые пакеты R или использовать пакеты R, установленные другими пользователями, может потребоваться включить управление пакетами в экземпляре, а затем назначить дополнительные разрешения. Дополнительные сведения см. в разделе [Включение или отключение управления пакетами R](r/r-package-how-to-enable-or-disable.md).

### <a name="what-folders-are-subject-to-locking-by-antivirus-software"></a>Какие папки подвергаются блокированию антивирусного по?

Антивирусная программа может блокировать папки, что предотвращает настройку функций машинного обучения и выполнение сценариев. Определите, подвергаются ли какие либо папки в дереве SQL Server поиском вирусов.

Однако если на экземпляре установлены несколько служб или компонентов, может быть трудно перечислить все возможные папки, используемые экземпляром. Например, при добавлении новых возможностей новые папки должны быть идентифицированы и исключены.

Более того, некоторые функции динамически создают новые папки во время выполнения. Например, таблицы, хранимые процедуры и функции OLTP в памяти создают новые каталоги во время выполнения. Эти имена папок часто содержат идентификаторы GUID и не могут быть прогнозируемыми. SQL Server Доверенная панель запуска создает новые рабочие каталоги для заданий скриптов R и Python.

Поскольку невозможно исключить все папки, необходимые для процесса SQL Server и его функций, рекомендуется исключить все дерево каталогов SQL Server экземпляра.

### <a name="is-the-firewall-open-for-sql-server-does-the-instance-support-remote-connections"></a>Открыт ли брандмауэр для SQL Server? Поддерживает ли экземпляр удаленные подключения?

1. Чтобы определить, поддерживает ли SQL Server удаленные подключения, см. раздел [Настройка подключений к удаленному серверу](../database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md).

2. Определите, было ли создано правило брандмауэра для SQL Server. По соображениям безопасности при установке по умолчанию удаленный клиент R или Python может подключиться к экземпляру невозможным. Дополнительные сведения см. [в разделе Устранение неполадок подключения к SQL Server](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md).

## <a name="see-also"></a>См. также

[Устранение неполадок машинного обучения в SQL Server](machine-learning-troubleshooting-faq.md)
