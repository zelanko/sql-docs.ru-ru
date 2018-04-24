---
title: Пример. Поэтапное восстановление базы данных (простая модель восстановления) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
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
helpviewer_keywords:
- piecemeal restores [SQL Server], simple recovery model
- restore sequences [SQL Server], piecemeal
- simple recovery model [SQL Server], RESTORE examples
ms.assetid: 9834b14a-4e56-4654-b190-c2a38624b6b4
caps.latest.revision: 27
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 777bc74e2b51bc2da1d180e72d828673d1fac5f1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="example-piecemeal-restore-of-database-simple-recovery-model"></a>Пример. Поэтапное восстановление базы данных (простая модель восстановления)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В последовательности поэтапного восстановления база данных восстанавливается за несколько шагов на уровне файловой группы, начиная с первичной и всех вторичных файловых групп, доступных для чтения и записи.  
  
 В данном примере база данных `adb` восстанавливается после сбоя на новом компьютере. Для базы данных выбрана простая модель восстановления. До сбоя все файловые группы работали в режиме «в сети». Файловые группы `A` и `C` предназначены для считывания и записи, а файловые группы `B` предназначены только для чтения. Файловая группа `B` становится доступной только для чтения до последнего частичного резервного копирования, содержащего первичную файловую группу и вторичные файловые группы, предназначенные для считывания и записи, `A` и `C`. Отдельная резервная копия файлов файловой группы `B` была создана после того, как файловая группа `B` стала доступной только для чтения.  
  
## <a name="restore-sequences"></a>Последовательности восстановления  
  
1.  Частичное восстановление первичной файловой группы и файловых групп `A` и `C`.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='A',FILEGROUP='C'   
       FROM partial_backup   
       WITH PARTIAL, RECOVERY;  
  
    ```  
  
     На этом этапе первичная файловая группа и файловые группы `A` и `C` работают в режиме «в сети». Все файлы из файловой группы `B` ожидают восстановления, а файловая группа работает в режиме «вне сети».  
  
2.  Восстановление файловой группы `B`«в сети».  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup WITH RECOVERY;  
  
    ```  
  
     Теперь все файловые группы находятся в режиме «в сети».  
  
## <a name="additional-examples"></a>Дополнительные примеры  
  
-   [Пример. Поэтапное восстановление отдельных файловых групп (простая модель восстановления)](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [Пример. Оперативное восстановление доступного только для чтения файла (простая модель восстановления)](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [Пример. Поэтапное восстановление базы данных (модель полного восстановления)](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Пример. Поэтапное восстановление только некоторых файловых групп (модель полного восстановления)](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [Пример. Оперативное восстановление файла, доступного для чтения и записи (модель полного восстановления)](../../relational-databases/backup-restore/example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [Пример. Оперативное восстановление файла, доступного только для чтения (модель полного восстановления)](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a>См. также:  
 [Восстановление в сети (SQL Server)](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Поэтапное восстановление (SQL Server)](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)  
  
  
