---
title: "Пример. Автономное восстановление основной и еще одной файловой группы (модель полного восстановления) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "модель полного восстановления [SQL Server], пример RESTORE"
  - "восстановление в сети [SQL Server]"
  - "последовательности восстановления [SQL Server], автономное"
ms.assetid: 7d6c50eb-dc84-4d66-855a-0b5f1bd89737
caps.latest.revision: 32
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 32
---
# Пример. Автономное восстановление основной и еще одной файловой группы (модель полного восстановления)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Данный раздел относится только к базам данных с моделью полного восстановления, содержащим несколько файловых групп.  
  
 В данном примере база данных `adb` содержит три файловые группы. Файловые группы `A` и `C` предназначены для считывания и записи, а файловые группы `B` предназначены только для чтения. Первичная файловая группа и файловая группа `B` повреждены, но файловые группы `A` и `C` не затронуты. До аварии все файловые группы находились в режиме «в сети».  
  
 Администратор базы данных принял решение восстановить первичную файловую группу и файловую группу `B`. Используется полная модель восстановления базы данных, поэтому перед началом восстановления необходимо сделать резервную копию заключительного фрагмента журнала базы данных. Когда база данных переходит в режим «в сети», файловые группы `A` и `C` автоматически переходят в режим «в сети».  
  
> [!NOTE]  
>  В последовательности восстановления вне сети предусмотрено меньше шагов, чем для восстановления файлов в сети только для чтения. Например, см. раздел [Пример. Оперативное восстановление файла, доступного только для чтения (модель полного восстановления)](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-full-recovery-model.md). Однако в процессе выполнения последовательности в режиме «вне сети» находится вся база данных.  
  
## Резервная копия заключительного фрагмента журнала  
 Перед тем как восстановить базу данных из копии, администратор этой базы данных должен создать резервную копию заключительного фрагмента журнала. Поскольку база данных повреждена, для создания резервной копии заключительного фрагмента журнала требуется применение параметра NO_TRUNCATE:  
  
```  
BACKUP LOG adb TO tailLogBackup   
   WITH NORECOVERY, NO_TRUNCATE  
```  
  
 Резервная копия заключительного фрагмента журнала — это последняя резервная копия, используемая в следующих последовательностях восстановления.  
  
## Последовательность восстановления  
 Чтобы восстановить первичную файловую группу и файловую группу `B`, администратор базы данных использует последовательность восстановления без параметра PARTIAL, как указано ниже:  
  
```  
RESTORE DATABASE adb FILEGROUP='Primary' FROM backup1   
WITH NORECOVERY  
RESTORE DATABASE adb FILEGROUP='B' FROM backup2   
WITH NORECOVERY  
RESTORE LOG adb FROM backup3 WITH NORECOVERY  
RESTORE LOG adb FROM backup4 WITH NORECOVERY  
RESTORE LOG adb FROM backup5 WITH NORECOVERY  
RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
```  
  
 Файлы, которые не затрагивает процесс восстановления, автоматически переводятся в режим «в сети». Сейчас все файловые группы переведены в режим «в сети».  
  
## См. также:  
 [Восстановление в сети (SQL Server)](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [Поэтапное восстановление (SQL Server)](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)   
 [Восстановление файлов (модель полного восстановления)](../../relational-databases/backup-restore/file-restores-full-recovery-model.md)   
 [Применение резервных копий журналов транзакций (SQL Server)](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)   
 [RESTORE (Transact-SQL)](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  