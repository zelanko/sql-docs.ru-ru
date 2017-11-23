---
title: "sp_msx_get_account (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_msx_get_account_TSQL
- sp_msx_get_account
dev_langs: TSQL
helpviewer_keywords: sp_msx_get_account
ms.assetid: 7b478049-e2d0-4bac-865a-b97fd1d8dfbc
caps.latest.revision: "20"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a7a8702d1537ef91a5c090a8769abedefb470406
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="spmsxgetaccount-transact-sql"></a>sp_msx_get_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выводит сведения об учетных данных, которые целевой сервер использует для входа на главный сервер.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_msx_get_account  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает следующий результирующий набор.  
  
|Имя столбца|Тип|Description|  
|-----------------|----------|-----------------|  
|msx_connection|**int**|Номер соединения с главным сервером.|  
|msx_credential_id|**int**|Идентификатор учетных данных, используемых для данного соединения с главным сервером.|  
|msx_credential_name|**sysname**|Имя учетных данных, используемых для данного соединения с главным сервером.|  
|msx_login_name|**nvarchar(4000)**|Имя домена и имя пользователя Windows для учетных данных.|  
  
## <a name="remarks"></a>Замечания  
 Возвращает пустой результирующий набор, если для целевого сервера не указаны учетные данные. Для задания учетных данных следует использовать процедуру sp_msx_set_account.  
  
## <a name="permissions"></a>Permissions  
 Требует членства в предопределенной роли сервера sysadmin.  
  
## <a name="examples"></a>Примеры  
 Следующий пример выводит сведения об учетных данных, которые целевой сервер использует для входа на главный сервер.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sp_msx_get_account ;  
GO  
```  
  
 Образец результирующего набора:  
  
 `msx_connection msx_credential_id msx_credential_name  msx_login_name`  
  
 `-------------- ----------------- -------------------- ------------------------------`  
  
 `1              65538             MsxAccount           AdventureWorks2012\MsxAccount`  
  
## <a name="see-also"></a>См. также:  
 [Агент SQL Server хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_msx_set_account &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-msx-set-account-transact-sql.md)  
  
  
