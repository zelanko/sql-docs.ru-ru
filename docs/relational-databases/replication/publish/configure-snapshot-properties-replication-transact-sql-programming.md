---
title: "настроить свойства моментального снимка (программирование репликации на языке Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
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
  - "моментальные снимки [репликация SQL Server], свойства"
ms.assetid: 978d150f-8971-458a-ab2b-3beba5937b46
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# настроить свойства моментального снимка (программирование репликации на языке Transact-SQL)
  Свойства моментального снимка можно определять и изменять программно с помощью хранимых процедур репликации, где используемые хранимые процедуры зависят от типа публикации.  
  
### Настройка свойств моментального снимка при создании снимка публикации транзакций  
  
1.  На издателе, хранимую [sp_addpublication](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md). Укажите имя публикации для **@publication**, значение **моментального снимка** или **непрерывного** для **@repl_freq**, и один или несколько из следующих параметров, связанных с моментальными снимками:  
  
    -   **@alt_snapshot_folder** -указать путь, если моментальный снимок для этой публикации осуществляется из этого расположения вместо или в дополнение к папке моментальных снимков по умолчанию.  
  
    -   **@compress_snapshot** -Укажите значение **true** Если файлы моментальных снимков в альтернативной папке моментальных снимков сжаты в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] CAB-файл.  
  
    -   **@pre_snapshot_script** — Укажите полный путь и имя файла **.sql** файл, который будет выполнен на подписчике во время инициализации до применения исходного моментального снимка.  
  
    -   **@post_snapshot_script** — Укажите полный путь и имя файла **.sql** файл, который будет выполнен на подписчике во время инициализации после применения исходного моментального снимка.  
  
    -   **@snapshot_in_defaultfolder** -Укажите значение **false** Если моментальный снимок доступен только в месте не по умолчанию.  
  
     Дополнительные сведения о создании публикаций см. в разделе [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
### Настройка свойств моментального снимка при создании снимка публикации слиянием  
  
1.  На издателе, хранимую [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Укажите имя публикации для **@publication**, значение **моментального снимка** или **непрерывного** для **@repl_freq**, и один или несколько из следующих параметров, связанных с моментальными снимками:  
  
    -   **@alt_snapshot_folder** -указать путь, если моментальный снимок для этой публикации осуществляется из этого расположения вместо или в дополнение к папке моментальных снимков по умолчанию.  
  
    -   **@compress_snapshot** -Укажите значение **true** Если файлы моментальных снимков в альтернативной папке моментальных снимков сжимаются в CAB-файл.  
  
    -   **@pre_snapshot_script** — Укажите полный путь и имя файла **.sql** файл, который будет выполнен на подписчике во время инициализации до применения исходного моментального снимка.  
  
    -   **@post_snapshot_script** — Укажите полный путь и имя файла **.sql** файл, который будет выполнен на подписчике во время инициализации после применения исходного моментального снимка.  
  
    -   **@snapshot_in_defaultfolder** -Укажите значение **false** Если моментальный снимок доступен только в месте не по умолчанию.  
  
2.  Дополнительные сведения о создании публикаций см. в разделе [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
### Изменение свойств существующего моментального снимка публикации транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md). Укажите значение **1** для **@force_invalidate_snapshot** и одно из следующих значений для **@property**:  
  
    -   **alt_snapshot_folder** -также указать новый путь к папке моментальных **@value**.  
  
    -   **compress_snapshot** -также указать значение либо **true** или **false** для **@value** для указания, является ли файлы моментальных снимков в альтернативной папке моментальных снимков сжимаются в CAB-файл.  
  
    -   **pre_snapshot_script** — также для **@value** Укажите полный путь и имя файла **.sql** файл, который будет выполнен на подписчике во время инициализации до применения исходного моментального снимка.  
  
    -   **post_snapshot_script** — также для **@value** Укажите полный путь и имя файла **.sql** файл, который будет выполнен на подписчике во время инициализации после применения исходного моментального снимка.  
  
    -   **snapshot_in_defaultfolder** -также указать значение либо **true** или **false** для указания ли моментальный снимок доступен только в месте не по умолчанию.  
  
2.  (Необязательно) На издателе в базе данных публикации выполните хранимую процедуру [sp_changepublication_snapshot](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md). Укажите параметр **@publication** и один или несколько параметров планирования или учетных данных безопасности, которые нужно изменить.  
  
    > [!IMPORTANT]  
    >  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
3.  Чтобы сформировать новый моментальный снимок, запустите агент моментальных снимков репликации ( [Replication Snapshot Agent](../../../relational-databases/replication/agents/replication-snapshot-agent.md) ) из командной строки или задание агента моментальных снимков. Дополнительные сведения см. в статье [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
### Изменение свойств существующего моментального снимка публикации слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md). Укажите значение **1** для **@force_invalidate_snapshot** и одно из следующих значений для **@property**:  
  
    -   **alt_snapshot_folder** -также указать новый путь к папке моментальных **@value**.  
  
    -   **compress_snapshot** -также указать значение либо **true** или **false** для **@value** для указания, является ли файлы моментальных снимков в альтернативной папке моментальных снимков сжимаются в CAB-файл.  
  
    -   **pre_snapshot_script** — также для **@value** Укажите полный путь и имя файла **.sql** файл, который будет выполнен на подписчике во время инициализации до применения исходного моментального снимка.  
  
    -   **post_snapshot_script** — также для **@value** Укажите полный путь и имя файла **.sql** файл, который будет выполнен на подписчике во время инициализации после применения исходного моментального снимка.  
  
    -   **snapshot_in_defaultfolder** -также указать значение либо **true** или **false** для указания ли моментальный снимок доступен только в месте не по умолчанию.  
  
2.  Чтобы сформировать новый моментальный снимок, запустите агент моментальных снимков репликации ( [Replication Snapshot Agent](../../../relational-databases/replication/agents/replication-snapshot-agent.md) ) из командной строки или задание агента моментальных снимков. Дополнительные сведения см. в статье [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
## Пример  
 В этом примере создается публикация, использующая альтернативную папку моментальных снимков и сжатый моментальный снимок.  
  
 [!code-sql[HowTo#sp_mergealtsnapshot](../../../relational-databases/replication/codesnippet/tsql/configure-snapshot-prope_1.sql)]  
  
## См. также:  
 [Альтернативные местоположения папки моментальных снимков](../../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [Сжатые моментальные снимки](../../../relational-databases/replication/compressed-snapshots.md)   
 [Выполнение скриптов до и после применения моментального снимка](../../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)   
 [Основные понятия системных хранимых процедур репликации](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Передача моментальных снимков через FTP](../../../relational-databases/replication/transfer-snapshots-through-ftp.md)   
 [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)  
  
  