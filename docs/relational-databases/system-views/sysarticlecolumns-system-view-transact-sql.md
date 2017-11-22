---
title: "sysarticlecolumns (Системное представление) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sysarticlecolumns
- sysarticlecolumns_TSQL
dev_langs: TSQL
helpviewer_keywords: sysarticlecolumns view
ms.assetid: a8dd8d13-c827-45c4-87ba-802725301382
caps.latest.revision: "10"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a7e5f8c29826bd37306fe2fc455b449ab6362c67
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysarticlecolumns-system-view-transact-sql"></a>Системное представление sysarticlecolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sysarticlecolumns** содержит дополнительные сведения о столбцах в публикуемых статьях. Это представление хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Определяет статью.|  
|**идентификатора столбца**|**int**|Идентифицирует столбец в статье.|  
|**is_udt**|**int**|Указывает, принадлежит ли столбец к пользовательскому типу данных (UDT). Значение **1** означает столбец определяемого пользователем ТИПА.|  
|**is_xml**|**int**|Если столбец является **xml** столбца. Значение **1** указывает **xml** столбца.|  
|**is_max**|**int**|Если столбец является столбцом типа данных больших значений (**varchar(max)**, **nvarchar(max)** или **varbinary(max)**). Значение **1** означает столбец больших значений.|  
  
## <a name="see-also"></a>См. также:  
 [sp_articlecolumn (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sysarticlecolumns &#40; Transact-SQL &#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
