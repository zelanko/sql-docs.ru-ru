---
title: sp_help_proxy (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_proxy
- sp_help_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_proxy
ms.assetid: a2fce164-2b64-40c2-8f35-6eeb7844abf1
caps.latest.revision: 38
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 314eeb6365afafce64ff85aa822e9b2be8c64770
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpproxy-transact-sql"></a>sp_help_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выводит сведения об одной и нескольких учетных записях-посредниках.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_proxy   
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name' ,  
    [ @subsystem_name = ] 'subsystem_name' ,  
    [ @name = ] 'name'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@proxy_id** = ] *id*  
 Идентификационный номер учетной записи-посредника, для которой необходимо вывести список сведений. *Proxy_id* — **int**, значение по умолчанию NULL. Либо *идентификатор* или *proxy_name* может быть указан.  
  
 [ **@proxy_name** =] **"***proxy_name***"**  
 Имя учетной записи-посредника, для которой необходимо вывести список сведений. *Proxy_name* — **sysname**, значение по умолчанию NULL. Либо *идентификатор* или *proxy_name* может быть указан.  
  
 [ **@subsystem_name** =] '*subsystem_name*"  
 Имя подсистемы, для которой будут выводиться учетные записи-посредники. *Subsystem_name* — **sysname**, значение по умолчанию NULL. Когда *subsystem_name* указано, *имя* также должен быть указан.  
  
 В следующей таблице показаны значения для каждой подсистемы.  
  
|Значение|Описание|  
|-----------|-----------------|  
|ActiveScripting|ActiveX-скрипт|  
|CmdExec|Операционная система (CmdExec)|  
|Моментальный снимок|Агент моментальных снимков репликации|  
|LogReader|Агент чтения журнала репликации|  
|Distribution|Агент распространителя репликации|  
|Объединить|Агент слияния репликации|  
|QueueReader|Агент чтения очереди репликации|  
|ANALYSISQUERY|Команда служб Analysis Services|  
|ANALYSISCOMMAND|Запрос служб Analysis Services|  
|Dts|Выполнение пакетов служб SSIS|  
|PowerShell|Скрипт PowerShell|  
  
 [ **@name** =] '*имя*"  
 Имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], для которого должны быть перечислены учетные записи-посредники. Имя — **nvarchar(256)**, значение по умолчанию NULL. Когда *имя* указано, *subsystem_name* также должен быть указан.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|Идентификационный номер учетной записи-посредника.|  
|**name**|**sysname**|Имя учетной записи-посредника.|  
|**credential_identity**|**sysname**|Имя домена и имя пользователя Microsoft Windows для учетных данных, относящихся к учетной записи-посреднику.|  
|**Включен**|**tinyint**|Указывает, включена ли учетная запись-посредник. { **0** — не включено, **1** = включена}|  
|**Описание**|**nvarchar(1024)**|Описание этой учетной записи-посредника.|  
|**user_sid**|**varbinary(85)**|Идентификатор безопасности Windows для пользователя Windows, соответствующего этой учетной записи-посреднику.|  
|**credential_id**|**int**|Идентификатор учетных данных, связанных с учетной записью-посредником.|  
|**credential_identity_exists**|**int**|Указывает, существует ли столбец credential_identity. { 0 = не существует, 1 = существует }|  
  
## <a name="remarks"></a>Замечания  
 Если параметры не указаны, **sp_help_proxy** выводятся сведения обо всех прокси-серверов в экземпляре.  
  
 Чтобы определить, какие учетные записи-посредники определенное имя входа можно использовать для данной подсистемы, укажите *имя* и *subsystem_name*. Если эти аргументы определены, **sp_help_proxy** перечислены учетные записи-посредники, которым указанное имя входа может доступа, которые могут использоваться для указанной подсистемы.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена предопределенная роль базы данных **SQLAgentOperatorRole** в базе данных **msdb** .  
  
 Дополнительные сведения о **SQLAgentOperatorRole**, в разделе [SQL Server Agent Fixed Database Roles](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
> [!NOTE]  
>  **Credential_identity** и **user_sid** столбцы возвращаются только в результирующий набор, если члены **sysadmin** выполнения этой хранимой процедуры.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-information-for-all-proxies"></a>A. Перечисление сведений обо всех учетных записях-посредниках  
 В следующем примере выводятся сведения обо всех учетных записях-посредниках для экземпляра.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_proxy ;  
GO  
```  
  
### <a name="b-listing-information-for-a-specific-proxy"></a>Б. Перечисление сведений для определенной учетной записи-посредника  
 В следующем примере выводятся сведения, относящиеся к учетной записи-посреднику с именем `Catalog application proxy`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_proxy  
    @proxy_name = N'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры агента SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [Хранимая процедура sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)  
  
  
