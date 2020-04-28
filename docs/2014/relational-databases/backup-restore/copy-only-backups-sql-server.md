---
title: Резервные копии только для копирования (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- copy-only backups [SQL Server]
- COPY_ONLY option [BACKUP statement]
- backups [SQL Server], copy-only backups
ms.assetid: f82d6918-a5a7-4af8-868e-4247f5b00c52
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 96267b98d7e17b920e0a7cee70b69e4c964584e4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "72798008"
---
# <a name="copy-only-backups-sql-server"></a>Резервные копии только для копирования (SQL Server)
  *Резервная копия только для копирования* — это резервная копия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которая не зависит от обычной последовательности создания традиционных резервных копий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Обычно создание резервного копирования приводит к изменению базы данных и влияет на то, как будут восстанавливаться последующие резервные копии. Однако иногда приходится выполнять резервное копирование базы данных для особых нужд, когда это не сказывается на общем процессе резервного копирования и восстановления. Этой цели служат резервные копии только для копирования.  
  
 Резервные копии только для копирования имеют следующие типы.  
  
-   Полные резервные копии только для копирования (все модели восстановления).  
  
     Резервная копия только для копирования не может служить в качестве базовой копии для разностного копирования или разностного резервного копирования и не влияет на базовую копию для разностного копирования.  
  
     Операция восстановления полной резервной копии только для копирования аналогична операции восстановления любой полной резервной копии.  
  
-   Резервные копии журналов только для копирования (модель полного восстановления и модель восстановления с неполным протоколированием).  
  
     Резервная копия журналов только для копирования сохраняет текущую точку архивирования журнала и, следовательно, не влияет на последовательность обычных резервных копий журналов. Никакой необходимости в резервных копиях журналов только для копирования обычно нет. Вместо этого можно создать новую обычную резервную копию журналов (с параметром WITH NORECOVERY), затем использовать ее совместно со всеми остальными ранее созданными резервными копиями журналов, которые необходимы для последовательности восстановления. Однако резервная копия журналов только для копирования иногда может быть полезна для выполнения восстановления в сети. Пример см. в разделе [Пример. Оперативное восстановление файла, доступного для чтения и записи (модель полного восстановления)](example-online-restore-of-a-read-write-file-full-recovery-model.md).  
  
     Журнал транзакций никогда не усекается после создания резервной копии только для копирования.  
  
 Резервные копии только для копирования записываются в столбец **is_copy_only** таблицы [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) .  
  
## <a name="to-create-a-copy-only-backup"></a>Создание резервной копии только для копирования  
 Резервную копию только для копирования можно создать с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или PowerShell.  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
1.  На странице **Общие** диалогового окна **Создание резервной копии базы данных** выберите **Резервная копия только для копирования** .  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 Требуемый синтаксис [!INCLUDE[tsql](../../../includes/tsql-md.md)] выглядит следующим образом:  
  
-   Для полных резервных копий только для копирования:  
  
     РЕЗЕРВное *database_name* копирование database_name \<базы*>* данных в backup_device... С COPY_ONLY...  
  
    > [!NOTE]  
    >  Если параметр COPY_ONLY указан одновременно с параметром DIFFERENTIAL, он не имеет эффекта.  
  
-   Для резервных копий журнала только для копирования:  
  
     РЕЗЕРВное *database_name* копирование журнала *\<* database_name*>* в backup_device... С COPY_ONLY...  
  
###  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Использование PowerShell  
  
Используйте командлет `Backup-SqlDatabase` с параметром `-CopyOnly`.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Связанные задачи  

### <a name="to-create-a-full-or-log-backup"></a>Создание полной резервной копии или резервной копии журнала
  
-   [Создание полной резервной копии базы данных (SQL Server)](create-a-full-database-backup-sql-server.md)  
  
-   [Создание резервной копии журнала транзакций (SQL Server)](back-up-a-transaction-log-sql-server.md)  
  
### <a name="to-view-copy-only-backups"></a>Просмотр резервных копий только для копирования
  
-   [backupset (Transact-SQL)](/sql/relational-databases/system-tables/backupset-transact-sql)  
  
### <a name="to-set-up-and-use-the-sql-server-powershell-provider"></a>Настройка и использование поставщика SQL Server PowerShell
  
-   [Поставщик SQL Server PowerShell](../../powershell/sql-server-powershell-provider.md)  

## <a name="see-also"></a>См. также:  
 [Общие сведения о резервном копировании (SQL Server)](backup-overview-sql-server.md)   
 [Модели восстановления (SQL Server)](recovery-models-sql-server.md)   
 [Копирование баз данных с помощью резервного копирования и восстановления](../databases/copy-databases-with-backup-and-restore.md)   
 [Обзор процессов восстановления (SQL Server)](restore-and-recovery-overview-sql-server.md)  
