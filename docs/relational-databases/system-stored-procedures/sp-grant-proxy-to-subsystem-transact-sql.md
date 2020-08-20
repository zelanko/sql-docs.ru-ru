---
description: sp_grant_proxy_to_subsystem (Transact-SQL)
title: sp_grant_proxy_to_subsystem (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_grant_login_to_subsystem_TSQL
- sp_grant_login_to_subsystem
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grant_proxy_to_subsystem
ms.assetid: 866aaa27-a1e0-453a-9b1b-af39431ad9c2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 964bab1ac95d80d05f16fa8b538f1ecd5f15352c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469407"
---
# <a name="sp_grant_proxy_to_subsystem-transact-sql"></a>sp_grant_proxy_to_subsystem (Transact-SQL)

[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Предоставляет подсистеме доступ к учетной записи-посреднику.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_grant_proxy_to_subsystem  
     { [ @proxy_id = ] proxy_id | [ @proxy_name = ] 'proxy_name' },  
     { [ @subsystem_id = ] subsystem_id | [ @subsystem_name = ] 'subsystem_name' }  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @proxy_id = ] id` Идентификационный номер прокси-сервера, для которого предоставляется доступ. *Proxy_id* имеет **тип int**и значение по умолчанию NULL. Необходимо указать либо *proxy_id* , либо *proxy_name* , но нельзя указать оба значения.  
  
`[ @proxy_name = ] 'proxy_name'` Имя учетной записи-посредника, для которой предоставляется доступ. Аргумент *proxy_name* имеет тип **sysname**и значение по умолчанию NULL. Необходимо указать либо *proxy_id* , либо *proxy_name* , но нельзя указать оба значения.  
  
`[ @subsystem_id = ] id` Идентификационный номер подсистемы, к которой предоставляется доступ. *Subsystem_id* имеет **тип int**и значение по умолчанию NULL. Необходимо указать либо *subsystem_id* , либо *subsystem_name* , но нельзя указать оба значения. В следующей таблице показаны значения для каждой подсистемы.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**2**|Скрипт [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX<br /><br /> ** \* \* Важно \* ! \* ** подсистема сценариев ActiveX будет удалена из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента в следующей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.|  
|**3**|Операционная система (**CmdExec**)|  
|**4**|Агент моментальных снимков репликации|  
|**5**|Агент чтения журнала репликации|  
|**6**|Агент распространения репликации|  
|**7**|Replication Merge Agent|  
|**8**|Агент чтения очереди репликации|  
|**9**|Запрос служб Analysis Services|  
|**10**|Команда служб Analysis Services|  
|**11**|[!INCLUDE[ssIS](../../includes/ssis-md.md)] выполнение пакетов служб|  
|**12**|Скрипт PowerShell|  
| &nbsp; | &nbsp; |
  
`[ @subsystem_name = ] 'subsystem_name'` Имя подсистемы, к которой предоставляется доступ. Аргумент **subsystem_name** имеет тип **sysname**и значение по умолчанию NULL. Необходимо указать либо *subsystem_id* , либо *subsystem_name* , но нельзя указать оба значения. В следующей таблице показаны значения для каждой подсистемы.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**ActiveScripting**|ActiveX-скрипт|  
|**CmdExec**|Операционная система (**CmdExec**)|  
|**Моментальный снимок**|Агент моментальных снимков репликации|  
|**LogReader**|Агент чтения журнала репликации|  
|**Distribution**|агент распространения репликации|  
|**Объединить**|Replication Merge Agent|  
|**QueueReader**|Агент чтения очереди репликации|  
|**ANALYSISQUERY**|Запрос служб Analysis Services|  
|**ANALYSISCOMMAND**|Команда служб Analysis Services|  
|**Dts**|Выполнение пакетов служб SSIS|  
|**PowerShell**|Скрипт PowerShell|  
| &nbsp; | &nbsp; |
  
## <a name="remarks"></a>Комментарии  
 Предоставление подсистеме доступа к учетной записи-посреднику не изменяет разрешений, предоставленных участнику, указанному в учетной записи-посреднике.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_grant_proxy_to_subsystem**.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-granting-access-to-a-subsystem-by-id"></a>A. Предоставление доступа к подсистеме по идентификатору  
 В следующем примере предоставляется доступ к учетной записи-посреднику `Catalog application proxy` подсистеме «Сценарий ActiveX».  
  
```sql
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_proxy_to_subsystem  
    @proxy_name = 'Catalog application proxy',  
    @subsystem_id = 2;  
GO  
```  
  
### <a name="b-granting-access-to-a-subsystem-by-name"></a>Б. Предоставление доступа к подсистеме по имени.  
 В следующем примере учетной записи-посреднику `Catalog application proxy` предоставляется доступ к подсистеме «Выполнение пакета служб SSIS».  
  
```sql
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_proxy_to_subsystem  
    @proxy_name = N'Catalog application proxy',  
    @subsystem_name = N'Dts' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Реализация агент SQL Server безопасности](../../ssms/agent/implement-sql-server-agent-security.md)   
 [sp_revoke_proxy_from_subsystem &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-proxy-from-subsystem-transact-sql.md)   
 [sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)   
 [sp_update_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-proxy-transact-sql.md)  
  
  
