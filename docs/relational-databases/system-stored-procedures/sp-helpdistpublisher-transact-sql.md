---
title: Хранимая процедура sp_helpdistpublisher (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpdistpublisher_TSQL
- sp_helpdistpublisher
helpviewer_keywords:
- sp_helpdistpublisher
ms.assetid: f207c22d-8fb2-4756-8a9d-6c51d6cd3470
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 11901d38105ed0c8c6618028e622fb33035ad2a0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sphelpdistpublisher-transact-sql"></a>Хранимая процедура sp_helpdistpublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает свойства издателя, использующего распространитель. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpdistpublisher [ [ @publisher=] 'publisher']   
    [ , [ @check_user = ] check_user  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publisher=** ] **"***издатель***"**  
 Имя издателя, для которого возвращаются свойства. *издатель* — **sysname**, значение по умолчанию **%**.  
  
 [  **@check_user=** ] *check_user*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя издателя.|  
|**distribution_db**|**sysname**|База данных распространителя для указанного издателя.|  
|**security_mode**|**int**|Режим безопасности, используемый агентами репликации для подключения к издателю обновляемых посредством очередей подписок, или к издателю, не являющемуся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности<br /><br /> **1** = проверка подлинности Windows|  
|**Имя входа**|**sysname**|Имя входа, используемое агентами репликации для подключения к издателю обновляемых посредством очередей подписок, или к издателю, не являющемуся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**password**|**nvarchar(524)**|Возвращаемый пароль (в простой зашифрованной форме). Пароль равен NULL для пользователей, отличных от **sysadmin**.|  
|**Активный**|**бит**|Использует ли удаленный издатель локальный сервер в качестве распространителя:<br /><br /> **0** = Нет<br /><br /> **1** = Да|  
|**working_directory**|**nvarchar(255)**|Имя рабочего каталога.|  
|**доверенные**|**бит**|Требуется ли пароль при подключении издателя к распространителю. Для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий всегда возвращается значение **0**, означающее, что пароль требуется.|  
|**thirdparty_flag**|**бит**|Будет ли публикация включена [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или приложением стороннего разработчика:<br /><br /> **0** = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], oracle или издатель Oracle Gateway.<br /><br /> **1** = издатель интегрирован с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью приложения сторонних разработчиков.|  
|**publisher_type**|**sysname**|Тип издателя; возможны следующие варианты:<br /><br /> **MSSQLSERVER**<br /><br /> **ORACLE**<br /><br /> **ORACLE GATEWAY**|  
|**publisher_data_source**|**nvarchar(4000)**|Имя источника данных OLE DB на издателе.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **Хранимая процедура sp_helpdistpublisher** используется во всех типах репликации.  
  
 **Хранимая процедура sp_helpdistpublisher** не будет отображаться имя входа издателя или задать пароль в результате для не -**sysadmin** имена входа.  
  
## <a name="permissions"></a>Разрешения  
 Члены **sysadmin** предопределенной роли сервера может выполняться **sp_helpdistpublisher** для любого издателя, используя локальный сервер в качестве распространителя. Члены **db_owner** предопределенной роли базы данных или **replmonitor** роли в базе данных распространителя могут выполнять **sp_helpdistpublisher** для любого издателя, используя который База данных распространителя. Список пользователей в списке доступа к публикации для публикации на указанном *издатель* может привести к выполнению **sp_helpdistpublisher**. Если *издатель* не указан, возвращаются сведения для всех издателей, что у пользователя есть права доступа.  
  
## <a name="see-also"></a>См. также  
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  
