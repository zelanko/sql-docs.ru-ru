---
title: Пример поэтапного восстановления некоторых файловых групп (модель полного восстановления) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- piecemeal restores [SQL Server], full recovery model
- restore sequences [SQL Server], piecemeal
ms.assetid: bced4b54-e819-472b-b784-c72e14e72a0b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a3ea7a4c7d9189ace988ef57f25e99d61a4273dd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62876164"
---
# <a name="example-piecemeal-restore-of-only-some-filegroups-full-recovery-model"></a>Пример поэтапного восстановления некоторых файловых групп (модель полного восстановления)
  Сведения в этом разделе относятся только к базам данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , использующим полную модель восстановления, которые содержат несколько файлов или файловых групп.  
  
 В последовательности поэтапного восстановления база данных восстанавливается за несколько шагов на уровне файловой группы, начиная с первичной и всех вторичных файловых групп, доступных для чтения и записи.  
  
 В этом примере база данных `adb`, которая использует модель полного восстановления, содержит три файловые группы. Файловая группа `A` доступна для записи и для чтения, файловые группы `B` и `C` доступны только для чтения. Изначально все файловые группы находятся в режиме в сети.  
  
 Первичная файловая группа и файловая группа `B` базы данных `adb` , вероятно, повреждены. Первичная файловая группа достаточно мала и может быть быстро восстановлена. Администратор базы данных решает восстановить обе группы с помощью последовательности поэтапного восстановления. Сначала восстанавливается первичная файловая группа и связанные с ней журналы транзакций, при этом восстанавливается база данных.  
  
 Неизменившиеся файловые группы `A` и `C` содержат важные данные. Поэтому они будут восстановлены следующим образом и переведены в режим «в сети» как можно быстрее. Наконец, восстанавливается поврежденная вторичная файловая группа `B`.  
  
## <a name="restore-sequences"></a>Последовательности восстановления  
  
> [!NOTE]  
>  Синтаксис последовательности восстановления в сети тот же самый, что и в случае последовательности восстановления вне сети.  
  
1.  Создайте резервную копию заключительного фрагмента журнала базы данных `adb`. Этот этап важен, чтобы привести неповрежденные файловые группы `A` и `C` в соответствие с точкой восстановления базы данных.  
  
    ```  
    BACKUP LOG adb TO tailLogBackup WITH NORECOVERY  
    ```  
  
2.  Произведите частичное восстановление первичной файловой группы.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='Primary' FROM backup   
    WITH PARTIAL, NORECOVERY  
    RESTORE LOG adb FROM backup1 WITH NORECOVERY  
    RESTORE LOG adb FROM backup2 WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
     В этот момент первичная группа файлов переходит в режим «в сети». Файлы в файловых группах `A`, `B`и `C` ожидают восстановления и поэтому находятся в режиме «вне сети».  
  
3.  Восстановление файлов `A` и `C`в сети.  
  
     Так как данные этих файловых групп не повреждены, их не нужно восстанавливать из резервной копии, но их нужно перевести в режим «в сети».  
  
     Администратор базы данных сразу же восстанавливает файловые группы `A` и `C` .  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='A', FILEGROUP='C' WITH RECOVERY  
    ```  
  
     На этом этапе первичная файловая группа и файловые группы `A` и `C` находятся в режиме в сети. Файлы в файловой группе `B` ожидают восстановления, при этом она находится в режиме «вне сети».  
  
4.  Восстановление файловой группы `B`«в сети».  
  
     Файлы в файловой группе `B` могут быть восстановлены позже в любое время.  
  
    > [!NOTE]  
    >  После того как файловая группа `B` становится доступной только для чтения, используется ее резервная копия, что исключает необходимость выполнения наката.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup WITH RECOVERY  
    ```  
  
     Теперь все файловые группы находятся в режиме «в сети».  
  
## <a name="additional-examples"></a>Дополнительные примеры  
  
-   [Пример. Поэтапное восстановление базы данных &#40;простая модель восстановления&#41;](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Пример. Поэтапное восстановление отдельных файловых групп &#40;простая модель восстановления&#41;](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [Пример. Оперативное восстановление доступного только для чтения файла &#40;простая модель восстановления&#41;](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [Пример. Поэтапное восстановление базы данных &#40;модель полного восстановления&#41;](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Пример. Оперативное восстановление файла, доступного для чтения и записи &#40;модель полного восстановления&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [Пример. Оперативное восстановление файла, доступного только для чтения &#40;модель полного восстановления&#41;](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a>См. также  
 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)   
 [Восстановление в сети (SQL Server)](online-restore-sql-server.md)   
 [Применение резервных копий журналов транзакций (SQL Server)](transaction-log-backups-sql-server.md)   
 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)   
 [Поэтапное восстановление (SQL Server)](piecemeal-restores-sql-server.md)  
  
  
