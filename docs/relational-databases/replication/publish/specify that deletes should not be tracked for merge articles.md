---
title: "отключить отслеживание операций удаления для статей публикации слиянием (программирование репликации на языке Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
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
  - "отслеживание условного удаления [репликация SQL Server]"
  - "репликация слиянием [репликация SQL Server], отслеживание условного удаления"
ms.assetid: 0fe330ca-5fb5-422e-ad6f-92fb5d6a3b6c
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# отключить отслеживание операций удаления для статей публикации слиянием (программирование репликации на языке Transact-SQL)
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 По умолчанию репликация слиянием производит синхронизацию команд DELETE между издателем и подписчиком. Репликация слиянием позволяет извлекать строки из базы данных подписки даже в том случае, если они были удалены из публикации (и наоборот). При создании новой статьи можно отключить выполнение команд DELETE программным путем, либо сделать это позже с помощью хранимых процедур репликации.  
  
> [!IMPORTANT]  
>  Включение этой функции приведет к потере конвергенции, то есть возникнет несоответствие данных, содержащихся на подписчике и на издателе. Потребуется реализация собственного механизма очистки удаленных строк.  
  
### Отключение обработки команд удаления для новой статьи слияния  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Укажите значение **false** для **@delete_tracking**. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  Если исходная таблица для статьи уже опубликована в другой публикации, значение **delete_tracking** должно быть одинаковым для обеих статей.  
  
### Отключение обработки команд удаления для существующих статей слияния  
  
1.  Чтобы определить, включена ли компенсация ошибок для статьи, выполните [sp_helpmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) и обратите внимание на значение **delete_tracking** в результирующем наборе. Если это значение равно **0**, то команды удаления уже не обрабатываются.  
  
2.  Если значение из шага 1 **1**, выполнение [sp_changemergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) на издателе в базе данных публикации. Укажите значение **delete_tracking** для **@property**, а значение **false** для **@value**.  
  
    > [!NOTE]  
    >  Если исходная таблица для статьи уже опубликована в другой публикации, значение **delete_tracking** должно быть одинаковым для обеих статей.  
  
## См. также:  
 [Оптимизация производительности репликации слиянием с помощью отслеживания условного удаления](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  