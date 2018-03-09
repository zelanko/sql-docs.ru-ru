---
title: "Развертывание проекта служб SSIS из командной строки | Документы Майкрософт"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: non-specific
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a753aa1418e935604148d0d42afa22716dec1b17
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="deploy-an-ssis-project-from-the-command-prompt-with-isdeploymentwizardexe"></a>Развертывание проекта служб SSIS из командной строки с помощью ISDeploymentWizard.exe
В этом кратком руководстве описывается развертывание проекта служб SSIS из командной строки с помощью мастера развертывания служб Integration Services Deployment, `ISDeploymentWizard.exe`.

Дополнительные сведения о мастере развертывания служб Integration Services см. в [этом разделе](packages/deploy-integration-services-ssis-projects-and-packages.md#integration-services-deployment-wizard).

## <a name="start-the-integration-services-deployment-wizard"></a>Запуск мастера развертывания Integration Services
1. Откройте окно командной строки.

2. Выполните `ISDeploymentWizard.exe`. Откроется мастер развертывания служб Integration Services.

    Если папка, где находится `ISDeploymentWizard.exe`, не указана в переменной среды `path`, может потребоваться перейти в этот каталог с помощью команды `cd`. Для SQL Server 2017 этой папкой обычно является `C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn`.

## <a name="deploy-a-project-with-the-wizard"></a>Развертывание проекта с помощью мастера
1. Ознакомьтесь с информацией, представленной на странице **Введение** мастера. Нажмите кнопку **Далее**, чтобы перейти на страницу **Выбор источника**.

2. На странице **Выбор источника** выберите существующий проект служб SSIS для развертывания.
    -   Чтобы развернуть созданный файл развертывания проекта, выберите **Файл развертывания проекта** и введите путь к ISPAC-файлу.
    -   Для развертывания проекта, который находится в каталоге служб SSIS, выберите **Каталог служб Integration Services**, а затем введите имя сервера и путь к проекту в каталоге.
    Нажмите кнопку **Далее** , чтобы просмотреть страницу **Выбор назначения** .
  
3.  На странице **Выбор назначения** выберите назначение для проекта.
    -   Введите полное имя сервера. Если в качестве целевого выступает сервер базы данных SQL Azure, используйте следующий формат имени: `<server_name>.database.windows.net`.
    -   Нажмите кнопку **Обзор** для выбора целевой папки в SSISDB.
    Нажмите кнопку **Далее**, чтобы перейти на страницу **Проверка**.  
  
4.  Просмотрите выбранные параметры на странице **Проверка**.
    -   Вы можете изменить выбранные параметры, нажав кнопку **Назад**или кнопку любого из шагов на левой панели.
    -   Щелкните **Развернуть** , чтобы начать развертывание.
  
5.  После завершения развертывания появится страница **Результаты**. На ней отображается состояние выполнения каждого действия.
    -   Если действие не выполнено, нажмите кнопку **Ошибка** в столбце **Результат** для отображения описания ошибки.
    -   Чтобы сохранить результаты в XML-файл при необходимости, нажмите кнопку **Сохранить отчет...**.
    -   Нажмите кнопку **Закрыть**, чтобы выйти из мастера.

## <a name="next-steps"></a>Следующие шаги
- Рассмотрите другие варианты развертывания пакета.
    - [Развертывание пакета служб SSIS с помощью SSMS](./ssis-quickstart-deploy-ssms.md)
    - [Развертывание пакета служб SSIS с помощью Transact-SQL (SSMS)](./ssis-quickstart-deploy-tsql-ssms.md)
    - [Развертывание пакета служб SSIS с помощью Transact-SQL (Visual Studio Code)](ssis-quickstart-deploy-tsql-vscode.md)
    - [Развертывание пакета служб SSIS с помощью PowerShell](ssis-quickstart-deploy-powershell.md)
    - [Развертывание пакета служб SSIS с помощью C#](./ssis-quickstart-deploy-dotnet.md) 
- Выполните развернутый пакет. Для выполнения пакета можно использовать различные средства и языки. Дополнительные сведения см. в следующих статьях:
    - [Выполнение пакета служб SSIS с помощью SSMS](./ssis-quickstart-run-ssms.md)
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (Visual Studio Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Выполнение пакета служб SSIS из командной строки](./ssis-quickstart-run-cmdline.md)
    - [Выполнение пакета служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)
    - [Выполнение пакета служб SSIS с помощью C#](./ssis-quickstart-run-dotnet.md) 
