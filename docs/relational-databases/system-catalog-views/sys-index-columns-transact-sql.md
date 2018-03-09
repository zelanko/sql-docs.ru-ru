---
title: "sys.index_columns (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.index_columns
- sys.index_columns_TSQL
- index_columns
- index_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.index_columns catalog view
ms.assetid: 211471aa-558a-475c-9b94-5913c143ed12
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: aee9551240096547e37d4157179f80ca7e936182
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sysindexcolumns-transact-sql"></a>sys.index_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит по одной строке для каждого столбца, который является частью **sys.indexes** индекса или неупорядоченной таблице (куче).  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта, с которым ассоциирован индекс.|  
|**index_id**|**int**|Идентификатор индекса, в котором определен столбец.|  
|**index_column_id**|**int**|Идентификатор столбца индекса. **index_column_id** уникально только в пределах **index_id**.|  
|**Идентификатор column_id**|**int**|Идентификатор столбца в **object_id**.<br /><br /> 0 = Идентификатор строки (RID) в некластеризованном индексе.<br /><br /> **Идентификатор column_id** уникально только в пределах **object_id**.|  
|**key_ordinal**|**tinyint**|Порядковый номер (нумерация начинается с 1) внутри набора ключевых столбцов.<br /><br /> 0 = неключевой столбец или XML-индекс, индекс columnstore или пространственный индекс.<br /><br /> Примечание: XML-индекс или пространственный индекс не может быть так, как базовые столбцы не являются сравнимыми, это означает, что их значения не может быть упорядочен.|  
|**partition_ordinal**|**tinyint**|Порядковый номер (нумерация начинается с 1) внутри набора столбцов секционирования. Кластеризованный индекс columnstore может иметь самое большее 1 столбец секционирования.<br /><br /> 0 = Объект не является столбцом секционирования.|  
|**is_descending_key**|**bit**|1 = Направление сортировки ключевого столбца индексов по убыванию.<br /><br /> 0 = ключевой столбец индекса имеет направление сортировки по возрастанию, или столбец входит в состав индекса columnstore или хэш-индекса.|  
|**is_included_column**|**bit**|1 = столбец является неключевым столбцом, добавленным к индексу с использованием предложения CREATE INDEX INCLUDE, или столбец входит в состав индекса columnstore.<br /><br /> 0 = Столбец не является включенным.<br /><br /> Столбцы, добавленные неявно, поскольку они являются частью ключа кластеризации, не перечислены в **sys.index_columns**.<br /><br /> Столбцы, добавленные неявно, поскольку они представляют собой столбец секционирования, возвращаются как 0.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются все индексы и индексированные столбцы для таблицы `Production.BillOfMaterials`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT i.name AS index_name  
    ,COL_NAME(ic.object_id,ic.column_id) AS column_name  
    ,ic.index_column_id  
    ,ic.key_ordinal  
,ic.is_included_column  
FROM sys.indexes AS i  
INNER JOIN sys.index_columns AS ic   
    ON i.object_id = ic.object_id AND i.index_id = ic.index_id  
WHERE i.object_id = OBJECT_ID('Production.BillOfMaterials');  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
index_name                                                 column_name        index_column_id key_ordinal is_included_column  
---------------------------------------------------------- -----------------  --------------- ----------- -------------  
AK_BillOfMaterials_ProductAssemblyID_ComponentID_StartDate ProductAssemblyID  1               1           0  
AK_BillOfMaterials_ProductAssemblyID_ComponentID_StartDate ComponentID        2               2           0  
AK_BillOfMaterials_ProductAssemblyID_ComponentID_StartDate StartDate          3               3           0  
PK_BillOfMaterials_BillOfMaterialsID                       BillOfMaterialsID  1               1           0  
IX_BillOfMaterials_UnitMeasureCode                         UnitMeasureCode    1               1           0  
  
(5 row(s) affected)  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога объектов &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.Objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [Часто задаваемые вопросы о запросах к системному каталогу SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
