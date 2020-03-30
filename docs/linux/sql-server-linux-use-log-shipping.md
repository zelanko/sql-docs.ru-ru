---
title: Настройка доставки журналов для SQL Server на Linux
description: В этом руководстве представлен простой пример репликации экземпляра SQL Server на Linux в дополнительный экземпляр с помощью доставки журналов.
author: VanMSFT
ms.author: vanto
ms.date: 04/19/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 8bc7fa51eeb5d02400b15556a3bec06ce721c1de
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "73240710"
---
# <a name="get-started-with-log-shipping-on-linux"></a>Начало работы с доставкой журналов в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Доставка журналов SQL Server — это конфигурация с высоким уровнем доступности, предполагающая репликацию базы данных с сервера-источника на один или несколько серверов-получателей. Если говорить коротко, резервная копия базы данных-источника восстанавливается на сервере-получателе. Затем сервер-источник периодически создает резервные копии журналов транзакций, а серверы-получатели восстанавливают их, обновляя копию базы данных-получателя. 

  ![Доставка журналов](https://preview.ibb.co/hr5Ri5/logshipping.png)


Как показано на этой иллюстрации, сеанс доставки журналов состоит из следующих этапов:

- резервное копирование файла журнала транзакций в экземпляре-источнике SQL Server;
- копирование файла резервной копии журнала транзакций по сети в один или несколько экземпляров-получателей SQL Server;
- восстановление файла резервной копии журнала транзакций в экземплярах-получателях SQL Server.

## <a name="prerequisites"></a>предварительные требования
- [Установка агента SQL Server в Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-sql-agent)

## <a name="setup-a-network-share-for-log-shipping-using-cifs"></a>Настройка сетевой папки для доставки журналов с помощью CIFS 

> [!NOTE] 
> В этом учебнике для настройки сетевой папки используются CIFS и Samba. Если вы хотите использовать NFS, оставьте комментарий и мы добавим соответствующую информацию в статью.       

### <a name="configure-primary-server"></a>Настройка сервера-источника
-   Выполните следующие команды для установки Samba:

    ```bash
    sudo apt-get install samba #For Ubuntu
    sudo yum -y install samba #For RHEL/CentOS
    ```
-   Создайте каталог для хранения журналов в рамках доставки журналов и предоставьте mssql необходимые разрешения:

    ```bash
    mkdir /var/opt/mssql/tlogs
    chown mssql:mssql /var/opt/mssql/tlogs
    chmod 0700 /var/opt/mssql/tlogs
    ```

-   Измените файл /etc/samba/smb.conf (требуются разрешения привилегированного пользователя) и добавьте следующий раздел:

    ```bash
    [tlogs]
    path=/var/opt/mssql/tlogs
    available=yes
    read only=yes
    browsable=yes
    public=yes
    writable=no
    ```

-   Создайте пользователя mssql для Samba:

    ```bash
    sudo smbpasswd -a mssql
    ```

-   Перезапустите службы Samba:
    ```bash
    sudo systemctl restart smbd.service nmbd.service
    ```
 
### <a name="configure-secondary-server"></a>Настройка сервера-получателя

-   Выполните следующие команды для установки клиента CIFS:
    ```bash   
    sudo apt-get install cifs-utils #For Ubuntu
    sudo yum -y install cifs-utils #For RHEL/CentOS
    ```

-   Создайте файл для хранения учетных данных. Используйте пароль, который вы недавно установили для учетной записи mssql Samba. 

        vim /var/opt/mssql/.tlogcreds
        #Paste the following in .tlogcreds
        username=mssql
        domain=<domain>
        password=<password>

-   Выполните следующие команды, чтобы создать пустой каталог для подключения и правильно настроить разрешения и членство:
    ```bash   
    mkdir /var/opt/mssql/tlogs
    sudo chown root:root /var/opt/mssql/tlogs
    sudo chmod 0550 /var/opt/mssql/tlogs
    sudo chown root:root /var/opt/mssql/.tlogcreds
    sudo chmod 0660 /var/opt/mssql/.tlogcreds
    ```

-   Добавьте строку в etc/fstab, чтобы сохранить папку: 

        //<ip_address_of_primary_server>/tlogs /var/opt/mssql/tlogs cifs credentials=/var/opt/mssql/.tlogcreds,ro,uid=mssql,gid=mssql 0 0
        
-   Подключите общие папки:
    ```bash   
    sudo mount -a
    ```
       
## <a name="setup-log-shipping-via-t-sql"></a>Настройка доставки журналов с помощью T-SQL

- Выполните этот скрипт на сервере-источнике:

    ```sql
    BACKUP DATABASE SampleDB
    TO DISK = '/var/opt/mssql/tlogs/SampleDB.bak'
    GO
    ```
    ```sql
    DECLARE @LS_BackupJobId AS uniqueidentifier 
    DECLARE @LS_PrimaryId   AS uniqueidentifier 
    DECLARE @SP_Add_RetCode As int 
    EXEC @SP_Add_RetCode = master.dbo.sp_add_log_shipping_primary_database 
             @database = N'SampleDB' 
            ,@backup_directory = N'/var/opt/mssql/tlogs' 
            ,@backup_share = N'/var/opt/mssql/tlogs' 
            ,@backup_job_name = N'LSBackup_SampleDB' 
            ,@backup_retention_period = 4320
            ,@backup_compression = 2
            ,@backup_threshold = 60 
            ,@threshold_alert_enabled = 1
            ,@history_retention_period = 5760 
            ,@backup_job_id = @LS_BackupJobId OUTPUT 
            ,@primary_id = @LS_PrimaryId OUTPUT 
            ,@overwrite = 1 

    IF (@@ERROR = 0 AND @SP_Add_RetCode = 0) 
    BEGIN 

    DECLARE @LS_BackUpScheduleUID   As uniqueidentifier 
    DECLARE @LS_BackUpScheduleID    AS int 

    EXEC msdb.dbo.sp_add_schedule 
            @schedule_name =N'LSBackupSchedule' 
            ,@enabled = 1 
            ,@freq_type = 4 
            ,@freq_interval = 1 
            ,@freq_subday_type = 4 
            ,@freq_subday_interval = 15 
            ,@freq_recurrence_factor = 0 
            ,@active_start_date = 20170418 
            ,@active_end_date = 99991231 
            ,@active_start_time = 0 
            ,@active_end_time = 235900 
            ,@schedule_uid = @LS_BackUpScheduleUID OUTPUT 
            ,@schedule_id = @LS_BackUpScheduleID OUTPUT 

    EXEC msdb.dbo.sp_attach_schedule 
            @job_id = @LS_BackupJobId 
            ,@schedule_id = @LS_BackUpScheduleID  

    EXEC msdb.dbo.sp_update_job 
            @job_id = @LS_BackupJobId 
            ,@enabled = 1 
            
    END 

    EXEC master.dbo.sp_add_log_shipping_alert_job 

    EXEC master.dbo.sp_add_log_shipping_primary_secondary 
            @primary_database = N'SampleDB' 
            ,@secondary_server = N'<ip_address_of_secondary_server>' 
            ,@secondary_database = N'SampleDB' 
            ,@overwrite = 1 
    ```


- Выполните этот скрипт на сервере-получателе:

    ```sql
    RESTORE DATABASE SampleDB FROM DISK = '/var/opt/mssql/tlogs/SampleDB.bak'
    WITH NORECOVERY;
    ```
    
    ```sql
    DECLARE @LS_Secondary__CopyJobId    AS uniqueidentifier 
    DECLARE @LS_Secondary__RestoreJobId AS uniqueidentifier 
    DECLARE @LS_Secondary__SecondaryId  AS uniqueidentifier 
    DECLARE @LS_Add_RetCode As int 

    EXEC @LS_Add_RetCode = master.dbo.sp_add_log_shipping_secondary_primary 
            @primary_server = N'<ip_address_of_primary_server>' 
            ,@primary_database = N'SampleDB' 
            ,@backup_source_directory = N'/var/opt/mssql/tlogs/' 
            ,@backup_destination_directory = N'/var/opt/mssql/tlogs/' 
            ,@copy_job_name = N'LSCopy_SampleDB' 
            ,@restore_job_name = N'LSRestore_SampleDB' 
            ,@file_retention_period = 4320 
            ,@overwrite = 1 
            ,@copy_job_id = @LS_Secondary__CopyJobId OUTPUT 
            ,@restore_job_id = @LS_Secondary__RestoreJobId OUTPUT 
            ,@secondary_id = @LS_Secondary__SecondaryId OUTPUT 

    IF (@@ERROR = 0 AND @LS_Add_RetCode = 0) 
    BEGIN 

    DECLARE @LS_SecondaryCopyJobScheduleUID As uniqueidentifier 
    DECLARE @LS_SecondaryCopyJobScheduleID  AS int 

    EXEC msdb.dbo.sp_add_schedule 
            @schedule_name =N'DefaultCopyJobSchedule' 
            ,@enabled = 1 
            ,@freq_type = 4 
            ,@freq_interval = 1 
            ,@freq_subday_type = 4 
            ,@freq_subday_interval = 15 
            ,@freq_recurrence_factor = 0 
            ,@active_start_date = 20170418 
            ,@active_end_date = 99991231 
            ,@active_start_time = 0 
            ,@active_end_time = 235900 
            ,@schedule_uid = @LS_SecondaryCopyJobScheduleUID OUTPUT 
            ,@schedule_id = @LS_SecondaryCopyJobScheduleID OUTPUT 

    EXEC msdb.dbo.sp_attach_schedule 
            @job_id = @LS_Secondary__CopyJobId 
            ,@schedule_id = @LS_SecondaryCopyJobScheduleID  

    DECLARE @LS_SecondaryRestoreJobScheduleUID  As uniqueidentifier 
    DECLARE @LS_SecondaryRestoreJobScheduleID   AS int 

    EXEC msdb.dbo.sp_add_schedule 
            @schedule_name =N'DefaultRestoreJobSchedule' 
            ,@enabled = 1 
            ,@freq_type = 4 
            ,@freq_interval = 1 
            ,@freq_subday_type = 4 
            ,@freq_subday_interval = 15 
            ,@freq_recurrence_factor = 0 
            ,@active_start_date = 20170418 
            ,@active_end_date = 99991231 
            ,@active_start_time = 0 
            ,@active_end_time = 235900 
            ,@schedule_uid = @LS_SecondaryRestoreJobScheduleUID OUTPUT 
            ,@schedule_id = @LS_SecondaryRestoreJobScheduleID OUTPUT 

    EXEC msdb.dbo.sp_attach_schedule 
            @job_id = @LS_Secondary__RestoreJobId 
            ,@schedule_id = @LS_SecondaryRestoreJobScheduleID  
            
    END 
    DECLARE @LS_Add_RetCode2    As int 
    IF (@@ERROR = 0 AND @LS_Add_RetCode = 0) 
    BEGIN 

    EXEC @LS_Add_RetCode2 = master.dbo.sp_add_log_shipping_secondary_database 
            @secondary_database = N'SampleDB' 
            ,@primary_server = N'<ip_address_of_primary_server>' 
            ,@primary_database = N'SampleDB' 
            ,@restore_delay = 0 
            ,@restore_mode = 0 
            ,@disconnect_users  = 0 
            ,@restore_threshold = 45   
            ,@threshold_alert_enabled = 1 
            ,@history_retention_period  = 5760 
            ,@overwrite = 1 

    END 

    IF (@@error = 0 AND @LS_Add_RetCode = 0) 
    BEGIN 

    EXEC msdb.dbo.sp_update_job 
            @job_id = @LS_Secondary__CopyJobId 
            ,@enabled = 1 

    EXEC msdb.dbo.sp_update_job 
            @job_id = @LS_Secondary__RestoreJobId 
            ,@enabled = 1 

    END 
    ```

## <a name="verify-log-shipping-works"></a>Проверка работы доставки журналов

- Чтобы проверить, работает ли доставка журналов, запустите следующее задание на сервере-источнике:

    ```sql
    USE msdb ;  
    GO  

    EXEC dbo.sp_start_job N'LSBackup_SampleDB' ;  
    GO  
    ```

- Чтобы проверить, работает ли доставка журналов, запустите следующее задание на сервере-получателе:
 
    ```sql
    USE msdb ;  
    GO  

    EXEC dbo.sp_start_job N'LSCopy_SampleDB' ;  
    GO  
    EXEC dbo.sp_start_job N'LSRestore_SampleDB' ;  
    GO  
    ```
 - Убедитесь, что отработка отказа доставки журналов работает, выполнив следующую команду.
 
    > [!WARNING]
    > Эта команда переводит базу данных-получатель в оперативный режим и нарушает конфигурацию доставки журналов. После выполнения этой команды необходимо будет перенастроить доставку журналов.
 
    ```sql
    RESTORE DATABASE SampleDB WITH RECOVERY;
    ```


