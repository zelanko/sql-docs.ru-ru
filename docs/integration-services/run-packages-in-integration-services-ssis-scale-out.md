---
title: "Выполнение пакетов в масштабном развертывании служб Integration Services (SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c2f4cd7-9c47-416d-bb1e-40acc3e05342
caps.latest.revision: 5
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 5
---
# Выполнение пакетов в масштабном развертывании служб Integration Services (SSIS)
После развертывания пакетов на сервере служб Integration Services их можно выполнить в масштабном развертывании.

## <a name="run-packages-with-execute-package-in-scale-out-dialog"></a>Выполнение пакетов с помощью диалогового окна **Выполнение пакета в сценарии масштабирования** 

1. ### <a name="open-the-execute-package-in-scale-out-dialog-box"></a>Открытие диалогового окна "Выполнение пакета в сценарии масштабирования" ###
    В [!INCLUDE[ssManStudioFull_md](../includes/ssmanstudiofull-md.md)] подключитесь к серверу служб Integration Services. В обозревателе объектов разверните дерево для отображения узлов в разделе **Каталоги служб Integration Services**. Щелкните правой кнопкой мыши узел **SSISDB** либо проект или пакет, который требуется запустить, и выберите пункт **Execute in Scale Out** (Выполнить в масштабном развертывании).
2. ### <a name="select-packages-and-set-the-options"></a>Выбор пакетов и задание параметров ###
    На странице **Выбор пакета** выберите несколько пакетов, которые нужно запустить, и настройте среду, параметры, диспетчеры подключений и дополнительные параметры для каждого из них. Чтобы задать эти параметры, щелкните пакет.
    
    На вкладке **Дополнительно** задайте параметр масштабного развертывания **Число повторных попыток**. Он указывает, сколько раз будет предприниматься повторная попытка выполнения пакета в случае сбоя.
3. ### <a name="select-machines"></a>Выбор компьютеров ###
    На странице **Выбор компьютера** выберите компьютеры масштабного развертывания для выполнения пакетов. По умолчанию выполнять пакеты разрешено любому компьютеру. 

   > [!NOTE]
> Пакеты выполняются с учетными данными пользовательских учетных записей служб рабочих ролей масштабного развертывания, которые приведены на странице **Выбор компьютера**. По умолчанию используется учетная запись NT Service\SSISScaleOutWorker140. Вы можете использовать свои лабораторные учетные записи.

4. ### <a name="run-the-packages-and-view-reports"></a>Выполнение пакетов и просмотр отчетов 
    Нажмите кнопку **ОК**, чтобы начать выполнение пакетов. Чтобы просмотреть для пакета отчет о выполнении, щелкните пакет правой кнопкой мыши в обозревателе объектов, выберите **Отчеты**, **Все выполнения** и найдите выполнение.
    
    
## <a name="run-packages-with-stored-procedures"></a>Выполнение пакетов с помощью хранимых процедур

1. ### <a name="create-executions"></a>Создание выполнений ###
    Вызовите [catalog].[create_execution] для каждого пакета. Задайте для параметра **@runincluster** значение True. Если выполнять пакет разрешено не всем компьютерам масштабного развертывания, задайте для параметра **@useanyworker** значение False.   
2. ### <a name="set-execution-parameters"></a>Задание параметров выполнения ###
    Вызовите [catalog].[set_execution_parameter_value] для каждого выполнения.
3. ### <a name="set-scale-out-workers"></a>Задание рабочих ролей масштабного развертывания ###
    Вызовите [catalog].[add_execution_worker]. Если выполнять пакет разрешено любому компьютеру, вызывать эту хранимую процедуру не требуется. 
4. ### <a name="start-executions"></a>Запуск выполнений ###
    Вызовите [catalog].[start_execution]. Задайте параметр **@retry_count**, указывающий, сколько раз будет предприниматься повторная попытка выполнения пакета в случае сбоя.
    
    ### <a name="example"></a>Пример  ###  
    В следующем примере выполняются два пакета — package1.dtsx и package2.dtsx — в масштабном развертывании с использованием одной рабочей роли.  
    ```
    Declare @execution_id bigint
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'package1.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'folder1', @project_name=N'project1', @use32bitruntime=False, @reference_id=Null, @useanyworker=False, @runincluster=True
    Select @execution_id
    DECLARE @var0 smallint = 1
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0
    EXEC [SSISDB].[catalog].[add_execution_worker] @execution_id,  @workeragent_id=N'64c020e2-f819-4c2d-a22f-efb31a91e70a'
    EXEC [SSISDB].[catalog].[start_execution] @execution_id,  @retry_count=0
    GO

    Declare @execution_id bigint
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'package2.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'folder2', @project_name=N'project2', @use32bitruntime=False, @reference_id=Null, @useanyworker=False, @runincluster=True
    Select @execution_id
    DECLARE @var0 smallint = 1
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0
    EXEC [SSISDB].[catalog].[add_execution_worker] @execution_id,  @workeragent_id=N'64c020e2-f819-4c2d-a22f-efb31a91e70a'
    EXEC [SSISDB].[catalog].[start_execution] @execution_id,  @retry_count=0
    GO
    ```


## <a name="permissions"></a>Permissions
Для выполнения пакетов в масштабном развертывании требуется одно из следующих разрешений:

-   Членство в роли базы данных **ssis_admin**  

-   Членство в роли базы данных **ssis_cluster_executor**  
  
-   Членство в роли сервера **sysadmin**  
    