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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68032609"
---
# <a name="mspublisher_databases-transact-sql"></a>MSpublisher_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Таблица **MSpublisher_databases** содержит по одной строке для каждой пары базы данных издателя или издателя, обслуживаемой локальным распространителем. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**имеет sysname**|Имя базы данных издателя.|  
|**удостоверения**|**int**|Идентификатор строки.|  
|**publisher_engine_edition**|**int**|Выпуск издателя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который может иметь следующие значения.<br /><br /> **10** = персональный выпуск<br /><br /> **11** = Desktop Engine (MSDE)<br /><br /> **20** = Стандартный<br /><br /> **21** = Рабочая группа<br /><br /> **30** = Enterprise (ознакомительная версия)<br /><br /> **31** = разработчик<br /><br /> **40** = Express (экспресс-выпуск не может быть издателем. Это значение вставлено для обеспечения полноты.)|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
