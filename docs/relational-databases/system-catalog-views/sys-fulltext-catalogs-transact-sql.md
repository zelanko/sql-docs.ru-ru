---
title: sys.fulltext_catalogs (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fulltext_catalogs_TSQL
- sys.fulltext_catalogs
- fulltext_catalogs
- fulltext_catalogs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_catalogs catalog view
ms.assetid: cf1489ff-4819-41fa-a62a-4ed797a16207
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d4f6099b6f741dd5f0f29687cacc37e6cdfe6fb2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62465778"
---
# <a name="sysfulltextcatalogs-transact-sql"></a>sys.fulltext_catalogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по строке для каждого полнотекстового каталога.  
  
> [!NOTE]  
>  Следующие столбцы будут удалены в одном из будущих выпусков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **data_space_id**, **file_id**, и **путь**. Не используйте эти столбцы в новых разработках и как можно быстрее измените приложения, в которых сейчас используются эти столбцы.  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|fulltext_catalog_id|**int**|Идентификатор полнотекстового каталога. Уникален в полнотекстовых каталогах базы данных.|  
|name|**sysname**|Имя каталога. Уникален в пределах базы данных.|  
|path|**nvarchar(260)**|Имя папки в файловой системе, где располагается полнотекстовый каталог.|  
|is_default|**bit**|Является ли полнотекстовый каталог каталогом по умолчанию.<br /><br /> True = по умолчанию.<br /><br /> False = не по умолчанию.|  
|is_accent_sensitivity_on|**bit**|Учитывает ли каталог диакритические знаки.<br /><br /> True = диакритические знаки учитываются.<br /><br /> False = диакритические знаки не учитываются.|  
|data_space_id|**int**|Файловая группа, в которой был создан каталог.|  
|file_id|**int**|Идентификатор полнотекстового файла, связанного с каталогом.|  
|principal_id|**int**|Идентификатор участника базы данных, владеющего полнотекстовым каталогом.|  
|is_importing|**bit**|Указывает, выполняется ли в настоящее время импорт полнотекстового каталога:<br /><br /> 1 = выполняется импорт каталога.<br /><br /> 2 = импорт каталога не выполняется.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [CREATE FULLTEXT CATALOG (Transact-SQL)](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [ALTER FULLTEXT CATALOG (Transact-SQL)](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)   
 [DROP FULLTEXT CATALOG (Transact-SQL)](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md)  
  
  
