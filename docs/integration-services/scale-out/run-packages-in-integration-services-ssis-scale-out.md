---
title: "Выполнение пакетов в SQL Server Integration Services (SSIS) Scale Out | Документы Майкрософт"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
f1_keywords: sql13.ssis.ssms.ispackageexecuteinscaleout.f1
ms.workload: Inactive
ms.openlocfilehash: 88537ff52ada042d642b8915342e374ecca3246e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="run-packages-in-integration-services-ssis-scale-out"></a>Выполнение пакетов в SQL Server Integration Services (SSIS) Scale Out
После развертывания пакетов на сервере служб Integration Services их можно выполнить в масштабном развертывании.

## <a name="run-packages-with-execute-package-in-scale-out-dialog"></a>Выполнение пакетов с помощью диалогового окна "Выполнение пакета в Scale Out" 

1. Открытие диалогового окна "Выполнение пакета в сценарии масштабирования"

    В [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] подключитесь к серверу служб Integration Services. В обозревателе объектов разверните дерево для отображения узлов в разделе **Каталоги служб Integration Services**. Щелкните правой кнопкой мыши узел **SSISDB** либо проект или пакет, который требуется запустить, и выберите пункт **Execute in Scale Out**(Выполнить в масштабном развертывании).

2. Выбор пакетов и задание параметров

    На странице **Выбор пакета** выберите несколько пакетов, которые нужно запустить, и настройте среду, параметры, диспетчеры подключений и дополнительные параметры для каждого из них. Чтобы задать эти параметры, щелкните пакет.
    
    На вкладке **Дополнительно** задайте параметр масштабного развертывания **Число повторных попыток**. Он указывает, сколько раз будет предприниматься повторная попытка выполнения пакета в случае сбоя.

    > [!Note]
    > Параметр **Дамп при ошибках** действует только в том случае, если учетная запись, под которой выполняется служба рабочей роли Scale Out, является администратором локального компьютера.

3. Выбор компьютеров

    На странице **Выбор компьютера** выберите компьютеры масштабного развертывания для выполнения пакетов. По умолчанию выполнять пакеты разрешено любому компьютеру. 

   > [!Note] 
   > Пакеты выполняются с учетными данными пользовательских учетных записей служб рабочих ролей масштабного развертывания, которые приведены на странице **Выбор компьютера** . По умолчанию используется учетная запись NT Service\SSISScaleOutWorker140. Вы можете использовать свои лабораторные учетные записи.

   >[!WARNING]
   >Пакеты, выполнение которых инициируется разными пользователями одной рабочей роли, выполняются в одной учетной записи. Границы безопасности между ними не устанавливаются. 

4. Выполнение пакетов и просмотр отчетов 

    Нажмите кнопку **ОК** , чтобы начать выполнение пакетов. Чтобы просмотреть для пакета отчет о выполнении, щелкните пакет правой кнопкой мыши в обозревателе объектов, выберите **Отчеты**, **Все выполнения**и найдите выполнение.
    
## <a name="run-packages-with-stored-procedures"></a>Выполнение пакетов с помощью хранимых процедур

1. Создание выполнений

    Вызовите [catalog].[create_execution] для каждого пакета. Задайте для параметра **@runinscaleout** значение True. Если выполнять пакет разрешено не всем компьютерам масштабного развертывания, задайте для параметра **@useanyworker** значение False.   

2. Задание параметров выполнения

    Вызовите [catalog].[set_execution_parameter_value] для каждого выполнения.

3. Задание рабочих ролей масштабного развертывания

    Вызовите [catalog].[add_execution_worker]. Если выполнять пакет разрешено любому компьютеру, вызывать эту хранимую процедуру не требуется. 

4. Запуск выполнений

    Вызовите [catalog].[start_execution]. Задайте параметр **@retry_count** , указывающий, сколько раз будет предприниматься повторная попытка выполнения пакета в случае сбоя.
    
#### <a name="example"></a>Пример
В следующем примере выполняются два пакета — package1.dtsx и package2.dtsx — в масштабном развертывании с использованием одной рабочей роли.  

```sql
Declare @execution_id bigint
EXEC [SSISDB].[catalog].[create_execution] @package_name=N'package1.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'folder1', @project_name=N'project1', @use32bitruntime=False, @reference_id=Null, @useanyworker=False, @runinscaleout=True
Select @execution_id
DECLARE @var0 smallint = 1
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0
EXEC [SSISDB].[catalog].[add_execution_worker] @execution_id,  @workeragent_id=N'64c020e2-f819-4c2d-a22f-efb31a91e70a'
EXEC [SSISDB].[catalog].[start_execution] @execution_id,  @retry_count=0
GO

Declare @execution_id bigint
EXEC [SSISDB].[catalog].[create_execution] @package_name=N'package2.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'folder2', @project_name=N'project2', @use32bitruntime=False, @reference_id=Null, @useanyworker=False, @runinscaleout=True
Select @execution_id
DECLARE @var0 smallint = 1
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0
EXEC [SSISDB].[catalog].[add_execution_worker] @execution_id,  @workeragent_id=N'64c020e2-f819-4c2d-a22f-efb31a91e70a'
EXEC [SSISDB].[catalog].[start_execution] @execution_id,  @retry_count=0
GO
```

### <a name="permissions"></a>Permissions
Для выполнения пакетов в масштабном развертывании требуется одно из следующих разрешений:

-   Членство в роли базы данных **ssis_admin**  

-   Членство в роли базы данных **ssis_cluster_executor**  
  
-   Членство в роли сервера **sysadmin**  

## <a name="set-default-execution-mode"></a>Установка режима выполнения по умолчанию
Чтобы установить режим выполнения по умолчанию "Scale Out", щелкните правой кнопкой мыши узел **SSISDB** в обозревателе объектов служб SSMS и выберите пункт **Свойства**.
В диалоговом окне **Свойства каталога** присвойте параметру **Серверный режим выполнения по умолчанию** значение **Scale Out**.

После этого не требуется задавать параметр **@runinscaleout** для [catalog].[create_execution]. Все операции выполнения автоматически осуществляются в Scale Out. 

![Режим выполнения](media\exe-mode.PNG)

Чтобы отключить выполнение в режиме Scale Out по умолчанию, присвойте параметру **Серверный режим выполнения по умолчанию** значение **Сервер**.

## <a name="run-package-in-sql-agent-job"></a>Выполнение пакета в задании агента SQL
В задании агента SQL можно выбрать выполнение пакета служб SSIS в рамках одного из шагов задания. Чтобы выполнить пакет в сценарии Scale Out, можно использовать один из показанных выше режимов выполнения по умолчанию. После того, как настроен режим выполнения по умолчанию "Scale Out", пакеты в заданиях агента SQL будут выполняться в режиме Scale Out.
