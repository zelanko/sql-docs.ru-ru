---
title: "Развертывание проекта служб SSIS из командной строки | Документы Microsoft"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: bc1321dd91a0fcb7ab76b207301c6302bb3a5e64
ms.openlocfilehash: 0f1c7733f0ce6b132c209961a1fd12da80cbd282
ms.contentlocale: ru-ru
ms.lasthandoff: 10/06/2017

---
# <a name="deploy-an-ssis-project-from-the-command-prompt-with-isdeploymentwizardexe"></a>Развертывание проекта служб SSIS из командной строки с ISDeploymentWizard.exe
Этого краткого руководства показано, как развернуть проект служб SSIS из командной строки, запустив мастер развертывания служб интеграции, `ISDeploymentWizard.exe`.

Дополнительные сведения о мастере развертывания служб интеграции см. в разделе [мастер развертывания служб Integration Services](packages/deploy-integration-services-ssis-projects-and-packages.md#integration-services-deployment-wizard).

## <a name="start-the-integration-services-deployment-wizard"></a>Запуск мастера развертывания служб Integration Services
1. Откройте окно командной строки.

2. Выполните `ISDeploymentWizard.exe`. Откроется мастер развертывания служб Integration Services.

    Если папка, содержащая `ISDeploymentWizard.exe` не находится в вашей `path` переменной среды, может потребоваться использовать `cd` команду, чтобы изменить его каталог. Для SQL Server 2017 г, эта папка обычно является `C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn`.

## <a name="deploy-a-project-with-the-wizard"></a>Развертывание проекта с помощью мастера
1. На **Введение** страницы мастера, ознакомьтесь с общими сведениями. Нажмите кнопку **Далее** Открытие **Выбор источника** страницы.

2. На **Выбор источника** выберите существующий проект служб SSIS для развертывания.
    -   Чтобы развернуть созданный файл развертывания проекта, выберите **Файл развертывания проекта** и введите путь к ISPAC-файлу.
    -   Для развертывания проекта, который находится в каталоге служб SSIS, выберите **каталог служб Integration Services**, а затем введите имя сервера и путь к проекту в каталоге.
    Нажмите кнопку **Далее** , чтобы просмотреть страницу **Выбор назначения** .
  
3.  На **Выбор назначения** выберите место назначения для проекта.
    -   Введите полное имя сервера. Если целевой сервер является сервером базы данных SQL Azure, то имя будет в следующем формате: `<server_name>.database.windows.net`.
    -   Нажмите кнопку **Обзор** для выбора целевой папки в SSISDB.
    Нажмите кнопку **Далее** Открытие **проверки** страницы.  
  
4.  На **просмотрите** просмотрите выбранные параметры.
    -   Вы можете изменить выбранные параметры, нажав кнопку **Назад**или кнопку любого из шагов на левой панели.
    -   Щелкните **Развернуть** , чтобы начать развертывание.
  
5.  После завершения процесса развертывания **результатов** откроется страница. На ней отображается состояние выполнения каждого действия.
    -   Если не удалось выполнить действие, нажмите кнопку **сбой** в **результат** столбец для отображения описания ошибки.
    -   При необходимости щелкните **сохранить отчет...**  для сохранения результатов в XML-файл.
    -   Нажмите кнопку **закрыть** для завершения работы мастера.

## <a name="next-steps"></a>Следующие шаги
- Рассмотрите другие возможности для развертывания пакета.
    - [Развертывание пакета служб SSIS с помощью SSMS](./ssis-quickstart-deploy-ssms.md)
    - [Развертывание пакета служб SSIS с помощью Transact-SQL (среда SSMS)](./ssis-quickstart-deploy-tsql-ssms.md)
    - [Развертывание пакета служб SSIS с помощью Transact-SQL (VS Code)](ssis-quickstart-deploy-tsql-vscode.md)
    - [Развертывание пакета служб SSIS с помощью PowerShell](ssis-quickstart-deploy-powershell.md)
    - [Развертывание пакета служб SSIS с помощью C#](./ssis-quickstart-deploy-dotnet.md) 
- Выполнения развернутого пакета. Чтобы запустить пакет, можно выбрать несколько средств и языков. Дополнительные сведения см. в следующих статьях:
    - [Запустить пакет служб SSIS с помощью SSMS](./ssis-quickstart-run-ssms.md)
    - [Запустить пакет служб SSIS с помощью Transact-SQL (среда SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Запустить пакет служб SSIS с помощью Transact-SQL (VS Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Выполните пакет служб SSIS из командной строки](./ssis-quickstart-run-cmdline.md)
    - [Выполнить пакет служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)
    - [Запустить пакет служб SSIS с помощью C#](./ssis-quickstart-run-dotnet.md) 

