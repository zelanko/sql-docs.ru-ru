---
title: Подготовка зеркальной базы данных к зеркальному отображению (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], preparing for mirroring
- logins [SQL Server], database mirroring
- mirror database [SQL Server]
ms.assetid: 8676f9d8-c451-419b-b934-786997d46c2b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 844879c0e1b02bc9b6fd88ab153cb2a5dbd6ebe6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48130084"
---
# <a name="prepare-a-mirror-database-for-mirroring-sql-server"></a>Подготовка зеркальной базы данных к зеркальному отображению (SQL Server)
  Перед началом сеанса зеркального отображения базы данных ее владелец или системный администратор должен убедиться, что зеркальная база данных создана и готова к работе. Чтобы создать новую зеркальную базу данных, требуется как минимум наличие полной резервной копии основной базы данных и последующих резервных копий журналов. Они восстанавливаются на экземпляре зеркального сервера с параметром WITH NORECOVERY.  
  
 В этом разделе описано, как подготовить зеркальную базу данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Requirements"></a> Требования  
  
-   На основном сервере и на экземплярах зеркального сервера должна работать одна и та же версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для зеркального сервера возможна более поздняя версия SQL Server, но эта конфигурация рекомендуется только во время процесса тщательно спланированного обновления. В такой конфигурации есть риск автоматического перехода на другой ресурс, в котором движение данных автоматически приостанавливается, так как данные нельзя переместить на более раннюю версию SQL Server. Дополнительные сведения см. в разделе [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md).  
  
-   На основном сервере и на экземплярах зеркального сервера должен работать один и тот же выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения о зеркальном отображении базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] см. в разделе [Функции, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
-   База данных должна использовать модель полного восстановления.  
  
     Дополнительные сведения см. в статьях [Просмотр или изменение модели восстановления базы данных (SQL Server)](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md) или [sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) и [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql).  
  
-   Имя зеркальной базы данных должно совпадать с именем основной базы данных.  
  
-   Для работы зеркального отображения необходимо, чтобы зеркальная база данных находилась в состоянии RESTORING. При подготовке зеркальной базы данных необходимо использовать инструкцию RESTORE WITH NORECOVERY для каждой операции восстановления. Как минимум необходимо восстановить с параметром WITH NORECOVERY полную резервную копию основной базы данных, а затем все последующие резервные копии журналов.  
  
-   В системе, где предполагается создать зеркальную базу данных, должен быть жесткий диск, на котором достаточно свободного места.  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Зеркальное отображение системных баз данных **master**, **msdb**, **temp**и **model** невозможно.  
  
-   Нельзя осуществлять зеркальное отображение базы данных, к которой принадлежит [группы доступности AlwaysOn (SQL Server)](../availability-groups/windows/always-on-availability-groups-sql-server.md).  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Используйте либо самую последнюю полную копию базы данных, либо разностную резервную копию основной базы данных.  
  
-   Если запланировано частое выполнение задания резервного копирования журналов основной базы данных, то, возможно, его придется отключить до запуска зеркального отображения.  
  
-   Желательно, чтобы путь зеркальной базы данных (включая имя диска) был идентичен пути основной базы данных.  
  
     Если пути к файлам должны различаться, например если основная база данных расположена на диске «F:», а в зеркальной системе нет диска «F:», необходимо включить в инструкцию RESTORE параметр MOVE.  
  
    > [!IMPORTANT]  
    >  Добавление файлов во время сеанса зеркального отображения без влияния на сеанс требует, чтобы путь к файлам существовал на обоих серверах. Поэтому перемещение файлов базы данных во время создания зеркального отображения может привести к его ошибке или остановке при выполнении операции добавления файла. Дополнительные сведения об обработке ошибок операции создания файла см. в статье [Диагностика конфигурации зеркального отображения базы данных (SQL Server)](troubleshoot-database-mirroring-configuration-sql-server.md).  
  
-   Если основная база данных содержит любые полнотекстовые каталоги, см. статью [Зеркальное отображение баз данных и полнотекстовые каталоги (SQL Server)](database-mirroring-and-full-text-catalogs-sql-server.md).  
  
-   Для производственной базы данных необходимо всегда создавать резервные копии на разных устройствах.  
  
###  <a name="Security"></a> безопасность  
 Параметр TRUSTWORTHY устанавливается в значение OFF каждый раз при создании резервной копии базы данных. Таким образом, в новой зеркальной базе данных он всегда имеет значение OFF. Если после отработки отказа необходимо, чтобы база данных снова стала надежной, следует выполнить дополнительные действия. Дополнительные сведения см. в статье [Настройка зеркальной базы данных на использование свойства TRUSTWORTHY (Transact-SQL)](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md).  
  
 Сведения о включении автоматической расшифровки главного ключа базы данных в зеркальной базе данных см. в статье [Настройка зашифрованной зеркальной базы данных](set-up-an-encrypted-mirror-database.md).  
  
####  <a name="Permissions"></a> Permissions  
 Владелец базы данных или системный администратор.  
  
##  <a name="PrepareToRestartMirroring"></a> Подготовка существующей зеркальной базы данных к повторному запуску зеркального отображения  
 Если зеркальное отображение было удалено, а зеркальная база данных остается в состоянии RECOVERING, то зеркальное отображение можно запустить повторно.  
  
1.  Создайте хотя бы одну резервную копию журналов основной базы данных. Дополнительные сведения см. в статье [Создание резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md).  
  
2.  В зеркальной базе данных следует восстановить с помощью инструкции RESTORE WITH NORECOVERY все резервные копии журналов, созданные в основной базе данных с момента удаления зеркальной базы данных. Дополнительные сведения см. в статье [Восстановление резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md).  
  
##  <a name="CombinedProcedure"></a> Подготовка новой зеркальной базы данных  
 **Подготовка зеркальной базы данных**  
  
> [!NOTE]  
>  Пример этой процедуры на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] см. в подразделе [Пример (Transact-SQL)](#TsqlExample)ниже в этом разделе.  
  
1.  Установите соединение с основным экземпляром на сервере.  
  
2.  Создайте либо полную копию базы данных, либо разностную резервную копию основной базы данных.  
  
    -   [Создание полной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
    -   [Создание разностной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)  
  
3.  Как правило, необходимо создать хотя бы одну резервную копию журналов основной базы данных. Однако резервная копия журналов может не понадобиться, если база данных только что создана и в ней еще не было создано ни одной резервной копии журналов либо если модель восстановления только что изменена с SIMPLE на FULL.  
  
    -   [Создание резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
4.  Если резервная копия находится не на сетевом диске, доступном для обеих систем, то скопируйте базу данных и резервные копии журналов на компьютер, где размещен экземпляр зеркального сервера.  
  
5.  Установите соединение с зеркальным экземпляром сервера.  
  
6.  С помощью инструкции RESTORE WITH NORECOVERY создайте зеркальную базу, восстановив полную резервную копию и, возможно, последнюю разностную резервную копию базы данных, на экземпляре зеркального сервера.  
  
    > [!NOTE]  
    >  При восстановлении файловой группы базы данных по файловой группе следует восстановить базу данных целиком.  
  
    -   [Восстановление резервной копии базы данных &#40;SQL Server Management Studio&#41;](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
    -   [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql) и [Аргументы инструкции RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql).  
  
7.  С помощью инструкции RESTORE WITH NORECOVERY примените все необработанные резервные копии и резервные копии журналов на зеркальной базе данных.  
  
    -   [Восстановление резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 Перед тем как начать сеанс зеркального отображения базы данных, нужно создать зеркальную базу данных. Это нужно сделать непосредственно перед запуском сеанса зеркального отображения.  
  
 В этом примере используется образец базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , в котором по умолчанию применяется простая модель восстановления.  
  
1.  Чтобы включить зеркальное отображение базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , переключите базу данных на модель полного восстановления.  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks   
    SET RECOVERY FULL;  
    GO  
    ```  
  
2.  После изменения модели восстановления с SIMPLE на FULL создайте полную резервную копию, с помощью которой затем можно будет создать зеркальную базу данных. Так как модель восстановления только что была изменена, указывается параметр WITH FORMAT для создания нового набора носителей. Это полезно для отделения резервных копий при модели полного восстановления от резервных копий, сделанных при простой модели восстановления. В данном примере файл резервной копии (`C:\AdventureWorks.bak`) создается на том же диске, на котором находится база данных.  
  
    > [!NOTE]  
    >  Для производственной базы данных необходимо всегда делать резервные копии на разные устройства.  
  
     На экземпляре основного сервера ( `PARTNERHOST1`) создайте полную резервную копию основной базы данных следующим образом.  
  
    ```  
    BACKUP DATABASE AdventureWorks   
        TO DISK = 'C:\AdventureWorks.bak'   
        WITH FORMAT  
    GO  
    ```  
  
3.  Создайте полную резервную копию на зеркальном сервере.  
  
4.  Восстановите полную резервную копию на экземпляр зеркального сервера с помощью инструкции RESTORE WITH NORECOVERY. Команда восстановления зависит от того, идентичны ли пути основной и зеркальной баз данных.  
  
    -   **Если пути идентичны:**  
  
         на экземпляре зеркального сервера ( `PARTNERHOST5`) выполните восстановление из полной резервной копии следующим образом:  
  
        ```  
        RESTORE DATABASE AdventureWorks   
            FROM DISK = 'C:\AdventureWorks.bak'   
            WITH NORECOVERY  
        GO  
        ```  
  
    -   **Если пути отличаются:**  
  
         Если путь зеркальной базы данных отличается от пути основной базы данных (например, отличаются имена дисков), то при создании зеркальной базы данных в операцию восстановления нужно будет добавить предложение MOVE.  
  
        > [!IMPORTANT]  
        >  Если отличаются пути основной и зеркальной баз данных, то добавлять файлы нельзя. Это происходит потому, что при появлении в журнале записи об операции добавления файла экземпляр зеркального сервера пытается поместить новый файл в местоположение, указанное для основной базы данных.  
  
         Например, следующая команда восстанавливает резервную копию основной базы данных, которая находится в каталоге "C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\", в другое расположение — "D:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Dat`a\`", где должна находиться зеркальная база данных.  
  
        ```  
        RESTORE DATABASE AdventureWorks  
           FROM DISK='C:\AdventureWorks.bak'  
           WITH NORECOVERY,   
              MOVE 'AdventureWorks_Data' TO   
                 'D:\Program Files\Microsoft SQL Server\MSSQL.n\MSSQL\Data\AdventureWorks_Data.mdf',   
              MOVE 'AdventureWorks_Log' TO  
                 'D:\Program Files\Microsoft SQL Server\MSSQL.n\MSSQL\Data\AdventureWorks_Log.ldf';  
        GO  
        ```  
  
5.  После создания полной резервной копии обязательно создается резервная копия журналов для основной базы данных. В следующем примере с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] создается резервная копия журналов для того же файла, который использовался в предыдущей полной резервной копии.  
  
    ```  
    BACKUP LOG AdventureWorks   
        TO DISK = 'C:\AdventureWorks.bak'   
    GO  
    ```  
  
6.  Перед тем как приступать к зеркальному отображению, необходимо применить требуемую резервную копию журналов (и все последующие резервные копии журналов).  
  
     Например, следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] восстанавливает первый журнал из `C:\AdventureWorks.bak`:  
  
    ```  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\AdventureWorks.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
7.  Если перед запуском зеркального отображения создавались дополнительные резервные копии журналов, то необходимо последовательно восстановить их на зеркальном сервере с параметром WITH NORECOVERY.  
  
     Например, следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] восстанавливает два дополнительных журнала из `C:\AdventureWorks.bak`:  
  
    ```  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\AdventureWorks.bak'   
        WITH FILE=2, NORECOVERY  
    GO  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\AdventureWorks.bak'   
        WITH FILE=3, NORECOVERY  
    GO  
    ```  
  
 Подробный пример настройки зеркального отображения базы данных, в котором показана настройка защиты, подготовка зеркальной базы данных, настройка партнеров и добавление следящего сервера, см. в статье [Настройка зеркального отображения базы данных (SQL Server)](database-mirroring-sql-server.md).  
  
##  <a name="FollowUp"></a> Продолжение: после подготовки зеркальной базы данных  
  
1.  Если были сняты какие-либо дополнительные резервные копии журналов с момента самой последней операции RESTORE LOG, то необходимо вручную применить каждую дополнительную резервную копию с параметром RESTORE WITH NORECOVERY.  
  
2.  Запустите сеанс зеркального отображения. Дополнительные сведения см. в статье [Создание сеанса зеркального отображения базы данных с использованием проверки подлинности Windows (среда SQL Server Management Studio)](establish-database-mirroring-session-windows-authentication.md) или [Создание сеанса зеркального отображения базы данных с использованием проверки подлинности Windows (Transact-SQL)](database-mirroring-establish-session-windows-authentication.md).  
  
3.  Если задание резервного копирования в основной базе данных отключено, то необходимо снова включить его.  
  
4.  Если для базы данных после отработки отказа с переходом на другой ресурс требуется доверие, это потребует дополнительных действий по настройке после начала зеркального отображения. Дополнительные сведения см. в статье [Настройка зеркальной базы данных на использование свойства TRUSTWORTHY (Transact-SQL)](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md).  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Создание полной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [Восстановление резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
-   [Создание сеанса зеркального отображения базы данных с использованием проверки подлинности Windows (среда SQL Server Management Studio)](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Создание сеанса зеркального отображения базы данных с использованием проверки подлинности Windows (Transact-SQL)](database-mirroring-establish-session-windows-authentication.md)  
  
-   [Настройка зашифрованной зеркальной базы данных](set-up-an-encrypted-mirror-database.md)  
  
-   [Настройка зеркальной базы данных на использование свойства TRUSTWORTHY (Transact-SQL)](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)  
  
## <a name="see-also"></a>См. также  
 [Зеркальное отображение базы данных (SQL Server)](database-mirroring-sql-server.md)   
 [Безопасность транспорта для зеркального отображения базы данных и групп доступности AlwaysOn &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md)   
 [Настройка зеркального отображения базы данных (SQL Server)](database-mirroring-sql-server.md)   
 [Создание резервных копий и восстановление полнотекстовых каталогов и индексов](../../relational-databases/indexes/indexes.md)   
 [Зеркальное отображение баз данных и полнотекстовые каталоги (SQL Server)](database-mirroring-and-full-text-catalogs-sql-server.md)   
 [Зеркальное отображение и репликация баз данных (SQL Server)](database-mirroring-and-replication-sql-server.md)   
 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)   
 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)   
 [Аргументы инструкции RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql)  
  
  
