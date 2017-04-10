---
title: "MSSQL_ENG003724 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG003724, ошибка"
ms.assetid: 10cb119d-92df-4124-b85d-cd2f2666c99c
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# MSSQL_ENG003724
    
## Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3724|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Невозможно %S_MSG %S_MSG "%.*ls", так как она используется для репликации.|  
  
## Объяснение  
 При репликации объектов в базе данных они помечаются как реплицированные в системной таблице **sysarticles** (для репликации моментальных снимков и публикаций транзакций) или **sysmergearticles** (для публикаций слиянием). При попытке удалить реплицированный объект возникает данная ошибка.  
  
## Действие пользователя  
 Убедитесь в том, что объект базы данных не подвергался репликации, прежде чем предпримете попытку удалить его. Например:  
  
-   Если данная ошибка появляется в базе данных публикации, удалите статью из публикации, прежде чем удалить объект. Дополнительные сведения см. в разделе [Добавление и удаление статей в существующих публикациях](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
-   Если данная ошибка появляется в базе данных подписки, удалите подписку, прежде чем удалить объект. Дополнительные сведения см. в разделе [подписаться на публикации](../../relational-databases/replication/subscribe-to-publications.md). Для подписок на публикации транзакций имеется возможность удаления подписки на отдельную статью вместо удаления всей публикации. Дополнительные сведения см. в разделе [sp_dropsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md).  
  
 Если эта ошибка возникает в базе данных, не реплицируются, выполнение [sp_removedbreplication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) Чтобы убедиться, что объекты базы данных не помечены как реплицированные.  
  
## См. также:  
 [Ошибки и события ссылку & #40; Репликация & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  