---
title: Установка SQL Server с помощью PowerShell Desired State Configuration | Документация Майкрософт
description: Сведения об установке SQL Server с использованием PowerShell Desired State Configuration (DSC).
ms.custom: ''
ms.date: 10/26/2018
ms.devlang: PowerShell
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
author: randomnote1
ms.author: dareist
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 16d425d8eb66a950f432fa3ef9c68a8e68a78d22
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2018
ms.locfileid: "50148486"
---
# <a name="install-sql-server-with-powershell-desired-state-configuration"></a>Установка SQL Server с помощью PowerShell Desired State Configuration

Часто ли вам приходится буквально "на автомате" пролистывать интерфейс установки SQL Server, нажимая одни и те же кнопки и вводя давно знакомую информацию? А потом, после установки, вы вдруг вспоминаете: "Надо же было еще указать группу DBA в роли sysadmin!" Теперь придется тратить драгоценное время на переход в однопользовательский режим, добавление нужных пользователей и групп, возврат SQL в многопользовательский режим и последующую проверку. Но еще хуже то, что вы больше не уверены в установке: "Вдруг что-то еще забылось?" Лично со мной такое случалось много раз.

На помощь приходит [PowerShell Desired State Configuration (DSC)](https://docs.microsoft.com/powershell/dsc/overview). DSC позволяет создать один шаблон конфигурации и использовать его на сотнях тысяч серверов. В зависимости от сборки может потребоваться подправить несколько установочных параметров, но это не проблема, так как все стандартные параметры остаются без изменений. Особенно удобно, что даже если мои дети всю ночь не дадут мне спать, я не рискую забыть ни один важный параметр.

В этой статье я расскажу о начальной установке автономного экземпляра SQL Server 2017 на Windows Server 2016 с использованием DSC-ресурса SqlServerDsc. Будет не лишним, если вы уже знакомы с DSC, так как я не буду рассказывать, как работает эта служба.

Для этого пошагового руководства потребуются следующие элементы.

- Компьютер под управлением Windows Server 2016
- Установочный носитель SQL Server 2017
- DSC-ресурс SqlServerDsc (на момент написания статьи актуальная версия — 10.0.0.0)

## <a name="prerequisites"></a>Предварительные требования

В большинстве случаев для обработки предварительных требований будет использоваться служба DSC. Однако в целях демонстрации я сделаю это вручную.

## <a name="install-the-sqlserverdsc-dsc-resource"></a>Установка DSC-ресурса SqlServerDsc

DSC-ресурс [SqlServerDsc](https://www.powershellgallery.com/packages/SqlServerDsc) можно скачать в [коллекции PowerShell](https://www.powershellgallery.com/) с помощью командлета [Install-Module](https://docs.microsoft.com/powershell/module/powershellget/Install-Module?view=powershell-5.1). _Примечание. Для установки модуля служба PowerShell должна быть запущена от имени администратора._

```PowerShell
Install-Module -Name SqlServerDsc
```

Получение установочного носителя SQL Server 2017 Скачайте установочный носитель SQL Server 2017 на сервер. Я скачал SQL Server 2017 Enterprise в подписке Visual Studio и скопировал файл ISO сюда: "C:\en_sql_server_2017_enterprise_x64_dvd_11293666.iso".

Теперь извлеките ISO в каталог.

```PowerShell
New-Item -Path C:\SQL2017 -ItemType Directory
$mountResult = Mount-DiskImage -ImagePath 'C:\en_sql_server_2017_enterprise_x64_dvd_11293666.iso' -PassThru
$volumeInfo = $mountResult | Get-Volume
$driveInfo = Get-PSDrive -Name $volumeInfo.DriveLetter
Copy-Item -Path ( Join-Path -Path $driveInfo.Root -ChildPath '*' ) -Destination C:\SQL2017\ -Recurse
Dismount-DiskImage -ImagePath 'C:\en_sql_server_2017_enterprise_x64_dvd_11293666.iso'
```

## <a name="create-the-configuration"></a>Создание конфигурации

### <a name="configuration"></a>Конфигурация

Создайте функцию конфигурации, которая будет вызываться для создания документов в формате [MOF](https://docs.microsoft.com/windows/desktop/WmiSdk/managed-object-format--mof-).

```PowerShell
Configuration SQLInstall
{...}
```

### <a name="modules"></a>Модули

Импортируйте модули в текущий сеанс. Эти модули указывают документу конфигурации, как выполнять сборку документов MOF, а подсистеме DSC — как применять документы MOF к серверу.

```PowerShell
Import-DscResource -ModuleName SqlServerDsc
```

### <a name="resources"></a>Ресурсы

#### <a name="net-framework"></a>.NET Framework

SQL Server использует .NET Framework, поэтому нужно установить эту платформу перед установкой SQL Server. Для установки компонента Windows "Net-Framework-45-Core" используется ресурс WindowsFeature.

```PowerShell
WindowsFeature 'NetFramework45'
{
     Name = 'Net-Framework-45-Core'
     Ensure = 'Present'
}
```

#### <a name="sqlsetup"></a>SqlSetup

Ресурс SqlSetup сообщает DSC параметры для установки SQL Server. Для базовой установки необходимы следующие параметры.

- **InstanceName**: имя экземпляра. Для экземпляра по умолчанию используйте MSSQLSERVER.
- **Features**: устанавливаемые компоненты. В этом примере я устанавливаю только компонент SQLEngine.
- **SourcePath**: путь к установочному носителю SQL. В этом примере я сохранил установочный носитель SQL в папке "C:\SQL2017". Чтобы занимаемое место на сервере было минимальным, можно использовать сетевую папку.
- **SQLSysAdminAccounts**: пользователи или группы, которые будут участниками роли sysadmin. В этом примере я предоставляю доступ sysadmin локальной группе Administrators. _Примечание. Эта конфигурация не рекомендуется в среде с повышенной безопасностью._

Полный список и описание параметров, доступных в SqlSetup, см. в [GitHub-репозитории SqlServerDsc](https://github.com/PowerShell/SqlServerDsc/tree/master#sqlsetup).

Ресурс SqlSetup необычный, так как он только устанавливает SQL и не сохраняет применяемые параметры. Например, если указать во время установки значения SQLSysAdminAccount, администратор сможет изменять состав участников роли sysadmin, но ресурса SqlSetup это никак не коснется. Если нужно, чтобы служба DSC принудительно назначала членство роли sysadmin, следует использовать ресурс [SqlServerRole](https://github.com/PowerShell/SqlServerDsc/tree/master#sqlserverrole).

#### <a name="complete-configuration"></a>Полная конфигурация

```PowerShell
Configuration SQLInstall
{
     Import-DscResource -ModuleName SqlServerDsc

     node localhost
     {
          WindowsFeature 'NetFramework45'
          {
               Name   = 'NET-Framework-45-Core'
               Ensure = 'Present'
          }

          SqlSetup 'InstallDefaultInstance'
          {
               InstanceName        = 'MSSQLSERVER'
               Features            = 'SQLENGINE'
               SourcePath          = 'C:\SQL2017'
               SQLSysAdminAccounts = @('Administrators')
               DependsOn           = '[WindowsFeature]NetFramework45'
          }
     }
}
```

## <a name="build-and-deploy"></a>Сборка и развертывание

### <a name="compile-the-configuration"></a>Компиляция конфигурации

Укажите через точку скрипт конфигурации:

```PowerShell
. .\SQLInstallConfiguration.ps1
```

Выполните функцию конфигурации:

```PowerShell
SQLInstall
```

В рабочем каталоге будет создан каталог SQLInstall с файлом localhost.mof. Содержимое MOF-файла — скомпилированная конфигурация DSC.

### <a name="deploy-the-configuration"></a>Развертывание конфигурации

Чтобы запустить развертывание SQL Server с DCS, вызовите командлет Start-DscConfiguration. Для командлета указываются следующие параметры.

- **Path**: путь к папке с документами MOF для развертывания (например, "C:\SQLInstall").
- **Wait**: ожидание завершения задания конфигурации.
- **Force**: переопределение существующих конфигураций DSC.
- **Verbose**: отображение подробных выходных данных. Это помогает устранить неполадки при отправке конфигурации в первый раз.

```PowerShell
Start-DscConfiguration -Path C:\SQLInstall -Wait -Force -Verbose
```

По мере применения конфигурации подробные выходные данные будут показывать, что сейчас происходит, а вы будете уверены — работа кипит! Если никаких ошибок (красный текст) не возникнет, то на экране появится сообщение "Операция «Invoke CimMethod» завершена." , и SQL Server будет установлен.

## <a name="validate-installation"></a>Проверка установки

### <a name="dsc"></a>DSC

Командлеты [Test-DscConfiguration](https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/test-dscconfiguration) позволяют определить, соответствует ли текущее состояние сервера (в данном случае установка SQL) желаемому. Результатом выполнения Test-DscConfiguration должно быть значение True (Истина).

```PowerShell
PS C:\> Test-DscConfiguration
True
```

### <a name="services"></a>Службы

Список служб теперь должен возвращать службы SQL Server

```PowerShell
PS C:\> Get-Service -Name *SQL*
Status  Name           DisplayName
------  ----           -----------
Running MSSQLSERVER    SQL Server (MSSQLSERVER)
Stopped SQLBrowser     SQL Server Browser
Running SQLSERVERAGENT SQL Server Agent (MSSQLSERVER)
Running SQLTELEMETRY   SQL Server CEIP service (MSSQLSERVER)
Running SQLWriter      SQL Server VSS Writer
```

### <a name="sql-server"></a>SQL Server

```PowerShell
PS C:\> & sqlcmd -S $env:COMPUTERNAME
1> SELECT @@SERVERNAME
2> GO
1> quit
```

## <a name="see-also"></a>См. также раздел

[Обзор Windows PowerShell Desired State Configuration](https://docs.microsoft.com/powershell/dsc/overview)

[Установка SQL Server из командной строки](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)

[Установка SQL Server с помощью файла конфигурации](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md)
