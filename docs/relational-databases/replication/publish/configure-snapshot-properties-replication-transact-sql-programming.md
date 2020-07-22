---
title: Настройка свойств моментальных снимков (хранимая процедура репликации)
description: Используйте хранимые процедуры репликации для настройки свойств моментального снимка для моментальных снимков или публикаций транзакций.
ms.custom: seo-lt-2019
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots [SQL Server replication], properties
ms.assetid: 978d150f-8971-458a-ab2b-3beba5937b46
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 0f2aa6766320367af813852a2d1012ab6c7fef29
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86912420"
---
# <a name="configure-snapshot-properties-replication-transact-sql-programming"></a>настроить свойства моментального снимка (программирование репликации на языке Transact-SQL)
[!INCLUDE[sql-asdbmi](../../../includes/applies-to-version/sql-asdbmi.md)]
  Свойства моментального снимка можно определять и изменять программно с помощью хранимых процедур репликации, где используемые хранимые процедуры зависят от типа публикации.  
  
### <a name="to-configure-snapshot-properties-when-creating-a-snapshot-or-transactional-publication"></a>Настройка свойств моментального снимка при создании снимка публикации транзакций  
  
1.  Выполните процедуру [sp_addpublication](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)на издателе. Укажите имя публикации в параметре `@publication`, значение **snapshot** или **continuous** в параметре `@repl_freq`, а также один или несколько следующих параметров, связанных с моментальными снимками:  
  
    -   `@alt_snapshot_folder` — определяет путь, где хранится моментальный снимок для этой публикации, если он отличается от папки хранения мгновенных снимков по умолчанию.    
    -   `@compress_snapshot` — определяет значение **true**, если файлы моментальных снимков в альтернативной папке моментальных снимков сжаты в формате CAB [!INCLUDE[msCoName](../../../includes/msconame-md.md)].    
    -   `@pre_snapshot_script` — определяет имя и полный путь к **SQL**-файлу, который будет выполнен в подписчике во время инициализации до применения исходного моментального снимка.    
    -   `@post_snapshot_script` — определяет имя и полный путь к **SQL**-файлу, который будет выполнен в подписчике во время инициализации после применения исходного моментального снимка.    
    -   `@snapshot_in_defaultfolder` — укажите значение **false**, если моментальный снимок доступен только в месте хранения, отличном от места по умолчанию.  
  
     Дополнительные сведения о создании публикаций см. в разделе [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
### <a name="to-configure-snapshot-properties-when-creating-a-merge-publication"></a>Настройка свойств моментального снимка при создании снимка публикации слиянием  
  
1.  Выполните процедуру [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)на издателе. Укажите имя публикации в параметре `@publication`, значение **snapshot** или **continuous** в параметре `@repl_freq`, а также один или несколько следующих параметров, связанных с моментальными снимками:  
  
    -   **alt_snapshot_folder** — определяет путь, где хранится моментальный снимок для этой публикации, если он отличается от папки хранения мгновенных снимков по умолчанию.    
    -   `@compress_snapshot` — укажите значение **true**, если файлы моментальных снимков в альтернативной папке моментальных снимков сжаты в формате CAB.   
    -   `@pre_snapshot_script` — определяет имя и полный путь к **SQL**-файлу, который будет выполнен в подписчике во время инициализации до применения исходного моментального снимка.    
    -   `@post_snapshot_script` — определяет имя и полный путь к **SQL**-файлу, который будет выполнен в подписчике во время инициализации после применения исходного моментального снимка.    
    -   `@snapshot_in_defaultfolder` — укажите значение **false**, если моментальный снимок доступен только в месте хранения, отличном от места по умолчанию.  
  
2.  Дополнительные сведения о создании публикаций см. в разделе [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
### <a name="to-modify-snapshot-properties-of-an-existing-snapshot-or-transactional-publication"></a>Изменение свойств существующего моментального снимка публикации транзакций  
  
1.  На издателе в базе данных публикации выполните процедуру [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md). Укажите значение **1** для `@force_invalidate_snapshot` и одно из следующих значений для `@property`:  
  
    -   **alt_snapshot_folder** — также укажите новый путь к альтернативной папке моментальных снимков в параметре `@value`.    
    -   **compress_snapshot** — также задайте значение **true** или **false** в параметре `@value`, чтобы указать, сжаты ли файлы моментальных снимков в альтернативной папке в формате CAB.    
    -   **pre_snapshot_script** — также в параметре `@value` укажите имя и полный путь к **SQL**-файлу, который будет выполнен в подписчике во время инициализации до применения исходного моментального снимка.    
    -   **pre_snapshot_script** — также в параметре `@value` укажите имя и полный путь к **SQL**-файлу, который будет выполнен в подписчике во время инициализации после применения исходного моментального снимка.    
    -   **snapshot_in_defaultfolder** — также укажите значение **true** или **false** , чтобы указать, доступен ли моментальный снимок только в месте хранения, отличном от места по умолчанию.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_changepublication_snapshot](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md)(необязательно). Укажите параметр `@publication` и один или несколько параметров планирования или учетных данных безопасности, которые нужно изменить.  
  
    > [!IMPORTANT]  
    >  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
3.  Чтобы сформировать новый моментальный снимок, запустите агент моментальных снимков репликации ( [Replication Snapshot Agent](../../../relational-databases/replication/agents/replication-snapshot-agent.md) ) из командной строки или задание агента моментальных снимков. Дополнительные сведения см. в разделе [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
### <a name="to-modify-snapshot-properties-of-an-existing-merge-publication"></a>Изменение свойств существующего моментального снимка публикации слиянием  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md). Укажите значение **1** для `@force_invalidate_snapshot` и одно из следующих значений для `@property**`:  
  
    -   **alt_snapshot_folder** — также укажите новый путь к альтернативной папке моментальных снимков в параметре `@value`.    
    -   **compress_snapshot** — также задайте значение **true** или **false** в параметре `@value`, чтобы указать, сжаты ли файлы моментальных снимков в альтернативной папке в формате CAB.    
    -   **pre_snapshot_script** — также в параметре `@value` укажите имя и полный путь к **SQL**-файлу, который будет выполнен в подписчике во время инициализации до применения исходного моментального снимка.    
    -   **pre_snapshot_script** — также в параметре `@value` укажите имя и полный путь к **SQL**-файлу, который будет выполнен в подписчике во время инициализации после применения исходного моментального снимка.    
    -   **snapshot_in_defaultfolder** — также укажите значение **true** или **false** , чтобы указать, доступен ли моментальный снимок только в месте хранения, отличном от места по умолчанию.  
  
2.  Чтобы сформировать новый моментальный снимок, запустите агент моментальных снимков репликации ( [Replication Snapshot Agent](../../../relational-databases/replication/agents/replication-snapshot-agent.md) ) из командной строки или задание агента моментальных снимков. Дополнительные сведения см. в разделе [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
## <a name="example"></a>Пример  
 В этом примере создается публикация, использующая альтернативную папку моментальных снимков и сжатый моментальный снимок.  
  
 [!code-sql[HowTo#sp_mergealtsnapshot](../../../relational-databases/replication/codesnippet/tsql/configure-snapshot-prope_1.sql)]  
  
## <a name="see-also"></a>См. также:  
 [Изменение параметров моментального снимка](../../../relational-databases/replication/snapshot-options.md)   
 [Выполнение скриптов до и после применения моментального снимка](../../../relational-databases/replication/snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied)   
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Передача моментальных снимков через FTP](../../../relational-databases/replication//publish/deliver-a-snapshot-through-ftp.md)   
 [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)  
  
  
