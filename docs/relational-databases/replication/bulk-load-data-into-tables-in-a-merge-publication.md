---
title: "Массовая загрузка данных в таблицы при публикации слиянием | Документация Майкрософт"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: TSQL
helpviewer_keywords:
- bulk load [SQL Server replication]
- merge replication bulk loading [SQL Server replication]
- sp_addtabletocontents
ms.assetid: 16e6498a-b449-4051-aec4-ea814a2ad993
caps.latest.revision: "33"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1bbacd34cc3bc10e398c3d467d2c430b8ca535bc
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="bulk-load-data-into-tables-in-a-merge-publication"></a>Массовая загрузка данных в таблицы при публикации слиянием
  При загрузке данных в таблицы с использованием методов, описанных в разделе [bcp Utility](../../tools/bcp-utility.md) , или инструкцией [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) триггеры репликации слиянием, которые обеспечивают отслеживание данных в системной таблице [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) , выполняться не будут. В этом случае можно либо принудительно выполнять в процессе загрузки данных триггеры репликации слиянием, либо с помощью хранимых процедур репликации программным путем вставить созданные метаданные репликации после завершения массового копирования.  
  
### <a name="to-bulk-load-data-into-tables-published-by-merge-replication-using-the-bcp-utility"></a>Массовая загрузка данных в таблицы, публикуемые в репликации слиянием с помощью программы bcp  
  
1.  На издателе или на подписчике запустите программу [bcp Utility](../../tools/bcp-utility.md) или выполните инструкцию [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) , чтобы вставить данные в таблицу, публикуемую в репликации слиянием.  
  
2.  Одним из следующих методов сформируйте для вставленных данных метаданные репликации.  
  
    -   Выполните операцию массового копирования с параметром FIRE_TRIGGERS.  
  
    -   В базе данных, в которую вставлены данные, выполните процедуру [sp_addtabletocontents (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql.md). Укажите в параметре **@table_name**.  
  
  
