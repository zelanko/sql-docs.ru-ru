---
title: sysmail_help_profile_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_profile_sp_TSQL
- sysmail_help_profile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_profile_sp
ms.assetid: d7169a8e-92b1-49eb-9124-3b2f69755ddb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 061016b3a9f1283f82263a4f89fdb81acfc86889
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890909"
---
# <a name="sysmail_help_profile_sp-transact-sql"></a>sysmail_help_profile_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отображает сведения об одном или нескольких профилях электронной почты.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_help_profile_sp  [   [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @profile_id = ] profile_id`Идентификатор профиля, для которого возвращаются сведения. *profile_id* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @profile_name = ] 'profile_name'`Имя профиля, для которого возвращаются сведения. Аргумент *profile_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает результирующий набор со следующими столбцами.  
  
||||  
|-|-|-|  
|Имя столбца|Тип данных|Описание|  
|**profile_id**|**int**|Идентификатор профиля.|  
|**name**|**sysname**|Имя профиля.|  
|**nописание**|**nvarchar(256)**|Описание профиля.|  
  
## <a name="remarks"></a>Комментарии  
 Если указано имя профиля или профиля, **sysmail_help_profile_sp** возвращает сведения об этом профиле. В противном случае **sysmail_help_profile_sp** возвращает сведения о каждом профиле в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляре.  
  
 Хранимая процедура **sysmail_help_profile_sp** находится в базе данных **msdb** и принадлежит схеме **dbo** . Процедура должна быть выполнена с именем, сопоставленным с тремя частями, если текущей базой данных не является **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения EXECUTE для этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 **A. Список всех профилей**  
  
 Этот пример отображает список всех профилей экземпляра.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profile_sp;  
```  
  
 Далее приведен образец результирующего набора, повторно форматированный под длину строки:  
  
```  
profile_id  name                          description  
----------- ----------------------------- ------------------------------  
56          AdventureWorks Administrator  Administrative mail profile.    
57          AdventureWorks Operator       Operator mail profile.          
```  
  
 **Б. Отображение заданного профиля**  
  
 Этот пример отображает сведения для профиля `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profile_sp  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
 Далее приведен образец результирующего набора, повторно форматированный под длину строки:  
  
```  
profile_id  name                          description  
----------- ----------------------------- ------------------------------  
56          AdventureWorks Administrator  Administrative mail profile.    
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Database Mail хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
