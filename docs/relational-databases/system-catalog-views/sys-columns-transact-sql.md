---
title: sys.Columns (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 11/21/2017
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
- sys.columns_TSQL
- sys.columns
- columns_TSQL
- columns
dev_langs:
- TSQL
helpviewer_keywords:
- sys.columns catalog view
ms.assetid: 323ac9ea-fc52-4b8c-8a7e-e0e44f8ed86c
caps.latest.revision: 57
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7688ad8f8157d12e0f3379b5375074bd818a9f16
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="syscolumns-transact-sql"></a>sys.columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает строку для каждого столбца объекта, имеющего столбцы, например представления или таблицы. Далее следует список типов объектов, имеющих столбцы:  
  
-   возвращающие табличное значение функции сборки (FT);  
  
-   встроенные возвращающие табличное значение функции SQL (IF);  
  
-   внутренние таблицы (IT);  
  
-   системные таблицы (S);  
  
-   возвращающие табличное значение функции SQL (TF);  
  
-   пользовательские таблицы (U);  
  
-   представления (V).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Идентификатор объекта, которому принадлежит этот столбец.|  
|имя|**sysname**|Имя столбца. Уникален в пределах объекта.|  
|column_id|**int**|Идентификатор столбца. Уникален в пределах объекта.<br /><br /> Идентификаторы столбца могут быть непоследовательными.|  
|system_type_id|**tinyint**|Идентификатор системного типа столбца.|  
|user_type_id|**int**|Идентификатор определенного пользователем типа столбца.<br /><br /> Чтобы вернуть имя типа, присоединение к [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) представления на этот столбец каталога.|  
|max_length|**smallint**|Максимальная длина столбца (в байтах).<br /><br /> -1 = тип данных столбца — **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, или **xml**.<br /><br /> Для **текст** столбцов значением max_length будет 16 или значение, установленное процедурой sp_tableoption «text in row».|  
|precision|**tinyint**|Точность столбца, если он является числовым; в противном случае — 0.|  
|масштаб|**tinyint**|Масштаб значений столбца в случае числового выражения; в противном случае — 0.|  
|collation_name|**sysname**|Имя параметров сортировки столбца, если он символьный; в противном случае — значение NULL.|  
|is_nullable|**бит**|1 = столбец может принимать значение NULL.|  
|is_ansi_padded|**бит**|1 = столбец использует поведение ANSI_PADDING ON, если имеет тип данных character, binary или variant.<br /><br /> 0 = столбец имеет тип данных, отличный от character, binary или variant.|  
|is_rowguidcol|**бит**|1 = столбец объявлен как ROWGUIDCOL.|  
|is_identity|**бит**|1 = столбец содержит значения идентификаторов.|  
|is_computed|**бит**|1 = столбец является вычисляемым.|  
|is_filestream|**бит**|1 — столбец является столбцом FILESTREAM.|  
|is_replicated|**бит**|1 = столбец реплицирован.|  
|is_non_sql_subscribed|**бит**|1 = у столбца есть подписчик, отличный от подписчика SQL Server.|  
|is_merge_published|**бит**|1 = столбец публикуется слиянием.|  
|is_dts_replicated|**бит**|1 = столбец реплицируется с помощью служб [!INCLUDE[ssIS](../../includes/ssis-md.md)].|  
|is_xml_document|**бит**|1 = содержимое является готовым XML-документом.<br /><br /> 0 = содержимое является фрагментом документа или тип данных столбца не **xml**.|  
|xml_collection_id|**int**|Ненулевое значение, если тип данных столбца является **xml** и XML типизирован. Значением будет идентификатор коллекции, содержащей пространство имен для проверки схем XML столбца.<br /><br /> 0 = нет коллекции схем XML.|  
|default_object_id|**int**|Идентификатор объекта по умолчанию, даже если он является автономным объектом [sys.sp_bindefault](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md), или встроенным ограничением уровня столбца по умолчанию. Столбец parent_object_id встроенного объекта «значение по умолчанию» уровня столбца представляет собой ссылку на саму таблицу.<br /><br /> 0 = значение по умолчанию отсутствует.|  
|rule_object_id|**int**|Идентификатор изолированного правила, привязанного к столбцу с помощью процедуры sys.sp_bindrule.<br /><br /> 0 = изолированное правило отсутствует. Ограничения CHECK уровня столбца, в разделе [sys.check_constraints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md).|  
|is_sparse|**бит**|1 = столбец является разреженным. Дополнительные сведения см. в статье [Использование разреженных столбцов](../../relational-databases/tables/use-sparse-columns.md).|  
|is_column_set|**бит**|1 = столбец является набором столбцов. Дополнительные сведения см. в статье [Использование разреженных столбцов](../../relational-databases/tables/use-sparse-columns.md).|  
|generated_always_type|**tinyint**|**Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Определяет, когда создается значение столбца (имеет значение 0 для столбцов в системных таблицах):<br /><br /> 0 = NOT_APPLICABLE<br /><br /> 1 = AS_ROW_START<br /><br /> 2 = AS_ROW_END<br /><br /> Дополнительные сведения см. в разделе [временных таблицах &#40;реляционных баз данных&#41;](../../relational-databases/tables/temporal-tables.md).|  
|generated_always_type_desc|**nvarchar(60)**|**Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Текстовое описание `generated_always_type`его значение (всегда NOT_APPLICABLE столбцам системных таблиц) <br /><br /> NOT_APPLICABLE<br /><br /> AS_ROW_START<br /><br /> AS_ROW_END|  
|encryption_type|**int**|**Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Тип шифрования:<br /><br /> 1 = детерминированного шифрования<br /><br /> 2 = случайного шифрования|  
|encryption_type_desc|**nvarchar(64)**|**Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Описание типа шифрования:<br /><br /> СЛУЧАЙНОЕ ШИФРОВАНИЕ<br /><br /> DETERMINISTIC|  
|encryption_algorithm_name|**sysname**|**Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Имя алгоритма шифрования.<br /><br /> Поддерживается только AEAD_AES_256_CBC_HMAC_SHA_512.|  
|column_encryption_key_id|**int**|**Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Идентификатор ключа.|  
|column_encryption_key_database_name|**sysname**|**Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDW_md](../../includes/sssds-md.md)].<br /><br /> Имя базы данных, где существует ключа шифрования столбца, если оно отличается от базы данных столбца. Значение NULL, если ключ присутствует в той же базе данных, что и столбец.|  
|is_hidden|**бит**|**Применимо к**: с [!INCLUDE[ssCurrentLong](../../includes/sscurrentlong-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Указывает, если столбец скрыт.<br /><br /> 0 = столбец регулярные, не скрыты, видимыми<br /><br /> 1 = скрытых столбцов|  
|is_masked|**бит**|**Применимо к**: с [!INCLUDE[ssCurrentLong](../../includes/sscurrentlong-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Указывает, если столбец является Замаскировано маскирование динамических данных:<br /><br /> 0 = обычный, не скрытие столбца<br /><br /> 1 = столбец скрыт.|  


 
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Системные представления &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Запросив системный каталог SQL Server часто задаваемые вопросы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.system_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-columns-transact-sql.md)  
  
  
