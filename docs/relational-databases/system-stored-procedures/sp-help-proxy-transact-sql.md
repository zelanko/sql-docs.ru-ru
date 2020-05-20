---
title: sp_help_proxy (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_proxy
- sp_help_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_proxy
ms.assetid: a2fce164-2b64-40c2-8f35-6eeb7844abf1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c091872c7e79a45fd6fb135d20c0910f9cd0158d
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828420"
---
# <a name="sp_help_proxy-transact-sql"></a>sp_help_proxy (Transact-SQL)
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
`[ @proxy_id = ] id`Идентификационный номер прокси-сервера, для которого необходимо получить список сведений. *Proxy_id* имеет **тип int**и значение по умолчанию NULL. Можно указать либо *идентификатор* , либо *proxy_name* .  
  
`[ @proxy_name = ] 'proxy_name'`Имя учетной записи-посредника для получения списка сведений. Аргумент *proxy_name* имеет тип **sysname**и значение по умолчанию NULL. Можно указать либо *идентификатор* , либо *proxy_name* .  
  
`[ @subsystem_name = ] 'subsystem_name'`Имя подсистемы, для которой перечисляются прокси-серверы. Аргумент *subsystem_name* имеет тип **sysname**и значение по умолчанию NULL. Если указано *subsystem_name* , необходимо также указать *Name* .  
  
 В следующей таблице показаны значения для каждой подсистемы.  
  
|Значение|Описание|  
|-----------|-----------------|  
|ActiveScripting|ActiveX-скрипт|  
|CmdExec|Операционная система (CmdExec)|  
|Снимок|Агент моментальных снимков репликации|  
|LogReader|Агент чтения журнала репликации|  
|Distribution|агент распространения репликации|  
|Объединить|Replication Merge Agent|  
|QueueReader|Агент чтения очереди репликации|  
|ANALYSISQUERY|Команда служб Analysis Services|  
|ANALYSISCOMMAND|Запрос служб Analysis Services|  
|Dts|Выполнение пакетов служб SSIS|  
|PowerShell|Скрипт PowerShell|  
  
`[ @name = ] 'name'`Имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа, для которого перечисляются учетные записи-посредники. Имя имеет тип **nvarchar (256)** и значение по умолчанию NULL. Если указано *имя* , необходимо также указать *subsystem_name* .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|Идентификационный номер учетной записи-посредника.|  
|**name**|**sysname**|Имя учетной записи-посредника.|  
|**credential_identity**|**sysname**|Имя домена и имя пользователя Microsoft Windows для учетных данных, относящихся к учетной записи-посреднику.|  
|**доступной**|**tinyint**|Указывает, включена ли учетная запись-посредник. { **0** = не включено, **1** = включено}|  
|**nописание**|**nvarchar(1024)**|Описание этой учетной записи-посредника.|  
|**user_sid**|**varbinary(85)**|Идентификатор безопасности Windows для пользователя Windows, соответствующего этой учетной записи-посреднику.|  
|**credential_id**|**int**|Идентификатор учетных данных, связанных с учетной записью-посредником.|  
|**credential_identity_exists**|**int**|Указывает, существует ли столбец credential_identity. { 0 = не существует, 1 = существует }|  
  
## <a name="remarks"></a>Примечания  
 Если параметры не указаны, **sp_help_proxy** выводит сведения для всех прокси-серверов в экземпляре.  
  
 Чтобы определить, какие прокси-серверы могут использоваться для входа в данную подсистему, укажите *имя* и *subsystem_name*. При указании этих аргументов **sp_help_proxy** перечисляет прокси-серверы, к которым может получить доступ указанное имя входа, которые могут использоваться для указанной подсистемы.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена предопределенная роль базы данных **SQLAgentOperatorRole** в базе данных **msdb** .  
  
 Дополнительные сведения о **SQLAgentOperatorRole**см. в разделе [Агент SQL Server предопределенных ролей базы данных](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
> [!NOTE]  
>  Столбцы **credential_identity** и **user_sid** возвращаются в результирующем наборе только тогда, когда члены **роли sysadmin** выполняют эту хранимую процедуру.  
  
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
 [Агент SQL Server хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)  
  
  
