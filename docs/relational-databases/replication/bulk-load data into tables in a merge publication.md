---
title: "выполнить массовую загрузку данных в таблицы при публикации слиянием (программирование репликации на языке Transact-SQL) | Microsoft Docs"
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
  - "массовая загрузка [репликация SQL Server]"
  - "массовая загрузка данных репликации слиянием [репликация SQL Server]"
  - "sp_addtabletocontents"
ms.assetid: 16e6498a-b449-4051-aec4-ea814a2ad993
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# выполнить массовую загрузку данных в таблицы при публикации слиянием (программирование репликации на языке Transact-SQL)
  При загрузке данных в таблицах с помощью [программы bcp](../../tools/bcp-utility.md) или [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) команд по умолчанию, триггеры репликации слиянием, которые обеспечивают отслеживание данных в [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) Системная таблица не запускаются. В этом случае можно либо принудительно выполнять в процессе загрузки данных триггеры репликации слиянием, либо с помощью хранимых процедур репликации программным путем вставить созданные метаданные репликации после завершения массового копирования.  
  
### Массовая загрузка данных в таблицы, публикуемые в репликации слиянием с помощью программы bcp  
  
1.  На издателе или на подписчике запустите программу [bcp Utility](../../tools/bcp-utility.md) или выполните инструкцию [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) , чтобы вставить данные в таблицу, публикуемую в репликации слиянием.  
  
2.  Одним из следующих методов сформируйте для вставленных данных метаданные репликации.  
  
    -   Выполните операцию массового копирования с параметром FIRE_TRIGGERS.  
  
    -   В базе данных, в которую была вставлена данных, выполнение [sp_addtabletocontents & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql.md). Укажите имя таблицы, в которую были вставлены данные **@table_name**.  
  
  