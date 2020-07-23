---
title: Выполнение пакета служб SSIS из командной строки | Документы Майкрософт
ms.date: 05/21/2018
ms.topic: quickstart
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: chugugrace
ms.author: chugu
ms.openlocfilehash: abac052f7da501f298cc0166273ca624e2fc38f1
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86921872"
---
# <a name="run-an-ssis-package-from-the-command-prompt-with-dtexecexe"></a>Выполнение пакета служб SSIS из командной строки

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]


Это краткое руководство показывает, как запускать пакет служб SSIS из командной строки путем выполнения `DTExec.exe` с соответствующими параметрами.

> [!NOTE]
> Описываемый в этой статье метод не был проверен для пакетов, развернутых на сервере базы данных SQL Azure.

Дополнительные сведения о `DTExec.exe` см. в разделе [Служебная программа dtexec](https://docs.microsoft.com/sql/integration-services/packages/dtexec-utility).

## <a name="supported-platforms"></a>Поддерживаемые платформы

Сведения, приведенные в этом кратком руководстве, можно использовать для выполнения пакета SSIS на следующих платформах:

-   SQL Server в Windows.

Описываемый в этой статье метод не был проверен для пакетов, развернутых на сервере базы данных SQL Azure. Дополнительные сведения о развертывании и запуске пакетов в Azure см. в разделе [Перенос рабочих нагрузок SQL Server Integration Services в облако](lift-shift/ssis-azure-lift-shift-ssis-packages-overview.md).

Сведения, приведенные в этом кратком руководстве, не могут быть использованы для выполнения пакета SSIS в Linux. Дополнительные сведения о запуске пакетов на Linux см. в разделе [Извлечение, преобразование и загрузка данных в Linux с помощью служб SSIS](../linux/sql-server-linux-migrate-ssis.md).

## <a name="run-a-package-with-dtexec"></a>Выполнение пакета с помощью программы dtexec

Если папка, где находится `DTExec.exe`, не указана в переменной среды `path`, может потребоваться перейти в этот каталог с помощью команды `cd`. Для SQL Server 2017 этой папкой обычно является `C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn`.

При значениях параметров, используемых в следующем примере, программа выполняет пакет по указанному пути к папке на сервере SSIS, на котором размещается база данных каталога служб SSIS (SSISDB). Параметр `/Server` задает имя сервера. Программа подключается в качестве текущего пользователя с помощью встроенной проверки подлинности Windows. Чтобы использовать проверку подлинности SQL, укажите параметры `/User` и `Password` с соответствующими значениями.

1. Откройте окно командной строки и

2. Запустите `DTExec.exe` и укажите как минимум значения параметров `ISServer` и `Server`, как показано в следующем примере:

    ```cmd
    dtexec /ISServer "\SSISDB\Project1Folder\Integration Services Project1\Package.dtsx" /Server "localhost"
    ```

## <a name="next-steps"></a>Дальнейшие действия
- Рассмотрите другие варианты выполнения пакета.
    - [Выполнение пакета служб SSIS с помощью SSMS](./ssis-quickstart-run-ssms.md)
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (Visual Studio Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Выполнение пакета служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)
    - [Выполнение пакета служб SSIS с помощью C#](./ssis-quickstart-run-dotnet.md) 
