---
title: logmarkhistory (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- logmarkhistory
- logmarkhistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- logmarkhistory system table
ms.assetid: 5c1becc5-f34e-4869-bf69-dfafab684540
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0674bf993087b349d4e8b6f9947c65167e94df8e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68001799"
---
# <a name="logmarkhistory-transact-sql"></a>logmarkhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит одну строку для каждой зафиксированной помеченной транзакции. Эта таблица хранится в базе данных **msdb** .  
  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|Локальная база данных, в которой возникла помеченная транзакция.|  
|**mark_name**|**nvarchar(128)**|Предоставляемое пользователем имя помеченной транзакции.|  
|**nописание**|**nvarchar(255)**|Предоставляемое пользователем описание помеченной транзакции. Может иметь значение NULL.|  
|**user_name**|**nvarchar(128)**|Имя пользователя базы данных, выполнившего помеченную транзакцию. Может иметь значение NULL.|  
|**lsn**|**numeric(25,0)**|Номер LSN записи транзакции с пометкой.|  
|**mark_time**|**datetime**|Время фиксации помеченной транзакции (локальное время).|  
  
## <a name="see-also"></a>См. также:  
 [Восстановление базы данных до помеченной транзакции &#40;SQL Server Management Studio&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)   
 [Используйте помеченные транзакции для согласованного восстановления связанных баз данных &#40;модели полного восстановления&#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md)   
 [Системные таблицы (Transact-SQL)](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
