---
title: "в sys.CHECK_CONSTRAINTS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/28/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.check_constraints
- sys.check_constraints_TSQL
- check_constraints_TSQL
- check_constraints
dev_langs: TSQL
helpviewer_keywords: sys.check_constraints catalog view
ms.assetid: 940ebc5e-44ba-4dae-8b29-da94f2d1d6c4
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 99edd7d87c774d1f400c4fe060c1e28543d6311a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="syscheckconstraints-transact-sql"></a>sys.check_constraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого объекта, являющегося ограничением CHECK с **sys.objects.type** = «C».  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**\<Столбцы, наследуемые из sys.objects >**||Список столбцов, наследуемых этим представлением см. в разделе [sys.objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**is_disabled**|**bit**|Ограничение CHECK отключено.|  
|**is_not_for_replication**|**bit**|Ограничение CHECK было создано с параметром NOT FOR REPLICATION.|  
|**is_not_trusted**|**bit**|Ограничение CHECK не было подтверждено системой для всех строк.|  
|**parent_column_id**|**int**|Значение 0 указывает на ограничение CHECK на уровне таблицы.<br /><br /> Ненулевое значение указывает на ограничение CHECK уровня столбца, определенное в столбце с указанным значением идентификатора.|  
|**Определение**|**nvarchar(max)**|Выражение SQL, которым определяется это ограничение CHECK.|  
|**uses_database_collation**|**bit**|1 = определение ограничения зависит от принятых по умолчанию параметров сортировки базы данных для правильной оценки; в противном случае — 0. Такая зависимость предотвращает изменение параметров сортировки по умолчанию для базы данных.|  
|**is_system_named**|**bit**|1 = имя сформировано системой.<br /><br /> 0 = имя предоставлено пользователем.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога объектов &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
