---
title: Включение управляемого резервного копирования SQL Server в Microsoft Azure | Документация Майкрософт
ms.custom: ''
ms.date: 10/03/2016
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 68ebb53e-d5ad-4622-af68-1e150b94516e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7ef52db1ccafaeaf9539974032da3622b23838c4
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52787096"
---
# <a name="enable-sql-server-managed-backup-to-microsoft-azure"></a>Включение управляемого резервного копирования SQL Server в Microsoft Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описано, как включить [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] с параметрами по умолчанию на уровне базы данных и экземпляра. Здесь также объясняется, как включить уведомления по электронной почте и как отслеживать резервное копирование.  
  
 В этом руководстве используется Azure PowerShell. Перед началом работы с руководством [скачайте и установите Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).  
  
> [!IMPORTANT]  
>  Если также требуется включить дополнительные параметры или использовать настраиваемое расписание, выполните эти настройки, прежде чем включать [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Дополнительные сведения см. в статье [Configure Advanced Options for SQL Server Managed Backup to Microsoft Azure](../../relational-databases/backup-restore/configure-advanced-options-for-sql-server-managed-backup-to-microsoft-azure.md).  
  
## <a name="enable-and-configure-includesssmartbackupincludesss-smartbackup-mdmd-with-default-settings"></a>Как включить и настроить [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] с параметрами по умолчанию  
  
#### <a name="create-the-azure-blob-container"></a>Создание контейнера BLOB-объектов Azure  
  
1.  **Оформите подписку Azure**. Если у вас уже есть подписка Azure, перейдите к следующему шагу. В противном случае вы можете начать работу с [бесплатной пробной версией](https://azure.microsoft.com/pricing/free-trial/) или просмотреть [варианты приобретения](https://azure.microsoft.com/pricing/purchase-options/).  
  
2.  **Создайте учетную запись хранения Azure**. Если у вас уже есть учетная запись хранения, перейдите к следующему шагу. В противном случае можно создать учетную запись хранения с помощью [портала управления Azure](https://manage.windowsazure.com/) или Azure PowerShell. Следующая команда `New-AzureStorageAccount` создает учетную запись хранения с именем `managedbackupstorage` в восточной части США.  
  
    ```powershell  
    New-AzureStorageAccount -StorageAccountName "managedbackupstorage" -Location "EAST US"  
    ```  
  
     Дополнительные сведения об учетных записях хранения см. в статье [Об учетных записях хранения Azure](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).  
  
3.  **Создайте контейнер больших двоичных объектов для файлов резервных копий.** Контейнер больших двоичных объектов можно создать на портале управления Azure или с помощью Azure PowerShell. Следующая команда `New-AzureStorageContainer` создает контейнер BLOB-объектов с именем `backupcontainer` в учетной записи хранения `managedbackupstorage` .  
  
    ```powershell  
    $context = New-AzureStorageContext -StorageAccountName managedbackupstorage -StorageAccountKey (Get-AzureStorageKey -StorageAccountName managedbackupstorage).Primary  
    New-AzureStorageContainer -Name backupcontainer -Context $context  
    ```  
  
4.  **Создайте подписанный URL-адрес (SAS)**. Для доступа к контейнеру необходимо создать SAS. Это можно сделать с помощью кода и Azure PowerShell. Следующая команда `New-AzureStorageContainerSASToken` создает маркер SAS для контейнера BLOB-объектов `backupcontainer` , срок действия которого истекает через год.  
  
    ```powershell  
    $context = New-AzureStorageContext -StorageAccountName managedbackupstorage -StorageAccountKey (Get-AzureStorageKey -StorageAccountName managedbackupstorage).Primary   
    New-AzureStorageContainerSASToken -Name backupcontainer -Permission rwdl -ExpiryTime (Get-Date).AddYears(1) -FullUri -Context $context  
    ```  
    В случае с AzureRM используйте следующую команду:
       ```powershell
    Connect-AzureRmAccount
    Set-AzureRmContext -SubscriptionId "YOURSUBSCRIPTIONID"
    $StorageAccountKey = (Get-AzureRmStorageAccountKey -ResourceGroupName YOURRESOURCEGROUPFORTHESTORAGE -Name managedbackupstorage)[0].Value
    $context = New-AzureStorageContext -StorageAccountName managedbackupstorage -StorageAccountKey $StorageAccountKey 
    New-AzureStorageContainerSASToken -Name backupcontainer -Permission rwdl -ExpiryTime (Get-Date).AddYears(1) -FullUri -Context $context
   ```  
  
     Выходные данные этой команды будут содержать как URL-адрес контейнера, так и маркер SAS. Ниже представлен пример такого кода:  
  
    ```  
    https://managedbackupstorage.blob.core.windows.net/backupcontainer?sv=2014-02-14&sr=c&sig=xM2LXVo1Erqp7LxQ%9BxqK9QC6%5Qabcd%9LKjHGnnmQWEsDf%5Q%se=2015-05-14T14%3B93%4V20X&sp=rwdl  
    ```  
  
     В предыдущем примере разделите URL-адрес контейнера от маркера SAS на вопросительном знаке (не включая вопросительный знак). Например, предыдущие выходные данные будут разделены на следующие два значения.  
  
    |||  
    |-|-|  
    |**URL-адрес контейнера:**|https://managedbackupstorage.blob.core.windows.net/backupcontainer|  
    |**Маркер SAS:**|sv=2014-02-14&sr=c&sig=xM2LXVo1Erqp7LxQ%9BxqK9QC6%5Qabcd%9LKjHGnnmQWEsDf%5Q%se=2015-05-14T14%3B93%4V20X&sp=rwdl|  
  
     Запишите URL-адрес контейнера и SAS для использования при создании учетных данных (CREDENTIAL) SQL. Дополнительные сведения о SAS см. в статье [Подписанные URL-адреса. Часть 1. Общие сведения о модели SAS](https://azure.microsoft.com/documentation/articles/storage-dotnet-shared-access-signature-part-1/).  
  
#### <a name="enable-includesssmartbackupincludesss-smartbackup-mdmd"></a>Как включить [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]  
  
1.  **Создайте учетные данные SQL для URL-адреса SAS**. Используйте маркер SAS, чтобы создать учетные данные SQL для URL-адреса контейнера больших двоичных объектов. В SQL Server Management Studio с помощью указанного ниже запроса Transact-SQL создайте учетные данные для URL-адреса контейнера BLOB-объектов, основываясь на следующем примере:  
  
    ```sql  
    CREATE CREDENTIAL [https://managedbackupstorage.blob.core.windows.net/backupcontainer]   
    WITH IDENTITY = 'Shared Access Signature',  
    SECRET = 'sv=2014-02-14&sr=c&sig=xM2LXVo1Erqp7LxQ%9BxqK9QC6%5Qabcd%9LKjHGnnmQWEsDf%5Q%se=2015-05-14T14%3B93%4V20X&sp=rwdl'  
    ```  
  
2.  **Убедитесь в том, что служба агента SQL Server запущена и работает.** Запустите агент SQL Server, если он не запущен.  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] требует, чтобы агент SQL Server был запущен на экземпляре.  Можно установить автоматический запуск агента SQL Server, чтобы обеспечить регулярное выполнение операций резервного копирования.  
  
3.  **Определение срока хранения.** Определите срок хранения файлов резервной копии. Срок хранения указывается в днях и может принимать значение от 1 до 30.  
  
4.  **Включение и настройка [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].** Запустите SQL Server Management Studio и подключитесь к целевому экземпляру SQL Server. В окне запроса выполните приведенную ниже инструкцию, предварительно изменив значения имени базы данных, URL-адреса контейнера и срока хранения в соответствии с вашими требованиями.  
  
    > [!IMPORTANT]  
    >  Чтобы включить управляемое резервное копирование на уровне экземпляра, укажите значение `NULL` для параметра `database_name` .  
  
    ```sql  
    Use msdb;  
    GO  
    EXEC msdb.managed_backup.sp_backup_config_basic   
     @enable_backup = 1,   
     @database_name = 'yourdatabasename',  
     @container_url = 'https://managedbackupstorage.blob.core.windows.net/backupcontainer',   
     @retention_days = 30  
    GO  
    ```  
  
     [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] включено на указанной базе данных. Может потребоваться до 15 минут, прежде чем начнут выполняться операции резервного копирования для базы данных.  
  
5.  **Просмотр конфигурации расширенных событий по умолчанию.** Просмотрите параметры расширенных событий, для этого запустите приведенную ниже инструкцию Transact-SQL.  
  
    ```  
    SELECT * FROM msdb.managed_backup.fn_get_current_xevent_settings()  
    ```  
  
     Обратите внимание, что события каналов Admin, Operational и Analytical включены по умолчанию и их нельзя отключить. Этого должно быть достаточно для наблюдения за событиями, требующими ручного вмешательства.  Можно включить события отладки, но каналы отладки содержат информационные и отладочные события, которые [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] использует для обнаружения и устранения проблем.  
  
6.  **Включите и настройте уведомление о состоянии работоспособности.** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] входит хранимая процедура, создающая задание агента для отправки по электронной почте уведомлений об ошибках или предупреждений, которые могут требовать внимания пользователя. Приведенные ниже шаги описывают процесс включения и настройки уведомлений по электронной почте.  
  
    1.  Настройте компонент Database Mail, если он еще не включен на экземпляре. Дополнительные сведения см. в разделе [Configure Database Mail](../../relational-databases/database-mail/configure-database-mail.md).  
  
    2.  Настройте уведомления агента SQL Server для использования компонента Database Mail. Дополнительные сведения см. в статье [Configure SQL Server Agent Mail to Use Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  **Включите уведомления по электронной почте для получения ошибок и предупреждений, связанных с резервными копиями**. В окне запроса выполните следующие инструкции Transact-SQL:  
  
        ```  
        EXEC msdb.managed_backup.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email1;email2>'  
  
        ```  
  
7.  **Просмотр файлов резервных копий в учетной записи хранения Microsoft Azure**. Подключитесь к учетной записи хранения из SQL Server Management Studio либо с помощью портала управления Azure. Все файлы резервных копий отобразятся в указанном контейнере. Обратите внимание, что база данных и резервная копия журнала могут отобразиться в течение 5 минут после включения [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для базы данных.  
  
8.  **Мониторинг состояния работоспособности**.  Можно вести мониторинг с помощью настроенных ранее уведомлений по электронной почте либо активно просматривать события в журнале. Ниже приведены примеры инструкций Transact-SQL, которые используются для просмотра событий.  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC managed_backup.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    -- to enable debug events  
    Use msdb;  
    Go  
             EXEC managed_backup.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC managed_backup.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 Шаги, описанные в этом разделе, специально предназначены для первой настройки [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] в базе данных. Существующие конфигурации можно изменять с помощью тех же системных хранимых процедур и указывать новые значения.  
  
## <a name="see-also"></a>См. также:  
 [Управляемое резервное копирование SQL Server в Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
