---
title: "Фиктивное обновление для статьи публикации слиянием (программирование репликации на языке T-SQL) | Документация Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: TSQL
helpviewer_keywords:
- sp_mergedummyupdate
- dummy updates [SQL Server replication]
ms.assetid: 2f339210-4d85-4843-bd94-e86f7100d3ef
caps.latest.revision: "31"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2df0a31b6397cfce16c4d12b43dbfc1031c6929b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming"></a>выполнить фиктивное обновление для статьи репликации слиянием (программирование репликации на языке Transact-SQL)
  Триггеры являются частью процесса репликации слиянием. При обновлении опубликованной таблицы, срабатывают триггеры Update. В некоторых случаях данные могут обновляться без срабатывания триггеров, например, при выполнении операций WRITETEXT и UPDATETEXT. В таких случаях для репликации изменения необходимо явно добавить фиктивную инструкцию UPDATE. Это можно сделать с помощью хранимых процедур репликации.  
  
### <a name="to-add-a-dummy-update-statement"></a>Добавление фиктивной инструкции UPDATE  
  
1.  Выполните операцию (например UPDATETEXT) для строки таблицы, опубликованной в репликации слияния, требующую фиктивного обновления.  
  
2.  На сервере (издателя или подписчика) в той базе данных, где было сделано изменение, выполните процедуру [sp_mergedummyupdate &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql.md). Укажите в параметре **@source_object**таблицу, в которой было сделано изменение, а в параметре **@rowguid**.  
  
3.  Синхронизируйте подписку для репликации измененной строки.  
  
  
