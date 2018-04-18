---
title: sys.sysoledbusers (Transact-SQL) | Документы Microsoft
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
- sys.sysoledbusers
- sys.sysoledbusers_TSQL
- sysoledbusers
- sysoledbusers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysoledbusers system table
- sys.sysoledbusers compatibility view
ms.assetid: fe924c17-9cad-4b2b-8124-1e0fd82931e3
caps.latest.revision: 34
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d413a9a07af247a62611946bf687c53e6f42d878
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="syssysoledbusers-transact-sql"></a>sys.sysoledbusers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  Эта системная таблица [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] включена в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в качестве представления только для обеспечения обратной совместимости. Мы рекомендуем использовать [представления каталога](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md) вместо него.  
  
 Содержит по одной строке для каждой пары пользователя и пароля для указанного связанного сервера. **sysoledbusers** хранится в **master** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**rmtsrvid**|**smallint**|Идентификатор защиты (SID) сервера.|  
|**rmtloginame**|**nvarchar (**128**)**|Имя удаленного входа, **loginsid** сопоставляется для связанных **rmtservid**.|  
|**rmtpassword**|**nvarchar (**128**)**|Возвращает значение NULL.|  
|**loginsid**|**varbinary (**85**)**|Идентификатор SID локального имени входа для сопоставления.|  
|**status**|**smallint**|Если значение равно 1, то при сопоставлении необходимо использовать учетные данные пользователя.|  
|**changedate**|**datetime**|Дата последнего изменения сведений о сопоставлении.|  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
