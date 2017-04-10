---
title: "Резервные копии только для копирования (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "08/10/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "резервные копии только для копирования [SQL Server]"
  - "COPY_ONLY, параметр [BACKUP, инструкция]"
  - "резервные копии [SQL Server], резервные копии только для копирования"
ms.assetid: f82d6918-a5a7-4af8-868e-4247f5b00c52
caps.latest.revision: 48
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 47
---
# Резервные копии только для копирования (SQL Server)
  *Резервная копия только для копирования* — это резервная копия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которая не зависит от обычной последовательности создания традиционных резервных копий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Обычно создание резервного копирования приводит к изменению базы данных и влияет на то, как будут восстанавливаться последующие резервные копии. Однако иногда приходится выполнять резервное копирование базы данных для особых нужд, когда это не сказывается на общем процессе резервного копирования и восстановления. Этой цели служат резервные копии только для копирования.  
  
 Резервные копии только для копирования имеют следующие типы.  
  
-   Полные резервные копии только для копирования (все модели восстановления).  
  
     Резервная копия только для копирования не может служить в качестве базовой копии для разностного копирования или разностного резервного копирования и не влияет на базовую копию для разностного копирования.  
  
     Операция восстановления полной резервной копии только для копирования аналогична операции восстановления любой полной резервной копии.  
  
-   Резервные копии журналов только для копирования (модель полного восстановления и модель восстановления с неполным протоколированием).  
  
     Резервная копия журналов только для копирования сохраняет текущую точку архивирования журнала и, следовательно, не влияет на последовательность обычных резервных копий журналов. Никакой необходимости в резервных копиях журналов только для копирования обычно нет. Вместо этого можно создать новую обычную резервную копию журналов (с параметром WITH NORECOVERY), затем использовать ее совместно со всеми остальными ранее созданными резервными копиями журналов, которые необходимы для последовательности восстановления. Однако резервная копия журналов только для копирования иногда может быть полезна для выполнения восстановления в сети. Пример см. в разделе [Пример. Оперативное восстановление файла, доступного для чтения и записи (модель полного восстановления)](../../relational-databases/backup-restore/example-online-restore-of-a-read-write-file-full-recovery-model.md).  
  
     Журнал транзакций никогда не усекается после создания резервной копии только для копирования.  
  
 Резервные копии только для копирования записываются в столбец **is_copy_only** таблицы [backupset](../../relational-databases/system-tables/backupset-transact-sql.md).  
  
## Создание резервной копии только для копирования  
 Резервную копию только для копирования можно создать с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или PowerShell.  

### Примеры  
###  <a name="SSMSProcedure"></a> A.  Использование среды SQL Server Management Studio  
В этом примере резервная копия только для копирования для базы данных `Sales` будет заархивирована на диск в папку резервных копий по умолчанию.

1.  В **обозревателе объектов** подключитесь к экземпляру компонента SQL Server Database Engine и разверните его.

2.  Разверните узел **Базы данных**, щелкните правой кнопкой `Sales`, укажите на пункт **Задачи**и выберите **Создать резервную копию...**

3.  На странице **Общие** в разделе **Источник** установите флажок **Архивная копия только для копирования**.

4.  Нажмите кнопку **ОК**.

  
###  <a name="TsqlProcedure"></a>Б.  Использование Transact-SQL  
В этом примере создается резервная копия только для копирования для базы данных `Sales` с использованием параметра COPY_ONLY.  Также создается резервная копия только для копирования для журнала транзакций.

```tsql
BACKUP DATABASE Sales
TO DISK = 'E:\BAK\Sales_Copy.bak'
WITH COPY_ONLY;

BACKUP LOG Sales
TO DISK = 'E:\BAK\Sales_LogCopy.trn'
WITH COPY_ONLY;
```
  
> [!NOTE]  
> Если параметр COPY_ONLY указан одновременно с параметром DIFFERENTIAL, он не имеет эффекта.  

  
###  <a name="PowerShellProcedure"></a>В.  Использование PowerShell  
В этом примере создается резервная копия только для копирования для базы данных `Sales` с использованием параметра -CopyOnly.  
```powershell
Backup-SqlDatabase -ServerInstance 'SalesServer' -Database 'Sales' -BackupFile 'E:\BAK\Sales_Copy.bak' -CopyOnly
```  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Создание полной резервной копии или резервной копии журнала**  
  
-   [Создание полной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [Создание резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
 **Просмотр резервных копий только для копирования**  
  
-   [backupset (Transact-SQL)](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [SQL Server PowerShell, поставщик](../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
 [&#91;В начало&#93;](#Top)  
  
## См. также:  
 [Общие сведения о резервном копировании (SQL Server)](../../relational-databases/backup-restore/backup-overview-sql-server.md)   
 [Модели восстановления (SQL Server)](../../relational-databases/backup-restore/recovery-models-sql-server.md)   
 [Копирование баз данных путем создания и восстановления резервных копий](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)   
 [Обзор процессов восстановления (SQL Server)](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)  
[BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)  
[Backup-SqlDatabase](https://technet.microsoft.com/library/mt683378.aspx)

  