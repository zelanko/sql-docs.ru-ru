---
title: Резервное копирование в SQL Server по URL-адресу — рекомендации и устранение неполадок | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: backup-restore
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de676bea-cec7-479d-891a-39ac8b85664f
caps.latest.revision: 26
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 305b5c00edd3f1a2549bbfaa6080d1fd37aa4103
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sql-server-backup-to-url-best-practices-and-troubleshooting"></a>Резервное копирование SQL Server на URL-адрес — рекомендации и устранение неполадок
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этом разделе рассматриваются рекомендации и советы по устранению неполадок SQL Server при создании резервных копий и восстановлении с помощью службы хранилища больших двоичных объектов Windows Azure.  
  
 Дополнительную информацию по использованию службы хранилища больших двоичных объектов Windows Azure для операций резервного копирования или восстановления SQL Server см. в разделах:  
  
-   [Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
-   [Tutorial: SQL Server Backup and Restore to Windows Azure Blob Storage Service](~/relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="managing-backups"></a>Управление резервными копиями  
 В следующем списке перечислены общие рекомендации по управлению резервным копированием.  
  
-   Рекомендуется присваивать каждому файлу уникальное имя, чтобы предотвратить случайное перезаписывание больших двоичных объектов.  
  
-   При создании контейнера рекомендуется установить уровень доступа **private**, чтобы большие двоичные объекты в контейнере могли читать или записывать только те пользователи или учетные записи, которые предоставили необходимую информацию для проверки подлинности.  
  
-   При работе с базами данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], размещенными в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который установлен на виртуальной машине Windows Azure, используйте учетную запись хранилища в том же регионе, где находится виртуальная машина, чтобы избежать издержек, связанных с передачей данных между регионами. Использование одного региона также обеспечивает оптимальную производительность операций резервного копирования и восстановления.  
  
-   Сбой во время резервного копирования может привести к созданию неработоспособного файла резервной копии. Рекомендуется периодически проводить поиск неудачных резервных копий и удалять файлы больших двоичных объектов. Дополнительные сведения см. в разделе [Deleting Backup Blob Files with Active Leases](../../relational-databases/backup-restore/deleting-backup-blob-files-with-active-leases.md).  
  
-   Использование параметра `WITH COMPRESSION` во время резервного копирования может уменьшить стоимость хранения и транзакционные издержки хранения. Также может сократиться время, необходимое для выполнения резервного копирования.  

- Задайте аргументы `MAXTRANSFERSIZE` и `BLOCKSIZE`, как указано в разделе [Резервное копирование в SQL Server по URL-адресу](./sql-server-backup-to-url.md).
  
## <a name="handling-large-files"></a>Обработка больших файлов  
  
-   Операция резервного копирования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется в несколько потоков, чтобы оптимизировать передачу данных к службам хранилищ больших двоичных объектов Windows Azure.  Однако производительность зависит от различных факторов, в том числе от пропускной способности ISV и размера базы данных. Если планируется создавать резервные копии больших баз данных или файловых групп в локальной базе данных SQL Server, вначале рекомендуется проверить пропускную способность. В [соглашении об уровне обслуживания для службы хранилища Azure](http://azure.microsoft.com/support/legal/sla/storage/v1_0/) определены максимальные значения времени обработки для больших двоичных объектов, которыми можно руководствоваться.  
  
-   При создании резервных копий больших файлов очень важно использовать параметр `WITH COMPRESSION` в соответствии с рекомендациями, приведенными в разделе [Управление резервным копированием](##managing-backups).  
  
## <a name="troubleshooting-backup-to-or-restore-from-url"></a>Устранение неполадок при резервном копирование или восстановлении по URL-адресу  
 Ниже приведено несколько простых способов устранения ошибок при создании резервной копии или восстановлении из службы хранилища больших двоичных объектов Windows Azure.  
  
 Чтобы избежать ошибок из-за неподдерживаемых параметров или ограничений, просмотрите список ограничений и информацию о поддержке для команд BACKUP и RESTORE в статье [Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) .  
  
 **Ошибки проверки подлинности:**  
  
-   `WITH CREDENTIAL` — это новый параметр, который нужно использовать при создании резервных копий или восстановлении с помощью службы хранилища больших двоичных объектов Microsoft Azure. Ниже приводятся возможные ошибки, связанные с учетными данными.  
  
     Учетные данные, заданные в команде **BACKUP** или **RESTORE** , не существуют. Чтобы избежать этой проблемы, можно включить инструкцию T-SQL для создания учетных данных, если она отсутствует в инструкции резервного копирования. Ниже приводится пример, который можно использовать.  
  
    ```sql  
    IF NOT EXISTS  
    (SELECT * FROM sys.credentials   
    WHERE credential_identity = 'mycredential')  
    CREATE CREDENTIAL <credential name> WITH IDENTITY = 'mystorageaccount'  
    ,SECRET = '<storage access key> ;  
    ```  
  
-   Учетные данные существуют, но учетная запись, которая используется для запуска команды резервного копирования, не имеет разрешения доступа к учетным данным. Используйте учетную запись для входа в роль **db_backupoperator** с разрешением ***Изменение любых учетных данных*** .  
  
-   Проверьте имя учетной записи хранилища и значение ключа. Информация, которая хранится в учетных данных, должна соответствовать значениям свойств учетной записи хранилища Windows Azure, которые используются в операциях резервного копирования и восстановления.  
  
 **Ошибки и сбои резервного копирования:**  
  
-   Параллельное выполнение резервного копирования в один большой двоичный объект вызывает сбой одной из резервных копий с ошибкой **Ошибка инициализации** .  
  
-   Используйте следующие журналы об ошибке, чтобы помочь при устранении неполадок в резервных ошибках:  
  
    -   Установите флаг трассировки 3051, чтобы включить ведение записей в конкретном журнале ошибок в следующем формате:  
  
        `BackupToUrl-\<instname>-\<dbname>-action-\<PID>.log` где `\<action>` является одним из следующих:  
  
        -   **DB**  
        -   **FILELISTONLY**  
        -   **LABELONLY**  
        -   **HEADERONLY**  
        -   **VERIFYONLY**  
  
    -   Дополнительную информацию можно найти в журнале событий Windows или в журналах приложений с именем `SQLBackupToUrl`.  
  
-   При восстановлении из сжатой резервной копии может появиться следующее сообщение об ошибке:  
  
    -   `SqlException 3284 occurred. Severity: 16 State: 5  
        Message Filemark on device 'https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_0.bak' is not aligned.           Reissue the Restore statement with the same block size used to create the backupset: '65536' looks like a possible value.`  
  
        Чтобы устранить эту ошибку, издайте инструкцию **BACKUP** повторно и укажите для нее значение **BLOCKSIZE = 65536** .  
  
-   Ошибка во время архивации из-за больших двоичных объектов с активной арендой: сбой операции архивации может привести к появлению больших двоичных объектов с активными арендами.  
  
     Если эта инструкция резервного копирования повторяется, то операция резервного копирования может завершиться со следующей ошибкой:  
  
     `Backup to URL received an exception from the remote endpoint. Exception Message: The remote server returned an error: (412) There is currently a lease on the blob and no lease ID was specified in the request.`  
  
     Если инструкция восстановления выполнялись в резервном файле большого двоичного объекта с активной арендой, операция резервного копирования может завершиться со следующей ошибкой:  
  
     `Exception Message: The remote server returned an error: (409) Conflict..`  
  
     Если возникает такая ошибка, файлы больших двоичных объектов следует удалить. Дополнительные сведения об этом сценарии и устранении этой проблемы см. в разделе [Deleting Backup Blob Files with Active Leases](../../relational-databases/backup-restore/deleting-backup-blob-files-with-active-leases.md).  
  
## <a name="proxy-errors"></a>Ошибки прокси-сервера  
 При использовании прокси-серверов для доступа к Интернету возможны следующие проблемы.  
  
 **Регулирование соединений прокси-серверами.**  
  
 Прокси-серверы могут иметь параметры, ограничивающие количество соединений в минуту. Процесс резервного копирования на URL-адрес является многопоточным, в связи с чем заданное ограничение может быть превышено. В этом случае прокси-сервер разрывает соединение. Чтобы устранить эту проблему, измените параметры прокси-сервера таким образом, чтобы SQL Server его не использовал. Далее приведено несколько примеров типов или сообщений об ошибках, которые можно встретить в журнале ошибок.  
  
```
Write on "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak" failed: Backup to URL received an exception from the remote endpoint. Exception Message: Unable to read data from the transport connection: The connection was closed.
```  
  
```
A nonrecoverable I/O error occurred on file "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak:" Error could not be gathered from Remote Endpoint.  
  
Msg 3013, Level 16, State 1, Line 2  
  
BACKUP DATABASE is terminating abnormally.  
```

```
BackupIoRequest::ReportIoError: write failure on backup device http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak'. Operating system error Backup to URL received an exception from the remote endpoint. Exception Message: Unable to read data from the transport connection: The connection was closed.
```  
  
Если включить подробный уровень ведения журнала с помощью флага трассировки 3051, то в журналы также может быть занесено следующее сообщение.  
  
`HTTP status code 502, HTTP Status Message Proxy Error (The number of HTTP requests per minute exceeded the configured limit. Contact your ISA Server administrator.) ` 
  
 **Параметры прокси-сервера по умолчанию не используются.**  
  
Иногда, если не выбраны параметры по умолчанию, это приводит к ошибкам проверки подлинности на прокси-сервере наподобие следующей:
 
 `A nonrecoverable I/O error occurred on file "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak:" Backup to URL received an exception from the remote endpoint. Exception Message: The remote server returned an error: (407)* **Proxy Authentication Required.`  
  
Чтобы устранить эту проблему, создайте файл конфигурации, позволяющий процессу резервного копирования по URL-адресу использовать параметры прокси-сервера по умолчанию. Для этого выполните следующие действия.  
  
1.  Создайте файл конфигурации `BackuptoURL.exe.config` со следующим XML-кодом:  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>   
                    <system.net>   
                                    <defaultProxy enabled="true" useDefaultCredentials="true">   
                                                    <proxy usesystemdefault="true" />   
                                    </defaultProxy>   
                    </system.net>  
    </configuration>  
    ```  
  
2.  Поместите файл конфигурации в папку Binn на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Например, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлен на диске C компьютера, поместите файл конфигурации в `C:\Program Files\Microsoft SQL Server\MSSQL13.\<InstanceName>\MSSQL\Binn`.  
  
## <a name="see-also"></a>См. также:  
 [Восстановление из резервных копий в Microsoft Azure](../../relational-databases/backup-restore/restoring-from-backups-stored-in-microsoft-azure.md)  
[BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)  
[RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)
  
