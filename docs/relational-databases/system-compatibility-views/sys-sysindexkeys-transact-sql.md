---
title: sys.sysindexkeys (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysindexkeys
- sys.sysindexkeys_TSQL
- sysindexkeys_TSQL
- sys.sysindexkeys
dev_langs:
- TSQL
helpviewer_keywords:
- sysindexkeys system table
- sys.sysindexkeys compatibility view
ms.assetid: 53a33c8d-e5f0-430d-a712-b65f43d64318
caps.latest.revision: 31
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cf5462246fa5b619f78eb5943263da226acfdd92
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="syssysindexkeys-transact-sql"></a>sys.sysindexkeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения о ключах или столбцах, включенных в индекс базы данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор таблицы.|  
|**indid**|**smallint**|Идентификатор индекса.|  
|**идентификатора столбца**|**smallint**|Идентификатор столбца.|  
|**keyno**|**smallint**|Порядковое положение столбца в индексе.|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [sys.index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  
