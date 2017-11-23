---
title: "MSmerge_errorlineage (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSmerge_errorlineage_TSQL
- MSmerge_errorlineage
dev_langs: TSQL
helpviewer_keywords: MSmerge_errorlineage system table
ms.assetid: 3bcbd328-c958-4cd4-a573-3c35539fa919
caps.latest.revision: "27"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 50e8b8e9745a29155d71cfd3ff1a027321ef878e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="msmergeerrorlineage-transact-sql"></a>MSmerge_errorlineage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_errorlineage** таблица содержит строки, которые были удалены на подписчике, но удаление которых не распространяются на издатель. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Целочисленное значение, присваиваемое таблице, публикуемой для выполнения репликации слиянием. Соответствует полю псевдоним в **sysmergearticles** таблицы.|  
|**ROWGUID**|**uniqueidentifier**|Идентификатор строки.|  
|**журнала обращений и преобразований**|**varbinary(501)**|Хранит список обновлений строки подписчиками и издателями. Используется для выявления и разрешения конфликтных ситуаций.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
