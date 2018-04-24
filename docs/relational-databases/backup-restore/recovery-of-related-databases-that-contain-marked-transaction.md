---
title: Восстановление связанных баз данных, которые содержат помеченную транзакцию | Документация Майкрософт
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
- transaction logs [SQL Server], marks
- STOPBEFOREMARK option [RESTORE statement]
- STOPATMARK option [RESTORE statement]
- point in time recovery [SQL Server]
- restoring databases [SQL Server], point in time
- recovery [SQL Server], databases
- restoring [SQL Server], point in time
- transactions [SQL Server], recovering to a mark
- database recovery [SQL Server]
- marked transactions [SQL Server], restoring
- database restores [SQL Server], point in time
ms.assetid: 77a0d9c0-978a-4891-8b0d-a4256c81c3f8
caps.latest.revision: 37
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9e1dca60a6866edbf654428656c29d639f96dbb9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="recovery-of-related--databases-that-contain-marked-transaction"></a>Восстановление связанных баз данных, которые содержат помеченную транзакцию
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Этот раздел относится только к базам данных, содержащим помеченные транзакции и использующим полную модель восстановления или модель восстановления с неполным протоколированием.  
  
 Дополнительные сведения о требованиях к восстановлению до указанной точки восстановления см. в статье [Восстановление базы данных SQL Server до определенного момента времени (модель полного восстановления)](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает вставку именованных меток в журнал транзакций, чтобы обеспечить возможность восстановления до определенной метки. Метки журнала являются специальным средством транзакции и вставляются только в случае, если связанная с ними транзакция зафиксирована. В итоге, метки могут быть привязаны к конкретной работе, и можно выполнить восстановление до точки, которая включает или не включает эту работу.  
  
 Перед вставкой именованных меток в журнал транзакций следует учесть следующее.  
  
-   Метки транзакций занимают место в журнале, поэтому их следует использовать только для транзакций, играющих важную роль в стратегии восстановления базы данных.  
  
-   После фиксации помеченной транзакции в таблицу [logmarkhistory](../../relational-databases/system-tables/logmarkhistory-transact-sql.md) базы данных **msdb**вставляется строка.  
  
-   Если в помеченной транзакции задействованы несколько баз данных на одном сервере баз данных или на разных серверах, то метки должны записываться в журналах всех задействованных баз данных. Дополнительные сведения см. в статье [Использование помеченных транзакций для согласованного восстановления связанных баз данных (модель полного восстановления)](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md).  
  
> [!NOTE]  
>  Дополнительные сведения о том, как пометить транзакции, см. в статье [Использование помеченных транзакций для согласованного восстановления связанных баз данных (модель полного восстановления)](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md).  
  
## <a name="transact-sql-syntax-for-inserting-named-marks-into-a-transaction-log"></a>Синтаксис языка Transact-SQL для вставки именованных меток в журнал транзакций  
 Чтобы вставлять метки в журналы транзакций, используйте инструкцию [BEGIN TRANSACTION](../../t-sql/language-elements/begin-transaction-transact-sql.md) и предложение WITH MARK [*описание*]. Имя метки совпадает с именем транзакции. Необязательное *описание* представляет собой текстовое описание, а не имя метки. Например, именем транзакции и метки, которые созданы следующей инструкцией `BEGIN TRANSACTION` , будет `Tx1`.  
  
```wmimof  
BEGIN TRANSACTION Tx1 WITH MARK 'not the mark name, just a description'    
```  
  
 В журнале транзакций записывается имя метки (имя транзакции), описание, база данных, пользователь, данные **datetime** и регистрационный номер транзакции в журнале (LSN). Данные **datetime** используются с именем метки, чтобы уникально идентифицировать метку.  
  
 Дополнительные сведения о вставке метки в транзакцию, которая охватывает несколько баз данных, см. в статье [Использование помеченных транзакций для согласованного восстановления связанных баз данных (модель полного восстановления)](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md).  
  
## <a name="transact-sql-syntax-for-recovering-to-a-mark"></a>Синтаксис языка Transact-SQL для восстановления до метки  
 Отметив помеченную транзакцию с помощью инструкции[RESTORE LOG](../../t-sql/statements/restore-statements-transact-sql.md), можно использовать одно из следующих предложений, чтобы остановиться на метке или перед ней.  
  
-   Используйте предложение WITH STOPATMARK = **'***<имя_метки>***'**, чтобы указать, что помеченная транзакция представляет собой точку восстановления.  
  
     С помощью предложения STOPATMARK выполняется накат к метке, при этом помеченная транзакция включается в накат.  
  
-   Используйте предложение WITH STOPBEFOREMARK = **'***<имя_метки>***'**, чтобы указать, что запись журнала непосредственно перед меткой представляет собой точку восстановления.  
  
     С помощью предложения STOPBEFOREMARK выполняется накат к метке, при этом помеченная транзакция не включается в накат.  
  
 В обоих вариантах, с предложением STOPATMARK и с предложением STOPBEFOREMARK, поддерживается необязательное предложение AFTER *datetime* . При использовании *datetime* уникальность имен меток необязательна.  
  
 Если предложение AFTER *datetime* опущено, накат останавливается на первой метке с указанным именем. Если предложение AFTER *datetime* указано, накат останавливается на первой метке с указанным именем точно в *datetime*или сразу после.  
  
> [!NOTE]  
>  Как и во всех случаях операций восстановления на момент времени, восстановление к метке запрещено, когда в базе данных совершаются операции с массовым протоколированием.  
  
 **Восстановление до помеченной транзакции**  
  
 [Восстановление базы данных до помеченной транзакции (среда SQL Server Management Studio)](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)  
  
### <a name="preparing-the-log-backups"></a>Подготовка резервных копий журнала  
 Например, подходящей стратегией резервного копирования для этих связанных баз данных будет следующая.  
  
1.  Использование модели полного восстановления для обеих баз данных.  
  
2.  Создание полной резервной копии каждой базы данных.  
  
     Отдельное или одновременное резервное копирование баз данных.  
  
3.  Перед созданием резервной копии журнала транзакций необходимо отметить транзакцию, выполняющуюся во всех базах данных. Дополнительные сведения о создании помеченных транзакций см. в статье [Использование помеченных транзакций для согласованного восстановления связанных баз данных (модель полного восстановления)](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md).  
  
4.  Резервное копирование журнала транзакции в каждой базе данных.  
  
### <a name="recovering-the-database-to-a-marked-transaction"></a>Восстановление базы данных до помеченной транзакции  
 **Восстановление резервной копии**  
  
1.  При необходимости создайте [резервные копии заключительного фрагмента журнала](../../relational-databases/backup-restore/tail-log-backups-sql-server.md) неповрежденных баз данных, если возможно.  
  
2.  Восстановите последнюю полную резервную копию каждой базы данных.  
  
3.  Идентифицируйте недавно помеченные транзакции, доступные во всех резервных копиях журнала транзакций. Данные сведения хранятся в таблице **logmarkhistory** в базе данных **msdb** на каждом сервере.  
  
4.  Идентифицируйте резервные копии журналов для всех связанных баз данных, содержащих данную отметку.  
  
5.  Восстановите каждую резервную копию журнала, остановившись на помеченной транзакции.  
  
6.  Восстановите каждую базу данных.  
  
## <a name="see-also"></a>См. также:  
 [BEGIN TRANSACTION (Transact-SQL)](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Применение резервных копий журналов транзакций (SQL Server)](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)   
 [Использование помеченных транзакций для согласованного восстановления связанных баз данных (модель полного восстановления)](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md)   
 [Обзор процессов восстановления (SQL Server)](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)   
 [Восстановление базы данных SQL Server до определенного момента времени (модель полного восстановления)](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)   
 [Планирование и выполнение последовательностей восстановления (модель полного восстановления)](../../relational-databases/backup-restore/plan-and-perform-restore-sequences-full-recovery-model.md)  
  
  
