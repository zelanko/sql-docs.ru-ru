---
title: sys.fulltext_catalogs (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1f4d19de44beaf6e63a7ae84ba15e8d7353945e0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysfulltextcatalogs-transact-sql"></a>sys.fulltext_catalogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по строке для каждого полнотекстового каталога.  
  
> [!NOTE]  
>  Следующие столбцы будут удалены в будущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **data_space_id**, **file_id**, и **путь**. Не используйте эти столбцы в новых разработках и как можно быстрее измените приложения, в которых сейчас используются эти столбцы.  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|fulltext_catalog_id|**int**|Идентификатор полнотекстового каталога. Уникален в полнотекстовых каталогах базы данных.|  
|имя|**sysname**|Имя каталога. Уникален в пределах базы данных.|  
|path|**nvarchar(260)**|Имя папки в файловой системе, где располагается полнотекстовый каталог.|  
|is_default|**бит**|Является ли полнотекстовый каталог каталогом по умолчанию.<br /><br /> True = по умолчанию.<br /><br /> False = не по умолчанию.|  
|is_accent_sensitivity_on|**бит**|Учитывает ли каталог диакритические знаки.<br /><br /> True = диакритические знаки учитываются.<br /><br /> False = диакритические знаки не учитываются.|  
|data_space_id|**int**|Файловая группа, в которой был создан каталог.|  
|file_id|**int**|Идентификатор полнотекстового файла, связанного с каталогом.|  
|principal_id|**int**|Идентификатор участника базы данных, владеющего полнотекстовым каталогом.|  
|is_importing|**бит**|Указывает, выполняется ли в настоящее время импорт полнотекстового каталога:<br /><br /> 1 = выполняется импорт каталога.<br /><br /> 2 = импорт каталога не выполняется.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [CREATE FULLTEXT CATALOG #40; Transact-SQL & #41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [ALTER FULLTEXT CATALOG (Transact-SQL)](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)   
 [DROP FULLTEXT CATALOG (Transact-SQL)](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md)  
  
  
