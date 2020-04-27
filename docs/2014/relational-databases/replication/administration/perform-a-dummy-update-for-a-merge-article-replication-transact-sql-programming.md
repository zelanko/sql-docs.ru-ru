---
title: Выполнить фиктивное обновление для статьи публикации слиянием (программирование репликации на языке Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_mergedummyupdate
- dummy updates [SQL Server replication]
ms.assetid: 2f339210-4d85-4843-bd94-e86f7100d3ef
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 691988cd229f9b0c9ab81f31713a2b2e46806bdb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63162004"
---
# <a name="perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming"></a>выполнить фиктивное обновление для статьи репликации слиянием (программирование репликации на языке Transact-SQL)
  Триггеры являются частью процесса репликации слиянием. При обновлении опубликованной таблицы, срабатывают триггеры Update. В некоторых случаях данные могут обновляться без срабатывания триггеров, например, при выполнении операций WRITETEXT и UPDATETEXT. В таких случаях для репликации изменения необходимо явно добавить фиктивную инструкцию UPDATE. Это можно сделать с помощью хранимых процедур репликации.  
  
### <a name="to-add-a-dummy-update-statement"></a>Добавление фиктивной инструкции UPDATE  
  
1.  Выполните операцию (например UPDATETEXT) для строки таблицы, опубликованной в репликации слияния, требующую фиктивного обновления.  
  
2.  На сервере (издателя или подписчика) в той базе данных, где было сделано изменение, выполните процедуру [sp_mergedummyupdate &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql). Укажите таблицу **@source_object**, в которой было внесено изменение, и уникальный идентификатор измененной строки для **@rowguid**.  
  
3.  Синхронизируйте подписку для репликации измененной строки.  
  
  
