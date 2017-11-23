---
title: "sp_changedbowner (Transact-SQL) | Документы Microsoft"
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
- sp_changedbowner
- sp_changedbowner_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_changedbowner
ms.assetid: 516ef311-e83b-45c9-b9cd-0e0641774c04
caps.latest.revision: "35"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 69f2e158959f2a73ec36ef3f13d25742aec6fcdc
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spchangedbowner-transact-sql"></a>sp_changedbowner (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет владельца текущей базы данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Используйте [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md) вместо него.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changedbowner [ @loginame = ] 'login'  
     [ , [ @map = ] remap_alias_flag ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @loginame=] '*входа*"  
 Идентификатор имени входа нового владельца текущей базы данных. *Имя входа* — **sysname**, не имеет значения по умолчанию. *Имя входа* должен быть уже существующим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа или пользователя Windows. *Имя входа* не может стать владельцем текущей базы данных, если он уже имеет доступ к базе данных через существующую учетную запись безопасности пользователя в базе данных. Чтобы избежать этой ситуации, сначала удалите данного пользователя в текущей базе данных.  
  
 [ @map=] *remap_alias_flag*  
 *Remap_alias_flag* параметр является устаревшим, поскольку псевдонимы имени входа были удалены из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. С помощью *remap_alias_flag* параметр не вызывает ошибку, но не влияет.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 После выполнения процедуры sp_changedbowner новый владелец становится известным в базе данных как пользователь dbo. Пользователь dbo имеет неявные разрешения на выполнение любых действий в базе данных.  
  
 Владельца системных баз данных master, model или tempdb нельзя изменить.  
  
 Чтобы отобразить список допустимых *входа* значения, выполните хранимую процедуру sp_helplogins.  
  
 Выполнение процедуры sp_changedbowner только с *входа* параметр изменения владельца базы данных на *входа*.  
  
 Можно изменить владельца любого защищаемого объекта с помощью инструкции ALTER AUTHORIZATION. Дополнительные сведения см. в разделе [ALTER AUTHORIZATION &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение TAKE OWNERSHIP для базы данных. Если новый владелец имеет соответствующего пользователя в базе данных, требуется разрешение IMPERSONATE для имени входа, в противном случае необходимо разрешение CONTROL SERVER для сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как сделать имя входа `Albert` владельцем текущей базы данных.  
  
```  
EXEC sp_changedbowner 'Albert';  
```  
  
## <a name="see-also"></a>См. также:  
 [Безопасность хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [sp_dropalias &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropalias-transact-sql.md)   
 [sp_dropuser (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helpdb &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helplogins &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
