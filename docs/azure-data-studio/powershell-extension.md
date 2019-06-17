---
title: Расширение PowerShell
titleSuffix: Azure Data Studio
description: Установить и использовать PowerShell для Azure Data Studio
ms.custom: seodec18
ms.date: 04/19/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: SQLvariant
ms.author: aanelson
manager: matthend
ms.openlocfilehash: c7a2dbdccf92a52d5733a04915acc3f76dc3f033
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65105950"
---
# <a name="powershell-editor-support-for-azure-data-studio"></a>Поддержка редактора PowerShell для Azure Data Studio

Это расширение обеспечивает обширную поддержку редактора PowerShell в [Azure Data Studio](https://github.com/Microsoft/azuredatastudio).
Теперь можно писать и отлаживать сценарии PowerShell, с помощью отличную интегрированную среду разработки по принципу интерфейс, предоставляющий Studio данных Azure.

![Расширение PowerShell](media/powershell-extension/powershell-extension.png)


## <a name="features"></a>Компоненты

- Выделение синтаксиса
- Фрагменты кода
- IntelliSense для командлетов и многое другое
- Анализ на основе правил, предоставляемые средством [анализатор скриптов PowerShell](http://github.com/PowerShell/PSScriptAnalyzer)
- Перейти к определению командлетов и переменные
- Найти ссылки на командлеты и переменные
- Обнаружение символа документа и рабочей области
- Запуск выбранного выбранного с помощью кода PowerShell <kbd>F8</kbd>
- Запустить справку в Интернете для символа под курсора с помощью <kbd>Ctrl</kbd>+<kbd>F1</kbd>
- Поддержка основных интерактивной консоли!


## <a name="installing-the-extension"></a>Установка расширения

Официальный выпуск расширения PowerShell можно установить, выполнив действия, описанные в [документации по Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/extensions).
В области расширений поиска для «PowerShell» расширения и устанавливать этот.  Вы получите уведомление автоматически об обновлениях последующего расширения!

Вы также можете установить пакет VSIX из наших [страницы выпуски](https://github.com/PowerShell/vscode-powershell/releases) и установить его с помощью командной строки:

```powershell
azuredatastudio --install-extension PowerShell-<version>.vsix
```

## <a name="platform-support"></a>Поддержка платформ

- **Windows 7 по 10** с Windows PowerShell версии 3 и более поздних версий и PowerShell Core
- **Linux** с PowerShell Core (для всех дистрибутивов PowerShell поддерживается)
- **macOS** с PowerShell Core

Чтение [часто задаваемые вопросы о](https://github.com/PowerShell/vscode-powershell/wiki/FAQ) ответы на часто задаваемые вопросы.

## <a name="installing-powershell-core"></a>Установка PowerShell Core

Если вы используете Azure Data Studio в MacOS или Linux, также может потребоваться установить PowerShell Core.

PowerShell Core — это проект с открытым исходным кодом на [GitHub](https://github.com/powershell/powershell).
Дополнительные сведения об установке PowerShell Core на платформах MacOS или Linux см. в разделе со следующими статьями:

- [Установка PowerShell Core в Linux](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-6)
- [Установка PowerShell Core в macOS](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-6)

## <a name="example-scripts"></a>Примеры скриптов

Существуют некоторые примеры скриптов в расширении `examples` папку, можно использовать для обнаружения PowerShell редактирования и отладки функции.  Просмотрите включенные [README.md](https://github.com/PowerShell/vscode-powershell/blob/master/examples/README.md) файл, чтобы узнать больше о том, как их использовать.

Эту папку можно найти по следующему пути:

```powershell
$HOME/.azuredatastudio/extensions/ms-vscode.PowerShell-<version>/examples
```

или если вы используете предварительную версию расширения

 ```powershell
$HOME/.azuredatastudio/extensions/ms-vscode.powershell-preview-<version>/examples
```

Чтобы открыть и просмотреть примеры расширения студии данных Azure, выполните следующий код в командной строке PowerShell:

```powershell
azuredatastudio (Get-ChildItem $Home\.azuredatastudio\extensions\ms-vscode.PowerShell-*\examples)[-1]
```

### <a name="creating-and-opening-files"></a>Создание и открытие файлов

Чтобы создать и открыть новый файл в редакторе, используйте New-EditorFile из в окне интегрированного терминала PowerShell.

```powershell
PS C:\temp> New-EditorFile ExportData.ps1
```

Эта команда работает для файлов любого типа, не только файлы PowerShell.

```powershell
PS C:\temp> New-EditorFile ImportData.py
```

Чтобы открыть один или несколько файлов в Azure Data Studio, используйте `Open-EditorFile` команды.

```powershell
Open-EditorFile ExportData.ps1, ImportData.py
```

### <a name="no-focus-on-console-when-executing"></a>Нет сосредоточиться на консоль при выполнении

Для пользователей, которые используются для работы с SSMS вы привыкли возможность выполнить запрос и затем вы можете повторно выполните ее без переключения на панель запроса.  В этом случае поведение по умолчанию редактора кода может показаться странной вам.  Чтобы полностью сосредоточиться в редакторе, при выполнении с <kbd>F8</kbd> измените следующий параметр:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

По умолчанию используется `true` для специальных возможностей.

Имейте в виду, этот параметр будет предотвратить изменение в консоль, даже в том случае, если выбрать команду, которая явным образом, вызовы для входных данных, такие как фокус `Get-Credential`.

## <a name="sql-powershell-examples"></a>Примеры PowerShell для SQL
Чтобы использовать эти примеры (см. ниже), необходимо установить модуль SqlServer из [коллекции PowerShell](https://www.powershellgallery.com/packages/SqlServer).

```powershell
Install-Module -Name SqlServer
```

> [!NOTE]
> С помощью версии `21.1.18102` и выше, `SqlServer` модуль поддерживает [PowerShell Core](https://github.com/PowerShell/PowerShell) 6.2 и выше, в дополнение к Windows PowerShell.

В этом примере мы используем `Get-SqlInstance` для получения объектов SMO сервера ServerA и ServerB.  Имя выхода для этой команды будет содержать имя экземпляра по умолчанию версию пакета обновления & уровень CU обновления экземпляров.

```powershell
Get-SqlInstance -ServerInstance ServerA, ServerB
```

Ниже приведен пример того, что результат будет выглядеть так:

```
Instance Name             Version    ProductLevel UpdateLevel  HostPlatform HostDistribution
-------------             -------    ------------ -----------  ------------ ----------------
ServerA                   13.0.5233  SP2          CU4          Windows      Windows Server 2016 Datacenter
ServerB                   14.0.3045  RTM          CU12         Linux        Ubuntu
```
`SqlServer` Модуль содержит поставщика с именем `SQLRegistration` позволяет программно получить доступ к следующие типы сохраненные подключения SQL Server:

+ Сервер ядра базы данных (зарегистрированные серверы)
+ Центральный сервер управления (CMS)
+ Службы Analysis Services
+ Службы Integration Services
+ Службы Reporting Services

 В следующем примере мы будем использовать `dir` (псевдоним для `Get-ChildItem`) для получения списка всех экземпляров SQL Server, перечисленных в файле зарегистрированные серверы.

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse 
```

Ниже приведен пример того, что выходные данные могут выглядеть так:

```powershell
Mode Name
---- ----
-    ServerA
-    ServerB
-    localhost\SQL2017
-    localhost\SQL2016Happy
-    localhost\SQL2017
```

Для многих операций, которые включают в себя базу данных или объекты в базе данных `Get-SqlDatabase` можно использовать командлет.  Если необходимо указать значения для обоих `-ServerInstance` и `-Database` параметров, только этот объект одной базы данных будут извлекаться.  Тем не менее если указать только `-ServerInstance` параметр, возвращается полный список всех баз данных на этом экземпляре.

Ниже приведен пример того, что результат будет выглядеть так:

```
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

В следующем примере использует `Get-SqlDatabase` командлет, чтобы получить список всех баз данных на экземпляре ServerB затем представляет таблицы (с помощью `Out-GridView` командлет) чтобы выбрать, какие базы данных необходимо выполнить резервное.  Когда пользователь нажимает кнопку «ОК», будет скопирована только выделенный для баз данных.

```powershell
Get-SqlDatabase -ServerInstance ServerB |
Out-GridView -PassThru |
Backup-SqlDatabase -CompressionOption On
```

В этом примере, опять же, получение списка всех экземпляров SQL Server, присутствует в файле зарегистрированных серверов, затем вызывается `Get-SqlAgentJobHistory` какие отчеты каждый сбой задания агента SQL Server после полуночи, для каждого экземпляра SQL Server в списке.

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse |
WHERE {$_.Mode -ne 'd' } |
FOREACH {
    Get-SqlAgentJobHistory -ServerInstance  $_.Name -Since Midnight -OutcomesType Failed
}
```

В этом примере мы будем использовать `dir` (псевдоним для `Get-ChildItem`) для получения списка всех экземпляров SQL Server, перечисленных в файле зарегистрированные серверы, а затем используйте `Get-SqlDatabase` для получения списка баз данных для каждого из этих экземпляров.

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse |
WHERE { $_.Mode -ne 'd' } |
FOREACH {
    Get-SqlDatabase -ServerInstance $_.Name
}
```

Ниже приведен пример того, что результат будет выглядеть так:

```
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

## <a name="reporting-problems"></a>Сообщения о проблемах

При возникновении проблем с расширением PowerShell см. в разделе [документы по устранению неполадок](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md) сведения о диагностике и сообщить о проблеме.

#### <a name="security-note"></a>Примечание по безопасности.

По вопросам обеспечения безопасности, см. в разделе [здесь](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md#note-on-security).

## <a name="contributing-to-the-code"></a>Работает над кодом

Ознакомьтесь с [документации по разработке приложений](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md) Дополнительные сведения о том, как вносить изменения этого расширения!

## <a name="maintainers"></a>Издатели

- [Кит Хилл](https://github.com/rkeithhill) - [@r_keith_hill](http://twitter.com/r_keith_hill)
- [Тайлер Leonhardt](https://github.com/tylerl0706) - [@TylerLeonhardt](http://twitter.com/tylerleonhardt)
- [Роб Holt](https://github.com/rjmholt)

## <a name="license"></a>Лицензия

Это расширение [предоставлено по лицензии MIT](https://github.com/PowerShell/vscode-powershell/blob/master/LICENSE.txt). Дополнительные сведения о сторонних двоичных файлов, которые мы включаем с выпусками этого проекта, см. в разделе [третьих](https://github.com/PowerShell/vscode-powershell/blob/master/Third%20Party%20Notices.txt) файл.

## <a name="code-of-conductconduct-md"></a>[Правила поведения][conduct-md]

Этот проект распространяются [Microsoft Open источника поведения][conduct-code].
Дополнительные сведения см. в разделе [код из поведения часто задаваемые вопросы о] [ conduct-FAQ] или обратитесь в службу [ opencode@microsoft.com ] [ conduct-email] с вопросы или комментарии.

[conduct-code]: http://opensource.microsoft.com/codeofconduct/
[conduct-FAQ]: http://opensource.microsoft.com/codeofconduct/faq/
[conduct-email]: mailto:opencode@microsoft.com
[conduct-md]: https://github.com/PowerShell/vscode-powershell/blob/master/CODE_OF_CONDUCT.md
