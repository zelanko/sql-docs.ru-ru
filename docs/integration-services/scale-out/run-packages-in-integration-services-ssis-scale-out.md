---
title: "Масштабировать выполнения пакетов в SQL Server Integration Services (SSIS) | Документы Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
f1_keywords:
- sql13.ssis.ssms.ispackageexecuteinscaleout.f1
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2c158ae6a711ecb5f5065561c0c8c303e9a09980
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---

# <a name="run-packages-in-integration-services-ssis-scale-out"></a>Запуск пакетов в Integration Services (SSIS) масштабное развертывание
После развертывания пакетов на сервере служб Integration Services их можно выполнить в масштабном развертывании.

## <a name="run-packages-with-execute-package-in-scale-out-dialog"></a>Запуск пакетов с помощью диалогового окна Выполнение пакета в масштабное развертывание 

1. Открытие диалогового окна "Выполнение пакета в сценарии масштабирования"

    В [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] подключитесь к серверу служб Integration Services. В обозревателе объектов разверните дерево для отображения узлов в разделе **Каталоги служб Integration Services**. Щелкните правой кнопкой мыши узел **SSISDB** либо проект или пакет, который требуется запустить, и выберите пункт **Execute in Scale Out**(Выполнить в масштабном развертывании).

2. Выбор пакетов и задание параметров

    На странице **Выбор пакета** выберите несколько пакетов, которые нужно запустить, и настройте среду, параметры, диспетчеры подключений и дополнительные параметры для каждого из них. Чтобы задать эти параметры, щелкните пакет.
    
    На вкладке **Дополнительно** задайте параметр масштабного развертывания **Число повторных попыток**. Он указывает, сколько раз будет предприниматься повторная попытка выполнения пакета в случае сбоя.

    > [!Note]
    > **Дамп при ошибках** параметр вступает в силу только после учетной записи службы шкалы Out рабочих администратора локального компьютера.

3. Выбор компьютеров

    На странице **Выбор компьютера** выберите компьютеры масштабного развертывания для выполнения пакетов. По умолчанию выполнять пакеты разрешено любому компьютеру. 

   > [!Note] 
   > Пакеты выполняются с учетными данными пользовательских учетных записей служб рабочих ролей масштабного развертывания, которые приведены на странице **Выбор компьютера** . По умолчанию используется учетная запись NT Service\SSISScaleOutWorker140. Вы можете использовать свои лабораторные учетные записи.

   >[!WARNING]
   >Выполнения пакета, активируемых разных пользователей в одном рабочем процессе, выполняются с той же учетной записи. Нет существует границы безопасности между ними. 

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

## <a name="set-default-execution-mode"></a>Установить режим выполнения по умолчанию
Чтобы задать режим выполнения по умолчанию для «Масштабное развертывание», щелкните правой кнопкой мыши **SSISDB** узел в обозревателе объектов SSMS и выберите **свойства**.
В **свойства каталога** диалогового окна, набор **режим выполнения по умолчанию уровня сервера** для **масштабное развертывание**.

После этого параметра нет необходимости для указания  **@runinscaleout**  параметр [catalog]. [ create_execution]. Количество выполнений, автоматически выполняются в масштабное развертывание. 

![Режим exe-файла](media\exe-mode.PNG)

Переключить режим выполнения по умолчанию обратно в режим не - масштабное развертывание, просто установите **режим выполнения по умолчанию уровня сервера** для **сервера**.

## <a name="run-package-in-sql-agent-job"></a>Запустите пакет в задании агента SQL
Задание агента Sql Server вы можете запустить пакет служб SSIS как один шаг задания. Чтобы запустить пакет в масштабное развертывание, можно использовать выше режим выполнения по умолчанию. После настройки по умолчанию режим выполнения для «Масштабное развертывание» будет выполняться пакетов из заданий агента Sql Server в масштабное развертывание.
