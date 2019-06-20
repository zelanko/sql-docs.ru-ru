---
title: sys.index_resumable_operations (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/14/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 780cffa17f6ee1af70d942545632c98c9d6dc1e7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63004384"
---
# <a name="indexresumableoperations-transact-sql"></a>index_resumable_operations (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]
**sys.index_resumable_operations** — это системное представление, которое отслеживает и проверяет текущее состояние выполнения для возобновляемого перестроения индекса.  
**Область применения**: SQL Server 2017 и Azure базы данных SQL
  
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

```sql
SELECT * FROM  sys.index_resumable_operations WHERE STATE = 1;  
```

## <a name="see-also"></a>См. также

- [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)
- [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md)
- [Представления каталога](catalog-views-transact-sql.md)
- [Представления каталога объектов](object-catalog-views-transact-sql.md)
- [sys.indexes](sys-xml-indexes-transact-sql.md)
- [sys.index_columns](sys-index-columns-transact-sql.md)
- [sys.xml_indexes](sys-xml-indexes-transact-sql.md)
- [sys.objects](sys-index-columns-transact-sql.md)
- [sys.key_constraints](sys-key-constraints-transact-sql.md)
- [sys.filegroups](sys-filegroups-transact-sql.md)
- [sys.partition_schemes](sys-partition-schemes-transact-sql.md)
- [Часто задаваемые вопросы о запросах к системному каталогу SQL Server](querying-the-sql-server-system-catalog-faq.md)
