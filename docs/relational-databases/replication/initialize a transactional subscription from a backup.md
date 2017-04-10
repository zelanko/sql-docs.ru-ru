---
title: "инициализировать подписку на публикацию транзакций из резервной копии (программирование репликации на языке Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/29/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "ручная инициализация подписки [репликация SQL Server]"
  - "подписки [репликация SQL Server], инициализация"
  - "инициализация подписок [репликация SQL Server], без моментальных снимков"
  - "репликация транзакций, резервное копирование и восстановление"
  - "резервные копии [репликация SQL Server], репликация транзакций"
ms.assetid: d0637fc4-27cc-4046-98ea-dc86b7a3bd75
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# инициализировать подписку на публикацию транзакций из резервной копии (программирование репликации на языке Transact-SQL)
  Хотя инициализация подписки на публикацию транзакций осуществляется через моментальный снимок, она также может быть выполнена с помощью хранимых процедур репликации. Дополнительные сведения см. в разделе [инициализировать транзакционной подписки без моментального снимка](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
### Инициализация подписчика на публикацию транзакций из резервной копии  
  
1.  Для существующей публикации, убедитесь, что публикация поддерживает возможность инициализации из резервной копии, выполнив [sp_helppublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) на издателе в базе данных публикации. Обратите внимание на значение **allow_initialize_from_backup** в результирующем наборе.  
  
    -   Если оно равно **1**, то публикация поддерживает данную функцию.  
  
    -   Если значение равно **0**, выполнение [sp_changepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) на издателе в базе данных публикации. Укажите значение **allow_initialize_from_backup** для **@property** и значение **true** для **@value**.  
  
2.  Создать публикацию, выполнить [sp_addpublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) на издателе в базе данных публикации. Укажите значение **true** для **allow_initialize_from_backup**. Дополнительные сведения см. в статье [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
    > [!WARNING]  
    >  Чтобы предотвратить отсутствие данных подписчика при использовании **sp_addpublication** с `@allow_initialize_from_backup = N'true'`, всегда используйте `@immediate_sync = N'true'`.  
  
3.  Создайте резервную копию базы данных публикации с помощью [резервное копирование и #40; Transact-SQL & #41;](../../t-sql/statements/backup-transact-sql.md) инструкция.  
  
4.  Восстановите резервную копию на подписчике с помощью [восстановления & #40; Transact-SQL & #41;](../Topic/RESTORE%20\(Transact-SQL\).md) инструкция.  
  
5.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Укажите значения следующих параметров.  
  
    -   **@sync_type** -значение **инициализации при помощи резервной копии**.  
  
    -   **@backupdevicetype** -тип устройства резервного копирования: **логических** (по умолчанию), **диск**, или **ленту**.  
  
    -   **@backupdevicename** -логическое или физическое устройство резервного копирования для восстановления.  
  
         Логическое устройство, укажите имя устройства резервного копирования, указанное при **sp_addumpdevice** был использован для создания устройства.  
  
         Для физического устройства укажите полный путь и имя файла, например: `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\BACKUP\Mybackup.dat'` или `TAPE = '\\.\TAPE0'`.  
  
    -   (Необязательно) **@password** -пароль, предоставленный при создании резервного набора.  
  
    -   (Необязательно) **@mediapassword** -пароль, который был предоставлен при форматировании набора носителей.  
  
    -   (Необязательно) **@fileidhint** -идентификатор для резервного копирования, которую требуется восстановить. Например, значение **1** указывает первый резервный набор данных на носителе данных резервных копий, а значение **2** — второй резервный набор данных.  
  
    -   (Необязательно для ленточных устройств) **@unload** -Укажите значение **1** (по умолчанию), если лента должна быть выгружен из дисковода после завершения восстановления и **0** если он не должен быть выгружен.  
  
6.  (Необязательно) Подписки по запросу, выполните [sp_addpullsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md) и [sp_addpullsubscription_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) на подписчике в базе данных подписки. Дополнительные сведения см. в разделе [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
7.  (Необязательно) Запустите агент распространителя. Дополнительные сведения см. в разделе [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) или [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
## См. также:  
 [Копирование баз данных путем создания и восстановления резервных копий](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)   
 [Резервное копирование и восстановление баз данных SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  