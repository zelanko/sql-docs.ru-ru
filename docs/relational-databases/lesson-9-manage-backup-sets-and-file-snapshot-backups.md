---
title: Занятие 9. Управление резервными наборами данных и резервными копиями моментальных снимков файлов | Документация Майкрософт
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 766a0846-db15-4346-b814-4049039bcbfc
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 892b2857bf95fa6de7d042c1a59a1efb4f6d7148
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732432"
---
# <a name="lesson-9-manage-backup-sets-and-file-snapshot-backups"></a>Занятие 9. Управление резервными наборами данных и резервными копиями моментальных снимков файлов
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
На этом занятии вы удалите резервный набор данных с помощью системной хранимой процедуры [sp_delete_backup (Transact-SQL)](../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md) . Эта процедура удаляет файл резервной копии и моментальный снимок файла для каждого файла базы данных, связанного с резервным набором данных.  
  
> [!NOTE]  
> Если вы попытаетесь удалить резервный набор данных, просто удалив файл резервной копии из контейнера BLOB-объектов Azure, то будет удален только сам файл резервной копии — связанные с ним моментальные снимки файлов останутся. Если у вас возникла такая ситуация, используйте системную функцию [sys.fn_db_backup_file_snapshots (Transact-SQL)](../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md) для определения URL-адреса потерянных моментальных снимков файлов, а затем используйте системную хранимую процедуру [sp_delete_backup_file_snapshot (Transact-SQL)](../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md) для удаления каждого утерянного моментального снимка файла. Дополнительные сведения см. в разделе  [Резервные копии моментальных снимков файлов для файлов базы данных в Azure](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
Чтобы удалить резервный набор моментальных снимков файлов, выполните указанные ниже действия.  
  
1.  Подключитесь к среде Microsoft SQL Server Management Studio.  
  
2.  Откройте новое окно запроса и подключитесь к экземпляру SQL Server 2016 ядра СУБД в виртуальной машине Azure (или к любому экземпляру SQL Server 2016 с разрешениями на чтение и запись в этот контейнер).  
  
3.  Скопируйте и вставьте приведенный ниже скрипт Transact-SQL в окне запроса. Выберите резервную копию журнала, которую нужно удалить вместе со связанными моментальными снимками файлов. Измените URL-адрес в соответствии с именем учетной записи хранения и контейнером, которые были указаны на занятии 1, укажите имя файла резервной копии журнала, а затем выполните этот скрипт.  
  
    ```  
  
    sys.sp_delete_backup 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/tutorial-9164-20150726012420.bak';  
  
    ```  
  
4.  В обозревателе объектов подключитесь к хранилищу Azure.  
  
5.  Разверните узел "Контейнеры", разверните контейнер, созданный на занятии 1, и убедитесь в том, что файл резервной копии, который использовался в шаге 3, больше не отображается в этом контейнере (при необходимости обновите узел).  
  
    ![Контейнер Azure, демонстрирующий удаление большого двоичного объекта с резервной копией журнала](../relational-databases/media/c0070b08-4667-4db5-aaff-987a404ec934.JPG "Контейнер Azure, демонстрирующий удаление большого двоичного объекта с резервной копией журнала")  
  
6.  Чтобы убедиться в том, что оба моментальных снимка файлов были удалены, скопируйте и вставьте приведенный ниже скрипт Transact-SQL в окно запроса, а затем выполните его.  
  
    ```  
  
    -- verify that two file snapshots have been removed  
    SELECT * from sys.fn_db_backup_file_snapshots ('AdventureWorks2014');  
  
    ```  
  
    ![Область результатов, в которой удаляются два моментальных снимка файлов](../relational-databases/media/f3891361-dfb6-4f4d-a090-ebfeb977981e.JPG "Область результатов, в которой удаляются два моментальных снимка файлов")  
  
**Конец учебника**  
  
## <a name="see-also"></a>См. также:  
[Резервные копии моментальных снимков файлов для файлов базы данных в Azure](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)  
[sp_delete_backup (Transact-SQL)](../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
[sys.fn_db_backup_file_snapshots (Transact-SQL)](../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)  
[sp_delete_backup_file_snapshot (Transact-SQL)](../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)  
  
  
  

