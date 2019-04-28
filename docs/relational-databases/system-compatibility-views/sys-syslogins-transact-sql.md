---
title: sys.syslogins (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syslogins_TSQL
- syslogins
- sys.syslogins
- sys.syslogins_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.syslogins compatibility view
- syslogins system table
ms.assetid: 4cb34f17-a4bb-469f-a218-71f074e6308f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 54372511cab4cbcc3ecd7d2afe875325e105163d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62671933"
---
# <a name="syssyslogins-transact-sql"></a>sys.syslogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой учетной записи входа.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](https://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**ИД безопасности**|**varbinary(85)**|Идентификатор защиты.|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**CREATEDATE**|**datetime**|Дата добавления имени входа.|  
|**updatedate**|**datetime**|Дата обновления имени входа.|  
|**accdate**|**datetime**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**totcpu**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**totio**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**spacelimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**TimeLimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**resultlimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**name**|**sysname**|Имя входа пользователя.|  
|**DBName**|**sysname**|Имя базы данных по умолчанию для пользователя при установлении соединения.|  
|**password**|**nvarchar(128)**|Возвращает значение NULL.|  
|**language**|**sysname**|Язык по умолчанию для пользователя.|  
|**denylogin**|**int**|1 = Имя входа принадлежит пользователю или группе [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, и ему отказано в доступе.|  
|**hasaccess**|**int**|1 = Имени входа разрешен доступ на сервер.|  
|**Isntname**|**int**|1 = Имя входа принадлежит пользователю или группе Windows.<br /><br /> 0 = Имя входа является именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Isntgroup**|**int**|1 = Имя входа принадлежит группе Windows.|  
|**isntuser**|**int**|1 = Имя входа принадлежит пользователю Windows.|  
|**sysadmin**|**int**|1 = имя входа является членом **sysadmin** роли сервера.|  
|**securityadmin**|**int**|1 = имя входа является членом **securityadmin** роли сервера.|  
|**serveradmin**|**int**|1 = имя входа является членом **serveradmin** предопределенной роли сервера.|  
|**setupadmin**|**int**|1 = имя входа является членом **setupadmin** предопределенной роли сервера.|  
|**processadmin**|**int**|1 = имя входа является членом **processadmin** предопределенной роли сервера.|  
|**diskadmin**|**int**|1 = имя входа является членом **diskadmin** предопределенной роли сервера.|  
|**dbcreator**|**int**|1 = имя входа является членом **dbcreator** предопределенной роли сервера.|  
|**bulkadmin**|**int**|1 = имя входа является членом **bulkadmin** предопределенной роли сервера.|  
|**LoginName**|**nvarchar(128)**|Имя входа пользователя. Предоставляется для обратной совместимости.|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
