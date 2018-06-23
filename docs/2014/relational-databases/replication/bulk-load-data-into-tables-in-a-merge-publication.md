---
title: Массовая загрузка данных в таблицы в публикации слиянием (Программирование репликации Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- bulk load [SQL Server replication]
- merge replication bulk loading [SQL Server replication]
- sp_addtabletocontents
ms.assetid: 16e6498a-b449-4051-aec4-ea814a2ad993
caps.latest.revision: 32
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 01c29e00546b0b90fce67fa4242c8398b2392614
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100829"
---
# <a name="bulk-load-data-into-tables-in-a-merge-publication-replication-transact-sql-programming"></a>выполнить массовую загрузку данных в таблицы при публикации слиянием (программирование репликации на языке Transact-SQL)
  При загрузке данных в таблицы с использованием методов, описанных в разделе [bcp Utility](../../tools/bcp-utility.md) , или инструкцией [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) триггеры репликации слиянием, которые обеспечивают отслеживание данных в системной таблице [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql) , выполняться не будут. В этом случае можно либо принудительно выполнять в процессе загрузки данных триггеры репликации слиянием, либо с помощью хранимых процедур репликации программным путем вставить созданные метаданные репликации после завершения массового копирования.  
  
### <a name="to-bulk-load-data-into-tables-published-by-merge-replication-using-the-bcp-utility"></a>Массовая загрузка данных в таблицы, публикуемые в репликации слиянием с помощью программы bcp  
  
1.  На издателе или на подписчике запустите программу [bcp Utility](../../tools/bcp-utility.md) или выполните инструкцию [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) , чтобы вставить данные в таблицу, публикуемую в репликации слиянием.  
  
2.  Одним из следующих методов сформируйте для вставленных данных метаданные репликации.  
  
    -   Выполните операцию массового копирования с параметром FIRE_TRIGGERS.  
  
    -   В базе данных, в которую вставлены данные, выполните процедуру [sp_addtabletocontents (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql). Укажите в параметре **@table_name**.  
  
  
