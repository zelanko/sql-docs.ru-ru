---
title: Восстановление файлов (простая модель восстановления) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- file restores [SQL Server]
- simple recovery model [SQL Server]
- restoring files [SQL Server], Transact-SQL restore sequence
- restoring files [SQL Server]
- Transact-SQL restore sequence
- restoring files [SQL Server], simple recovery model
- file restores [SQL Server], simple recovery model
- file restores [SQL Server], Transact-SQL restore sequence
ms.assetid: b6d07386-7c6f-4cc6-be32-93289adbd3d6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5157fcfeb54e22c404dcba29655771a1c2034e2c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62921831"
---
# <a name="file-restores-simple-recovery-model"></a>Восстановления файлов (простая модель восстановления)
  Сведения в этом разделе относятся только к базам данных, использующим простую модель восстановления и содержащим хотя бы одну вторичную файловую группу только для чтения.  
  
 Цель восстановления файлов — восстановить один или несколько поврежденных файлов, не восстанавливая всю базу данных. В рамках простой модели восстановления резервные копии файлов и файловых групп поддерживаются только на файлах только для чтения. Первичная файловая группа и вторичные файловые группы, доступные как для чтения и записи, всегда восстанавливаются вместе из резервной копии базы данных или частичной резервной копии.  
  
 Существуют следующие сценарии восстановления файлов.  
  
-   Восстановление файлов в режиме «вне сети»  
  
     При *автономном восстановлении файлов*база данных находится в режиме «вне сети», в то время как происходит восстановление поврежденных файлов или файловых групп. В конце последовательности восстановления база данных переходит в режим «в сети».  
  
     Автономное восстановление файлов поддерживают все выпуски [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
-   Восстановление файлов в сети  
  
     При *оперативном восстановлении файлов*, если база данных во время восстановления находится в режиме «в сети», то остается в этом режиме в течение времени восстановления файлов. Однако каждая файловая группа, в которой восстанавливается файл, во время операции восстановления находится в состоянии «вне сети». После восстановления всех файлов, входящих в файловую группу в режиме «вне сети», она автоматически переключается в режим «в сети».  
  
     Дополнительные сведения о поддержке оперативного восстановления страниц и файлов см. в разделе [Возможности, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md). Дополнительные сведения об оперативном восстановлении см. в разделе [Оперативное восстановление (SQL Server)](online-restore-sql-server.md).  
  
    > [!TIP]  
    >  Если желательно, чтобы база данных находилась в режиме "вне сети" при восстановлении файлов, переведите ее в режим "вне сети" перед запуском последовательности восстановления, выполнив следующую инструкцию [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) : ALTER DATABASE *имя_базы_данных* SET OFFLINE.  
  

  
##  <a name="Overview"></a>Общие сведения о восстановлении файлов и файловых групп в простой модели восстановления  
 Сценарий восстановления файлов состоит из единой последовательности восстановления, в процессе которой производится копирование, накат транзакций и восстановление соответствующих данных.  
  
1.  Восстановите каждый поврежденный файл из последней резервной копии поврежденного файла.  
  
2.  Восстановите базу данных и самую свежую разностную резервную копию файлов для каждого восстанавливаемого файла.  
  
### <a name="transact-sql-steps-for-file-restore-sequence-simple-recovery-model"></a>Шаги Transact-SQL для последовательности восстановления файлов (простая модель восстановления)  
 В этом разделе показаны основные параметры инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) для простой последовательности восстановления файлов. Синтаксис и прочие подробности, несущественные для данной цели, опущены.  
  
 Последовательность восстановления содержит только две инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] . Первая инструкция восстанавливает вторичный файл `A`, который восстанавливается с параметром WITH NORECOVERY. Вторая операция восстанавливает файлы `B` и `C` , которые восстанавливаются с другого устройства резервного копирования с параметром WITH RECOVERY:  
  
1.  Восстановление **=** файла *базы* данных базы данных _name_of_file_A_  
  
     FROM *резервная_копия_файла_A*  
  
     WITH NORECOVERY **;**  
  
2.  Восстановление **=** файла *базы* данных базы данных _name_of_file_B_**,**_name_of_file_C_  
  
     FROM *резервная_копия_файлов_Б_и_В*  
  
     WITH RECOVERY **;**  
  
### <a name="examples"></a>Примеры  
  
-   [Пример. оперативное восстановление файла, доступного только для чтения, &#40;простой модели восстановления&#41;](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [Пример. автономное восстановление основной и другой файловой группы &#40;модели полного восстановления&#41;](example-offline-restore-of-primary-and-one-other-filegroup-full-recovery-model.md)  
  
 
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Восстановление файлов и файловых групп**  
  
-   [Восстановление файлов и файловых групп поверх существующих файлов &#40;SQL Server&#41;](restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [Восстановление файлов и файловых групп &#40;SQL Server&#41;](restore-files-and-filegroups-sql-server.md)  
  
-   [Восстановление файлов и файловых групп &#40;SQL Server&#41;](restore-files-and-filegroups-sql-server.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>ОБЪЕКТАХ  
  
  
  
## <a name="see-also"></a>См. также:  
 [Резервное копирование и восстановление: взаимодействие и сосуществование &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md)   
 [Разностные резервные копии &#40;SQL Server&#41;](differential-backups-sql-server.md)   
 [&#40;SQL Server полных резервных копий файлов&#41;](full-file-backups-sql-server.md)   
 [Общие сведения о резервном копировании &#40;SQL Server&#41;](backup-overview-sql-server.md)   
 [Обзор восстановления и восстановления &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)   
 [Восстановление &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [Полное восстановление базы данных &#40;простой модели восстановления&#41;](complete-database-restores-simple-recovery-model.md)   
 [Поэтапное восстановление &#40;SQL Server&#41;](piecemeal-restores-sql-server.md)  
  
  
