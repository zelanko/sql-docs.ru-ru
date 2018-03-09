---
title: "sp_changereplicationserverpasswords (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- sp_changereplicationserverpasswords_TSQL
- sp_changereplicationserverpasswords
helpviewer_keywords:
- sp_changereplicationserverpasswords
ms.assetid: 9333da96-3a1c-4adb-9a74-5dac9ce596df
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fcd1cbfd5532703196e47d06f920ef7cfa81f019
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spchangereplicationserverpasswords-transact-sql"></a>sp_changereplicationserverpasswords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет сохраненные пароли для [!INCLUDE[msCoName](../../includes/msconame-md.md)] учетной записи Windows или [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа, используемое агентами репликации при подключении к серверам в топологии репликации. Обычно требуется менять пароль для каждого отдельного агента, выполняемого на сервере, даже если все они используют одно и то же имя входа или учетную запись. Эта хранимая процедура позволяет сменить пароль для всех экземпляров данного имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или учетной записи Windows, используемой всеми агентами репликации, выполняемыми на сервере. Эта хранимая процедура выполняется на любом сервере в топологии репликации в базе данных master.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changereplicationserverpasswords [ @login_type = ] login_type  
        , [ @login = ] 'login'   
        , [ @password = ] 'password'  
    [ , [ @server = ] 'server' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@login_type**  =] *login_type*  
 Тип проверки подлинности для предоставленных учетных данных. *Аргумент LOGIN_TYPE* — **tinyint**, не имеет значения по умолчанию.  
  
 **1** = встроенная проверка подлинности Windows  
  
 **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности  
  
 [  **@login**  =] **"***входа***"**  
 Имя учетной записи Windows или имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которое необходимо изменить. *Имя входа* — **nvarchar(257)**, не имеет значения по умолчанию  
  
 [  **@password**  =] **"***пароль***"**  
 Новый пароль должен быть сохранен для указанного *входа*. *пароль* — **sysname**, не имеет значения по умолчанию.  
  
> [!NOTE]  
>  После изменения пароля репликации необходимо остановить и перезапустить каждый агент, пользующийся этим паролем, прежде чем изменение вступит в силу для этого агента.  
  
 [  **@server**  =] **"***сервера***"**  
 Серверное соединение, для которого изменяется сохраненный пароль. *сервер* — **sysname**, и может принимать одно из следующих значений:  
  
|Значение|Description|  
|-----------|-----------------|  
|**распространитель**|Все соединения агентов с распространителем.|  
|**издатель**|Все соединения агентов с издателем.|  
|**подписчик**|Все соединения агентов с подписчиком.|  
|**%**(по умолчанию)|Все соединения агентов со всеми серверами в топологии репликации.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_changereplicationserverpasswords** используется со всеми типами репликации.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_changereplicationserverpasswords**.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение параметров безопасности репликации](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  
  
  
