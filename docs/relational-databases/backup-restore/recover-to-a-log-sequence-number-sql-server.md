---
title: Восстановление до регистрационного номера транзакции в журнале (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 10/23/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- log sequence numbers [SQL Server]
- STOPBEFOREMARK option [RESTORE statement]
- STOPATMARK option [RESTORE statement]
- point in time recovery [SQL Server]
- restoring databases [SQL Server], point in time
- recovery [SQL Server], databases
- restoring [SQL Server], point in time
- LSNs
- database recovery [SQL Server]
- database restores [SQL Server], point in time
ms.assetid: f7b3de5b-198d-448d-8c71-1cdd9239676c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 46ab24ff86eb7a68e48f58e67f03a859d0c43aa7
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "72916037"
---
# <a name="recover-to-a-log-sequence-number-sql-server"></a>Восстановление до номера LSN (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Этот раздел относится только к тем базам данных, которые используют модель полного восстановления или модель восстановления с неполным протоколированием.  
  
 Можно в качестве точки восстановления во время операции восстановления использовать номер LSN. Однако эта специальная возможность предназначена для средств поставщика, и представляется сомнительным, чтобы она могла оказаться в целом полезной.  
  
##  <a name="LSNs"></a> Общие сведения о регистрационных номерах транзакций в журнале  
 Регистрационные номера транзакций (LSN) в журнале используются во время последовательности восстановления для отслеживания момента времени, на который восстанавливаются данные. При восстановлении резервной копии данные восстанавливаются к регистрационному номеру транзакции в журнале, который соответствует моменту времени создания резервной копии. Разностные резервные копии и резервные копии журналов продвигают восстанавливаемую базу данных к более позднему моменту, которому соответствует больший регистрационный номер транзакции в журнале. Дополнительные сведения о номерах LSN см. в разделах [Руководство по архитектуре журнала транзакций SQL Server и управлению им](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch).  
  
> [!NOTE]  
> Регистрационные номера транзакций в журнале — это значения типа **numeric**(25,0). Арифметические операции (например сложение или вычитание) не имеют смысла и не должны использоваться для регистрационных номеров транзакций в журнале.  
 
## <a name="viewing-lsns-used-by-backup-and-restore"></a>Просмотр регистрационных номеров транзакций в журнале, используемых при создании резервных копий и восстановлении  
 Регистрационный номер транзакции в журнале, которому соответствует данное событие создания резервной копии или восстановления можно просмотреть в следующих источниках:  
  
-   [backupset;](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
-   [backupfile;](../../relational-databases/system-tables/backupfile-transact-sql.md)  
  
-   [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md); [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
-   [инструкция RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)  
  
-   [RESTORE FILELISTONLY](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)  
  
> [!NOTE]  
>  Регистрационные номера транзакций также появляются в некоторых текстовых сообщениях в журнале ошибок.  
  
## <a name="transact-sql-syntax-for-restoring-to-an-lsn"></a>Синтаксис языка Transact-SQL при восстановлении до номера LSN  
 Инструкция [RESTORE](../../t-sql/statements/restore-statements-transact-sql.md) позволяет остановить восстановление на транзакции по номеру LSN или непосредственно перед ней следующим образом:  
  
-   Используйте предложение WITH STOPATMARK **='** lsn: _<lsn_number>_ **'** , где lsn: *\<lsnNumber>*  — это строка, указывающая, что точкой восстановления является запись в журнале, которая содержит указанный номер LSN.  
  
     Предложение STOPATMARK выполняет накат до номера LSN, включая указанную запись журнала.  
  
-   Используйте предложение WITH STOPBEFOREMARK **='** lsn: _<lsn_number>_ **'** , где lsn: *\<lsnNumber>*  — это строка, указывающая, что запись журнала, стоящая непосредственно перед записью журнала, содержащей номер LSN, является точкой восстановления.  
  
     Параметр STOPBEFOREMARK выполняет накат до номера LSN, не включая в него указанную запись журнала.  
  
 Обычно включается или исключается конкретная транзакция. Хотя это необязательно, на практике задаваемая запись журнала обычно является записью фиксации транзакции.  
  
## <a name="examples"></a>Примеры  
 В следующем примере предполагается, что база данных `AdventureWorks` была переведена в модель полного восстановления.  
  
```sql  
RESTORE LOG AdventureWorks FROM DISK = 'c:\adventureworks_log.bak'   
WITH STOPATMARK = 'lsn:15000000040000037'  
GO  
```  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Restore a Database Backup Using SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
-   [Создание резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   [Восстановление резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
-   [Восстановление базы данных до точки сбоя в модели полного восстановления (Transact-SQL)](../../relational-databases/backup-restore/restore-database-to-point-of-failure-full-recovery.md)  
  
-   [Восстановление базы данных до помеченной транзакции (среда SQL Server Management Studio)](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [Восстановление базы данных SQL Server до определенного момента времени (модель полного восстановления)](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
## <a name="see-also"></a>См. также:  
 [Применение резервных копий журналов транзакций (SQL Server)](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)   
 [Журнал транзакций (SQL Server)](../../relational-databases/logs/the-transaction-log-sql-server.md)     
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)     
 [Обзор процессов восстановления (SQL Server)](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md#TlogAndRecovery)       
 [Руководство по архитектуре журнала транзакций SQL Server и управлению им](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md)      
  
