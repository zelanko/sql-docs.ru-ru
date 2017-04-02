---
title: "MSSQL_REPL020011 | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_REPL020011, ошибка"
ms.assetid: f72072d7-bbb6-48ad-ac88-afa74aeb4d58
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# MSSQL_REPL020011
    
## Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|20011|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Процессу не удалось выполнить '%1' на '%2'.|  
  
## Объяснение  
 Эта ошибка может возникать в ряде случаев во время обработки репликации транзакций, например, когда агент чтения журнала выполняет **sp_replcmds** (процессу не удалось выполнить 'хранимую процедуру sp_replcmds' на \< ServerName>) или **sp_repldone** (процессу не удалось выполнить 'хранимую процедуру sp_repldone' на \< ServerName>).  
  
## Действие пользователя  
 Если эта ошибка возникает в базе данных, который вы только что была восстановлена из резервной копии, убедитесь, были выполнены шаги, описанные в документации по резервного копирования и восстановления, включая выполнение **sp_replrestart** при необходимости. Дополнительные сведения см. в разделе [Strategies for Backing Up and Restoring Snapshot and Transactional Replication](../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).  
  
 Эта ошибка является внутренней ошибкой обработки, и если она возникает в ситуациях, отличных от восстановления, то она обычно указывает на необходимость удаления и перенастройки репликации. Если не удается удалить репликацию, обратитесь за консультацией в службу поддержки пользователей.  
  
## См. также:  
 [Ошибки и события ссылку & #40; Репликация & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [sp_replcmds & #40; Transact-SQL и #41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone & #40; Transact-SQL и #41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)  
  
  