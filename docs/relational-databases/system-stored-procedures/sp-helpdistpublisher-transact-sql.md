---
title: sp_helpdistpublisher (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdistpublisher_TSQL
- sp_helpdistpublisher
helpviewer_keywords:
- sp_helpdistpublisher
ms.assetid: f207c22d-8fb2-4756-8a9d-6c51d6cd3470
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5fa9e40e0f83e4d47d4f31cfd43f4215ec60ea49
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67943526"
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
`[ @publisher = ] 'publisher'` Является издателем, для которого возвращаются свойства. *издатель* — **sysname**, значение по умолчанию **%** .  
  
`[ @check_user = ] check_user` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя издателя.|  
|**distribution_db**|**sysname**|База данных распространителя для указанного издателя.|  
|**security_mode**|**int**|Режим безопасности, используемый агентами репликации для подключения к издателю обновляемых посредством очередей подписок, или к издателю, не являющемуся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности<br /><br /> **1** = проверка подлинности Windows|  
|**Имя входа**|**sysname**|Имя входа, используемое агентами репликации для подключения к издателю обновляемых посредством очередей подписок, или к издателю, не являющемуся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**password**|**nvarchar(524)**|Возвращаемый пароль (в простой зашифрованной форме). Пароль равен NULL для пользователей, не являющихся **sysadmin**.|  
|**Active**|**bit**|Использует ли удаленный издатель локальный сервер в качестве распространителя:<br /><br /> **0** = Нет<br /><br /> **1** = Да|  
|**working_directory**|**nvarchar(255)**|Имя рабочего каталога.|  
|**доверенные**|**bit**|Требуется ли пароль при подключении издателя к распространителю. Для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий всегда возвращается **0**, означающее, что пароль является обязательным.|  
|**thirdparty_flag**|**bit**|Будет ли публикация включена [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или приложением стороннего разработчика:<br /><br /> **0** = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], oracle или издатель Oracle Gateway.<br /><br /> **1** = издатель интегрирован с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью стороннего приложения.|  
|**publisher_type**|**sysname**|Тип издателя; возможны следующие варианты:<br /><br /> **MSSQLSERVER**<br /><br /> **ORACLE**<br /><br /> **ORACLE GATEWAY**|  
|**publisher_data_source**|**nvarchar(4000)**|Имя источника данных OLE DB на издателе.|  
|**storage_connection_string**|**nvarchar(4000)**|Ключ доступа к хранилищу для рабочий каталог при распространитель или издатель в базе данных SQL Azure.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpdistpublisher** используется во всех типах репликации.  
  
 **sp_helpdistpublisher** не будет отображаться имя для входа издателя, или пароль, в результате задания для отличных**sysadmin** имена входа.  
  
## <a name="permissions"></a>Разрешения  
 Членами **sysadmin** предопределенной роли сервера может выполняться **sp_helpdistpublisher** для любого издателя, используя локальный сервер как распространитель. Членами **db_owner** предопределенной роли базы данных или **replmonitor** роли в базе данных распространителя могут выполнять **sp_helpdistpublisher** для любого издателя, используя который База данных распространителя. Вывод списка пользователей в списке доступа к публикации для публикации на указанном *издателя* может выполняться **sp_helpdistpublisher**. Если *издателя* не указан, возвращаются сведения для всех издателей, что у пользователя есть права доступа.  
  
## <a name="see-also"></a>См. также  
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  
