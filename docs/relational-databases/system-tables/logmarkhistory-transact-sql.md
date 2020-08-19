---
description: logmarkhistory (Transact-SQL)
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d52c161baa58924a21966ed4c354fa614e677062
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419158"
---
# <a name="logmarkhistory-transact-sql"></a>logmarkhistory (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Содержит одну строку для каждой зафиксированной помеченной транзакции. Эта таблица хранится в базе данных **msdb** .  
  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|Локальная база данных, в которой возникла помеченная транзакция.|  
|**mark_name**|**nvarchar(128)**|Предоставляемое пользователем имя помеченной транзакции.|  
|**description**|**nvarchar(255)**|Предоставляемое пользователем описание помеченной транзакции. Может иметь значение NULL.|  
|**user_name**|**nvarchar(128)**|Имя пользователя базы данных, выполнившего помеченную транзакцию. Может иметь значение NULL.|  
|**Номера**|**numeric(25,0)**|Номер LSN записи транзакции с пометкой.|  
|**mark_time**|**datetime**|Время фиксации помеченной транзакции (локальное время).|  
  
## <a name="see-also"></a>См. также:  
 [Восстановление базы данных до помеченной транзакции (среда SQL Server Management Studio)](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)   
 [Использование помеченных транзакций для согласованного восстановления связанных баз данных (модель полного восстановления)](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md)   
 [Системные таблицы (Transact-SQL)](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
