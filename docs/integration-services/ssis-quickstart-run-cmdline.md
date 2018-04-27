---
title: Выполнение пакета служб SSIS из командной строки | Документы Майкрософт
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: quick-start
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 50fcd7e38148c0cdb306fefddab86b6f13efd758
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="run-an-ssis-package-from-the-command-prompt-with-dtexecexe"></a>Выполнение пакета служб SSIS из командной строки
В этом кратком руководстве описывается выполнение пакета служб SSIS из командной строки путем запуска программы `DTExec.exe` с соответствующими параметрами.

> [!NOTE]
> Описываемый в этой статье метод не был проверен для пакетов, развернутых на сервере базы данных SQL Azure.

Дополнительные сведения о `DTExec.exe` см. в разделе [Служебная программа dtexec](https://docs.microsoft.com/sql/integration-services/packages/dtexec-utility).

## <a name="run-a-package-with-dtexec"></a>Выполнение пакета с помощью программы dtexec

Если папка, где находится `DTExec.exe`, не указана в переменной среды `path`, может потребоваться перейти в этот каталог с помощью команды `cd`. Для SQL Server 2017 этой папкой обычно является `C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn`.

При значениях параметров, используемых в следующем примере, программа выполняет пакет по указанному пути к папке на сервере SSIS, на котором размещается база данных каталога служб SSIS (SSISDB). Параметр `/Server` задает имя сервера. Программа подключается в качестве текущего пользователя с помощью встроенной проверки подлинности Windows. Чтобы использовать проверку подлинности SQL, укажите параметры `/User` и `Password` с соответствующими значениями.

1. Откройте окно командной строки.

2. Запустите `DTExec.exe` и укажите как минимум значения параметров `ISServer` и `Server`, как показано в следующем примере:

    ```cmd
    dtexec /ISServer "\SSISDB\Project1Folder\Integration Services Project1\Package.dtsx" /Server "localhost"
    ```

## <a name="next-steps"></a>Следующие шаги
- Рассмотрите другие варианты выполнения пакета.
    - [Выполнение пакета служб SSIS с помощью SSMS](./ssis-quickstart-run-ssms.md)
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (Visual Studio Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Выполнение пакета служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)
    - [Выполнение пакета служб SSIS с помощью C#](./ssis-quickstart-run-dotnet.md) 
