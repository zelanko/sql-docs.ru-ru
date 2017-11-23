---
title: "представление sys.remote_logins (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.remote_logins_TSQL
- remote_logins
- remote_logins_TSQL
- sys.remote_logins
dev_langs: TSQL
helpviewer_keywords: sys.remote_logins catalog view
ms.assetid: 38477e91-d084-4df7-b1de-b930c5580189
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 774286d1827591144d50d7f0ad84feea1a463d2a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sysremotelogins-transact-sql"></a>sys.remote_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по строке для каждого соответствия между локальным и удаленным именем входа. Это представление каталога используется для сопоставления принимаемых локальных имен входа, якобы полученных от соответствующего сервера, с действительным локальным именем входа.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Идентификатор сервера в **sys.servers**. Это имя предоставляется соединением с «удаленным» сервером.|  
|**remote_name**|**sysname**|Имя входа, которое предоставляет соединение для сопоставления. Если это значение равно NULL, используется имя входа, указанное в соединении.|  
|**local_principal_id**|**int**|Идентификатор сервера-участника, которому сопоставляется имя входа. Если это значение равно 0, удаленное имя входа сопоставляется такому же имени.|  
|**modify_date**|**datetime**|Дата последнего изменения связанного имени входа.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога связанных серверов &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
