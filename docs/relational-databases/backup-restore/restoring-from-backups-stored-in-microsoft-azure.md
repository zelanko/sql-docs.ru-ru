---
title: Восстановление из резервных копий, сохраненных в Microsoft Azure | Документация Майкрософт
description: Сведения о восстановлении базы данных SQL Server с помощью резервной копии, хранящейся в хранилище BLOB-объектов Azure.
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 6ae358b2-6f6f-46e0-a7c8-f9ac6ce79a0e
author: cawrites
ms.author: chadam
ms.openlocfilehash: 5329181957e09e169caae74f9611a2426f377f7b
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/23/2020
ms.locfileid: "96125507"
---
# <a name="restoring-from-backups-stored-in-microsoft-azure"></a>Восстановление из резервных копий в Microsoft Azure
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  В этом разделе представлены вопросы восстановления базы данных с помощью резервной копии в службе хранилища BLOB-объектов Azure. Это относится к резервным копиям, созданным либо с помощью резервного копирования SQL Server на URL-адрес, либо с помощью служб [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 Рекомендуется ознакомиться с этим разделом, если у вас есть резервные копии в службе хранилища BLOB-объектов Azure, которые планируется восстановить. После этого изучите разделы, в которых описана процедура восстановления базы данных. Она аналогична для локальных резервных копий и резервных копий в Azure.  
  
## <a name="overview"></a>Обзор  
 Средства и методы, используемые для восстановления базы данных из локальной резервной копии, применимы для восстановления базы данных из облака.  Далее рассматриваются эти вопросы, а также различия, которые нужно учитывать при использовании резервных копий в службе хранилища BLOB-объектов Azure.  
  
### <a name="using-transact-sql"></a>Использование Transact-SQL  
  
-   Так как SQL Server должен подключиться к внешнему источнику данных для получения файлов резервных копий, для проверки подлинности учетной записи хранения используются учетные данные SQL. Соответственно, в инструкции RESTORE необходимо указать параметр WITH CREDENTIAL. Дополнительные сведения см. в разделе [Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
-   Если вы используете [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для управления вашими резервными копиями в облаке, можно просматривать все доступные резервные копии в хранилище с помощью функции **smart_admin.fn_available_backups** . Эта функция возвращает все доступные резервные копии для базы данных в таблице. Поскольку результаты возвращаются в виде таблицы, их можно фильтровать и сортировать. Дополнительные сведения см. в статье [managed_backup.fn_available_backups (Transact-SQL)](../../relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql.md).  
  
### <a name="using-sql-server-management-studio"></a>Использование среды SQL Server Management Studio  
  
-   Для восстановления базы данных из SQL Server Management Studio используется задача восстановления. На странице носителя резервных копий теперь доступен параметр **URL-адрес** для отображения файлов резервных копий, размещенных в службе хранилища BLOB-объектов Azure. Также необходимо указать учетные данные SQL, которые используются для проверки подлинности учетной записи хранения. После этого сетка **Восстанавливаемые резервные наборы данных** заполняется всеми резервными копиями, доступными в хранилище BLOB-объектов Azure. Дополнительные сведения см. в разделе [Восстановление из хранилища SQL Azure с помощью среды SQL Server Management Studio](../../relational-databases/backup-restore/sql-server-backup-to-url.md#RestoreSSMS).  
  
### <a name="optimizing-restores"></a>Оптимизация восстановления  
 Чтобы снизить время восстановления, добавьте учетной записи пользователя SQL Server право **Выполнение задач по обслуживанию томов** . Дополнительные сведения см. в разделе [Инициализация файлов базы данных](/previous-versions/sql/sql-server-2008-r2/ms175935(v=sql.105)). Если при включенной быстрой инициализации файлов операция восстановления по-прежнему идет медленно, посмотрите размер файла журнала для экземпляра, где была создана резервная копия базы данных. Если размер журнала очень большой (несколько ГБ), то ожидается, что восстановление будет идти медленно. Во время восстановления файл журнала необходимо обнулить, что занимает значительное количество времени.  
  
 Для сокращения времени восстановления, рекомендуется использовать сжатые резервные копии.  Для резервных копий, чей размер превышает 25 ГБ, используйте [служебную программу AzCopy](/archive/blogs/windowsazurestorage/azcopy-uploadingdownloading-files-for-windows-azure-blobs) для загрузки на локальный привод и для последующего выполнения восстановления. За дополнительными рекомендациями относительно резервных копий, обратитесь к [SQL Server Backup to URL Best Practices and Troubleshooting](../../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md).  
  
 Также при выполнении восстановления можно включить флаг трассировки 3051, что приведет к формированию подробного журнала. Этот файл журнала помещается в каталог журнала и получает имя в следующем формате: BackupToUrl-\<instancename>-\<dbname>-action-\<PID>.log. В файле журнала сохраняются сведения о каждом круговом пути со службой хранилища Azure, включая время операции, что может быть полезно при диагностике проблемы.  
  
### <a name="topics-on-performing-restore-operations"></a>Разделы об операциях восстановления  
  
-   [Выполнение полного восстановления базы данных (простая модель восстановления)](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)  
  
-   [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)  
  
-   [Выполнение полного восстановления базы данных (модель полного восстановления)](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md)  
  
-   [Восстановление файлов (простая модель восстановления)](../../relational-databases/backup-restore/file-restores-simple-recovery-model.md)  
  
-   [Файлы из резервных копий (модель полного восстановления)](../../relational-databases/backup-restore/file-restores-full-recovery-model.md)  
  
-   [Поэтапное восстановление (SQL Server)](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)  
  
