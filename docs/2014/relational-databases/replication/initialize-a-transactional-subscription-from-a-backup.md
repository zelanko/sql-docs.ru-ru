---
title: Инициализация подписки на публикацию транзакций из резервной копии (программирование репликации на языке Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: d0637fc4-27cc-4046-98ea-dc86b7a3bd75
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1563d58f2d54f77680781e22a162112ade1658e4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85057109"
---
# <a name="initialize-a-transactional-subscription-from-a-backup-replication-transact-sql-programming"></a>инициализировать подписку на публикацию транзакций из резервной копии (программирование репликации на языке Transact-SQL)
  Хотя инициализация подписки на публикацию транзакций осуществляется через моментальный снимок, она также может быть выполнена с помощью хранимых процедур репликации. Дополнительные сведения см. в статье [Инициализация подписки на публикацию транзакций без моментального снимка](initialize-a-transactional-subscription-without-a-snapshot.md).  
  
### <a name="to-initialize-a-transactional-subscriber-from-a-backup"></a>Инициализация подписчика на публикацию транзакций из резервной копии  
  
1.  Убедитесь, что существующая публикация поддерживает возможность инициализации из резервной копии. Для этого в базе данных публикации на издателе выполните хранимую процедуру [sp_helppublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). В результирующем наборе проверьте значение параметра **allow_initialize_from_backup** .  
  
    -   Если оно равно **1**, то публикация поддерживает данную функцию.  
  
    -   Если значение равно **0**, выполните хранимую процедуру [sp_changepublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql) на издателе в базе данных публикации. Укажите значение **allow_initialize_from_backup** для ** \@ Свойства** и значение `true` для параметра ** \@ значение**.  
  
2.  В новой публикации выполните хранимую процедуру [sp_addpublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) на издателе в базе данных публикации. Укажите значение `true` для **allow_initialize_from_backup**. Дополнительные сведения см. [в разделе Создание публикации](publish/create-a-publication.md).  
  
    > [!WARNING]  
    >  Чтобы предотвратить отсутствие данных подписчика, при использовании процедуры **sp_addpublication** с `@allow_initialize_from_backup = N'true'`всегда используйте `@immediate_sync = N'true'`.  
  
3.  Создайте резервную копию базы данных публикации с использованием инструкции [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql).  
  
4.  Восстановите резервную копию на подписчике, выполнив инструкцию [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql).  
  
5.  На издателе в базе данных издателя выполните хранимую процедуру [sp_addsubscription (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql). Укажите значения следующих параметров.  
  
    -   ** \@ sync_type** — значение " **инициализировать с резервной копией**".  
  
    -   ** \@ backupdevicetype** — тип устройства резервного копирования: **логический** (по умолчанию), **диск**или **Лента**.  
  
    -   ** \@ backupdevicename** — логическое или физическое устройство резервного копирования, используемое для восстановления.  
  
         Для логического устройства задайте имя устройства резервного копирования, указанное при создании устройства при помощи хранимой процедуры **sp_addumpdevice** .  
  
         Для физического устройства укажите полный путь и имя файла, например: `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\BACKUP\Mybackup.dat'` или `TAPE = '\\.\TAPE0'`.  
  
    -   Используемых ** \@ Password** — пароль, указанный при создании резервного набора данных.  
  
    -   Используемых ** \@ MEDIAPASSWORD** — пароль, указанный при форматировании набора носителей.  
  
    -   Используемых ** \@ fileidhint** — идентификатор восстанавливаемого резервного набора данных. Например, значение **1** указывает первый резервный набор данных на носителе данных резервных копий, а значение **2** — второй резервный набор данных.  
  
    -   (Необязательно для ленточных устройств) ** \@ выгрузка** — укажите значение **1** (по умолчанию), если лента должна быть выгружена с диска после завершения восстановления, и **0** , если его не нужно выгружать.  
  
6.  (Необязательно.) Для подписки по запросу выполните процедуру [sp_addpullsubscription (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql) и [sp_addpullsubscription_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) на подписчике в базе данных подписки. Дополнительные сведения см. в статье [Создание подписки по запросу](create-a-pull-subscription.md).  
  
7.  (Необязательно) Запустите агент распространителя. Дополнительные сведения см. в разделе [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md) или [Synchronize a Push Subscription](synchronize-a-push-subscription.md).  
  
## <a name="see-also"></a>См. также:  
 [Копирование баз данных путем создания и восстановления резервных копий](../databases/copy-databases-with-backup-and-restore.md)   
 [Резервное копирование и восстановление баз данных SQL Server](../backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  
