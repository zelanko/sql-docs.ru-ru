---
title: Расширение PowerShell
description: Узнайте, как установить и использовать расширение PowerShell для Azure Data Studio, которое предоставляет широкие возможности поддержки редактора PowerShell для написания и отладки скриптов.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: SQLvariant
ms.author: aanelson
ms.reviewer: alayu, maghan, sstein
ms.custom: ''
ms.date: 04/19/2019
ms.openlocfilehash: ede862fe5bbfe975e7c8694782960ced974122b6
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725139"
---
# <a name="powershell-editor-support-for-azure-data-studio"></a>Поддержка редактора PowerShell для Azure Data Studio

Это расширение обеспечивает полноценную поддержку редактора PowerShell в [Azure Data Studio](https://github.com/Microsoft/azuredatastudio).
С его помощью вы получаете возможность создания и отладки скриптов PowerShell в интерфейсе Azure Data Studio, схожем с интегрированной средой разработки.

![Расширение PowerShell](media/powershell-extension/powershell-extension.png)

## <a name="features"></a>Компоненты

- Выделение синтаксиса
- Фрагменты кода
- Технология IntelliSense для командлетов и многое другое
- Анализ на основе правил с использованием [анализатора скриптов PowerShell](http://github.com/PowerShell/PSScriptAnalyzer)
- Переход к определению командлетов и переменных
- Поиск ссылок на командлеты и переменные
- Обнаружение символов в документе и рабочей области
- Запуск выбранного фрагмента кода PowerShell с помощью клавиши <kbd>F8</kbd>
- Запуск интерактивной справки для символа под курсором с помощью сочетания клавиш <kbd>CTRL</kbd>+<kbd>F1</kbd>
- Базовая поддержка интерактивной консоли

## <a name="installing-the-extension"></a>Установка расширения

Чтобы установить официальный выпуск расширения PowerShell, выполните действия, указанные в [документации по Azure Data Studio](./add-extensions.md).
В области "Расширения" найдите расширение PowerShell и установите его.  Уведомления о последующих обновлениях этого расширения будут приходить автоматически.

Также вы можете установить пакет VSIX со страницы [Выпуски](https://github.com/PowerShell/vscode-powershell/releases) и с помощью командной строки:

```powershell
azuredatastudio --install-extension PowerShell-<version>.vsix
```

## <a name="platform-support"></a>Поддержка платформы

- **ОС с Windows 7 по Windows 10** с Windows PowerShell версии 3 или более поздней и PowerShell Core
- **Linux** с PowerShell Core (все поддерживаемые PowerShell дистрибутивы)
- **macOS** с PowerShell Core

Ответы на часто задаваемые вопросы см. в [этой статье](https://github.com/PowerShell/vscode-powershell/wiki/FAQ).

## <a name="installing-powershell-core"></a>Установка PowerShell Core

Если вы работаете с Azure Data Studio в MacOS или Linux, также может потребоваться установка PowerShell Core.

PowerShell Core — это проект с открытым исходным кодом на сайте [GitHub](https://github.com/powershell/powershell).
Дополнительные сведения об установке PowerShell Core на платформах MacOS или Linux см. в следующих статьях:

- [Установка PowerShell Core в Linux](/powershell/scripting/install/installing-powershell-core-on-linux)
- [Установка PowerShell Core в macOS](/powershell/scripting/install/installing-powershell-core-on-macos)

## <a name="example-scripts"></a>Примеры скриптов

Далее приводится несколько примеров скриптов в папке расширения `examples`, которые можно использовать для знакомства с возможностями редактирования и отладки PowerShell.  Дополнительные сведения об их использовании см. в файле [README.md](https://github.com/PowerShell/vscode-powershell/blob/master/examples/README.md).

Путь к этой папке:

```powershell
$HOME/.azuredatastudio/extensions/ms-vscode.PowerShell-<version>/examples
```

или для предварительной версии расширения

 ```powershell
$HOME/.azuredatastudio/extensions/ms-vscode.powershell-preview-<version>/examples
```

Чтобы открыть и просмотреть примеры расширения в Azure Data Studio, выполните следующий код из командной строки PowerShell:

```powershell
azuredatastudio (Get-ChildItem $Home\.azuredatastudio\extensions\ms-vscode.PowerShell-*\examples)[-1]
```

### <a name="creating-and-opening-files"></a>Создание и открытие файлов

Чтобы создать и открыть новый файл в редакторе, выполните команду New-EditorFile из встроенного терминала PowerShell.

```powershell
PS C:\temp> New-EditorFile ExportData.ps1
```

Эта команда работает для файлов любого типа, а не только для файлов PowerShell.

```powershell
PS C:\temp> New-EditorFile ImportData.py
```

Чтобы открыть один или несколько файлов в Azure Data Studio, воспользуйтесь командой `Open-EditorFile`.

```powershell
Open-EditorFile ExportData.ps1, ImportData.py
```

### <a name="no-focus-on-console-when-executing"></a>Отсутствие фокуса в консоли во время выполнения

Если вы работали с SSMS, то наверняка привыкли к возможности выполнить запрос и затем повторить его выполнение, не переключаясь обратно в панель запросов.  В таком случае реализованное по умолчанию поведение редактора кода может показаться вам непривычным.  Чтобы сохранять фокус в редакторе при выполнении с помощью клавиши <kbd>F8</kbd>, измените следующую настройку:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

Значение по умолчанию `true` устанавливается в соответствии с требованиями к поддержке специальных возможностей.

Обратите внимание, что при установке этой настройки фокус не будет переноситься в консоль, даже если вы используете команду, явно требующую ввода данных, например `Get-Credential`.

## <a name="sql-powershell-examples"></a>Примеры SQL для PowerShell

Чтобы использовать приведенные ниже примеры, установите модуль SqlServer из [коллекции PowerShell](https://www.powershellgallery.com/packages/SqlServer).

```powershell
Install-Module -Name SqlServer
```

> [!NOTE]
> В версии `21.1.18102` и более поздних модуль `SqlServer` помимо Windows PowerShell поддерживает [PowerShell Core](https://github.com/PowerShell/PowerShell) 6.2 и более поздних версий.

В этом примере используется командлет `Get-SqlInstance` для получения управляющих объектов SQL Server для экземпляров ServerA и ServerB.  По умолчанию в выходных данных этой команды будут содержаться имя экземпляра, версия, а также уровень пакета обновления и накопительного обновления для экземпляров.

```powershell
Get-SqlInstance -ServerInstance ServerA, ServerB
```

Ниже приводится пример соответствующих выходных данных:

```console
Instance Name             Version    ProductLevel UpdateLevel  HostPlatform HostDistribution
-------------             -------    ------------ -----------  ------------ ----------------
ServerA                   13.0.5233  SP2          CU4          Windows      Windows Server 2016 Datacenter
ServerB                   14.0.3045  RTM          CU12         Linux        Ubuntu
```

Модуль `SqlServer` содержит поставщик `SQLRegistration`, который обеспечивает программный доступ к следующим типам сохраненных подключений SQL Server:

+ Сервер ядра СУБД (зарегистрированные серверы)
+ Центральный сервер управления (CMS)
+ Службы Analysis Services
+ Службы Integration Services
+ Службы Reporting Services

 В следующем примере выполняется команда `dir` (псевдоним `Get-ChildItem`) для получения списка всех экземпляров SQL Server, которые перечислены в файле зарегистрированных серверов.

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse
```

Ниже приводится пример выходных данных:

```powershell
Mode Name
---- ----
-    ServerA
-    ServerB
-    localhost\SQL2017
-    localhost\SQL2016Happy
-    localhost\SQL2017
```

Для многих операций с базами данных или содержащимися в них объектами можно использовать командлет `Get-SqlDatabase`.  Если заданы значения параметров `-ServerInstance` и `-Database`, будут извлечены только эти объекты базы данных.  Тем не менее, если вы зададите только параметр `-ServerInstance`, будет возвращен полный список баз данных в этом экземпляре.

Ниже приводится пример соответствующих выходных данных:

```console
Name                 Status           Size     Space  Recovery Compat. Owner
                                            Available  Model     Level
----                 ------           ---- ---------- -------- ------- -----
AdventureWorks2017   Normal      336.00 MB   57.01 MB Simple       140 sa
master               Normal        6.00 MB  368.00 KB Simple       140 sa
model                Normal       16.00 MB    5.53 MB Full         140 sa
msdb                 Normal       48.44 MB    1.70 MB Simple       140 sa
PBIRS                Normal      144.00 MB   55.95 MB Full         140 sa
PBIRSTempDB          Normal       16.00 MB    4.20 MB Simple       140 sa
SSISDB               Normal      325.06 MB   26.21 MB Full         140 sa
tempdb               Normal       72.00 MB   61.25 MB Simple       140 sa
WideWorldImporters   Normal         3.2 GB     2.6 GB Simple       130 sa
```

В следующем примере используется командлет `Get-SqlDatabase` для извлечения списка всех баз данных на экземпляре ServerB. После этого с помощью командлета `Out-GridView` выводится таблица для выбора баз данных, для которых требуется выполнить резервное копирование.  После нажатия кнопки "ОК" будет выполнено резервное копирование только для выделенных баз данных.

```powershell
Get-SqlDatabase -ServerInstance ServerB |
Out-GridView -PassThru |
Backup-SqlDatabase -CompressionOption On
```

В этом примере снова возвращается список всех экземпляров SQL Server, перечисленных в файле зарегистрированных серверов, после чего вызывается командлет `Get-SqlAgentJobHistory`, который выводит список всех завершившихся сбоем заданий агента SQL (начиная с полуночи) для каждого представленного в списке экземпляра SQL Server.

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse |
WHERE {$_.Mode -ne 'd' } |
FOREACH {
    Get-SqlAgentJobHistory -ServerInstance  $_.Name -Since Midnight -OutcomesType Failed
}
```

В этом примере выполняется команда `dir` (псевдоним `Get-ChildItem`) для получения списка всех экземпляров SQL Server, перечисленных в файле зарегистрированных серверов. Затем выполняется командлет `Get-SqlDatabase` для получения списка баз данных для каждого из этих экземпляров.

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse |
WHERE { $_.Mode -ne 'd' } |
FOREACH {
    Get-SqlDatabase -ServerInstance $_.Name
}
```

Ниже приводится пример соответствующих выходных данных:

```console
Name                 Status           Size  Space     Recovery Compat. Owner
                                            Available Model    Level
----                 ------           ---- ---------- -------- ------- -----
AdventureWorks2017   Normal      336.00 MB   57.01 MB Simple       140 sa
master               Normal        6.00 MB  368.00 KB Simple       140 sa
model                Normal       16.00 MB    5.53 MB Full         140 sa
msdb                 Normal       48.44 MB    1.70 MB Simple       140 sa
PBIRS                Normal      144.00 MB   55.95 MB Full         140 sa
PBIRSTempDB          Normal       16.00 MB    4.20 MB Simple       140 sa
SSISDB               Normal      325.06 MB   26.21 MB Full         140 sa
tempdb               Normal       72.00 MB   61.25 MB Simple       140 sa
WideWorldImporters   Normal         3.2 GB     2.6 GB Simple       130 sa
```

## <a name="reporting-problems"></a>Отчеты о проблемах

Если вы столкнулись с проблемами при работе расширения PowerShell, ознакомьтесь со сведениями о диагностике ошибок и отправке сообщений о них в [документации по устранению неполадок](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md).

### <a name="security-note"></a>Примечание по безопасности.

Сведения о проблемах, связанных с безопасностью, см. в [этой статье](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md#note-on-security).

## <a name="contributing-to-the-code"></a>Участие в улучшении кода

Если вы хотите принять участие в улучшении этого расширения, ознакомьтесь с [документацией для разработчиков](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md).

## <a name="maintainers"></a>Издатели

- [Кит Хилл (Keith Hill)](https://github.com/rkeithhill) - [@r_keith_hill](http://twitter.com/r_keith_hill)
- Тайлер Леонхардт (Tyler Leonhardt) — [@TylerLeonhardt](http://twitter.com/tylerleonhardt)
- [Роб Холт (Rob Holt)](https://github.com/rjmholt)

## <a name="license"></a>Лицензия

Это расширение [лицензируется на условиях лицензии MIT](https://github.com/PowerShell/vscode-powershell/blob/master/LICENSE.txt). Дополнительные сведения о двоичных файлах сторонних производителей, включаемых в выпуски этого проекта, см. в файле [заметок стороннего производителя](https://github.com/PowerShell/vscode-powershell/blob/master/Third%20Party%20Notices.txt).

## <a name="code-of-conduct"></a>Правила поведения

В рамках этого проекта действуют [правила поведения в отношении продуктов с открытым исходным кодом Майкрософт][conduct-code].
Дополнительные сведения см. в статье [Вопросы и ответы, связанные с правилами поведения][conduct-FAQ]. Чтобы задать вопрос или получить комментарии, обратитесь по адресу [opencode@microsoft.com][conduct-email].

[conduct-code]: https://opensource.microsoft.com/codeofconduct/
[conduct-FAQ]: https://opensource.microsoft.com/codeofconduct/faq/
[conduct-email]: mailto:opencode@microsoft.com