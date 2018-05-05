---
title: sys.sysconstraints (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysconstraints
- sys.sysconstraints
- sysconstraints_TSQL
- sys.sysconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysconstraints compatibility view
- sysconstraints system table
ms.assetid: f2b2e2ad-ba24-48a1-913c-8ee4e0895dc4
caps.latest.revision: 32
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a945b5027afdaf58d5abc266f37d8c8823947b73
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="syssysconstraints-transact-sql"></a>sys.sysconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Содержит сопоставления ограничений с объектами, владеющими ограничениями внутри базы данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**constid**|**int**|Номер ограничения.|  
|**идентификатор**|**int**|Идентификатор таблицы, владеющей ограничением.|  
|**идентификатора столбца**|**smallint**|Идентификатор столбца, на котором определено ограничение.<br /><br /> 0 = ограничение таблицы|  
|**spare1**|**tinyint**|Зарезервировано|  
|**status**|**int**|Псевдобитовая маска, определяющая состояние. Возможные значения:<br /><br /> 1 = ограничение PRIMARY KEY;<br /><br /> 2 = ограничение UNIQUE KEY;<br /><br /> 3 = ограничение FOREIGN KEY;<br /><br /> 4 = ограничение CHECK;<br /><br /> 5 = ограничение DEFAULT;<br /><br /> 16 = ограничение на уровне столбца;<br /><br /> 32 = ограничение уровня таблицы.|  
|**действия**|**int**|Зарезервировано|  
|**Ошибка**|**int**|Зарезервировано|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
