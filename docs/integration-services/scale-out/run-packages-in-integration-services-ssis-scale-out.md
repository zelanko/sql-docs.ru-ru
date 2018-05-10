---
title: Выполнение пакетов в SQL Server Integration Services (SSIS) Scale Out | Документы Майкрософт
ms.description: This article describes how to run SSIS packages in Scale Out
ms.custom: ''
ms.date: 12/13/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: scale-out
ms.reviewer: douglasl
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: craigg
f1_keywords:
- sql13.ssis.ssms.ispackageexecuteinscaleout.f1
ms.openlocfilehash: 3566938f25a646206e203810a84451829b0206cb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="run-packages-in-integration-services-ssis-scale-out"></a>Выполнение пакетов в SQL Server Integration Services (SSIS) Scale Out
После развертывания пакетов на сервере служб Integration Services их можно запускать в Scale Out одним из следующих способов:

-   [Диалоговое окно "Выполнение пакета в сценарии масштабирования"](#scale_out_dialog)

-   [Хранимые процедуры](#stored_proc)

-   [задания агента SQL Server](#sql_agent)

## <a name="scale_out_dialog"></a> Выполнение пакетов с помощью диалогового окна "Выполнение пакета в сценарии масштабирования"

1. Откройте диалоговое окно "Выполнение пакета в сценарии масштабирования".

    В [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] подключитесь к серверу служб Integration Services. В обозревателе объектов разверните дерево для отображения узлов в разделе **Каталоги служб Integration Services**. Щелкните правой кнопкой мыши узел **SSISDB** либо проект или пакет, который требуется запустить, и выберите пункт **Execute in Scale Out**(Выполнить в масштабном развертывании).

2. Выберите пакеты и задайте параметры.

    На странице **Выбор пакетов** выберите один или несколько пакетов для выполнения. Для каждого пакета задайте среду, параметры, диспетчеры подключений и дополнительные параметры. Чтобы задать эти параметры, щелкните пакет.
    
    На вкладке **Дополнительно** укажите, сколько раз будут совершаться попытки выполнения пакета в случае сбоя, задав параметр Scale Out **Число повторных попыток**.

    > [!NOTE]
    > Параметр **Дамп при ошибках** действует только в том случае, если учетная запись, с которой выполняется служба рабочей роли Scale Out, является администратором локального компьютера.

3. Выберите компьютеры рабочей роли.

    На странице **Выбор компьютера** выберите компьютеры рабочей роли Scale Out для выполнения пакетов. По умолчанию выполнять пакеты разрешено любому компьютеру. 

   > [!NOTE] 
   > Пакеты выполняются с учетными данными служб рабочих ролей Scale Out. Они приведены на странице **Выбор компьютера**. По умолчанию используется учетная запись `NT Service\SSISScaleOutWorker140`.

   > [!WARNING]
   > Пакеты, выполнение которых инициируется разными пользователями одной рабочей роли, запускаются с одними и теми же учетными данными. Границы безопасности между ними не устанавливаются. 

4. Выполните пакеты и просмотрите отчеты.

    Нажмите кнопку **ОК** , чтобы начать выполнение пакетов. Чтобы просмотреть для пакета отчет о выполнении, щелкните пакет правой кнопкой мыши в обозревателе объектов, выберите **Отчеты**, **Все выполнения**и найдите выполнение.
    
## <a name="stored_proc"></a> Выполнение пакетов с помощью хранимых процедур

1.  Создайте выполнения.

    Вызовите процедуру `[catalog].[create_execution]` для каждого пакета. Задайте для параметра **@runinscaleout** значение `True`. Если выполнять пакет разрешено не всем компьютерам рабочей роли Scale Out, задайте для параметра **@useanyworker** значение `False`. Дополнительные сведения об этой хранимой процедуре и параметре **@useanyworker** см. в разделе [catalog.create_execution](../system-stored-procedures/catalog-create-execution-ssisdb-database.md). 

2. Задайте параметры выполнения.

    Вызовите процедуру `[catalog].[set_execution_parameter_value]` для каждого выполнения.

3. Задайте рабочие роли Scale Out.

    Вызовите процедуру `[catalog].[add_execution_worker]`. Если выполнять пакет разрешено всем компьютерам, вызывать эту хранимую процедуру не требуется. 

4. Запустите выполнения.

    Вызовите процедуру `[catalog].[start_execution]`. Задайте параметр **@retry_count**, указывающий, сколько раз будет предприниматься повторная попытка выполнения пакета в случае сбоя.
    
### <a name="example"></a>Пример
В приведенном ниже примере выполняются два пакета — `package1.dtsx` и `package2.dtsx` — в Scale Out с использованием одной рабочей роли.  

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

### <a name="permissions"></a>Разрешения
Для выполнения пакетов в Scale Out требуется одно из следующих разрешений:

-   Членство в роли базы данных **ssis_admin**  

-   Членство в роли базы данных **ssis_cluster_executor**  
  
-   Членство в роли сервера **sysadmin**  

## <a name="set-default-execution-mode"></a>Установка режима выполнения по умолчанию
Чтобы задать для пакетов режим выполнения по умолчанию **Scale Out**, выполните указанные ниже действия.

1.  В SQL Server Management Studio в обозревателе объектов щелкните правой кнопкой мыши узел **SSISDB** и выберите пункт **Свойства**.

2.  В диалоговом окне **Свойства каталога** присвойте свойству **Серверный режим выполнения по умолчанию** значение **Scale Out**.

После задания этого режима выполнения по умолчанию больше не нужно указывать параметр **@runinscaleout** при вызове хранимой процедуры `[catalog].[create_execution]`. Пакеты выполняются в Scale Out автоматически. 

![Режим выполнения](media\exe-mode.PNG)

Чтобы отключить выполнение в режиме Scale Out по умолчанию, присвойте свойству **Серверный режим выполнения по умолчанию** значение **Сервер**.

## <a name="sql_agent"></a> Выполнение пакета в рамках задания агента SQL Server
Пакет служб SSIS может выполняться как один из этапов задания агента SQL Server. Чтобы выполнить пакет в Scale Out, задайте **Scale Out** в качестве режима выполнения по умолчанию. После того, как настроен режим выполнения по умолчанию **Scale Out**, пакеты в заданиях агента SQL Server будут выполняться в режиме Scale Out.

## <a name="next-steps"></a>Следующие шаги
-   [Устранение неполадок Scale Out](troubleshooting-scale-out.md)
