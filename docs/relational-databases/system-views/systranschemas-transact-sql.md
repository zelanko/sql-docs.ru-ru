---
title: "systranschemas (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- systranschemas
- systranschemas_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- systranschemas system table
ms.assetid: 864c3966-cb61-4f2b-8939-ccda112de853
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b7acef96b95d2b74748d5b5b65f4910c71cd3dac
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="systranschemas-transact-sql"></a>systranschemas (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Systranschemas** таблица используется для отслеживания изменений схемы в статьях, опубликованных в публикациях транзакций или моментальных снимков. Эта таблица хранится в базах данных публикаций и подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**tabid**|**int**|Указывает статью таблицы, в которой произошло изменение схемы.|  
|**startlsn**|**binary**|Регистрационный номер транзакции в начале изменения схемы.|  
|**endlsn**|**binary**|Регистрационный номер транзакции в конце изменения схемы.|  
|**typeid**|**int**|Тип изменения схемы.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации (Transact-SQL)](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
