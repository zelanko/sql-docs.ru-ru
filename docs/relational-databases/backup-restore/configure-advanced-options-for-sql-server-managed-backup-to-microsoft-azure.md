---
title: Управляемое резервное копирование — настройка дополнительных параметров
description: В этом учебнике описывается, как задать дополнительные параметры для управляемого резервного копирования SQL Server в Microsoft Azure, если параметры по умолчанию не соответствуют вашим потребностям.
titleSuffix: to Microsoft Azure
ms.custom: seo-lt-2019
ms.date: 12/17/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: ffd28159-8de8-4d40-87da-1586bfef3315
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c3bc0a8e805b8a416cba9e7bf7786cfc9840e046
ms.sourcegitcommit: 9afb612c5303d24b514cb8dba941d05c88f0ca90
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2020
ms.locfileid: "82220484"
---
# <a name="configure-advanced-options-for-sql-server-managed-backup-to-microsoft-azure"></a>Настройка дополнительных параметров управляемого резервного копирования SQL Server в Microsoft Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом руководстве описана настройка дополнительных параметров для [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Эти процедуры необходимы, только если вам нужны соответствующие функции. В противном случае вы можете включить [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] и использовать параметры по умолчанию.  
  
 В каждом сценарии резервное копирование настраивается с использованием параметра `database_name` . Если параметр `database_name` имеет значение NULL или *, изменения затронут параметры по умолчанию на уровне экземпляра. Параметры на уровне экземпляра будут применены и к новым базам данных, созданным после такого изменения.  
  
 После настройки этих параметров вы сможете включить управляемое резервное копирование для базы данных или экземпляра с помощью системной хранимой процедуры [managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md). Дополнительные сведения см. в статье [Включение управляемого резервного копирования SQL Server для Microsoft Azure](../../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md).  
  
> [!WARNING]  
>  Прежде чем включать [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)], нужно обязательно настроить дополнительные параметры и пользовательские параметры планирования, используя процедуру [managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md). В противном случае могут быть запущены нежелательные операции резервного копирования в период между активацией [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] и настройкой параметров.  
  
## <a name="configure-encryption"></a>Настройка шифрования  
 Следующие шаги описывают настройку параметров шифрования с помощью хранимой процедуры [managed_backup.sp_backup_config_advanced (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md).  

1.  **Выберите алгоритм шифрования.** Сначала определитесь с алгоритмом шифрования, который будете использовать. Выберите один из следующих вариантов.  
  
    -   AES_128  
  
    -   AES_192  
  
    -   AES_256  
  
    -   TRIPLE_DES_3KEY  
  
    -   NO_ENCRYPTION  
  
2.  **Создайте главный ключ базы данных.** Выберите пароль для шифрования копии главного ключа базы данных, которая будет храниться в базе данных.  
  
    ```  
    -- Creates a database master key.  
    -- The key is encrypted using the password "<master key password>"  
    USE Master;  
    GO  
       CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
    ```  
  
3.  **Создайте сертификат или асимметричный ключ для резервной копии.** Вы можете использовать для шифрования сертификат или асимметричный ключ. Следующий пример демонстрирует создание сертификата, который будет использован для шифрования.  
  
    ```sql  
    USE Master;  
    GO  
       CREATE CERTIFICATE MyTestDBBackupEncryptCert  
          WITH SUBJECT = 'MyTestDBBackupEncryptCert';  
    GO  
    ```  
  
4.  **Настройте шифрование управляемого резервного копирования.** Вызовите хранимую процедуру **managed_backup.sp_backup_config_advanced** с соответствующими значениями. Следующий пример настраивает для базы данных `MyDB` шифрование с использованием сертификата с именем `MyTestDBBackupEncryptCert` и алгоритма шифрования `AES_128` .  
  
    ```  
    USE msdb;  
    GO  
       EXEC managed_backup.sp_backup_config_advanced  
          @database_name = 'MyDB'                
          ,@encryption_algorithm ='AES_128'  
          ,@encryptor_type = 'CERTIFICATE'  
          ,@encryptor_name = 'MyTestDBBackupEncryptCert';  
    GO  
    ```  
  
    > [!WARNING]  
    >  Если в предыдущем примере указать для `@database_name` значение NULL, параметры будут применены к экземпляру SQL Server.  
  
## <a name="configure-a-custom-backup-schedule"></a>Настройка расписания резервного копирования  
 Следующие шаги описывают настройку параметров шифрования с помощью хранимой процедуры [managed_backup.sp_backup_config_schedule (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md).  
  
1.  **Определите частоту полного резервного копирования.** Укажите, как часто будут создаваться полные резервные копии базы данных. Для полного резервного копирования доступны варианты "ежедневно" и "еженедельно".  
  
2.  **Определите частоту резервного копирования журналов.** Укажите, как часто будут создаваться резервные копии журналов. Это значение задается в часах или минутах.  
  
3.  **Определите день недели для еженедельного резервного копирования.** Если вы настроили еженедельное резервное копирование, выберите день недели для создания полной резервной копии.  
  
4.  **Определите время начала резервного копирования.** Выберите время запуска резервного копирования в 24-часовом формате.  
  
5.  **Определите продолжительность резервного копирования.** Здесь нужно указать время, необходимое для создания резервной копии.  
  
6.  **Установите пользовательское расписание резервного копирования.** Следующая хранимая процедура позволяет задать пользовательское расписание для базы данных `MyDB`. Полные резервные копии создаются еженедельно в `Monday` в `17:30`. Резервные копии журналов создаются каждые `5` минут. Резервное копирование выполняется не более двух часов.  
  
    ```  
    USE msdb;  
    GO  
    EXEC managed_backup.sp_backup_config_schedule   
         @database_name =  'MyDB'  
        ,@scheduling_option = 'Custom'  
        ,@full_backup_freq_type = 'Weekly'  
        ,@days_of_week = 'Monday'  
        ,@backup_begin_time =  '17:30'  
        ,@backup_duration = '02:00'  
        ,@log_backup_freq = '00:05'  
    GO  
  
    ```  
  
## <a name="next-steps"></a>Next Steps  
 После настройки дополнительных параметров и пользовательского расписания следует включить [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для целевой базы данных или экземпляра SQL Server. Дополнительные сведения см. в статье [Enable SQL Server Managed Backup to Microsoft Azure](../../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md).  
  
## <a name="see-also"></a>См. также:  
 [Управляемое резервное копирование SQL Server в Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
