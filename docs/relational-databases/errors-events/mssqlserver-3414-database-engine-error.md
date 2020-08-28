---
description: MSSQLSERVER_3414
title: MSSQLSERVER_3414 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3414 (Database Engine error)
ms.assetid: f25852f9-b91c-4356-b817-78bec9ec8db4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a7a7d69c27ed422763c5c697f003ba9fb4c82286
ms.sourcegitcommit: a0245fdae1ff9045f587a3a67b72f34405d35a4f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2020
ms.locfileid: "88618098"
---
# <a name="mssqlserver_3414"></a>MSSQLSERVER_3414
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|3414|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|REC_GIVEUP|  
|Текст сообщения|Во время восстановления произошла ошибка, препятствующая перезапуску базы данных «%.*ls» (идентификатор базы данных %d). Проведите диагностику ошибок восстановления и исправьте их, или проведите восстановление из проверенной рабочей резервной копии. Если ошибки не устранены или ожидаются в будущем, свяжитесь со службой технической поддержки.|  
  
## <a name="explanation"></a>Объяснение  
Заданная база данных была восстановлена, но не была запущена, так как при восстановлении возникли ошибки. В результате этой ошибки состояние базы данных изменилось на SUSPECT. Первичная файловая группа и, возможно, другие файловые группы могут быть повреждены. Эта база данных не может быть восстановлена во время загрузки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и поэтому недоступна. Для разрешения этой проблемы требуется вмешательство пользователя. Состояние SUSPECT отображается как в SQL Server Management Studio (рядом со значком базы данных), так и при просмотре столбца sys.databases.state_desc. Любая попытка использовать базу данных в этом состоянии приведет к следующей ошибке.

```
Msg 926, Level 14, State 1, Line 1 
Database 'mydb' cannot be opened. It has been marked SUSPECT by recovery. See the SQL Server errorlog for more information
```
  
Следует отметить, что, если эта ошибка возникает для базы данных **tempdb**, экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершает работу.  

## <a name="cause"></a>Причина
Эта ошибка может вызываться временным состоянием, существовавшим в системе во время данной попытки запуска экземпляра сервера или восстановления базы данных. Эта ошибка может быть также вызвана неустранимым сбоем, который возникает при каждой попытке запуска базы данных. Причина сбоя восстановления обычно находится в ошибках, которые предшествуют ошибке 3414 в журнале ошибок или журнале событий. Предыдущая ошибка в файле журнала содержит то же значение spid<n>. Например, следующая ошибка восстановления возникает из-за ошибки контрольной суммы при попытке чтения блока журнала. Обратите внимание, что *spid15s* есть во всех строках.

```
2020-03-31 17:33:13.00 spid15s     Error: 824, Severity: 24, State: 4.  
2020-03-31 17:33:13.00 spid15s     SQL Server detected a logical consistency-based I/O error: (bad checksum). It occurred during a read of page (0:-1) in database ID 13 at offset 0x0000000000b800 in file 'C:\Program Files\Microsoft SQL Server\MSSQL10.SQL2008\MSSQL\DATA\mydb_log.LDF'.  Additional messages in the SQL Server error log or system event log may provide more detail. This is a severe error condition that threatens database integrity and must be corrected immediately. Complete a full database consistency check (DBCC CHECKDB). This error can be caused by many factors; for more information, see SQL Server Books Online.   
2020-03-31 17:33:13.16 spid15s     Error: 3414, Severity: 21, State: 1.  
2020-03-31 17:33:13.16 spid15s     An error occurred during recovery, preventing the database 'mydb' (database ID 13) from restarting. Diagnose the recovery errors and fix them, or restore from a known good backup. If errors are not corrected or expected, contact Technical Support
```


Существует широкий диапазон ошибок, которые могут привести к сбою восстановления базы данных. Хотя каждую ошибку необходимо оценивать отдельно, проблема сбоя восстановления базы данных обычно решается так, как описано в разделе "Действия пользователя" ниже.

## <a name="user-action"></a>Рекомендуемые действия  
 
Для получения сведений о причине возникновения ошибки 3414 проверьте журнал событий Windows или журнал ошибок на наличие предыдущего сообщения об ошибке, в котором указан конкретный сбой. Соответствующее действие пользователя зависит от того, что указывают сведения в журнале событий Windows: ошибка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] была вызвана временным состоянием или неустранимым сбоем. В сообщении об ошибке указано: "Проведите диагностику ошибок восстановления и исправьте их или проведите восстановление из проверенной рабочей резервной копии". Таким образом, можно попытаться исправить возникшую ошибку, чтобы завершить восстановление (см. [Исправляемые ошибки и отложенные транзакции](#correctable-errors-and-deferred-transactions)).

Если ошибки не удается исправить, рекомендуется восстановить базу данных из работоспособной резервной копии. Если восстановление из резервной копии невозможно, у вас есть еще два варианта, которые не гарантируют полного восстановления данных: используйте аварийное восстановление с помощью [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) или попытайтесь скопировать как можно больше данных в другую базу данных. 

 1. Восстановление из последней известной работоспособной резервной копии базы данных.
 1. Использование метода аварийного восстановления с помощью [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md).
 1. Попытка скопировать как можно больше данных в другую базу данных.

Первый способ — восстановление работоспособной резервной копии базы данных — это лучший вариант для перевода базы данных в гарантированно согласованное состояние.  

Второй оптимальный вариант, если резервная копия недоступна, — восстановить доступность базы данных. Но вы должны понимать, что согласованность транзакций не может быть гарантирована после сбоя восстановления. Нет способа узнать, для каких транзакций должен быть выполнен откат или накат, который не состоялся из-за сбоя восстановления. Инструкции по аварийному восстановлению приводятся в разделе [Устранение ошибок базы данных в аварийном режиме](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md#resolving-errors-in-database-emergency-mode) в документации по DBCC CHECKDB. 

Если аварийное восстановление не работает и вы хотите попытаться сохранить некоторые данные в другой базе данных, то, чтобы получить доступ к базе данных, установите аварийный режим с помощью команды ALTER DATABASE <dbname> SET EMERGENCY. Затем можно попытаться скопировать данные из таблиц.

### <a name="correctable-errors-and-deferred-transactions"></a>Исправляемые ошибки и отложенные транзакции
Не все ошибки, обнаруженные во время восстановления базы данных, приводят к сбою восстановления и подозрительной базе данных.

Ошибки при первом открытии базы данных и/или файлов журнала транзакций возникают перед восстановлением. Примеры таких ошибок: [17204](mssqlserver-17204-database-engine-error.md) и [17207](mssqlserver-17207-database-engine-error.md). После исправления этих ошибок выполнение операции восстановления может быть продолжено (но не обязательно завершится успешно, если возникнут другие ошибки восстановления). Такие ошибки, как 17204 и 17207, не приводят к состоянию базы данных SUSPECT. При возникновении этих проблем база данных имеет состояние RECOVERY_PENDING. 

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет выполнять восстановление даже при возникновении ошибки на уровне страницы и поддерживает согласованность транзакций. Этот процесс сократил количество ситуаций, когда возникает состояние SUSPECT. Эта концепция называется [отложенными транзакциями](../backup-restore/deferred-transactions-sql-server.md).

Если ошибка, возникшая во время восстановления, указывает на проблему со страницей базы данных, например ошибку контрольной суммы или сообщение 824, завершение восстановления может быть разрешено с ошибками в состоянии ожидания. В случае, когда транзакция не зафиксирована, ошибка на странице может привести к [отложенной транзакции](../backup-restore/deferred-transactions-sql-server.md), позволяя выполнить восстановление.  

В следующих записях журнала ошибок показан пример сообщения об ошибке [824](mssqlserver-824-database-engine-error.md), возникшей во время восстановления, но завершение восстановления было разрешено с отложенной транзакцией. Обратите внимание на отсутствие ошибки 3414 в этой ситуации и на сообщение о завершении восстановления базы данных.

```2010-03-31 19:17:18.45 spid7s      Error: 824, Severity: 24, State: 2.   
2010-03-31 19:17:18.45 spid7s      SQL Server detected a logical consistency-based I/O error: incorrect checksum (expected: 0xb2c87a0a; actual: 0xb6c0a5e2). It occurred during a read of page (1:153) in database ID 13 at offset 0x00000000132000 in file 'C:\Program Files\Microsoft SQL Server\MSSQL10.SQL2008\MSSQL\DATA\mydb.mdf'.  Additional messages in the SQL Server error log or system event log may provide more detail. This is a severe error condition that threatens database integrity and must be corrected immediately. Complete a full database consistency check (DBCC CHECKDB). This error can be caused by many factors; for more information, see SQL Server Books Online.   
2010-03-31 19:17:18.45 spid7s      Error: 3314, Severity: 21, State: 1.   
2010-03-31 19:17:18.45 spid7s      During undoing of a logged operation in database 'mydb', an error occurred at log record ID (25:100:19). Typically, the specific failure is logged previously as an error in the Windows Event Log service. Restore the database or file from a backup, or repair the database.
2010-03-31 19:17:18.45 spid7s      Errors occurred during recovery while rolling back a transaction. The transaction was deferred. Restore the bad page or file, and re-run recovery.   
2010-03-31 19:17:18.45 spid7s      Recovery completed for database mydb (database ID 13) in 2 second(s) (analysis 204 ms, redo 25 ms, undo 1832 ms.) This is an informational message only. No user action is required.   
```

Если необходимо выполнить накат зафиксированной транзакции, эта страница может быть помечена как недоступная (любые дальнейшие попытки получить доступ к странице приведут к сообщению об ошибке 829) и восстановление может завершиться. В этом случае ошибку необходимо исправить, восстановив страницу из резервной копии или отменив выделение страницы с помощью инструкции DBCC CHECKDB во время восстановления.


  
## <a name="see-also"></a>См. также раздел  
[ALTER DATABASE (Transact-SQL)](~/t-sql/statements/alter-database-transact-sql-set-options.md)  
[DBCC CHECKDB (Transact-SQL)](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
[Выполнение полного восстановления базы данных (простая модель восстановления)](~/relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)  
[Отложенные транзакции](../backup-restore/deferred-transactions-sql-server.md)  
[MSSQLSERVER_824](~/relational-databases/errors-events/mssqlserver-824-database-engine-error.md)  
[sys.databases (Transact-SQL)](~/relational-databases/system-catalog-views/sys-databases-transact-sql.md)

  
