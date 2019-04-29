---
title: sys.identity_columns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- identity_columns
- sys.identity_columns
- sys.identity_columns_TSQL
- identity_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.identity_columns catalog view
ms.assetid: 97ee01e6-9c9e-4fd9-884b-68b4084669d5
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6d6c97b167cb69eec72ad771504a1070ed59e4f1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004366"
---
# <a name="sysidentitycolumns-transact-sql"></a>sys.identity_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит по одной строке для каждого столбца, который является столбцом идентификаторов.  
  
 **Sys.identity_columns** наследует строки из **sys.columns** представления. **Sys.identity_columns** возвращает столбцы в **sys.columns** представления, а также **seed_value**, **increment_value**, **last_value**, и **is_not_for_replication** столбцы. Дополнительные сведения см. в разделе [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**\<столбцы, наследованные из sys.columns >**||**Sys.identity_columns** представление возвращает все столбцы в **sys.columns** представления. Оно также возвращает дополнительные столбцы, описанные далее. Описание столбцов, **sys.identity_columns** наследует от представления **sys.columns**, см. в разделе [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md).|  
|**seed_value**|**sql_variant**|Начальное значение для столбца идентификаторов. Тип данных начального значения является тем же, что и тип данных самого столбца.|  
|**increment_value**|**sql_variant**|Значение приращения для столбца идентификаторов. Тип данных начального значения является тем же, что и тип данных самого столбца.|  
|**last_value**|**sql_variant**|Последнее значение, сформированное для данного столбца идентификаторов. Тип данных начального значения является тем же, что и тип данных самого столбца.|  
|**is_not_for_replication**|**bit**|Столбец идентификаторов объявлен как NOT FOR REPLICATION.|  
  
> [!NOTE]  
>  Сведения о том, как создать автоматически увеличивающееся числовое значение, которое может использоваться в нескольких таблицах или вызываться из приложений без ссылки на какие-либо таблицы, см. в разделе [Порядковые номера](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Часто задаваемые вопросы о запросах к системному каталогу SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
