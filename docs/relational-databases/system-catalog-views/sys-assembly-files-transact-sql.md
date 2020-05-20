---
title: sys. assembly_files (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.assembly_files
- assembly_files_TSQL
- assembly_files
- sys.assembly_files_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.assembly_files catalog view
ms.assetid: 1a384a2c-5556-4d12-a2ba-4da781363143
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4a30ad97dde1c27518976fc6ee631104b5fef7d4
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831903"
---
# <a name="sysassembly_files-transact-sql"></a>sys.assembly_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит строку для каждого файла из тех, что составляют сборку.  
    
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**assembly_id**|**int**|Идентификатор сборки, которой принадлежит файл.|  
|**name**|**nvarchar(260)**|Имя файла сборки.|  
|**file_id**|**int**|Идентификатор файла. Уникален в пределах сборки. Идентификатор файла с номером 1 представляет сборку DLL.|  
|**content**|**varbinary(max)**|Содержимое файла.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога сборок среды CLR &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/clr-assembly-catalog-views-transact-sql.md)   
 [Представления каталога &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [ASSEMBLYPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/assemblyproperty-transact-sql.md)  
  
  
