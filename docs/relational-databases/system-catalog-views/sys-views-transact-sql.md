---
title: sys.Views (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- views_TSQL
- views
- sys.views_TSQL
- sys.views
dev_langs:
- TSQL
helpviewer_keywords:
- sys.views catalog view
ms.assetid: f8a8ea39-5a09-4662-801e-b43519467def
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 96f0d1bf6d6210c41ec3b6ea228ef53b3c9c82a9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysviews-transact-sql"></a>sys.views (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит по одной строке для каждого объекта представления с **sys.objects.type** = V.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**\<Унаследованные столбцы >**||Список столбцов, наследуемых этим представлением см. в разделе [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)|  
|**is_replicated**|**бит**|1 = представление реплицировано.|  
|**has_replication_filter**|**бит**|1 = представление имеет фильтр репликации.|  
|**has_opaque_metadata**|**бит**|1 = для представления указан параметр VIEW_METADATA. Дополнительные сведения см. в статье [CREATE VIEW (Transact-SQL)](../../t-sql/statements/create-view-transact-sql.md).|  
|**has_unchecked_assembly_data**|**бит**|1 = представление содержит сохраняемые данные, зависящие от сборки, определение которых изменилось во время последней инструкции ALTER ASSEMBLY. Сбрасывается в 0 после следующей успешной инструкции DBCC CHECKDB или DBCC CHECKTABLE.|  
|**with_check_option**|**бит**|1 = в определении представления указано предложение WITH CHECK OPTION.|  
|**is_date_correlation_view**|**бит**|1 = представление было автоматически создано системой для хранения сведений о корреляции между столбцами типа datetime. Создание данного представления стало возможным вследствие установки значения ON для параметра DATE_CORRELATION_OPTIMIZATION.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [ALTER ASSEMBLY (Transact-SQL)](../../t-sql/statements/alter-assembly-transact-sql.md)   
 [Инструкция DBCC CHECKDB & #40; Transact-SQL & #41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)   
 [DBCC CHECKTABLE (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md)   
 [Часто задаваемые вопросы о запросах к системному каталогу SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
