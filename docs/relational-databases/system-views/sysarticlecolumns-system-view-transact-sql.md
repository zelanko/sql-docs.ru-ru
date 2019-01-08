---
title: Система представление sysarticlecolumns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysarticlecolumns
- sysarticlecolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticlecolumns view
ms.assetid: a8dd8d13-c827-45c4-87ba-802725301382
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1ffa8c9c45e1810fb4a81deed34f7c6c2e4a0ca0
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52756552"
---
# <a name="sysarticlecolumns-system-view-transact-sql"></a>Системное представление sysarticlecolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sysarticlecolumns** представление предоставляет дополнительную информацию о столбцах в публикуемых статьях. Это представление хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Определяет статью.|  
|**идентификатора столбца**|**int**|Идентифицирует столбец в статье.|  
|**is_udt**|**int**|Указывает, принадлежит ли столбец к пользовательскому типу данных (UDT). Значение **1** означает столбец определяемого пользователем ТИПА.|  
|**is_xml**|**int**|Указывает, принадлежит ли столбец **xml** столбца. Значение **1** указывает **xml** столбца.|  
|**is_max**|**int**|Указывает, принадлежит ли столбец столбцом типа данных больших значений (**varchar(max)**, **nvarchar(max)** или **varbinary(max)**). Значение **1** означает столбец больших значений.|  
  
## <a name="see-also"></a>См. также  
 [sp_articlecolumn (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sysarticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
