---
title: sys.system_columns (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- system_columns_TSQL
- system_columns
- sys.system_columns
- sys.system_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_columns catalog view
ms.assetid: 4ab1d48a-d57a-4e76-a08c-9627eeaf4588
caps.latest.revision: 46
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 21fb2ede958fa3daa15e74fed06559913954acd1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="syssystemcolumns-transact-sql"></a>sys.system_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит по одной строке на каждый столбец системных объектов, содержащих столбцы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта, которому принадлежит этот столбец.|  
|**name**|**sysname**|Имя столбца. Уникален в пределах объекта.|  
|**column_id**|**int**|Идентификатор столбца. Уникален в пределах объекта.<br /><br /> Идентификаторы столбца могут быть непоследовательными.|  
|**system_type_id**|**tinyint**|Идентификатор системного типа столбца.|  
|**user_type_id**|**int**|Идентификатор определенного пользователем типа столбца.<br /><br /> Чтобы вернуть имя типа, присоединение к [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) представления на этот столбец каталога.|  
|**max_length**|**smallint**|Максимальная ширина столбца (в байтах).<br /><br /> -1 = тип данных столбца — **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, или **xml**.<br /><br /> Для **текст** столбцы, **max_length** значение будет равно 16 или значение, установленное **sp_tableoption** «text in row».|  
|**precision**|**tinyint**|Точность столбца, если он является числовым; в противном случае — 0.|  
|**масштаб**|**tinyint**|Масштаб столбца, если он является числовым; в противном случае — 0.|  
|**collation_name**|**sysname**|Имя параметров сортировки столбца, если он символьный; в противном случае — значение NULL.|  
|**is_nullable**|**бит**|1 = столбец может принимать значение NULL.|  
|**is_ansi_padded**|**бит**|1 = столбец использует поведение ANSI_PADDING ON, если имеет тип данных character, binary или variant.<br /><br /> 0 = столбец имеет тип данных, отличный от character, binary или variant.|  
|**is_rowguidcol**|**бит**|1 = столбец объявлен как ROWGUIDCOL.|  
|**is_identity**|**бит**|1 = столбец идентификаторов.|  
|**is_computed**|**бит**|1 = столбец является вычисляемым.|  
|**is_filestream**|**бит**|1 = для столбца используется потоковое хранилище.|  
|**is_replicated**|**бит**|1 = столбец реплицирован.|  
|**is_non_sql_subscribed**|**бит**|1 = у столбца есть подписчик, отличный от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**is_merge_published**|**бит**|1 = столбец публикуется слиянием.|  
|**is_dts_replicated**|**бит**|1 = столбец реплицируется с помощью служб [!INCLUDE[ssIS](../../includes/ssis-md.md)].|  
|**is_xml_document**|**бит**|1 = содержимое является готовым XML-документом.<br /><br /> 0 = содержимое является фрагментом документа, или тип данных столбца не является **xml**.|  
|**xml_collection_id**|**int**|Ненулевое значение, если тип данных столбца является **xml** и XML типизирован. Значением будет идентификатор коллекции, содержащей пространство имен для проверки схем XML столбца.<br /><br /> 0 = нет коллекции схем XML.|  
|**default_object_id**|**int**|Идентификатор объекта по умолчанию, независимо от того, является ли автономный [sys.sp_bindefault](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md), или встроенным ограничением уровня столбца по умолчанию. **Parent_object_id** столбец встроенного объекта по умолчанию на уровне столбца является ссылкой на саму таблицу. Или 0 — в случае, если нет значения по умолчанию.|  
|**rule_object_id**|**int**|Идентификатор изолированного правила, привязанное к столбцу с помощью **sys.sp_bindrule**.<br /><br /> 0 = изолированное правило отсутствует.<br /><br /> Ограничения CHECK уровня столбца, в разделе [sys.check_constraints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md).|  
|is_sparse|**бит**|1 = столбец является разреженным. Дополнительные сведения см. в статье [Использование разреженных столбцов](../../relational-databases/tables/use-sparse-columns.md).|  
|is_column_set|**бит**|1 = столбец является набором столбцов. Дополнительные сведения см. в статье [Использование наборов столбцов](../../relational-databases/tables/use-column-sets.md).|  
|generated_always_type|**tinyint**|Числовое значение, представляющее тип столбца:<br /><br /> 0 = NOT_APPLICABLE<br /><br /> 1 = AS_ROW_START<br /><br /> 2 = AS_ROW_END|  
|generated_always_type_desc|**nvarchar(60)**|Текстовое описание типа столбца:<br /><br /> NOT_APPLICABLE<br /><br /> AS_ROW_START<br /><br /> AS_ROW_END<br /><br /> **Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Запросив системный каталог SQL Server часто задаваемые вопросы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)  
  
  
