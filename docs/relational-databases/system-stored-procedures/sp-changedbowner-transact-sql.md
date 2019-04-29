---
title: sp_changedbowner (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_changedbowner
- sp_changedbowner_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_changedbowner
ms.assetid: 516ef311-e83b-45c9-b9cd-0e0641774c04
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 1a38be84e5f1980b680d674e1c04c2ba95d1a537
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62994280"
---
# <a name="spchangedbowner-transact-sql"></a>sp_changedbowner (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет владельца текущей базы данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md) вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changedbowner [ @loginame = ] 'login'  
     [ , [ @map = ] remap_alias_flag ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @loginame=] '*входа*"  
 Идентификатор имени входа нового владельца текущей базы данных. *Имя входа* — **sysname**, не имеет значения по умолчанию. *Имя входа* должен быть уже существующим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имени входа или пользователя Windows. *Имя входа* не может стать владельцем текущей базы данных, если он уже имеет доступ к базе данных с помощью существующей учетной записи безопасности в базе данных. Чтобы избежать этой ситуации, сначала удалите данного пользователя в текущей базе данных.  
  
 [ @map= ] *remap_alias_flag*  
 *Remap_alias_flag* параметр является устаревшим, поскольку псевдонимы имени входа были удалены из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. С помощью *remap_alias_flag* параметр не вызывает ошибку, но не оказывает влияния.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 После выполнения процедуры sp_changedbowner новый владелец становится известным в базе данных как пользователь dbo. Пользователь dbo имеет неявные разрешения на выполнение любых действий в базе данных.  
  
 Владельца системных баз данных master, model или tempdb нельзя изменить.  
  
 Чтобы отобразить список допустимых *входа* значения, выполните хранимую процедуру sp_helplogins.  
  
 Выполнение sp_changedbowner только с *входа* параметр изменения владельца базы данных на *входа*.  
  
 Можно изменить владельца любого защищаемого объекта с помощью инструкции ALTER AUTHORIZATION. Дополнительные сведения см. в разделе [ALTER AUTHORIZATION (Transact-SQL)](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение TAKE OWNERSHIP для базы данных. Если новый владелец имеет соответствующего пользователя в базе данных, требуется разрешение IMPERSONATE для имени входа, в противном случае необходимо разрешение CONTROL SERVER для сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как сделать имя входа `Albert` владельцем текущей базы данных.  
  
```  
EXEC sp_changedbowner 'Albert';  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [sp_dropalias &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropalias-transact-sql.md)   
 [sp_dropuser (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helpdb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helplogins &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
