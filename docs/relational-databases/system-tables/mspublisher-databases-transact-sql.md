---
title: MSpublisher_databases (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpublisher_databases
- MSpublisher_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublisher_databases system table
ms.assetid: 59b0166e-a64c-46b8-befc-c222fa1ccce2
author: stevestein
ms.author: sstein
ms.openlocfilehash: da208c7fb83053c1817693bb16d16c3488fe90c8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68032609"
---
# <a name="mspublisherdatabases-transact-sql"></a>MSpublisher_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSpublisher_databases** таблица содержит по одной строке для каждой пары издатель базы данных, обслуживаемой локальным распространителем. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**идентификатор**|**int**|Идентификатор строки.|  
|**publisher_engine_edition**|**int**|Выпуск издателя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который может иметь следующие значения.<br /><br /> **10** = personal Edition<br /><br /> **11** = desktop Engine (MSDE)<br /><br /> **20** = standard<br /><br /> **21** = рабочей группы<br /><br /> **30** = Enterprise (вычисления)<br /><br /> **31** = разработчика<br /><br /> **40** = express (Express не может быть издателем. Это значение вставлено для обеспечения полноты.)|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации (Transact-SQL)](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
