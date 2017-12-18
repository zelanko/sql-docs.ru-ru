---
title: "Фиктивное обновление для статьи публикации слиянием (программирование репликации на языке T-SQL) | Документация Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
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
ms.openlocfilehash: d058cd7faeaccb781bcebf1968ac32c4400cf106
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming"></a>выполнить фиктивное обновление для статьи репликации слиянием (программирование репликации на языке Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Триггеры являются частью процесса репликации слиянием. При обновлении опубликованной таблицы срабатывают триггеры обновления. В некоторых случаях данные могут обновляться без срабатывания триггеров, например, при выполнении операций WRITETEXT и UPDATETEXT. В таких случаях для репликации изменения необходимо явно добавить фиктивную инструкцию UPDATE. Это можно сделать с помощью хранимых процедур репликации.  
  
### <a name="to-add-a-dummy-update-statement"></a>Добавление фиктивной инструкции UPDATE  
  
1.  Выполните операцию (например UPDATETEXT) для строки таблицы, опубликованной в репликации слияния, требующую фиктивного обновления.  
  
2.  На сервере (издателя или подписчика) в той базе данных, где было сделано изменение, выполните процедуру [sp_mergedummyupdate &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql.md). Укажите в параметре **@source_object**таблицу, в которой было сделано изменение, а в параметре **@rowguid**.  
  
3.  Синхронизируйте подписку для репликации измененной строки.  
  
  
