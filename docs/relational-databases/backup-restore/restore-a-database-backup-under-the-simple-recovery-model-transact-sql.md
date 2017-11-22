---
title: "Восстановление резервной копии базы данных в простой модели восстановления (Transact-SQL) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: backup-restore
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full backups [SQL Server]
- database restores [SQL Server], full backups
- backing up databases [SQL Server], full backups
- database backups [SQL Server], full backups
- restoring databases [SQL Server], full backups
ms.assetid: a928fa36-e285-476f-9a7b-6840a8bb7283
caps.latest.revision: "39"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 39ef8a6ae40be42412c580e3573aa51fb7a5a83d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="restore-a-database-backup-under-the-simple-recovery-model-transact-sql"></a>Восстановление резервной копии базы данных в простой модели восстановления (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Этот раздел содержит сведения о восстановлении полной резервной копии базы данных.  
  
> [!IMPORTANT]  
>  При восстановлении базы данных из полной резервной копии системный администратор должен быть единственным пользователем, работающим с базой данных.  
  
## <a name="prerequisites-and-recommendations"></a>Предварительные условия и рекомендации  
  
-   Чтобы восстановить зашифрованную базу данных, необходимо иметь доступ к сертификату или асимметричному ключу, который использовался для шифрования базы данных. Без сертификата или асимметричного ключа восстановить базу данных нельзя. Поэтому сертификат, используемый для шифрования ключа шифрования базы данных, должен храниться в течение всего времени, пока есть необходимость в резервной копии. Дополнительные сведения см. в статье [SQL Server Certificates and Asymmetric Keys](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  
  
-   В целях безопасности рекомендуется не присоединять и не восстанавливать базы данных, полученные из неизвестных или ненадежных источников. В этих базах данных может содержаться вредоносный код, вызывающий выполнение непредусмотренных инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] или появление ошибок из-за изменения схемы или физической структуры базы данных. Перед тем как использовать базу данных, полученную из неизвестного или ненадежного источника, выполните на тестовом сервере инструкцию [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) для этой базы данных, а также изучите исходный код в базе данных, например хранимые процедуры и другой пользовательский код.  
  
## <a name="database-compatibility-level-after-upgrade"></a>Уровень совместимости баз данных после обновления  
 После обновления для уровней совместимости баз данных **tempdb**, **model**, **msdb** and **Resource** задается значение [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Системная база данных **master** сохраняет уровень совместимости, существовавший до обновления, кроме тех случаев, когда этот уровень был ниже 100. Если перед обновлением уровень совместимости базы данных **master** был менее 100, то после обновления он становится равным 100.  
  
 Если уровень совместимости пользовательской базы данных до обновления был 100 или выше, после обновления он останется таким же. Если уровень совместимости до обновления был 90, в обновленной базе данных он устанавливается в значение 100, что является минимально поддерживаемым уровнем совместимости в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
> [!NOTE]  
>  Новые пользовательские базы данных наследуют уровень совместимости базы данных **model** .  
  
## <a name="procedures"></a>Процедуры  
  
#### <a name="to-restore-a-full-database-backup"></a>Восстановление полной резервной копии базы данных  
  
1.  Для восстановления полной резервной копии базы данных выполните инструкцию RESTORE DATABASE, указав:  
  
    -   Имя базы данных для восстановления.  
  
    -   устройство резервного копирования, с которого происходит восстановление полной резервной копии базы данных;  
  
    -   предложение NORECOVERY при наличии журнала транзакций или разностной резервной копии, которые необходимо применить после восстановления полной резервной копии.  
  
    > [!IMPORTANT]  
    >  Чтобы восстановить зашифрованную базу данных, необходимо иметь доступ к сертификату или асимметричному ключу, который использовался для шифрования базы данных. Без сертификата или асимметричного ключа восстановить базу данных нельзя. Поэтому сертификат, используемый для шифрования ключа шифрования базы данных, должен храниться в течение всего времени, пока есть необходимость в резервной копии. Дополнительные сведения см. в статье [SQL Server Certificates and Asymmetric Keys](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  
  
2.  Дополнительно можно указать следующее.  
  
    -   Предложение FILE, определяющее, из какого резервного набора, содержащегося на устройстве резервного копирования, будет выполнено восстановление.  
  
> [!NOTE]  
>  Обратите внимание, что если восстановить базу данных предыдущей версии до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], то эта база данных будет автоматически обновлена. Как правило, база данных сразу становится доступной. Но если база данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] содержит полнотекстовые индексы, при обновлении будет произведен их импорт, сброс или повторное создание в зависимости от установленного значения свойства сервера  **upgrade_option** . Если при обновлении выбран режим импорта (**upgrade_option** = 2) или перестроения (**upgrade_option** = 0), полнотекстовые индексы во время обновления будут недоступны. В зависимости от объема индексируемых данных процесс импорта может занять несколько часов, а перестроение — в несколько (до десяти) раз больше. Обратите внимание, что если для обновления выбран режим «Импортировать», а полнотекстовый каталог недоступен, то связанные с ним полнотекстовые индексы будут перестроены. Чтобы изменить значение свойства сервера **upgrade_option** , следует использовать процедуру [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md).  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 В следующем примере восстанавливается полная резервная копия базы [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] с магнитной ленты.  
  
### <a name="example"></a>Пример  
  
```  
USE master;  
GO  
RESTORE DATABASE AdventureWorks2012  
   FROM TAPE = '\\.\Tape0';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Выполнение полного восстановления базы данных (модель полного восстановления)](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md)   
 [Выполнение полного восстановления базы данных (простая модель восстановления)](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)   
 [Полные резервные копии баз данных (SQL Server)](../../relational-databases/backup-restore/full-database-backups-sql-server.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Журнал и сведения о заголовке резервной копии (SQL Server)](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)   
 [Перестроение системных баз данных](../../relational-databases/databases/rebuild-system-databases.md)  
  
  
