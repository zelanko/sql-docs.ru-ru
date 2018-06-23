---
title: Настройка SQL Server Managed Backup to Windows Azure для группы доступности | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4553cd-d8e4-4691-963a-4e414cc0f1ba
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8a367b7835b08c9a5b2b7226b8f3e4d127235487
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190053"
---
# <a name="setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups"></a>Настройка управляемого резервного копирования SQL Server в Windows Azure для групп доступности
  В этом разделе представлено руководство по настройке [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для баз данных, участвующих в группах доступности AlwaysOn.  
  
## <a name="availability-group-configurations"></a>Конфигурации групп доступности  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] поддерживается для баз данных групп доступности независимо от того, настроены ли все реплики локально, полностью в Windows Azure, или реализовано гибридное решение между локальным компьютером и одной или несколькими виртуальными машинами Windows Azure. Однако для одной или нескольких реализаций можно рассмотреть следующие аспекты.  
  
-   Интервал резервного копирования журналов: Частоты резервного копирования журнала является увеличение времени и журнала. Например, резервная копия журнала создается каждые 2 часа, если только объем журнала не превысил в течение этих двух часов 5 МБ. Это относится ко всем реализациям: локальным, облачным или гибридным.  
  
-   Пропускная способность сети: Это относится к реализации, где реплики находятся в разных местах, как в гибридном облаке или в разных регионах Windows Azure в облаке только конфигурации. Пропускная способность сети может повлиять на задержку баз данных-получателей, а также в случае, если в базах данных-получателях настроена синхронная репликация, что может привести к увеличению объема журнала в базе данных-источнике. Если в базах данных-получателях настроена синхронная репликация, то из-за задержки в сети они могут не успевать, что может привести к потере данных в случае переключения на вторичную реплику.  
  
### <a name="configuring-includesssmartbackupincludesss-smartbackup-mdmd-for-availability-databases"></a>Настройка [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для баз данных доступности.  
 **Разрешения:**  
  
-   Требуется членство в **db_backupoperator** роли базы данных с **ALTER ANY CREDENTIAL** разрешения, и `EXECUTE` разрешения на **sp_delete_backuphistory**хранимой процедуры.  
  
-   Требуется **ВЫБЕРИТЕ** разрешения на **smart_admin.fn_get_current_xevent_settings**функции.  
  
-   Требуется `EXECUTE` разрешения на **smart_admin.sp_get_backup_diagnostics** хранимой процедуры. Кроме того, необходимы разрешения `VIEW SERVER STATE`, так как процедура автоматически вызывает другие системные объекты, которым требуется это разрешение.  
  
-   Требуется `EXECUTE` разрешения на `smart_admin.sp_set_instance_backup` и `smart_admin.sp_backup_master_switch` хранимых процедур.  
  
 Ниже приведены основные шаги по настройке группы доступности AlwaysOn с [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Подробное пошаговое руководство описано далее в этом разделе.  
  
1.  После того как создана группа доступности, следует настроить предпочтительную реплику резервного копирования. Этот параметр для группы доступности также используется [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для определения реплики, используемой для резервного копирования. Пошаговые инструкции для настройки резервного копирования см. в разделе [настроить архивацию на репликах доступности &#40;SQL Server&#41;](availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).  При создании новой группы доступности AlwaysOn в разделе [Приступая к работе с группами доступности AlwaysOn &#40;SQL Server&#41;](availability-groups/windows/getting-started-with-always-on-availability-groups-sql-server.md).  
  
2.  Настройте доступ через соединение только для чтения к вторичным репликам. Пошаговые инструкции о том, как настроить доступ только для чтения, см. в разделе [Настройка доступа только для чтения в реплике доступности &#40;SQL Server&#41;](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
3.  Укажите реплику резервного копирования. С помощью параметра, указывающего предпочтительную реплику резервного копирования, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] определяет, какую базу данных выбрать для планирования резервного копирования.  Чтобы определить, является ли текущая реплика предпочитаемой репликой резервного копирования, используйте [sys.fn_hadr_backup_is_preferred_replica &#40;Transact-SQL&#41; ](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) функции.  
  
4.  На каждой реплике запустите [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] конфигурации для базы данных с помощью **смарт admin.sp_set_db_backup** хранимой процедуры.  
  
     **[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] поведение после отработки отказа:** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] продолжит работу и сохранит резервные копии и возможность восстановления после отработки отказа. После отработки отказа никакие особые действия не требуются.  
  
#### <a name="considerations-and-requirements"></a>Рекомендации и требования  
 Настройка [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для баз данных, участвующих в группах доступности AlwaysOn, требует соблюдения определенных требований. Ниже приведен список соображений и требований.  
  
-   Параметры конфигурации [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] должны быть одинаковыми для всех баз данных на всех узлах [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], участвующих в одной группе доступности. Этого можно добиться, задавая одинаковые конфигурации [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для основной базы данных и всех реплик на уровне базы данных или задавая одинаковые параметры [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] по умолчанию на всех узлах, участвующих в группе доступности. Рекомендуется настраивать [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для базы данных, поскольку настройка [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] на уровне базы данных позволяет изолировать параметры в базах данных, а изменения параметров по умолчанию влияют на все другие базы данных в экземпляре.  
  
-   Укажите реплику резервного копирования. Предпочитаемая реплика резервного копирования используется [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для планирования резервного копирования. Чтобы определить, является ли текущая реплика предпочитаемой репликой резервного копирования, используйте [sys.fn_hadr_backup_is_preferred_replica &#40;Transact-SQL&#41; ](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) функции.  
  
-   Если в качестве предпочтительной реплики настраивается вторичная реплика, ей должен быть назначен хотя бы доступ через соединение только для чтения. Группы доступности, у которых нет доступа к соединению с базами данных-получателями, не поддерживаются.  Дополнительные сведения см. в статье [Настройка доступа только для чтения в реплике доступности (SQL Server)](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md).  
  
-   Если вы настраиваете [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] после того, как была настроена группа доступности, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] пытается скопировать любые имеющиеся резервные копии в контейнер хранилища.  Если [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] не удается найти либо нет доступа к имеющимся резервным копиям, будет запланировано полное резервное копирование базы данных. Это сделано специально для оптимизации операций резервного копирования для баз данных группы доступности.  
  
-   Возможно, следует рассмотреть возможность отключения параметров на уровне экземпляра, если вы создаете новую базы данных доступности и не планируете применять к ней параметры уровня экземпляра.  
  
-   При использовании шифрования применяйте один и тот же сертификат на всех репликах. Это облегчает непрерывное выполнение резервного копирования при отработке отказа или восстановления на другую реплику.  
  
#### <a name="enable-and-configure-includesssmartbackupincludesss-smartbackup-mdmd-for-an-availability-database"></a>Включение и настройка [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для базы данных доступности  
 В этом учебнике приведены шаги по включению и настройке [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для базы данных (AGTestDB) на компьютерах «Node1» и «Node2», затем приведены шаги по включению наблюдения за состоянием работоспособности [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
1.  **Создать учетную запись хранилища Windows Azure:** резервных копий в службе хранилища больших двоичных объектов Windows Azure. Необходимо сначала создать учетную запись хранения службы Azure, если это еще не сделано. Дополнительные сведения см. в разделе [Создание учетной записи хранилища Windows Azure](http://www.windowsazure.com/manage/services/storage/how-to-create-a-storage-account/). Запишите имя учетной записи хранения, ключи доступа и URL-адрес учетной записи хранения. Имя учетной записи хранения и сведения о ключе доступа используются для создания учетных данных SQL. Учетные данные SQL используются в [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] во время операций с резервными копиями для проверки подлинности учетной записи хранения.  
  
2.  **Создание учетных данных SQL:** создайте учетные данные SQL, используя имя учетной записи хранения, как удостоверения и ключ доступа к хранилищу в качестве пароля.  
  
3.  **Убедитесь, что служба агента SQL Server запущена и работает.** Запустите агент SQL Server, если он еще не запущен. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] требует, чтобы агент SQL Server был запущен на экземпляре.  Можно установить автоматический запуск агента SQL Server, чтобы обеспечить регулярное выполнение операций резервного копирования.  
  
4.  **Определите срок хранения:** определите срок хранения для файлов резервных копий. Срок хранения указывается в днях и может принимать значение от 1 до 30. Срок хранения определяет интервал времени восстановления для базы данных.  
  
5.  **Создайте сертификат или асимметричный ключ, используемый для шифрования резервной:** создать сертификат на первом узле Node1, а затем экспортируйте его в файл с помощью [резервной копии сертификата &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql)... На узле Node 2 создайте сертификат с помощью файла, экспортированного с Node 1. Дополнительные сведения о создании сертификата из файла см. пример в [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).  
  
6.  **Включение и настройка [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для AGTestDB на Node1:** запустите SQL Server Management Studio и подключитесь к экземпляру на Node1, где установлена база данных доступности. В окне запроса выполните приведенную ниже инструкцию, предварительно задав значения имени базы данных, URL-адреса хранилища, учетных данных SQL и срока хранения.  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='AGTestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
  
    ```  
  
     Дополнительные сведения о создании сертификата для шифрования см. в разделе **создайте сертификат резервной копии** шага в [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).  
  
7.  **Включение и настройка [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для AGTestDB на Node2:** запустите SQL Server Management Studio и подключитесь к экземпляру на Node2, где установлена база данных доступности. В окне запроса выполните приведенную ниже инструкцию, предварительно задав значения имени базы данных, URL-адреса хранилища, учетных данных SQL и срока хранения.  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='AGTestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
  
    ```  
  
     [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] включено на указанной базе данных. Может потребоваться до 15 минут, прежде чем начнут выполняться операции резервного копирования для базы данных. Резервные копии будут появляться на предпочтительной реплике резервного копирования.  
  
8.  **Просмотрите конфигурацию по умолчанию расширенных событий:** Просмотр конфигурации расширенных событий, выполнив следующую инструкцию transact-SQL на реплике [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] с которой планирует резервное копирование. Обычно это параметр предпочтительной реплики для группы доступности, к которой принадлежит база данных.  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     Обратите внимание, что события каналов Admin, Operational и Analytical включены по умолчанию и их нельзя отключить. Этого должно быть достаточно для наблюдения за событиями, требующими ручного вмешательства.  Можно включить события отладки, но эти каналы содержат информационные и отладочные события, которые [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] использует для обнаружения и устранения проблем. Дополнительные сведения см. в разделе [монитора SQL Server Managed Backup to Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
9. **Enable and Configure Notification for Health Status:** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] has a stored procedure that creates an agent job to send out e-mail notifications of errors or warnings that may require attention.  Чтобы получать такие уведомления, необходимо включить запуск хранимой процедуры, которая создает задание агента SQL Server. Приведенные ниже шаги описывают процесс включения и настройки уведомлений по электронной почте.  
  
    1.  Настройте компонент Database Mail, если он еще не включен на экземпляре. Дополнительные сведения см. в разделе [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md).  
  
    2.  Настройте уведомления агента SQL Server для использования компонента Database Mail. Дополнительные сведения см. в статье [Configure SQL Server Agent Mail to Use Database Mail](../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  **Включите уведомления по электронной почте для получения сообщений об ошибках и предупреждений, связанных с резервным копированием.** В окне запроса выполните следующие инструкции Transact-SQL:  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email>'  
  
        ```  
  
         Дополнительные сведения и полный пример скрипта см. [монитора SQL Server Managed Backup to Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
10. **Просмотрите файлы резервных копий в учетной записи хранилища Windows Azure:** подключитесь к учетной записи хранения из SQL Server Management Studio или портала управления Azure. Вы увидите контейнер экземпляра SQL Server, в котором размещается база данных, настроенная на использование [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Кроме того, можно настроить базу данных и резервное копирование журналов за 15 минут либо включить [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для базы данных.  
  
11. **Отслеживайте состояние работоспособности.**  Вы можете использовать для мониторинга настроенные ранее уведомления по электронной почте либо активно отслеживать события в журнале. Ниже приведены примеры инструкций Transact-SQL, которые используются для просмотра событий.  
  
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
    event varchar (512),  
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
  
 Шаги, описанные в этом разделе, специально предназначены для первой настройки [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] в базе данных. Можно изменить существующие конфигурации с помощью той же системной хранимой процедуре **smart_admin.sp_set_db_backup** и указывать новые значения. Дополнительные сведения см. в разделе [SQL Server Managed Backup to Windows Azure — хранения и настройки хранилищ](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).  
  
### <a name="considerations-when-removing-a-database-from-alwayson-availability-group-configuration"></a>Соображения по удалению базы данных из конфигурации группы доступности AlwaysOn  
 Если база данных удаляется из конфигурации группы доступности AlwaysOn и становится автономной базой данных, рекомендуется делать резервную копию с помощью [smart_admin.sp_backup_on_demand &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql). При создании резервной копии базы данных таким образом формируется новая цепочка резервного копирования, а файл помещается в контейнер конкретного экземпляра в отличие от контейнера доступности, в котором хранятся резервные копии, если база данных является частью группы доступности.  
  
> [!WARNING]  
>  В этом сценарии возможность восстановления базы данных из резервных копий, созданных до изменения состояния группы доступности, не гарантируется.  
  
  
