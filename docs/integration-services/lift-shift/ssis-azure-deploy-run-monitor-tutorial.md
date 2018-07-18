---
title: Развертывание и запуск пакета служб SSIS в Azure | Документы Майкрософт
description: Узнайте, как развернуть проект служб SQL Server Integration Services (SSIS) в каталоге SSIS в базе данных SQL Azure и выполнить пакет.
ms.date: 5/22/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.suite: sql
ms.custom: ''
ms.technology: integration-services
author: swinarko
ms.author: sawinark
ms.reviewer: douglasl
manager: craigg
ms.openlocfilehash: 3bd32f6f60342a0224ebf353de6cda15696d8900
ms.sourcegitcommit: 70882926439a63ab9d812809429c63040eb9a41b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36262498"
---
# <a name="tutorial-deploy-and-run-a-sql-server-integration-services-ssis-package-in-azure"></a>Учебник. Развертывание и выполнение пакета служб SQL Server Integration Services (SSIS) в Azure
В этом учебнике рассказывается, как развернуть проект служб SQL Server Integration Services (SSIS) в каталоге SSISDB, расположенном в базе данных SQL Azure, запустить пакет в среде Azure-SSIS Integration Runtime и отслеживать его выполнение.

## <a name="prerequisites"></a>предварительные требования

Прежде чем начать, убедитесь в наличии SQL Server Management Studio версии 17.2 или более поздней. Чтобы скачать последнюю версию SSMS, перейдите на страницу [скачивания SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

Вы также должны настроить базу данных SSISDB в Azure и подготовить среду Azure-SSIS Integration Runtime. Дополнительные сведения о подготовке служб SSIS в Azure: [Развертывание пакетов SQL Server Integration Services в Azure](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure).

## <a name="for-azure-sql-database-get-the-connection-info"></a>Получение сведений о подключении для базы данных SQL Azure

Для запуска пакета в базе данных SQL Azure вам нужны сведения, необходимые для подключения к базе данных каталога служб SSIS (SSISDB). В описанных ниже процедурах вам потребуется полное имя сервера и имя для входа.

1. Войдите на [портал Azure](https://portal.azure.com/).
2. Выберите **Базы данных SQL** в меню слева, а затем на странице **Базы данных SQL** — базу данных SSISDB. 
3. На странице **Обзор** для базы данных просмотрите полное имя сервера. Чтобы увидеть параметр **Щелкните, чтобы скопировать**, наведите указатель мыши на имя сервера. 
4. Если вы забыли учетные данные входа на сервер базы данных SQL Azure, перейдите на страницу этого сервера, чтобы узнать имя его администратора. При необходимости вы можете сбросить пароль.

## <a name="connect-to-the-ssisdb-database"></a>Подключение к базе данных SSISDB

С помощью SQL Server Management Studio подключитесь к каталогу служб SSIS на сервере базы данных SQL Azure. Дополнительные сведения и снимки экрана см. в статье [Подключение к базе данных каталога SSISDB в Azure](ssis-azure-connect-to-catalog-database.md).

Ниже описаны два важных момента, о которых нужно помнить. Эти шаги описаны в следующей процедуре:
-   Введите полное доменное имя сервера базы данных SQL Azure в формате **mysqldbserver.database.windows.net**.
-   Выберите `SSISDB` в качестве базы данных для подключения.

> [!IMPORTANT]
> Сервер базы данных SQL Azure прослушивает порт 1433. Если вы пытаетесь подключиться к серверу базы данных SQL Azure изнутри корпоративного брандмауэра, для успешного подключения в этом брандмауэре должен быть открыт данный порт.

1. Откройте среду SQL Server Management Studio.

2. **Подключение к серверу**. В диалоговом окне **Соединение с сервером** введите следующие данные:

   | Настройка       | Предлагаемое значение | Описание | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Тип сервера** | Компонент Database Engine | Это значение обязательно. |
   | **Имя сервера** | Полное имя сервера | Имя должно быть в следующем формате: **mysqldbserver.database.windows.net**. Если вам нужно узнать имя сервера, см. раздел [Подключение к базе данных каталога SSISDB в Azure](ssis-azure-connect-to-catalog-database.md). |
   | **Проверка подлинности** | Проверка подлинности SQL Server | Вы не можете подключаться к базе данных SQL Azure с помощью проверки подлинности Windows. |
   | **Имя входа** | Учетная запись администратора сервера | Учетная запись, которая была указана при создании сервера. |
   | **Пароль** | Пароль для учетной записи администратора сервера | Пароль, который был указан при создании сервера. |

3. **Подключитесь к базе данных SSISDB**. Чтобы развернуть диалоговое окно **Соединение с сервером**, выберите **Параметры**. В развернутом окне **Соединение с сервером** откройте вкладку **Свойства подключения**. В поле **Подключение к базе данных** выберите или введите `SSISDB`.

4. В этом случае выберите **Подключиться**. В SSMS открывается окно обозревателя объектов. 

5. В обозревателе объектов разверните узел **Каталоги служб Integration Services** и затем узел **SSISDB** для просмотра объектов в базе данных каталога служб SSIS.

## <a name="deploy-a-project-with-the-deployment-wizard"></a>Развертывание проекта с помощью мастера развертываний

Дополнительные сведения о развертывании пакетов и о мастере развертывания см. в разделе [Развертывание проектов и пакетов служб Integration Services (SSIS)](../packages/deploy-integration-services-ssis-projects-and-packages.md) и [Мастер развертывания служб Integration Services](../packages/deploy-integration-services-ssis-projects-and-packages.md#integration-services-deployment-wizard).

> [!NOTE]
> Развертывание в Azure поддерживает только модели развертывания проекта.

### <a name="start-the-integration-services-deployment-wizard"></a>Запуск мастера развертывания Integration Services
1. В обозревателе объектов SSMS разверните узлы **Каталоги служб Integration Services** и **SSISDB**, а затем папку проекта.

2.  Выберите узел **Проекты**.

3.  Щелкните правой кнопкой мыши узел **Проекты** и выберите **Развернуть проект**. Откроется мастер развертывания служб Integration Services. Вы можете развернуть проект из базы данных каталога SSIS или из файловой системы.

    ![Развертывание проекта из SSMS](media/ssis-azure-deploy-run-monitor-tutorial/ssisdb-deploy-project1.png)

    ![Открытое диалоговое окно мастера развертывания служб SSIS](media/ssis-azure-deploy-run-monitor-tutorial/ssisdb-deploy-project2.png)

### <a name="deploy-a-project-with-the-deployment-wizard"></a>Развертывание проекта с помощью мастера развертываний
1. Ознакомьтесь с информацией, представленной на странице **Введение** мастера развертывания. Нажмите кнопку **Далее**, чтобы перейти на страницу **Выбор источника**.

2. На странице **Выбор источника** выберите существующий проект служб SSIS для развертывания.
    -   Чтобы развернуть созданный файл развертывания проекта, выберите **Файл развертывания проекта** и введите путь к ISPAC-файлу.
    -   Для развертывания проекта, который находится в каталоге служб SSIS, выберите **Каталог служб Integration Services**, а затем введите имя сервера и путь к проекту в каталоге.
    -   Нажмите кнопку **Далее**, чтобы просмотреть страницу **Выбор назначения**.
  
3.  На странице **Выбор назначения** выберите назначение для проекта.
    -   Введите полное имя сервера в формате `<server_name>.database.windows.net`.
    -   Предоставьте сведения о проверке подлинности и выберите **Подключиться**.
    -   Нажмите кнопку **Обзор** для выбора целевой папки в SSISDB.
    -   Затем нажмите кнопку **Далее**, чтобы перейти на страницу **Проверка**. (Кнопка **Далее** станет доступна, только когда вы выберете **Подключиться**.)
  
4.  Просмотрите выбранные параметры на странице **Проверка**.
    -   Вы можете изменить выбранные параметры, нажав кнопку **Назад** или кнопку любого из шагов на левой панели.
    -   Щелкните **Развернуть**, чтобы начать развертывание.

    > [!NOTE]
    > Если появляется сообщение об ошибке **Нет активного агента рабочей роли (поставщик данных .Net SqlClient)**, убедитесь, что запущена среда выполнения интеграции Azure и служб SSIS. Эта ошибка возникает при попытке выполнить развертывание, когда среда выполнения интеграции Azure и служб SSIS остановлена.

5.  После завершения развертывания появится страница **Результаты**. На ней отображается состояние выполнения каждого действия.
    -   Если действие не выполнено, нажмите кнопку **Ошибка** в столбце **Результат** для отображения описания ошибки.
    -   Чтобы сохранить результаты в XML-файл при необходимости, нажмите кнопку **Сохранить отчет...**.
    -   Нажмите кнопку **Закрыть**, чтобы выйти из мастера.

## <a name="deploy-a-project-with-powershell"></a>Развертывание проекта с помощью PowerShell

Чтобы развернуть проект с помощью PowerShell в базе данных SSISDB, размещенной в базе данных SQL Azure, приспособьте следующий скрипт под свои требования. Скрипт перечисляет дочерние папки в `$ProjectFilePath` и проекты в каждой дочерней папке, а затем создает те же папки в базе данных SSISDB и развертывает в них проекты.

На компьютере, где будет выполняться этот скрипт, должны быть установлены SQL Server Data Tools 17.x или среда SQL Server Management Studio.

```powershell
# Variables
$ProjectFilePath = "C:\<folder>"
$SSISDBServerEndpoint = "<servername>.database.windows.net"
$SSISDBServerAdminUserName = "<username>"
$SSISDBServerAdminPassword = "<password>"

# Load the IntegrationServices Assembly
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Management.IntegrationServices") | Out-Null;

# Store the IntegrationServices Assembly namespace to avoid typing it every time
$ISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"

Write-Host "Connecting to server ..."

# Create a connection to the server
$sqlConnectionString = "Data Source=" + $SSISDBServerEndpoint + ";User ID="+ $SSISDBServerAdminUserName +";Password="+ $SSISDBServerAdminPassword + ";Initial Catalog=SSISDB"
$sqlConnection = New-Object System.Data.SqlClient.SqlConnection $sqlConnectionString

# Create the Integration Services object
$integrationServices = New-Object $ISNamespace".IntegrationServices" $sqlConnection

# Get the catalog
$catalog = $integrationServices.Catalogs['SSISDB']

write-host "Enumerating all folders..."

$folders = ls -Path $ProjectFilePath -Directory

if ($folders.Count -gt 0)
{
    foreach ($filefolder in $folders)
    {
        Write-Host "Creating Folder " $filefolder.Name " ..."

        # Create a new folder
        $folder = New-Object $ISNamespace".CatalogFolder" ($catalog, $filefolder.Name, "Folder description")
        $folder.Create()

        $projects = ls -Path $filefolder.FullName -File -Filter *.ispac
        if ($projects.Count -gt 0)
        {
            foreach($projectfile in $projects)
            {
                $projectfilename = $projectfile.Name.Replace(".ispac", "")
                Write-Host "Deploying " $projectfilename " project ..."

                # Read the project file, and deploy it to the folder
                [byte[]] $projectFileContent = [System.IO.File]::ReadAllBytes($projectfile.FullName)
                $folder.DeployProject($projectfilename, $projectFileContent)
            }
        }
    }
}

Write-Host "All done." 
```

## <a name="run-a-package"></a>Запуск пакета

1. Выберите пакет, который хотите запустить, в обозревателе объектов SSMS.

2. Щелкните правой кнопкой мыши и выберите **Выполнить**, чтобы открыть диалоговое окно **Выполнение пакета**.

3.  В диалоговом окне **Выполнение пакета** настройте выполнение пакета с помощью параметров на вкладках **Параметры**, **Диспетчеры соединений** и **Расширенные**.

4.  Нажмите кнопку **ОК**, чтобы выполнить пакет.

## <a name="monitor-the-running-package-in-ssms"></a>Отслеживание выполнения пакета в SSMS

Чтобы просмотреть состояние запущенных операций служб Integration Services на сервере Integration Services, таких как развертывание, проверка и выполнение пакетов, используйте диалоговое окно **Активные операции** в SSMS. Чтобы открыть диалоговое окно **Активные операции**, щелкните базу данных **SSISDB** правой кнопкой мыши и выберите пункт **Активные операции**.

Вы также можете выбрать пакет в обозревателе объектов, щелкнуть его правой кнопкой мыши, выбрать пункт **Отчеты**, а затем **Стандартные отчеты** и **Все выполнения**.

Дополнительные сведения о том, как отслеживать выполнение запущенных пакетов в SSMS, см. в разделе [Наблюдение за выполнением пакетов и других операций](https://docs.microsoft.com/sql/integration-services/performance/monitor-running-packages-and-other-operations).

## <a name="monitor-the-execute-ssis-package-activity"></a>Отслеживание действия "Выполнение пакета служб SSIS"

Если пакет запускается как часть конвейера фабрики данных Azure с помощью действия "Выполнение пакета служб SSIS", можно отслеживать выполнение конвейера в пользовательском интерфейсе фабрики данных. Затем в выходных данных выполнения действия вы можете получить идентификатор выполнения SSISDB и использовать его для проверки более подробных журналов выполнения и сообщений об ошибках в среде SSMS.

![Получение идентификатора выполнения пакета в фабрике данных](media/ssis-azure-deploy-run-monitor-tutorial/get-execution-id.png)

## <a name="monitor-the-azure-ssis-integration-runtime"></a>Мониторинг среды Integration Runtime для Azure-SSIS

Чтобы получить сведения о состоянии среды Azure-SSIS Integration Runtime, где запускаются пакеты, используйте следующие команды PowerShell. Для каждой команды предоставьте имена фабрики данных, среды Azure-SSIS Integration Runtime и группы ресурсов.

См. дополнительные сведения о [Мониторинге среды выполнения интеграции Azure-SSIS](https://docs.microsoft.com/azure/data-factory/monitor-integration-runtime#azure-ssis-integration-runtime).

### <a name="get-metadata-about-the-azure-ssis-integration-runtime"></a>Получение метаданных о среде Integration Runtime для Azure-SSIS

```powershell
Get-AzureRmDataFactoryV2IntegrationRuntime -DataFactoryName $DataFactoryName -Name $AzureSsisIRName -ResourceGroupName $ResourceGroupName
```

### <a name="get-the-status-of-the-azure-ssis-integration-runtime"></a>Получение сведений о состоянии среды Integration Runtime для Azure-SSIS

```powershell
Get-AzureRmDataFactoryV2IntegrationRuntime -Status -DataFactoryName $DataFactoryName -Name $AzureSsisIRName -ResourceGroupName $ResourceGroupName
```

## <a name="next-steps"></a>Следующие шаги
- Сведения о планировании выполнения пакета. Дополнительные сведения см. в разделе [Планирование выполнения пакета служб SSIS в Azure](ssis-azure-schedule-packages.md).
