---
title: "dbo.sysproxylogin (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.sysproxylogin_TSQL
- sysproxylogin_TSQL
- dbo.sysproxylogin
- sysproxylogin
dev_langs: TSQL
helpviewer_keywords: sysproxylogin system table
ms.assetid: 433d33cb-bdf2-47bb-af78-2a40b7c8dfce
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5301ed0231793f50be14f536cd36ff2f5010df78
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysproxylogin-transact-sql"></a>dbo.sysproxylogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Регистрирует текущее соответствие учетных записей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетным записям-посредникам агента SQL Server. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|Идентификатор учетной записи-посредника агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это значение соответствует **proxy_id** столбца в **sysproxies** таблицы.|  
|**ИД безопасности**|**varbinary(85)**|Microsoft Windows *security_identifier* для имени входа SQL Server.|  
|**principal_id**|**int**|Идентификатор пользователя или группы, которая имеет разрешение на использование учетной записи-посредника для указанного шага подсистемы.|  
|**флаги**|**int**|Тип имени входа:<br /><br /> **0** = пользователь или группа, Windows и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа.<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Фиксированная системная роль<br /><br /> **2** = **msdb** роли базы данных|  
  
## <a name="remarks"></a>Замечания  
 Только члены **sysadmin** предопределенной роли сервера можно получить доступ к этой таблице.  
  
## <a name="see-also"></a>См. также:  
 [dbo.sysproxies &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
  
  
