---
title: "Выполните пакет служб SSIS из командной строки | Документы Microsoft"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 656e62f36446db4ef5b232129130a0253d2aebdf
ms.openlocfilehash: a33b8518ec3284f5de73d38c87209057dc1c7487
ms.contentlocale: ru-ru
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-from-the-command-prompt-with-dtexecexe"></a>Запустите из командной строки с DTExec.exe пакета служб SSIS
Этого краткого руководства показано, как выполнение пакета служб SSIS из командной строки, выполнив `DTExec.exe` с соответствующими параметрами.

> [!NOTE]
> Метод, описанный в этой статье не был проверен с пакетов развернуть на сервере базы данных SQL Azure.

Дополнительные сведения о `DTExec.exe`, в разделе [служебная программа dtexec](https://docs.microsoft.com/en-us/sql/integration-services/packages/dtexec-utility).

## <a name="run-a-package-with-dtexec"></a>Запуск пакета с помощью программы dtexec

Если папка, содержащая `DTExec.exe` не находится в вашей `path` переменной среды, может потребоваться использовать `cd` команду, чтобы изменить его каталог. Для SQL Server 2017 г, эта папка обычно является `C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn`.

С помощью значений параметров, используемых в следующем примере программа запускает пакет в указанный путь к папке на сервере служб SSIS — то есть сервер, на котором размещена база данных каталога служб SSIS (SSISDB). `/Server` Параметр предоставляет имя сервера. Программа подключается имени текущего пользователя с помощью встроенной проверки подлинности Windows. Чтобы использовать проверку подлинности SQL, укажите `/User` и `Password` параметры с соответствующими значениями.

1. Откройте окно командной строки.

2. Запустите `DTExec.exe` и укажите значения, по крайней мере для `ISServer` и `Server` параметров, как показано в следующем примере:

    ```cmd
    dtexec /ISServer "\SSISDB\Project1Folder\Integration Services Project1\Package.dtsx" /Server "localhost"
    ```

## <a name="next-steps"></a>Следующие шаги
- Рассмотрите другие возможности для выполнения пакета.
    - [Запустить пакет служб SSIS с помощью SSMS](./ssis-quickstart-run-ssms.md)
    - [Запустить пакет служб SSIS с помощью Transact-SQL (среда SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Запустить пакет служб SSIS с помощью Transact-SQL (VS Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Выполнить пакет служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)
    - [Запустить пакет служб SSIS с помощью C#](./ssis-quickstart-run-dotnet.md) 

