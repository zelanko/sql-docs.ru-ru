---
title: "Восстановление до номера LSN (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "LSN, номера [SQL Server]"
  - "STOPBEFOREMARK, параметр [инструкция RESTORE]"
  - "STOPATMARK, параметр [инструкция RESTORE]"
  - "восстановление на момент времени [SQL Server]"
  - "восстановление баз данных [SQL Server], определенный момент времени"
  - "восстановление [SQL Server], базы данных"
  - "восстановление [SQL Server], на определенный момент времени"
  - "номера LSN"
  - "восстановление базы данных [SQL Server]"
  - "восстановление баз данных [SQL Server], на определенный момент времени"
ms.assetid: f7b3de5b-198d-448d-8c71-1cdd9239676c
caps.latest.revision: 38
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 37
---
# Восстановление до номера LSN (SQL Server)
  Этот раздел относится только к тем базам данных, которые используют модель полного восстановления или модель восстановления с неполным протоколированием.  
  
 Можно в качестве точки восстановления во время операции восстановления использовать номер LSN. Однако эта специальная возможность предназначена для средств поставщика, и представляется сомнительным, чтобы она могла оказаться в целом полезной.  
  
##  <a name="LSNs"></a> Общие сведения о регистрационных номерах транзакций в журнале  
 Регистрационные номера транзакций (LSN) в журнале используются во время последовательности восстановления для отслеживания момента времени, на который восстанавливаются данные. При восстановлении резервной копии данные восстанавливаются к регистрационному номеру транзакции в журнале, который соответствует моменту времени создания резервной копии. Разностные резервные копии и резервные копии журналов продвигают восстанавливаемую базу данных к более позднему моменту, которому соответствует больший регистрационный номер транзакции в журнале.  
  
 Каждая запись в журнале транзакций однозначно идентифицируется регистрационным номером транзакции в журнале (номером LSN). Регистрационные номера транзакций в журнале упорядочены таким образом, что если два изменения описываются записями в журнале, помеченными номерами LSN1 и LSN2, а LSN2 больше LSN1, то изменение, помеченное номером LSN2, произошло после изменения LSN1.  
  
 Регистрационный номер транзакции в журнале, в которой произошло важное событие, может оказаться полезен при формировании правильных последовательностей восстановления. Так как регистрационные номера транзакций в журнале упорядочены, их можно проверять на равенство и неравенство (то есть **\<**, **>**, **=**, **\<=**, **>=**). Такие сравнения полезны при построении последовательностей восстановления.  
  
> [!NOTE]  
>  Регистрационные номера транзакций в журнале — это значения типа **numeric**(25,0). Арифметические операции (например сложение или вычитание) не имеют смысла и не должны использоваться для регистрационных номеров транзакций в журнале.  
  
 [&#91;В начало&#93;](#Top)  
  
## Просмотр регистрационных номеров транзакций в журнале, используемых при создании и восстановлении резервных копий  
 Регистрационный номер транзакции в журнале, которому соответствует данное событие создания резервной копии или восстановления можно просмотреть в следующих источниках:  
  
-   [backupset;](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
-   [backupfile;](../../relational-databases/system-tables/backupfile-transact-sql.md)  
  
-   представления каталога [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md); [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
-   [инструкция RESTORE HEADERONLY](../Topic/RESTORE%20HEADERONLY%20\(Transact-SQL\).md)  
  
-   [RESTORE FILELISTONLY](../Topic/RESTORE%20FILELISTONLY%20\(Transact-SQL\).md)  
  
> [!NOTE]  
>  Также регистрационные номера транзакций в журнале появляются в некоторых текстовых сообщениях.  
  
## Синтаксис языка Transact-SQL при восстановлении до номера LSN  
 Инструкция [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) позволяет остановить восстановление на транзакции по номеру LSN или непосредственно перед ней следующим образом:  
  
-   Используйте предложение WITH STOPATMARK **='**lsn:*<lsn_number>***'**, где lsn:*\<lsnNumber>* — это строка, указывающая, что точкой восстановления является запись в журнале, которая содержит указанный номер LSN.  
  
     Предложение STOPATMARK выполняет накат до номера LSN, включая указанную запись журнала.  
  
-   Используйте предложение WITH STOPBEFOREMARK **='**lsn:*<lsn_number>***'**, где lsn:*\<lsnNumber>* — это строка, указывающая, что запись журнала, стоящая непосредственно перед записью журнала, содержащей номер LSN, является точкой восстановления.  
  
     Параметр STOPBEFOREMARK выполняет накат до номера LSN, не включая в него указанную запись журнала.  
  
 Обычно включается или исключается конкретная транзакция. Хотя это необязательно, на практике задаваемая запись журнала обычно является записью фиксации транзакции.  
  
## Примеры  
 В следующем примере предполагается, что база данных `AdventureWorks` была переведена в модель полного восстановления.  
  
```  
RESTORE LOG AdventureWorks FROM DISK = 'c:\adventureworks_log.bak'   
WITH STOPATMARK = 'lsn:15000000040000037'  
GO  
```  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Restore a Database Backup Using SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
-   [Создание резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   [Восстановление резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
-   [Восстановление базы данных до точки сбоя в модели полного восстановления (Transact-SQL)](../../relational-databases/backup-restore/restore database to point of failure - full recovery.md)  
  
-   [Восстановление базы данных до помеченной транзакции (среда SQL Server Management Studio)](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [Восстановление базы данных SQL Server до определенного момента времени (модель полного восстановления)](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
## См. также:  
 [Применение резервных копий журналов транзакций (SQL Server)](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)   
 [Журнал транзакций (SQL Server)](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [RESTORE (Transact-SQL)](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  