---
title: sp_grant_proxy_to_subsystem (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_grant_login_to_subsystem_TSQL
- sp_grant_login_to_subsystem
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grant_proxy_to_subsystem
ms.assetid: 866aaa27-a1e0-453a-9b1b-af39431ad9c2
ms.author: vanto
manager: craigg
ms.openlocfilehash: 1cfa9e00a492cce8303a672a4ed5f99a40e47a21
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031497"
---
# <a name="spgrantproxytosubsystem-transact-sql"></a>sp_grant_proxy_to_subsystem (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет подсистеме доступ к учетной записи-посреднику.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_grant_proxy_to_subsystem  
     { [ @proxy_id = ] proxy_id | [ @proxy_name = ] 'proxy_name' },  
     { [ @subsystem_id = ] subsystem_id | [ @subsystem_name = ] 'subsystem_name' }  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@proxy_id =** ] *id*  
 Идентификационный номер учетной записи-посредника, к которой предоставляется доступ. *Proxy_id* — **int**, значение по умолчанию NULL. Либо *proxy_id* или *proxy_name* должен быть указан, но не оба аргумента одновременно.  
  
 [  **@proxy_name =** ] **"***proxy_name***"**  
 Имя учетной записи-посредника, к которой предоставляется доступ. *Proxy_name* — **sysname**, значение по умолчанию NULL. Либо *proxy_id* или *proxy_name* должен быть указан, но не оба аргумента одновременно.  
  
 [ **@subsystem_id =** ] *id*  
 Идентификационный номер подсистемы, которой предоставляется доступ. *Subsystem_id* — **int**, значение по умолчанию NULL. Либо *subsystem_id* или *subsystem_name* должен быть указан, но не оба аргумента одновременно. В следующей таблице показаны значения для каждой подсистемы.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**2**|Скрипт [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX<br /><br /> **\*\* Важные \* \***  подсистема сценариев ActiveX будет удалена из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агент в будущих версиях [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.|  
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
  
 [  **@subsystem_name =** ] **"***subsystem_name***"**  
 Имя подсистемы, которой предоставляется доступ. **Subsystem_name** — **sysname**, значение по умолчанию NULL. Либо *subsystem_id* или *subsystem_name* должен быть указан, но не оба аргумента одновременно. В следующей таблице показаны значения для каждой подсистемы.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**ActiveScripting**|ActiveX-скрипт|  
|**CmdExec**|Операционная система (**CmdExec**)|  
|**Моментальный снимок**|Агент моментальных снимков репликации|  
|**LogReader**|Агент чтения журнала репликации|  
|**Distribution**|Агент распространения репликации|  
|**Объединить**|Replication Merge Agent|  
|**QueueReader**|Агент чтения очереди репликации|  
|**ANALYSISQUERY**|Запрос служб Analysis Services|  
|**ANALYSISCOMMAND**|Команда служб Analysis Services|  
|**Dts**|Выполнение пакетов служб SSIS|  
|**PowerShell**|Скрипт PowerShell|  
  
## <a name="remarks"></a>Примечания  
 Предоставление подсистеме доступа к учетной записи-посреднику не изменяет разрешений, предоставленных участнику, указанному в учетной записи-посреднике.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_grant_proxy_to_subsystem**.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-granting-access-to-a-subsystem-by-id"></a>A. Предоставление доступа к подсистеме по идентификатору  
 В следующем примере предоставляется доступ к учетной записи-посреднику `Catalog application proxy` подсистеме «Сценарий ActiveX».  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_proxy_to_subsystem  
    @proxy_name = 'Catalog application proxy',  
    @subsystem_id = 2;  
GO  
```  
  
### <a name="b-granting-access-to-a-subsystem-by-name"></a>Б. Предоставление доступа к подсистеме по имени.  
 В следующем примере учетной записи-посреднику `Catalog application proxy` предоставляется доступ к подсистеме «Выполнение пакета служб SSIS».  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_proxy_to_subsystem  
    @proxy_name = N'Catalog application proxy',  
    @subsystem_name = N'Dts' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Обеспечение безопасности агента SQL Server](../../ssms/agent/implement-sql-server-agent-security.md)   
 [sp_revoke_proxy_from_subsystem &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-proxy-from-subsystem-transact-sql.md)   
 [Хранимая процедура sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)   
 [sp_update_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-proxy-transact-sql.md)  
  
  
