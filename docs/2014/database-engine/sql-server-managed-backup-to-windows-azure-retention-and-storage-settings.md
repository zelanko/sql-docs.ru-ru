---
title: SQL Server управляемое резервное копирование в Windows Azure — хранение и параметры хранилища | Документация Майкрософт
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: c4aa26ea-5465-40cc-8b83-f50603cb9db1
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4b1087efba30ef65a3b4f7e00ed82031e7318b6d
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50100385"
---
# <a name="sql-server-managed-backup-to-windows-azure---retention-and-storage-settings"></a>Управляемое резервное копирование SQL Server в Windows Azure — настройки периода хранения и хранилища
  В этом разделе описаны базовые шаги настройки [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для базы данных, а также настройки параметров экземпляра по умолчанию. Здесь также описываются действия, необходимые для приостановки и возобновления служб [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для экземпляра.  
  
 Полное Пошаговое руководство по настройке [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] см. в разделе [Настройка SQL Server Managed Backup to Windows Azure](../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md) и [Настройка SQL Server Managed Backup to Windows Azure для групп доступности](../../2014/database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).  
  
 
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Не включайте [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] в базах данных, где используются планы обслуживания или доставка журналов. Дополнительные сведения о взаимодействие и совместная работа с другими компонентами SQL Server, см. в разделе [SQL Server Managed Backup to Windows Azure: взаимодействие и совместная работа](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Агент SQL Server должен быть запущен.  
  
    > [!WARNING]  
    >  Если агент SQL Server останавливаются на какой-то срок, а затем перезапускается, то можно видеть увеличение числа операций резервного копирования в зависимости от длительности промежутка времени между остановкой и запуском SQL Server Agent, а также может возникнуть очередь ожидающих выполнения операций резервного копирования журнала. Рекомендуется настроить автоматический запуск SQL Server Agent при включении системы.  
  
-   Учетная запись хранения Windows Azure и учетные данные SQL, которые сохраняют данные для проверки подлинности в учетной записи хранения, необходимо создать перед настройкой [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Дополнительные сведения см. в разделе [Introduction to Key Components and Concepts](../relational-databases/backup-restore/sql-server-backup-to-url.md#intorkeyconcepts) статьи **Резервное копирование SQL Server в URL** и [Lesson 2: Create a SQL Server Credential](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md).  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] создает необходимые контейнеры для хранения резервных копий. Имя контейнера формируется в формате «имя компьютера-имя экземпляра». Для групп доступности AlwaysOn имя контейнера формируется с использованием GUID группы доступности.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для запуска хранимых процедур, включающих [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], необходимо быть либо `System Administrator` или члена в **db_backupoperator** роли базы данных с **ALTER ANY CREDENTIAL** разрешения и `EXECUTE` разрешения на **sp_delete_backuphistory**, и `smart_admin.sp_backup_master_switch` хранимых процедур.  Для хранимых процедур и функций, используемых для просмотра имеющихся параметров, обычно требуются разрешения `Execute` для хранимой процедуры и `Select` для функции соответственно.  
  

  
###  <a name="Considerations"></a> Замечания по включению [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для баз данных и экземпляров  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] можно включить для отдельных баз данных или для всего экземпляра. Выбор зависит от требований восстановления для баз данных в экземпляре, требований к управлению несколькими базами данных и экземплярами и стратегического использования хранилища Windows Azure.  
  
#### <a name="enabling-includesssmartbackupincludesss-smartbackup-mdmd-at-the-database-level"></a>Включение [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] на уровне базы данных  
 Если в базе данных применяются определенные требования для резервного копирования и срока хранения (соглашение об уровне обслуживания для восстановления), отличные от других баз данных в экземпляре, настройте для нее [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] на уровне базы данных. Настройки на уровне базы данных переопределяют настройки на уровне экземпляра. Однако оба этих параметра можно использовать совместно в одном и том же экземпляре. Далее представлен список преимуществ и рекомендаций, связанных с включением [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] на уровне базы данных.  
  
-   Повышенная точность: раздельные параметры конфигурации для каждой базы данных. Возможность поддержки различных сроков хранения для отдельных баз данных.  
  
-   Переопределяет параметры уровня экземпляра для базы данных.  
  
-   Может использоваться для сокращения расходов на хранение за счет выбора отдельных баз данных для резервного копирования.  
  
-   Требует управления каждой базой данных  
  
#### <a name="enabling-includesssmartbackupincludesss-smartbackup-mdmd-at-the-instance-level-with-default-settings"></a>Включение [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] на уровне экземпляра с параметрами по умолчанию  
 Указывайте этот параметр, если большинство баз данных экземпляра имеют одинаковые требования к политикам резервного копирования и хранения или если нужно, чтобы при создании новых экземпляров баз данных для них автоматически создавались резервные копии. Несколько баз данных, являющихся исключением для политики, по-прежнему можно настроить отдельно. Далее представлен список преимуществ и рекомендаций, связанных с включением [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] на уровне экземпляра.  
  
-   Автоматизация на уровне экземпляра: общие параметры применяются автоматически после добавления новых баз данных.  
  
-   После создания новых баз данных в экземплярах для них автоматически создаются резервные копии  
  
-   Можно применять к базам данных с одинаковыми требованиями срока хранения.  
  
-   Можно настроить отдельные базы данных с разными сроками хранения, даже если функция [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] включена на уровне экземпляра с параметрами по умолчанию. Можно также отключить [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для баз данных, если не предполагается использовать хранилище Windows Azure для резервного копирования.  
  
##  <a name="DatabaseConfigure"></a> Включение и настройка [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для базы данных  
 Системная хранимая процедура `smart_admin.sp_set_db_backup` используется для включения компонента [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] в указанной базе данных. При первом включении компонента [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] в базе данных необходимо, помимо включения [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], указать следующие сведения:  
  
-   Имя базы данных.  
  
-   Срок хранения.  
  
-   Учетные данные SQL, используемые для проверки подлинности в учетной записи хранения Windows Azure.  
  
-   Укажите отсутствие шифрования с помощью *@encryption_algorithm*  =  **NO_ENCRYPTION** или укажите поддерживаемый алгоритм шифрования. Дополнительные сведения о шифровании см. в разделе [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).  
  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для настройки на уровне базы данных поддерживается только через Transact-SQL.  
  
 После включения [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для базы данных эти сведения сохраняются. При изменении конфигурации необходимы только имя базы данных и изменяемый параметр; службы [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] сохраняют существующие значения для прочих параметров, если они не указаны.  
  
> [!IMPORTANT]  
>  Перед настройкой функции [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для базы данных может быть полезно проверить наличие существующей конфигурации, если таковая имеется. Анализ параметров конфигурации для базы данных описывается далее в этом разделе.  
  
-   **С помощью Transact-SQL:**  
  
     Если вы включаете [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] в первый раз, — обязательные параметры: *@database_name*, *@credential_name*, *@encryption_algorithm*, *@enable_backup* *@storage_url* Параметр является необязательным. Если вы не укажете значение для @storage_url параметр, значением является производным, используя данные учетной записи хранения из учетных данных SQL. При предоставлении URL-адреса хранилища следует предоставлять только корневой URL-адрес для учетной записи хранения, который должен соответствовать предоставленным учетным данным SQL.  
  
    1.  Установите соединение с компонентом [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
    2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
    3.  Скопируйте и вставьте следующий пример в окно запроса и нажмите кнопку `Execute`. В данном примере функция [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] включается для базы данных TestDB. Срок хранения — 30 дней. Этот пример использует параметр шифрования с указанием алгоритма шифрования и сведений о шифраторе.  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='TestDB'   
                    ,@enable_backup=1  
                    ,@retention_days =30   
                    ,@credential_name ='MyCredential'  
                    ,@encryption_algorithm ='AES_256'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
    GO  
  
    ```  
  
    > [!IMPORTANT]  
    >  Для срока хранения может быть задано любое значение от 1 до 30 дней.  
    >   
    >  Дополнительные сведения о создании сертификата для шифрования см. в пункте «Создание резервной копии сертификата» в разделе [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).  
  
     Дополнительные сведения об этой хранимой процедуре см. в разделе [smart_admin.set_db_backup &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/dn451013(v=sql.120).aspx)  
  
     Чтобы просмотреть параметры конфигурации базы данных, используйте следующий запрос.  
  
    ```  
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('TestDB')  
    ```  
  
##  <a name="InstanceConfigure"></a> Включение и настройка по умолчанию [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] параметров для экземпляра  
 Можно включить и настроить по умолчанию [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] параметры на уровне экземпляра, двумя способами: С помощью системной хранимой процедуры `smart_backup.set_instance_backup` или **SQL Server Management Studio**. Далее описаны два этих способа.  
  
 **smart_backup.set_instance_backup:**. Путем указания значения **1** для *@enable_backup* параметр, можно включить резервное копирование и задать настройки по умолчанию. После применения параметров по умолчанию на уровне экземпляра они применяются к новой базе данных, добавляемой к этому экземпляру.  При первом включении компонента [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] необходимо, помимо включения [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] в экземпляре, указать следующие сведения:  
  
-   Срок хранения.  
  
-   Учетные данные SQL, используемые для проверки подлинности в учетной записи хранения Windows Azure.  
  
-   Параметр Encryption. Укажите отсутствие шифрования с помощью *@encryption_algorithm*  =  **NO_ENCRYPTION** или укажите поддерживаемый алгоритм шифрования. Дополнительные сведения о шифровании см. в разделе [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).  
  
 После активации эти настройки сохраняются. При изменении конфигурации необходимо указать только имя базы данных и имя настраиваемого параметра. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] сохраняет существующие значения, если не заданы новые.  
  
> [!IMPORTANT]  
>  Перед настройкой функции [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для экземпляра может быть полезно проверить наличие существующей конфигурации, если таковая имеется. Анализ параметров конфигурации для базы данных описывается далее в этом разделе.  
  
 **SQL Server Management Studio:** для выполнения этой задачи в среде SQL Server Management Studio перейдите в обозреватель объектов, разверните узел **Управление** и нажмите правой кнопкой мыши **Управляемое резервное копирование**. Выберите **Настройка**. Откроется диалоговое окно **Управляемое резервное копирование** . В этом диалоговом окне укажите срок хранения, учетные данные SQL, URL-адрес хранилища и параметры шифрования. Справку по этому диалоговому окну см. в разделе [Настройка управляемого резервного копирования &#40;SQL Server Management Studio&#41;](configure-managed-backup-sql-server-management-studio.md).  
  
#### <a name="using-transact-sql"></a>Использование Transact-SQL  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте и вставьте следующий пример в окно запроса и нажмите кнопку `Execute`.  
  
```  
Use msdb;  
Go  
   EXEC smart_admin.sp_set_instance_backup  
                @retention_days=30   
                ,@credential_name='sqlbackuptoURL'  
                ,@encryption_algorithm ='AES_128'  
                ,@encryptor_type= 'Certificate'  
                ,@encryptor_name='MyBackupCert'  
                ,@enable_backup=1;  
GO  
  
```  
  
> [!IMPORTANT]  
>  Для срока хранения может быть задано любое значение от 1 до 30 дней.  
>   
>  Дополнительные сведения о создании сертификата для шифрования см. в пункте «Создание резервной копии сертификата» в разделе [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).  
  
 Чтобы просмотреть параметры конфигурации по умолчанию для экземпляра, используйте следующий запрос.  
  
```  
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_instance_config ();  
  
```  
  
#### <a name="using-powershell"></a>Использование PowerShell  
  
1.  Запуск экземпляра PowerShell  
  
2.  Запустите следующий скрипт, изменив его в соответствии с собственными настройками  
  
    ```  
    C:\ PS> cd SQLSERVER:\SQL\Computer\MyInstance   
    $encryptionOption = New-SqlBackupEncryptionOption -EncryptionAlgorithm Aes128 -EncryptorType ServerCertificate -EncryptorName "MyBackupCert"  
    Get-SqlSmartAdmin | Set-SqlSmartAdmin –BackupEnabled $True –BackupRetentionPeriodInDays 10 -EncryptionOption $encryptionOption  
    ```  
  
> [!IMPORTANT]  
>  При создании базы данных после настройки параметров по умолчанию для их применения может потребоваться до 15 минут. Это также применимо к базам данных, измененных с **Simple** на **Full** модель восстановления или на **Bulk-Logged** .  
  
##  <a name="DatabaseDisable"></a> Отключение [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для базы данных  
 Настройки [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] можно отключить с помощью системной хранимой процедуры `sp_set_db_backup`. *@enableparameter* Используется для включения и отключения [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] конфигурации для конкретной базы данных, при этом значение 1 включает, а значение 0 отключает параметры конфигурации.  
  
#### <a name="to-disable-includesssmartbackupincludesss-smartbackup-mdmd-for-a-specific-database"></a>Чтобы отключить [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для конкретной базы данных, выполните следующие действия.  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте и вставьте следующий пример в окно запроса и нажмите кнопку `Execute`.  
  
```  
Use msdb;  
Go  
EXEC smart_admin.sp_set_db_backup   
                @database_name='TestDB'   
                ,@enable_backup=0;  
GO  
  
```  
  
##  <a name="DatabaseAllDisable"></a> Отключение [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для всех баз данных в экземпляре  
 Следующая процедура позволяет отключить параметры конфигурации [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для всех баз данных, для которых функция [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] включена в экземпляре.  Такие параметры конфигурации, как URL-адрес хранилища, политика хранения и учетные данные SQL, сохранятся в метаданных, и их можно будет использовать, если функция [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] будет включена для базы данных в дальнейшем. Если нужно просто временно приостановить службы [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] , то можно вызвать основной переключатель, описанный далее в этом разделе.  
  
#### <a name="to-disable-includesssmartbackupincludesss-smartbackup-mdmdfor-all-the-databases"></a>Чтобы отключить [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]для всех баз данных, выполните следующие действия.  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте и вставьте следующий пример в окно запроса и нажмите кнопку `Execute`. Следующий пример определяет, настроена ли функция [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] на уровне экземпляра и во всех базах данных с активированной функцией [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], а затем выполняет хранимую процедуру `sp_set_db_backup` для отключения [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
```  
-- Create a working table to store the database names  
Declare @DBNames TABLE  
  
       (  
             RowID int IDENTITY PRIMARY KEY  
             ,DBName varchar(500)  
  
       )  
-- Define the variables  
DECLARE @rowid int  
DECLARE @dbname varchar(500)  
DECLARE @SQL varchar(2000)  
-- Get the database names from the system function  
  
INSERT INTO @DBNames (DBName)  
  
SELECT db_name  
       FROM   
  
       smart_admin.fn_backup_db_config (NULL)  
       WHERE is_smart_backup_enabled = 1  
  
       --Select DBName from @DBNames  
  
       select @rowid = min(RowID)  
       FROM @DBNames  
  
       WHILE @rowID IS NOT NULL  
       Begin  
  
             Set @dbname = (Select DBName From @DBNames Where RowID = @rowid)  
             Begin  
             Set @SQL = 'EXEC smart_admin.sp_set_db_backup    
                @database_name= '''+'' + @dbname+ ''+''',   
                @enable_backup=0'  
  
            EXECUTE (@SQL)  
  
             END  
             Select @rowid = min(RowID)  
             From @DBNames Where RowID > @rowid  
  
       END  
  
```  
  
 Чтобы просмотреть параметры конфигурации для всех баз данных в экземпляре, выполните следующий запрос.  
  
```  
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_db_config (NULL);  
GO  
  
```  
  
##  <a name="InstanceDisable"></a> Отключение параметров [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] по умолчанию для экземпляра  
 Параметры по умолчанию на уровне экземпляра применяются ко всем новым базам данных, созданным в этом экземпляре.  Если параметры по умолчанию больше не нужны, то можно отключить эту конфигурацию с помощью системной хранимой процедуры **smart_admin.sp_set_instance_backup** . При отключении остальные параметры конфигурации, такие как URL-адрес хранилища, политика хранения или учетные данные SQL, не удаляются. Эти настройки используются в том случае, если функция [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] будет включена для экземпляра позднее.  
  
#### <a name="to-disable-includesssmartbackupincludesss-smartbackup-mdmd-default-configuration-settings"></a>Чтобы отключить параметры конфигурации [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] по умолчанию, выполните следующие действия.  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте и вставьте следующий пример в окно запроса и нажмите кнопку `Execute`.  
  
    ```  
    Use msdb;  
    Go  
    EXEC smart_admin.sp_set_instance_backup  
                    @enable_backup=0;  
    GO  
  
    ```  
  
#### <a name="using-powershell"></a>Использование PowerShell  
  
1.  Запуск экземпляра PowerShell  
  
2.  Выполните следующий скрипт:  
  
    ```  
    C:\ PS> cd SQLSERVER:\SQL\Computer\MyInstance   
    Set-SqlSmartAdmin –BackupEnabled $False  
    ```  
  
##  <a name="InstancePause"></a> Приостановка [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] на уровне экземпляра  
 Возможны ситуации, когда требуется приостановить службы [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] на короткий период времени.  Системная хранимая процедура `smart_admin.sp_backup_master_switch` позволяет отключить службу [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] на уровне экземпляра.  Та же хранимая процедура используется для возобновления [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Параметр @state определяет, следует ли включить или отключить [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
#### <a name="to-pause-includesssmartbackupincludesss-smartbackup-mdmd-services-using-transact-sql"></a>Чтобы приостановить службы [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] с помощью Transact-SQL, выполните следующие действия.  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте и вставьте следующий пример в окно запроса и нажмите кнопку `Execute`  
  
```  
Use msdb;  
GO  
EXEC smart_admin.sp_backup_master_switch @new_state=0;  
Go  
  
```  
  
#### <a name="to-pause-includesssmartbackupincludesss-smartbackup-mdmd-using-powershell"></a>Приостановка [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] с помощью PowerShell  
  
1.  Запуск экземпляра PowerShell  
  
2.  Запустите следующий скрипт, изменив его в соответствии с собственными настройками  
  
    ```  
    C:\ PS> cd SQLSERVER:\SQL\Computer\MyInstance   
    Get-SqlSmartAdmin | Set-SqlSmartAdmin –MasterSwitch $False  
    ```  
  
#### <a name="to-resume-includesssmartbackupincludesss-smartbackup-mdmd-using-transact-sql"></a>Как возобновить [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] с помощью Transact-SQL  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте и вставьте следующий пример в окно запроса и нажмите кнопку `Execute`.  
  
```  
Use msdb;  
Go  
EXEC smart_admin. sp_backup_master_switch @new_state=1;  
GO  
  
```  
  
#### <a name="to-resume-includesssmartbackupincludesss-smartbackup-mdmd-using-powershell"></a>Возобновление [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] с помощью PowerShell  
  
1.  Запуск экземпляра PowerShell  
  
2.  Запустите следующий скрипт, изменив его в соответствии с собственными настройками  
  
    ```  
    C:\ PS> cd SQLSERVER:\SQL\Computer\MyInstance   
    Get-SqlSmartAdmin | Set-SqlSmartAdmin –MasterSwitch $True  
    ```  
  
  
