---
title: sysarticlecolumns (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysarticlecolumns
- sysarticlecolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticlecolumns system table
ms.assetid: 55918592-e05d-43b6-843b-7e4d82fa6275
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 030b409328d896f0f8b76fc9ef02a6f351c029c3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysarticlecolumns-transact-sql"></a>sysarticlecolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sysarticlecolumns** содержит по одной строке для каждого столбца таблицы, который публикуется в публикации транзакций или моментальных снимков и сопоставляет каждый столбец с его статьей. Эта таблица хранится в базе данных публикации.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Определяет статью.|  
|**идентификатора столбца**|**smallint**|Идентифицирует столбец в статье.|  
|**is_udt**|**бит**|Указывает, принадлежит ли столбец к пользовательскому типу данных (UDT). Значение **1** означает столбец определяемого пользователем ТИПА.|  
|**is_xml**|**бит**|Указывает, является ли столбец **xml** столбца. Значение **1** указывает XML-столбец.|  
|**is_max**|**бит**|Указывает, является ли столбец столбцом типа данных больших значений **varchar(max)**, **nvarchar(max)**, и **varbinary(max)**. Значение **1** означает столбец больших значений.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
