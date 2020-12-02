---
title: 'Этапы поэтапного восстановления: простая модель восстановления'
description: В этом примере показано поэтапное восстановление базы данных в SQL Server на новый компьютер с использованием простой модели восстановления.
ms.custom: seo-lt-2019
ms.date: 12/17/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- piecemeal restores [SQL Server], simple recovery model
- restore sequences [SQL Server], piecemeal
- simple recovery model [SQL Server], RESTORE examples
ms.assetid: 9834b14a-4e56-4654-b190-c2a38624b6b4
author: cawrites
ms.author: chadam
ms.openlocfilehash: b9114f8c2318b7b17692a6c522b6c87f019886a3
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/23/2020
ms.locfileid: "96126948"
---
# <a name="example-piecemeal-restore-of-database-simple-recovery-model"></a>Пример поэтапного восстановления базы данных (простая модель восстановления)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
  
-   [Пример. Поэтапное восстановление отдельных файловых групп &#40;простая модель восстановления&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [Пример. Оперативное восстановление доступного только для чтения файла &#40;простая модель восстановления&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [Пример. Поэтапное восстановление базы данных &#40;модель полного восстановления&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Пример. Поэтапное восстановление только некоторых файловых групп &#40;модель полного восстановления&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [Пример. Оперативное восстановление файла, доступного для чтения и записи &#40;модель полного восстановления&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [Пример. Оперативное восстановление файла, доступного только для чтения &#40;модель полного восстановления&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a>См. также:  
 [Восстановление в сети (SQL Server)](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Поэтапное восстановление (SQL Server)](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)  
  
  
