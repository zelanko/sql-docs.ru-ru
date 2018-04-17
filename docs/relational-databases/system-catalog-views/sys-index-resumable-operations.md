---
title: sys.index_resumable_operations (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 07/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.service: ''
ms.component: system-catalog-views
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.index_resumable_operations_TSQL
- sys.indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.indexes
- sys.index_resumable_operations
ms.assetid: ''
caps.latest.revision: 1
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2017 || = sqlallproducts-allversions
ms.openlocfilehash: 5ab677122523c42f27aa206104911f213510d35e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="indexresumableoperations-transact-sql"></a>index_resumable_operations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]
**sys.index_resumable_operations** представление системой, которая отслеживает и проверяет текущее состояние выполнения для возобновляемой перестроения индекса.  
**Применяется к**: SQL Server 2017 г. и Azure базы данных SQL 
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта, которому принадлежит (не допускает значения NULL) этот индекс.|  
|**index_id**|**int**|Идентификатор индекса (не допускает значение NULL). **index_id** уникально только в пределах объекта.|
|**name**|**sysname**|Имя индекса. **имя** уникально только в пределах объекта.|  
|**sql_text**|**nvarchar(max)**|Текст инструкции DDL T-SQL|
|**last_max_dop**|**smallint**|MAX_DOP используется последнее (по умолчанию = 0)|
|**partition_number**|**int**|Номер секции в индексе владельца или куче. Для несекционированных таблиц и индексов, или в случае всех секций выполняется перестроение значение этого столбца равно NULL.|
|**state**|**tinyint**|Рабочее состояние для возобновляемой индекса:<br /><br />0 = выполняется<br /><br />1 = Приостановка|
|**state_desc**|**nvarchar(60)**|Описание рабочее состояние для возобновляемой индекса (работает или приостановлена)|  
|**start_time**|**datetime**|Время начала операции индекса (не допускает значение NULL)|
|**last_pause_time**|**значения даты и времени**| Операции с индексами последнего паузы (допускающий значения NULL). Значение NULL, если операция выполняется и никогда не приостановлена.|
|**total_execution_time**|**int**|Общее время выполнения из начальное время в минутах (не допускает значение NULL)|
|**percent_complete**|**real**|Индекс завершение ход выполнения операции в % (не допускает значение NULL).|
|**page_count**|**bigint**|Общее количество страниц индекса, выделенной с помощью операции построения индекса для нового и сопоставления индексов (не допускает значение NULL). 

## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
   
## <a name="example"></a>Пример  
 Перечислены все операции перестроения индекса возобновляемой, которые находятся в состоянии ПРИОСТАНОВКИ. 
  
```  
SELECT * FROM  sys.index_resumable_operations WHERE STATE = 1;  
```  
  
## <a name="see-also"></a>См. также 
 [ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md)    
 [Представления каталога &#40;Transact-SQL&#41; ](catalog-views-transact-sql.md) [объекта представления каталога &#40;Transact-SQL&#41; ](object-catalog-views-transact-sql.md) [sys.indexes &#40;Transact-SQL&#41; ](sys-xml-indexes-transact-sql.md) [sys.index_columns &#40;Transact-SQL&#41;](sys-index-columns-transact-sql.md)   
 [sys.xml_indexes (Transact-SQL)](sys-xml-indexes-transact-sql.md)   
 [sys.objects (Transact-SQL)](sys-index-columns-transact-sql.md)   
 [sys.key_constraints &#40;Transact-SQL&#41;](sys-key-constraints-transact-sql.md)   
 [sys.filegroups (Transact-SQL)](sys-filegroups-transact-sql.md)   
 [sys.partition_schemes (Transact-SQL)](sys-partition-schemes-transact-sql.md)   
 [Часто задаваемые вопросы о запросах к системному каталогу SQL Server](querying-the-sql-server-system-catalog-faq.md)   
  
