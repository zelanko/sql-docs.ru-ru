---
title: sys. computed_columns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.computed_columns_TSQL
- sys.computed_columns
- computed_columns_TSQL
- computed_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sys.computed_columns catalog view
ms.assetid: c962c619-e18f-4315-9251-8d9862462299
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9e55274d1e6dfa34a3cfb92317bb4f205cfdd964
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68109575"
---
# <a name="syscomputed_columns-transact-sql"></a>sys.computed_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит по одной строке для каждого столбца, найденного в **sys. Columns** , который является вычисляемым столбцом.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**\<Наследуемые столбцы>**||Представление **sys. computed_columns** возвращает все столбцы в представлении **sys. Columns** . Оно также возвращает дополнительные столбцы, описанные далее. Описание столбцов, наследуемых представлением **sys. computed_columns** из **sys. Columns**, см. в разделе [sys. Columns &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md). Значение столбца **is_computed** всегда равно 1 в представлении **sys. computed_columns** .|  
|**definition**|**nvarchar(max)**|Текст на языке SQL, определяющий этот вычисляемый столбец.|  
|**uses_database_collation**|**bit**|1 = определение столбца зависит от принятых по умолчанию параметров сортировки базы данных для правильной оценки; в противном случае — 0. Такая зависимость предотвращает изменение параметров сортировки по умолчанию для базы данных.|  
|**is_persisted**|**bit**|Вычисляемый столбец сохраняется.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога объектов &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
