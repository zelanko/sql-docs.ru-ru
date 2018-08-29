---
title: sys.index_resumable_operations (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 07/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
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
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0d0da28f06dc079d468b2b8862855e1e2f957540
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43076951"
---
# <a name="indexresumableoperations-transact-sql"></a>index_resumable_operations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]
**sys.index_resumable_operations** — это системное представление, которое отслеживает и проверяет текущее состояние выполнения для возобновляемого перестроения индекса.  
**Применяется к**: SQL Server 2017 и Azure базы данных SQL 
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта, к которому принадлежит (не допускает значения NULL) данный индекс.|  
|**index_id**|**int**|Идентификатор индекса (не допускает значения NULL). **index_id** уникально только в пределах объекта.|
|**name**|**sysname**|Имя индекса. **имя** уникально только в пределах объекта.|  
|**sql_text**|**nvarchar(max)**|Текст инструкции DDL T-SQL|
|**last_max_dop**|**smallint**|Последнее MAX_DOP используется (по умолчанию = 0)|
|**partition_number**|**int**|Номер секции в индексе владельца или куче. Для несекционированных таблиц и индексов, или в случае всех секций выполняется перестроение значение этого столбца равно NULL.|
|**state**|**tinyint**|Рабочее состояние для возобновляемого индекса:<br /><br />0 = выполняется<br /><br />1 = приостановить|
|**state_desc**|**nvarchar(60)**|Описание операционного состояния для возобновляемых индексов (запущена или приостановлена)|  
|**start_time**|**datetime**|Время начала операции индекса (не допускает значения NULL)|
|**last_pause_time**|**значения даты и времени**| Операции с индексами время последней приостановки (допускающие значение NULL). Значение NULL, если операция работает и никогда не приостанавливается.|
|**total_execution_time**|**int**|Общее время выполнения со времени начала в минутах (не допускает значения NULL)|
|**percent_complete**|**real**|Ход выполнения завершения операции индекса в % (не допускает значения NULL).|
|**page_count**|**bigint**|Общее число страниц индекса, выделенной с помощью операции построения индекса для нового и сопоставления индексов (не допускает значения NULL). 

## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
   
## <a name="example"></a>Пример  
 Список всех возобновляемых операций перестроения индексов, которые находятся в состоянии ПРИОСТАНОВКИ. 
  
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
  
