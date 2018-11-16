---
title: Восстановление из резервных копий, сохраненных в Microsoft Azure | Документация Майкрософт
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 6ae358b2-6f6f-46e0-a7c8-f9ac6ce79a0e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e12e2b8d1578d85420d7a5f3ddd61a85fdd6de7d
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51663063"
---
# <a name="restoring-from-backups-stored-in-microsoft-azure"></a>Восстановление из резервных копий в Microsoft Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В данном разделе представлены вопросы восстановления базы данных с помощью резервной копии в службе хранилища больших двоичных объектов Windows Azure. Это относится к резервным копиям, созданным либо с помощью резервного копирования SQL Server на URL-адрес, либо с помощью служб [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 Рекомендуется ознакомиться с этим разделом, если у вас есть резервные копии в службе хранилища больших двоичных объектов Windows Azure, которые планируется восстановить. После этого изучите разделы, описывающие процедуру восстановления базы данных. Она аналогична для локальных резервных копий и резервных копий в Azure.  
  
## <a name="overview"></a>Обзор  
 Средства и методы, используемые для восстановления базы данных из локальной резервной копии, применимы для восстановления базы данных из облака.  Далее рассматриваются эти вопросы, а также различия, которые нужно учитывать при использовании резервных копий в службе хранилища больших двоичных объектов Windows Azure.  
  
### <a name="using-transact-sql"></a>Использование Transact-SQL  
  
-   Так как SQL Server должен подключиться к внешнему источнику данных для получения файлов резервных копий, для проверки подлинности учетной записи хранения используются учетные данные SQL. Соответственно, в инструкции RESTORE необходимо указать параметр WITH CREDENTIAL. Дополнительные сведения см. в разделе [Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
-   Если вы используете [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для управления вашими резервными копиями в облаке, можно просматривать все доступные резервные копии в хранилище с помощью функции **smart_admin.fn_available_backups** . Эта функция возвращает все доступные резервные копии для базы данных в таблице. Поскольку результаты возвращаются в виде таблицы, их можно фильтровать и сортировать. Дополнительные сведения см. в статье [managed_backup.fn_available_backups (Transact-SQL)](../../relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql.md).  
  
### <a name="using-sql-server-management-studio"></a>Использование среды SQL Server Management Studio  
  
-   Для восстановления базы данных из SQL Server Management Studio используется задача восстановления. На странице носителя резервных копий теперь доступен параметр **URL-адрес** для отображения файлов резервных копий, размещенных в службе хранилища больших двоичных объектов Windows Azure. Также необходимо указать учетные данные SQL, которые используются для проверки подлинности учетной записи хранения. После этого сетка **Резервные наборы данных для восстановления** заполняется всеми резервными копиями, доступными в хранилище больших двоичных объектов Windows Azure. Дополнительные сведения см. в статье [Restoring from Windows Azure storage Using SQL Server Management Studio](../../relational-databases/backup-restore/sql-server-backup-to-url.md#RestoreSSMS).  
  
### <a name="optimizing-restores"></a>Оптимизация восстановления  
 Чтобы снизить время восстановления, добавьте учетной записи пользователя SQL Server право **Выполнение задач по обслуживанию томов** . Дополнительные сведения см. в разделе [Инициализация файлов базы данных](https://go.microsoft.com/fwlink/?LinkId=271622). Если при включенной быстрой инициализации файлов операция восстановления по-прежнему идет медленно, посмотрите размер файла журнала для экземпляра, где была создана резервная копия базы данных. Если размер журнала очень большой (несколько ГБ), то ожидается, что восстановление будет идти медленно. Во время восстановления файл журнала необходимо обнулить, что занимает значительное количество времени.  
  
 Для сокращения времени восстановления, рекомендуется использовать сжатые резервные копии.  Для резервных копий, чей размер превышает 25 ГБ, используйте [служебную программу AzCopy](https://blogs.msdn.com/b/windowsazurestorage/archive/2012/12/03/azcopy-uploading-downloading-files-for-windows-azure-blobs.aspx) для загрузки на локальный привод и для последующего выполнения восстановления. За дополнительными рекомендациями относительно резервных копий, обратитесь к [SQL Server Backup to URL Best Practices and Troubleshooting](../../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md).  
  
 Также при выполнении восстановления можно включить флаг трассировки 3051, что приведет к формированию подробного журнала. Этот файл журнала помещается в каталог журнала и получает имя формата: BackupToUrl-\<имя_экземпляра>-\<имя_БД>-action-\<идентификатор_процесса>.log. В файле журнала сохраняются сведения о каждом обмене данными с хранилищем Windows Azure, включая время операции, что может быть полезно при диагностике проблемы.  
  
### <a name="topics-on-performing-restore-operations"></a>Разделы об операциях восстановления  
  
-   [Выполнение полного восстановления базы данных (простая модель восстановления)](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)  
  
-   [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)  
  
-   [Выполнение полного восстановления базы данных (модель полного восстановления)](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md)  
  
-   [Восстановление файлов (простая модель восстановления)](../../relational-databases/backup-restore/file-restores-simple-recovery-model.md)  
  
-   [Файлы из резервных копий (модель полного восстановления)](../../relational-databases/backup-restore/file-restores-full-recovery-model.md)  
  
-   [Поэтапное восстановление (SQL Server)](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)  
  
  
