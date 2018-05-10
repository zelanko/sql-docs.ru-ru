---
title: Общие сведения о резервном копировании (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 07/15/2016
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.suite: sql
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- tables [SQL Server], backing up data
- backups [SQL Server]
- database backups [SQL Server]
- backup types [SQL Server]
- data backups [SQL Server]
- backing up tables [SQL Server]
- database restores [SQL Server], backups
- backing up [SQL Server], about backing up
- restoring [SQL Server], backup types
- backups [SQL Server], about
- backups [SQL Server], table-level backups unsupported
ms.assetid: 09a6e0c2-d8fd-453f-9aac-4ff24a97dc1f
caps.latest.revision: 84
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: aeba4beeb3e52ba0dffb8df6ed8c860f9c6c8393
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="backup-overview-sql-server"></a>Backup Overview (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе представлены сведения о компоненте резервного копирования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Резервное копирование базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет важное значение для защиты данных. Здесь представлено описание типов резервных копий и ограничений резервного копирования. В рамках данной темы также рассмотрены устройства резервного копирования и носители данных резервных копий в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
  
## <a name="terms"></a>Термины
 
 **создание резервных копий**  
 Копирование данных или записей журнала из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или журнала ее транзакций на устройство для резервного копирования, например на диск, на котором создается резервная копия данных или журнала.  
  
**резервная копия**  
 Копия данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , используемая для восстановления данных после возникновения ошибки. Резервная копия данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создается на уровне базы данных для одного или нескольких файлов или групп файлов. Нельзя создать резервные копии на уровне таблиц. Кроме резервной копии данных модель полного восстановления требует создания резервной копии журнала транзакций.  
  
**[модель восстановления](../../relational-databases/backup-restore/recovery-models-sql-server.md)**  
 Свойство базы данных, с помощью которого выполняется управление обслуживанием журналов транзакций в базе данных. Существует три модели восстановления: простая модель восстановления, модель полного восстановления и модель восстановления с неполным протоколированием. Модель восстановления базы данных определяет требования к резервному копированию и восстановлению.  
  
 **[восстановление](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)**  
 Многоэтапный процесс, в ходе которого все данные и страницы журнала копируются из указанной резервной копии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в определенную базу данных, а затем выполняется накат всех фиксированных транзакций, записанных в резервной копии журнала, путем внесения новых данных на основе зарегистрированных изменений.  
  
 ## <a name="types-of-backups"></a>Типы резервного копирования  
  
 **[резервная копия, предназначенная только для копирования](../../relational-databases/backup-restore/copy-only-backups-sql-server.md)**  
 Специальная резервная копия, независимая от обычной последовательности резервных копий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
**резервное копирование данных**   
 Резервная копия данных всей базы данных (резервная копия базы данных), части базы данных (частичная резервная копия) или набора файлов данных или файловых групп (резервная копия файлов).  
  
**[резервное копирование базы данных](../../relational-databases/backup-restore/full-database-backups-sql-server.md)**  
 Резервная копия базы данных. Полные резервные копии базы данных отображают состояние всей базы данных на момент завершения резервного копирования. Разностные резервные копии базы данных содержат только изменения базы данных с момента последнего полного резервного копирования.  
  
 **[разностная резервная копия](../../relational-databases/backup-restore/full-database-backups-sql-server.md)**  
 Резервная копия, основанная на последнем полном резервировании частичной базы данных или набора файлов данных или групп файлов ( *базовая копия для разностного копирования*), которая содержит только добавочные данные, измененные по сравнению с базовой копией для разностного копирования.  
  
 Частичная разностная резервная копия, включающая только те экстенты данных, которые изменились в файловых группах с момента создания предыдущей частичной резервной копии, называется основой для разностной резервной копии.  
  
**полная резервная копия**  
 Резервная копия, которая содержит все данные заданной базы данных или наборов файлов или файловых групп, а также журналов для обеспечения возможности последующего восстановления этих данных.  
  
**[резервная копия журналов](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md)**  
 Резервная копия журналов транзакций, включающая все записи журнала, не входившие в предыдущую резервную копию журналов. (модель полного восстановления)  
  
 **[резервная копия файлов](../../relational-databases/backup-restore/full-file-backups-sql-server.md)**  
 Резервная копия одного или нескольких файлов или файловых групп базы данных.  
  
 **[частичная резервная копия](../../relational-databases/backup-restore/partial-backups-sql-server.md)**  
 Содержит данные только из некоторых файловых групп базы данных, включая данные в первичной файловой группе, все файловые группы, доступные для чтения-записи, а также любые дополнительно указанные файлы, доступные только для чтения.  
  
## <a name="backup-media-terms-and-definitions"></a>Носители резервных копий: термины и определения  
  
 **[устройство резервного копирования](../../relational-databases/backup-restore/backup-devices-sql-server.md)**  
 Диск или ленточное устройство, на которые записываются резервные копии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для последующего восстановления. Резервные копии SQL Server можно также записать в службу хранилища больших двоичных объектов Windows Azure, а формат **URL** используется, чтобы указать назначение и имя файла резервной копии. Дополнительные сведения см. в разделе [Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
 **[носитель данных резервной копии](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)**  
 Один или несколько наборов дисков или ленточных устройств, на которые записывается резервная копия.  
  
 **[резервный набор данных](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)**  
 Содержимое резервной копии добавляется на набор носителей при успешной операции резервного копирования.  
  
 **[семейство носителей](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)**  
 Резервные копии, созданные на одном устройстве без зеркального отображения или на наборе устройств с зеркальным отображением в наборе носителей  
  
 **[набор носителей](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)**  
 Упорядоченный набор носителей данных резервной копии в виде определенного количества ленточных устройств или дисков, на которые может быть записана одна или несколько операций резервного копирования, с использованием фиксированного типа и номера устройств резервного копирования.  
  
 **[зеркальный набор носителей](../../relational-databases/backup-restore/mirrored-backup-media-sets-sql-server.md)**  
 Составные копии (зеркала) набора носителей данных резервных копий.  
  
##  <a name="BackupCompression"></a> Сжатие резервных копий  
 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] и более поздние версии поддерживают сжатие резервных копий, а [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздние версии позволяют восстановить сжатые резервные копии. Дополнительные сведения см. в разделе [Сжатие резервных копий (SQL Server)](../../relational-databases/backup-restore/backup-compression-sql-server.md).  
  
##  <a name="Restrictions"></a>  Ограничения на операции резервного копирования 
 Резервное копирование может выполняться, если база данных находится в режиме «в сети» и используется. Однако действуют следующие ограничения.  
  
### <a name="cannot-back-up-offline-data"></a>Нельзя создать резервную копию данных, находящихся в режиме "вне сети"  
 Любая операция резервного копирования, которая явно или неявно ссылается на данные, находящиеся в режиме «вне сети», завершается неудачей. Ниже следуют некоторые наиболее распространенные примеры этого.  
  
-   Запрашивается создание полной резервной копии, но одна файловая группа в базе данных находится в режиме «вне сети». Операция завершается неудачно, так как в полное резервное копирование неявно включены все файловые группы.  
  
     Чтобы создать резервную копию этой базы данных, можно воспользоваться созданием резервных копий файлов (или файловых групп) и задать только те файловые группы, которые находятся в режиме «в сети».  
  
-   Запрашивается частичное резервное копирование, но файловые группы, доступные для чтения и записи, находятся в режиме «вне сети». Операция завершается неудачей, потому что для частичного резервного копирования запрашиваются все файловые группы, доступные для чтения и записи.  
  
-   Запрашивается резервное копирование заданных файлов, но один из файлов находится в режиме «в сети». Операция завершается неудачей. Чтобы создать резервную копию файлов, находящихся в режиме «в сети», устраните из списка файлы, находящиеся в режиме «вне сети», и повторите операцию.  
  
 Обычно резервное копирование журнала проходит успешно, даже если один или несколько файлов данных недоступны. Однако если какой-нибудь файл содержит массовые изменения, сделанные в модели восстановления с неполным протоколированием, то для успешного резервного копирования необходимо, чтобы все файлы находились в режиме «в сети».  
  
### <a name="concurrency-restrictions"></a>Ограничения параллелизма   
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует процесс резервного копирования в сети, что позволяет создавать резервную копию базы данных во время ее использования. Во время резервного копирования можно производить большинство операций. Например, во время создания резервной копии разрешены инструкции INSERT, UPDATE и DELETE. При попытке приступить к выполнению операции резервного копирования во время создания или удаления файла базы данных выполнение операции резервного копирования будет отложено до завершения создания или удаления либо до истечения времени ожидания.  
  
 Следующие операции запрещены во время создания резервной копии базы данных или журнала транзакций.  
  
-   Операции управления файлами, такие как инструкция ALTER DATABASE с параметром ADD FILE или с параметром REMOVE FILE.  
  
-   Операции сжатия базы данных или файла. Сюда же включены операции автоматического сжатия.  
  
-   При попытке создать или удалить файл базы данных во время выполнения операции резервного копирования, создание или удаление завершится неудачно.  
  
 Если операция резервного копирования перекрывается операцией сжатия или управления файлами, то возникает конфликт. Независимо от того, какая из конфликтующих операций начата первой, вторая операция ждет истечения времени ожидания первой (оно зависит от параметров сеанса). Если разблокировка происходит до истечения времени ожидания, работа второй операции продолжается. Если разблокировки за этот период не происходит, вторая операция заканчивается неудачно.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Устройства резервного копирования и носители резервных копий**  
  
-   [Определение логического устройства резервного копирования для дискового файла (SQL Server)](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [Определение логического устройства резервного копирования для ленточного накопителя (SQL Server)](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [Указание в качестве назначения резервного копирования диска или ленты (SQL Server)](../../relational-databases/backup-restore/specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [Удаление устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/delete-a-backup-device-sql-server.md)  
  
-   [Назначение срока хранения резервной копии (SQL Server)](../../relational-databases/backup-restore/set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [Просмотр содержимого ленты или файла резервной копии (SQL Server)](../../relational-databases/backup-restore/view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [Просмотр файлов данных и журналов в резервном наборе данных (SQL Server)](../../relational-databases/backup-restore/view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [Просмотр свойств и содержимого логического устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [Восстановление резервной копии с устройства (SQL Server)](../../relational-databases/backup-restore/restore-a-backup-from-a-device-sql-server.md)  
  
-   [Tutorial: SQL Server Backup and Restore to Windows Azure Blob Storage Service](~/relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
 **Создание резервной копии**  
  
> [!NOTE]  
>  Для создания частичной резервной копии или резервной копии только для копирования используется инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](../../t-sql/statements/backup-transact-sql.md) с параметром PARTIAL или COPY_ONLY.  
  
-   [Создание полной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [Создание резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   [Резервное копирование файлов и файловых групп (SQL Server)](../../relational-databases/backup-restore/back-up-files-and-filegroups-sql-server.md)  
  
-   [Создание разностной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)  
  
-   [Создание резервной копии журнала транзакций при повреждении базы данных (SQL Server)](../../relational-databases/backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
-   [Включение или отключение вычисления контрольных сумм резервных копий во время резервного копирования или восстановления (SQL Server)](../../relational-databases/backup-restore/enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
-   [Определение, продолжает ли операция резервного копирования или восстановления работу после возникновения ошибки (SQL Server)](../../relational-databases/backup-restore/specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
-   [Использование регулятора ресурсов для ограничения загрузки ЦП при сжатии резервной копии (Transact-SQL)](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)  
  
-   [Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Azure](~/relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="and-more"></a>См. также 
 [Резервное копирование и восстановление баз данных SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Обзор процессов восстановления (SQL Server)](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)   
 [Планы обслуживания](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Журнал транзакций (SQL Server)](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [Модели восстановления (SQL Server)](../../relational-databases/backup-restore/recovery-models-sql-server.md)  
  
  
