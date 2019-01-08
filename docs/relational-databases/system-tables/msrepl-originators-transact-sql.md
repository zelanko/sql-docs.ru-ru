---
title: MSrepl_originators (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_originators_TSQL
- MSrepl_originators
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_originators system table
ms.assetid: a3ac20a6-73f6-4fdc-ad5f-5f72746c9871
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9e12c62d9cbbc1f856e862fc64331f6cbb280ee7
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52792766"
---
# <a name="msreploriginators-transact-sql"></a>MSrepl_originators (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSrepl_originators** таблица содержит по одной строке на каждого обновляемого подписчика, из которой была начата транзакция. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Определяет обновляемого подписчика.|  
|**publisher_database_id**|**int**|Определяет базу данных публикации.|  
|**SRVNAME**|**sysname**|Имя обновляемого сервера.|  
|**DBName**|**sysname**|Имя обновляемой базы данных.|  
|**publication_id**|**int**|Определяет публикацию.|  
|**dbversion**|**int**|Определяет версию базы данных.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
