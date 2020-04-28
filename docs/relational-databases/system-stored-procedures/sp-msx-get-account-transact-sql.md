---
title: sp_msx_get_account (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_msx_get_account_TSQL
- sp_msx_get_account
dev_langs:
- TSQL
helpviewer_keywords:
- sp_msx_get_account
ms.assetid: 7b478049-e2d0-4bac-865a-b97fd1d8dfbc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3dab15a076200e464e82d0b01ef6a156447a537f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68108045"
---
# <a name="sp_msx_get_account-transact-sql"></a>sp_msx_get_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выводит сведения об учетных данных, которые целевой сервер использует для входа на главный сервер.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_msx_get_account  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает следующий результирующий набор.  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|msx_connection|**int**|Номер соединения с главным сервером.|  
|msx_credential_id|**int**|Идентификатор учетных данных, используемых для данного соединения с главным сервером.|  
|msx_credential_name|**sysname**|Имя учетных данных, используемых для данного соединения с главным сервером.|  
|msx_login_name|**nvarchar(4000)**|Имя домена и имя пользователя Windows для учетных данных.|  
  
## <a name="remarks"></a>Remarks  
 Возвращает пустой результирующий набор, если для целевого сервера не указаны учетные данные. Для задания учетных данных следует использовать процедуру sp_msx_set_account.  
  
## <a name="permissions"></a>Разрешения  
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
 [Агент SQL Server хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [Создание УЧЕТных данных &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_msx_set_account &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-set-account-transact-sql.md)  
  
  
