---
title: Фиктивное обновление для статьи публикации слиянием (программирование репликации на языке T-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_mergedummyupdate
- dummy updates [SQL Server replication]
ms.assetid: 2f339210-4d85-4843-bd94-e86f7100d3ef
caps.latest.revision: 31
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: eea3359fa0c0d3cbf91621277ce2737bbb5fc60b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32952919"
---
# <a name="perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming"></a>выполнить фиктивное обновление для статьи репликации слиянием (программирование репликации на языке Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Триггеры являются частью процесса репликации слиянием. При обновлении опубликованной таблицы, срабатывают триггеры Update. В некоторых случаях данные могут обновляться без срабатывания триггеров, например, при выполнении операций WRITETEXT и UPDATETEXT. В таких случаях для репликации изменения необходимо явно добавить фиктивную инструкцию UPDATE. Это можно сделать с помощью хранимых процедур репликации.  
  
### <a name="to-add-a-dummy-update-statement"></a>Добавление фиктивной инструкции UPDATE  
  
1.  Выполните операцию (например UPDATETEXT) для строки таблицы, опубликованной в репликации слияния, требующую фиктивного обновления.  
  
2.  На сервере (издателя или подписчика) в той базе данных, где было сделано изменение, выполните процедуру [sp_mergedummyupdate &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql.md). Укажите в параметре **@source_object**таблицу, в которой было сделано изменение, а в параметре **@rowguid**.  
  
3.  Синхронизируйте подписку для репликации измененной строки.  
  
  
