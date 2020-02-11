---
title: Восстановление до регистрационного номера транзакции в журнале (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 835057cdef6b7d2a336b64480515a5046cfde070
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62875767"
---
# <a name="recover-to-a-log-sequence-number-sql-server"></a>Восстановление до номера LSN (SQL Server)
  Этот раздел относится только к тем базам данных, которые используют модель полного восстановления или модель восстановления с неполным протоколированием.  
  
 Можно в качестве точки восстановления во время операции восстановления использовать номер LSN. Однако эта специальная возможность предназначена для средств поставщика, и представляется сомнительным, чтобы она могла оказаться в целом полезной.  
  
##  <a name="LSNs"></a> Общие сведения о регистрационных номерах транзакций в журнале  
 Регистрационные номера транзакций (LSN) в журнале используются во время последовательности восстановления для отслеживания момента времени, на который восстанавливаются данные. При восстановлении резервной копии данные восстанавливаются к регистрационному номеру транзакции в журнале, который соответствует моменту времени создания резервной копии. Разностные резервные копии и резервные копии журналов продвигают восстанавливаемую базу данных к более позднему моменту, которому соответствует больший регистрационный номер транзакции в журнале.  
  
 Каждая запись в журнале транзакций однозначно идентифицируется регистрационным номером транзакции в журнале (номером LSN). Регистрационные номера транзакций в журнале упорядочены таким образом, что если два изменения описываются записями в журнале, помеченными номерами LSN1 и LSN2, а LSN2 больше LSN1, то изменение, помеченное номером LSN2, произошло после изменения LSN1.  
  
 Регистрационный номер транзакции в журнале, в которой произошло важное событие, может оказаться полезен при формировании правильных последовательностей восстановления. Так как регистрационные номера LSN упорядочены, их можно сравнивать на равенство и неравенство **\<**( **>** т **=** ** \< **. е **>=**.,,,,). Такие сравнения полезны при построении последовательностей восстановления.  
  
> [!NOTE]  
>  Регистрационные номера транзакций в журнале — это значения типа `numeric`(25,0). Арифметические операции (например сложение или вычитание) не имеют смысла и не должны использоваться для регистрационных номеров транзакций в журнале.  
  

  
## <a name="viewing-lsns-used-by-backup-and-restore"></a>Просмотр регистрационных номеров транзакций в журнале, используемых при создании и восстановлении резервных копий  
 Регистрационный номер транзакции в журнале, которому соответствует данное событие создания резервной копии или восстановления можно просмотреть в следующих источниках:  
  
-   [backupset;](/sql/relational-databases/system-tables/backupset-transact-sql)  
  
-   [backupfile;](/sql/relational-databases/system-tables/backupfile-transact-sql)  
  
-   [sys. database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql); [sys. master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
-   [инструкция RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
-   [RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)  
  
> [!NOTE]  
>  Также регистрационные номера транзакций в журнале появляются в некоторых текстовых сообщениях.  
  
## <a name="transact-sql-syntax-for-restoring-to-an-lsn"></a>Синтаксис языка Transact-SQL при восстановлении до номера LSN  
 Инструкция [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) позволяет остановить восстановление на транзакции по номеру LSN или непосредственно перед ней следующим образом:  
  
-   Используйте предложение WITH STOPATMARK **= '** LSN:_<lsn_number>_ **'** , где lsn:*\<lsnNumber>* — это строка, указывающая, что запись журнала, содержащая указанный номер LSN, является точкой восстановления.  
  
     Предложение STOPATMARK выполняет накат до номера LSN, включая указанную запись журнала.  
  
-   Используйте предложение WITH STOPBEFOREMARK **= '** LSN:_<lsn_number>_ **'** , где lsn:*\<lsnNumber>* — это строка, указывающая, что запись журнала, которая находится непосредственно перед записью журнала, содержащей указанный номер LSN, является точкой восстановления.  
  
     Параметр STOPBEFOREMARK выполняет накат до номера LSN, не включая в него указанную запись журнала.  
  
 Обычно включается или исключается конкретная транзакция. Хотя это необязательно, на практике задаваемая запись журнала обычно является записью фиксации транзакции.  
  
## <a name="examples"></a>Примеры  
 В следующем примере предполагается, что база данных `AdventureWorks` была переведена в модель полного восстановления.  
  
```  
RESTORE LOG AdventureWorks FROM DISK = 'c:\adventureworks_log.bak'   
WITH STOPATMARK = 'lsn:15000000040000037'  
GO  
```  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Восстановление резервной копии базы данных &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)  
  
-   [Создание резервной копии журнала транзакций &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)  
  
-   [Восстановление резервной копии журнала транзакций &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)  
  
-   [Восстановление базы данных до точки сбоя в модели полного восстановления &#40;Transact-SQL&#41;](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [Восстановление базы данных до помеченной транзакции &#40;SQL Server Management Studio&#41;](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [Восстановление SQL Server базы данных на момент времени &#40;модель полного восстановления&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
## <a name="see-also"></a>См. также:  
 [Применение резервных копий журналов транзакций &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)   
 [&#40;SQL Server журнала транзакций&#41;](../logs/the-transaction-log-sql-server.md)   
 [Восстановление &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
