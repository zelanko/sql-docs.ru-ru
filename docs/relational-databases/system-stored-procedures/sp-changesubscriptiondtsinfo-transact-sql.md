---
title: sp_changesubscriptiondtsinfo (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changesubscriptiondtsinfo
- sp_changesubscriptiondtsinfo_TSQL
helpviewer_keywords:
- sp_changesubscriptiondtsinfo
ms.assetid: 64fc085f-f81b-493b-b59a-ee6192d9736d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5e691c78e0ef0ddf775b5a23baa7dde1d96f72a9
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54129249"
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
 Идентификатор задания агента распространителя для принудительной подписки. *job_id* — **varbinary(16)**, не имеет значения по умолчанию. Чтобы найти идентификатор задания распространения, выполните **sp_helpsubscription** или **sp_helppullsubscription**.  
  
 [ **@dts_package_name**=] **"**_dts_package_name_**"**  
 Указывает имя пакета DTS. *dts_package_name* — **sysname**, значение по умолчанию NULL. Например, чтобы указать пакет с именем **DTSPub_Package**, следует указать `@dts_package_name = N'DTSPub_Package'`.  
  
 [ **@dts_package_password**=] **"**_dts_package_password_**"**  
 Указывает пароль на пакет. *dts_package_password* — **sysname** значение по умолчанию NULL, который указывает, что свойство пароля должно быть оставлено без изменений.  
  
> [!NOTE]  
>  У пакета служб DTS должен быть пароль.  
  
 [ **@dts_package_location**=] **"**_dts_package_location_**"**  
 Указывает местоположение пакета. *dts_package_location* — **nvarchar(12)**, значение по умолчанию NULL, который указывает, что расположение пакета должно быть оставлено без изменений. Расположение пакета можно изменить на **распространителя** или **подписчика**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_changesubscriptiondtsinfo** используется для репликации моментальных снимков и репликации транзакций, которые только принудительные подписки.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера, **db_owner** предопределенной роли базы данных, или создатель подписки могут выполнять процедуру **sp_changesubscriptiondtsinfo**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
