---
title: Настройка управляемого резервного копирования SQL Server в Azure | Документация Майкрософт
ms.custom: ''
ms.date: 08/04/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 68ebb53e-d5ad-4622-af68-1e150b94516e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b69439226b55965e37f24f2131c77340ae833590
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154724"
---
# <a name="setting-up-sql-server-managed-backup-to-azure"></a>Настройка управляемого резервного копирования SQL Server в Azure
  В этот раздел входят два учебника:  
  
 Настройка [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] на уровне базы данных, включение уведомлений по электронной почте и мониторинг резервного копирования.  
  
 Настройка [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] на уровне экземпляра, включение уведомлений по электронной почте и мониторинг резервного копирования.  
  
 Руководство по настройке [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] групп доступности см. в статье [Настройка SQL Server управляемого резервного копирования в Microsoft Azure для групп доступности](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).  
  
## <a name="setting-up-includess_smartbackupincludesss-smartbackup-mdmd"></a>Настройка [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]  
  
### <a name="enable-and-configure-includess_smartbackupincludesss-smartbackup-mdmd-for-a-database"></a>Включение и настройка [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для базы данных  
 В этом учебнике приведены необходимые шаги по включению и настройке [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для базы данных (TestDB), затем приведены шаги по включению контроля работоспособности [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 **Разрешения**:  
  
-   Требуется членство в роли базы данных **db_backupoperator** с разрешениями **ALTER ANY CREDENTIAL** и `EXECUTE` разрешения на хранимую процедуру **sp_delete_backuphistory**.  
  
-   Требуются разрешения **SELECT** на функцию **smart_admin. fn_get_current_xevent_settings**.  
  
-   Требуются `EXECUTE` разрешения на хранимую процедуру **smart_admin. sp_get_backup_diagnostics** . Кроме того, необходимы разрешения `VIEW SERVER STATE`, так как процедура автоматически вызывает другие системные объекты, которым требуется это разрешение.  
  
-   Требуются `EXECUTE` `smart_admin.sp_backup_master_switch` разрешения`smart_admin.sp_set_instance_backup` для хранимых процедур и.  


1.  **Создайте учетную запись хранения Microsoft Azure:** Резервные копии хранятся в службе хранилища Microsoft Azure. Необходимо сначала создать учетную запись хранения Microsoft Azure, если у вас еще нет учетной записи.
    - SQL Server 2014 использует страничные большие двоичные объекты, которые отличаются от блочных и добавочных BLOB-объектов. Поэтому необходимо создать учетную запись общего назначения, а не учетную запись BLOB-объекта. Дополнительные сведения см. в статье [об учетных записях хранения Azure](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).
    - Запишите имя учетной записи хранения и ключи доступа. Имя учетной записи хранения и сведения о ключе доступа используются для создания учетных данных SQL. Учетные данные SQL используются для проверки подлинности учетной записи хранения.  
 
2.  **Создайте учетные данные SQL:** Создайте учетные данные SQL, используя имя учетной записи хранения в качестве удостоверения и ключ доступа к хранилищу в качестве пароля.  
  
3.  **Убедитесь в том, что служба агента SQL Server запущена и работает.**  Запустите агент SQL Server, если он не запущен.  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] требует, чтобы агент SQL Server был запущен на экземпляре.  Можно установить автоматический запуск агента SQL Server, чтобы обеспечить регулярное выполнение операций резервного копирования.  
  
4.  **Определение срока хранения.** Определите период хранения файлов резервной копии. Срок хранения указывается в днях и может принимать значение от 1 до 30.  
  
5.  **Включение и настройка [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].** Запустите SQL Server Management Studio и подключитесь к экземпляру, где установлена база данных. В окне запроса выполните приведенную ниже инструкцию, предварительно задав нужные значения имени базы данных, учетных данных SQL, срока хранения и параметров шифрования.  
  
     Дополнительные сведения о создании сертификата для шифрования см. в разделе Создание **резервной копии сертификата** статьи [Создание зашифрованного резервного копирования](create-an-encrypted-backup.md).  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='TestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
  
    ```  
  
     [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] включено на указанной базе данных. Может потребоваться до 15 минут, прежде чем начнут выполняться операции резервного копирования для базы данных.  
  
6.  **Просмотр конфигурации расширенных событий по умолчанию.** Просмотрите параметры расширенных событий, выполнив приведенную ниже инструкцию Transact-SQL.  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     Обратите внимание, что события каналов Admin, Operational и Analytical включены по умолчанию и их нельзя отключить. Этого должно быть достаточно для наблюдения за событиями, требующими ручного вмешательства.  Можно включить события отладки, но каналы отладки содержат информационные и отладочные события, которые [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] использует для обнаружения и устранения проблем. Дополнительные сведения см. [в статье мониторинг SQL Server управляемого резервного копирования для Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).  
  
7.  **Включите и настройте уведомление о состоянии работоспособности.** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] входит хранимая процедура, создающая задание агента для отправки по электронной почте уведомлений об ошибках или предупреждений, которые могут требовать внимания пользователя. Приведенные ниже шаги описывают процесс включения и настройки уведомлений по электронной почте.  
  
    1.  Настройте компонент Database Mail, если он еще не включен на экземпляре. Дополнительные сведения см. в разделе [Configure Database Mail](../database-mail/configure-database-mail.md).  
  
    2.  Настройте уведомления агента SQL Server для использования компонента Database Mail. Дополнительные сведения см. в статье [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  **Включите уведомления по электронной почте для получения ошибок и предупреждений, связанных с резервными копиями**. В окне запроса выполните следующие инструкции Transact-SQL:  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email1;email2>'  
  
        ```  
  
         Дополнительные сведения и полный пример скрипта см. [в разделе Monitor SQL Server управляемое резервное копирование в Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).  
  
8.  **Просмотр файлов резервных копий в учетной записи хранения Microsoft Azure**. Подключитесь к учетной записи хранения из SQL Server Management Studio либо с помощью портала управления Azure. Вы увидите контейнер экземпляра SQL Server, в котором размещается база данных, настроенная на использование [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Кроме того, можно настроить базу данных и резервное копирование журналов за 15 минут либо включить [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для базы данных.  
  
9. **Мониторинг состояния работоспособности**.  Можно вести мониторинг с помощью настроенных ранее уведомлений по электронной почте либо активно просматривать события в журнале. Ниже приведены примеры инструкций Transact-SQL, которые используются для просмотра событий.  
  
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
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    -- to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 Шаги, описанные в этом разделе, специально предназначены для первой настройки [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] в базе данных. Можно изменить существующие конфигурации, используя ту же системную хранимую процедуру **smart_admin. sp_set_db_backup** и указав новые значения. Дополнительные сведения см. [в разделе SQL Server управляемое резервное копирование в Microsoft Azure параметры хранения и хранения](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).  
  
### <a name="enable-includess_smartbackupincludesss-smartbackup-mdmd-for-the-instance-with-default-settings"></a>Включите [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для экземпляра с параметрами по умолчанию  
 В этом руководстве описываются шаги по включению и [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] настройке для экземпляра «myInstance\\». В него входят шаги для включения мониторинга состояния работоспособности [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 **Разрешения**:  
  
-   Требуется членство в роли базы данных **db_backupoperator** с разрешениями **ALTER ANY CREDENTIAL** и `EXECUTE` разрешения на хранимую процедуру **sp_delete_backuphistory**.  
  
-   Требуются разрешения **SELECT** на функцию **smart_admin. fn_get_current_xevent_settings**.  
  
-   Требуются `EXECUTE` разрешения на хранимую процедуру **smart_admin. sp_get_backup_diagnostics** . Кроме того, необходимы разрешения `VIEW SERVER STATE`, так как процедура автоматически вызывает другие системные объекты, которым требуется это разрешение.  


1.  **Создайте учетную запись хранения Microsoft Azure:** Резервные копии хранятся в службе хранилища Microsoft Azure. Необходимо сначала создать учетную запись хранения Microsoft Azure, если у вас еще нет учетной записи.
    - SQL Server 2014 использует страничные большие двоичные объекты, которые отличаются от блочных и добавочных BLOB-объектов. Поэтому необходимо создать учетную запись общего назначения, а не учетную запись BLOB-объекта. Дополнительные сведения см. в статье [об учетных записях хранения Azure](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).
    - Запишите имя учетной записи хранения и ключи доступа. Имя учетной записи хранения и сведения о ключе доступа используются для создания учетных данных SQL. Учетные данные SQL используются для проверки подлинности учетной записи хранения.  
  
2.  **Создайте учетные данные SQL:** Создайте учетные данные SQL, используя имя учетной записи хранения в качестве удостоверения и ключ доступа к хранилищу в качестве пароля.  
  
3.  **Убедитесь в том, что служба агента SQL Server запущена и работает.** Запустите агент SQL Server, если он не запущен. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] требует, чтобы агент SQL Server был запущен на экземпляре.  Можно установить автоматический запуск агента SQL Server, чтобы обеспечить регулярное выполнение операций резервного копирования.  
  
4.  **Определение срока хранения.** Определите период хранения файлов резервной копии. Срок хранения указывается в днях и может принимать значение от 1 до 30. После включения [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] на уровне экземпляра с параметрами по умолчанию все новые базы данных, созданные позднее, будут наследовать эти параметры. Поддерживаются только базы данных, для которых установлена полная модель восстановления или модель восстановления с неполным протоколированием. Эти базы данных будут настраиваться автоматически. Можно отключить [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для конкретной базы данных в любое время, если настройка [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] не требуется. Кроме того, можно изменить конфигурацию для отдельной базы данных, настроив [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] на уровне базы данных.  
  
5.  **Включение и настройка [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].** Запустите SQL Server Management Studio и подключитесь к экземпляру SQL Server. В окне запроса выполните приведенную ниже инструкцию, предварительно задав нужные значения имени базы данных, учетных данных SQL, срока хранения и параметров шифрования.  
  
     Дополнительные сведения о создании сертификата для шифрования см. в разделе Создание **резервной копии сертификата** статьи [Создание зашифрованного резервного копирования](create-an-encrypted-backup.md).  
  
    ```  
    Use msdb;  
    Go  
       EXEC smart_admin.sp_set_instance_backup  
                     @enable_backup=1  
                    ,@retention_days=30   
                    ,@credential_name='sqlbackuptoURL'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert';  
    GO  
  
    ```  
  
     [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] теперь включен на экземпляре.  
  
6.  Проверьте параметры конфигурации, запустив следующую инструкцию Transact-SQL:  
  
    ```  
    Use msdb;  
    GO  
    SELECT * FROM smart_admin.fn_backup_instance_config ();  
  
    ```  
  
7.  Создайте новую базу данных на экземпляре. Запустите следующую инструкцию Transact-SQL, чтобы просмотреть параметры конфигурации [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для базы данных:  
  
    ```  
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('NewDB')  
    ```  
  
     Может потребоваться до 15 минут, прежде чем параметры отобразятся и начнут выполняться операции резервного копирования для базы данных.  
  
8.  **Включите и настройте уведомление о состоянии работоспособности.** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] входит хранимая процедура, создающая задание агента для отправки по электронной почте уведомлений об ошибках или предупреждений, которые могут требовать внимания пользователя.  Чтобы получать такие уведомления, необходимо включить запуск хранимой процедуры, которая создает задание агента SQL Server. Приведенные ниже шаги описывают процесс включения и настройки уведомлений по электронной почте.  
  
    1.  Настройте компонент Database Mail, если он еще не включен на экземпляре. Дополнительные сведения см. в разделе [Configure Database Mail](../database-mail/configure-database-mail.md).  
  
    2.  Настройте уведомления агента SQL Server для использования компонента Database Mail. Дополнительные сведения см. в статье [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  **Включите уведомления по электронной почте для получения ошибок и предупреждений, связанных с резервными копиями**. В окне запроса выполните следующие инструкции Transact-SQL:  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email address>'  
  
        ```  
  
         Дополнительные сведения о мониторинге и полный пример скрипта см. в разделе [monitor SQL Server управляемое резервное копирование в Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).  
  
9. **Просмотр файлов резервных копий в учетной записи хранения Microsoft Azure**. Подключитесь к учетной записи хранения из SQL Server Management Studio либо с помощью портала управления Azure. Вы увидите контейнер экземпляра SQL Server, в котором размещается база данных, настроенная на использование [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Кроме того, вы увидите базу данных и резервную копию журнала в течение 15 минут после создания новой базы данных.  
  
10. **Мониторинг состояния работоспособности**.  Можно вести мониторинг с помощью настроенных ранее уведомлений по электронной почте либо активно просматривать события в журнале. Ниже приведены примеры инструкций Transact-SQL, которые используются для просмотра событий.  
  
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
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    --  to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 Параметры [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] по умолчанию могут переопределяться для конкретной базы данных путем специальной настройки параметров на уровне базы данных. Кроме того, можно временно приостанавливать службу [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] и возобновлять ее выполнение. Дополнительные сведения см. [в разделе SQL Server управляемое резервное копирование в Microsoft Azure-параметры хранения и хранения](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md) .  
  
  
