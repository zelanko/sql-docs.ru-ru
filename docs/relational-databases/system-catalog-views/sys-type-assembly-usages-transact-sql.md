---
title: sys. type_assembly_usages (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.type_assembly_usages
- sys.type_assembly_usages_TSQL
- type_assembly_usages_TSQL
- type_assembly_usages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.type_assembly_usages catalog view
ms.assetid: 79b8bf25-6e4e-4a07-ae93-7a4e44f65171
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d66d9e82c3d0b0d5d555e32fe4239decbe52e429
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833878"
---
# <a name="systype_assembly_usages-transact-sql"></a>sys.type_assembly_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке на тип для ссылки на сборку.  
  

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**user_type_id**|**int**|Идентификатор типа<br /><br /> Чтобы вернуть имя типа, присоединитесь к представлению каталога [sys. types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) в этом столбце.|  
|**assembly_id**|**int**|Идентификатор сборки|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога скалярных типов &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
