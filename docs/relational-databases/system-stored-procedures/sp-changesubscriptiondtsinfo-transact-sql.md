---
title: "sp_changesubscriptiondtsinfo (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_changesubscriptiondtsinfo
- sp_changesubscriptiondtsinfo_TSQL
helpviewer_keywords:
- sp_changesubscriptiondtsinfo
ms.assetid: 64fc085f-f81b-493b-b59a-ee6192d9736d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6b551a265d30632f7ee96c86b78191388099c7d0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spchangesubscriptiondtsinfo-transact-sql"></a>sp_changesubscriptiondtsinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет свойства пакета служб DTS для подписки. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changesubscriptiondtsinfo [ [ @job_id = ] job_id ]  
    [ , [ @dts_package_name= ] 'dts_package_name' ]  
    [ , [ @dts_package_password= ] 'dts_package_password' ]  
    [ , [ @dts_package_location= ] 'dts_package_location' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@job_id=**] *job_id*  
 Идентификатор задания агента распространителя для принудительной подписки. *Аргумент job_id* — **varbinary(16)**, не имеет значения по умолчанию. Чтобы узнать идентификатор задания распространения, запустите **sp_helpsubscription** или **sp_helppullsubscription**.  
  
 [  **@dts_package_name** =] **"***dts_package_name***"**  
 Указывает имя пакета DTS. *dts_package_name* — **sysname**, значение по умолчанию NULL. Например, чтобы указать пакет с именем **DTSPub_Package**, следует указать `@dts_package_name = N'DTSPub_Package'`.  
  
 [  **@dts_package_password** =] **"***dts_package_password***"**  
 Указывает пароль на пакет. *dts_package_password* — **sysname** значение по умолчанию NULL, при которой указывает, что свойство пароля должно быть оставлено без изменений.  
  
> [!NOTE]  
>  У пакета служб DTS должен быть пароль.  
  
 [  **@dts_package_location** =] **"***dts_package_location***"**  
 Указывает местоположение пакета. *dts_package_location* — **nvarchar(12)**, значение по умолчанию NULL, который указывает, что расположение пакета должно быть оставлено без изменений. Можно изменить значение расположения пакета **распространителя** или **подписчика**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_changesubscriptiondtsinfo** используется для репликации моментальных снимков и репликации транзакций, являющихся принудительными подписками.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера **db_owner** предопределенной роли базы данных, или создатель подписки могут выполнять процедуру **sp_changesubscriptiondtsinfo**.  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
