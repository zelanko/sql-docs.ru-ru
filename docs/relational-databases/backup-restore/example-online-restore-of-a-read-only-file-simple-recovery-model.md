---
title: "Пример. Оперативное восстановление доступного только для чтения файла (простая модель восстановления) | Microsoft Docs"
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
  - "последовательности восстановления [SQL Server], оперативное"
  - "оперативное восстановление [SQL Server], простая модель восстановления"
  - "простая модель восстановления [SQL Server], примеры RESTORE"
ms.assetid: 0c691fc6-9865-46a7-b055-8097424492d6
caps.latest.revision: 27
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 27
---
# Пример. Оперативное восстановление доступного только для чтения файла (простая модель восстановления)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Данный раздел относится только к базам данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которые содержат доступные только для чтения файловые группы в простой модели восстановления. При простой модели восстановления файл, доступный только для чтения, можно восстановить в режиме «в сети», если существует резервная копия файла, сделанная после того, как файл в последний раз стал доступен только для чтения.  
  
 В данном примере база данных `adb` содержит три файловые группы. Файловая группа `A` предназначена для чтения и записи, а файловые группы `B` и `C` предназначены только для чтения. Изначально все файловые группы находятся в режиме в сети. Необходимо восстановить доступный только для чтения файл из файловой группы `B`, `b1`. Администратор базы данных может восстановить его с помощью резервной копии, сделанной после того, как файл стал доступным только для чтения. На время восстановления файловая группа `B` будет переведена в режим «вне сети», однако остальная часть базы данных продолжит работать в режиме «в сети».  
  
## Последовательность восстановления  
  
> [!NOTE]  
>  Синтаксис последовательности восстановления в сети тот же самый, что и в случае последовательности восстановления вне сети.  
  
 Чтобы восстановить файл, администратор базы данных использует следующую последовательность восстановления:  
  
```  
RESTORE DATABASE adb FILE='b1' FROM filegroup_B_backup   
WITH RECOVERY  
```  
  
 Файл в настоящий момент находится в режиме «в сети».  
  
## Дополнительные примеры  
  
-   [Пример. Поэтапное восстановление базы данных (простая модель восстановления)](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Пример. Поэтапное восстановление отдельных файловых групп (простая модель восстановления)](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [Пример. Поэтапное восстановление базы данных (модель полного восстановления)](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Пример. Поэтапное восстановление только некоторых файловых групп (модель полного восстановления)](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [Пример. Оперативное восстановление файла, доступного для чтения и записи (модель полного восстановления)](../../relational-databases/backup-restore/example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [Пример. Оперативное восстановление файла, доступного только для чтения (модель полного восстановления)](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## См. также:  
 [Восстановление в сети (SQL Server)](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [Поэтапное восстановление (SQL Server)](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)   
 [Восстановление файлов (простая модель восстановления)](../../relational-databases/backup-restore/file-restores-simple-recovery-model.md)   
 [Обзор процессов восстановления (SQL Server)](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)   
 [RESTORE (Transact-SQL)](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  