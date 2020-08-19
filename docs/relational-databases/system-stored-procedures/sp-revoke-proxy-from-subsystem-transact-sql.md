---
description: sp_revoke_proxy_from_subsystem (Transact-SQL)
title: sp_revoke_proxy_from_subsystem (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_revoke_login_from_subsystem
- sp_revoke_login_from_subsystem_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revoke_proxy_from_subsystem
ms.assetid: b87bc8ba-3ea8-4aed-b54b-32c3d82d9d2a
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: d58ec6db017fee031a2de2e242a18281eb3b7a68
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469254"
---
# <a name="sp_revoke_proxy_from_subsystem-transact-sql"></a>sp_revoke_proxy_from_subsystem (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отменяет доступ к подсистеме у учетной записи-посредника.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_revoke_proxy_from_subsystem   
    [ @proxy_id = ] proxy_id,  
    [ @proxy_name = ] 'proxy_name',  
    [ @subsystem_id = ] subsystem_id,  
    [ @subsystem_name = ] 'subsystem_name'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @proxy_id = ] id` Идентификационный номер прокси-сервера для отмены доступа. *Proxy_id* имеет **тип int**и значение по умолчанию NULL. Необходимо указать либо *proxy_id* , либо *proxy_name* , но нельзя указать оба значения.  
  
`[ @proxy_name = ] 'proxy_name'` Имя прокси-сервера, с которого нужно отозвать доступ. Аргумент *proxy_name* имеет тип **sysname**и значение по умолчанию NULL. Необходимо указать либо *proxy_id* , либо *proxy_name* , но нельзя указать оба значения.  
  
`[ @subsystem_id = ] id` Идентификационный номер подсистемы, к которой нужно отозвать доступ. *Subsystem_id* имеет **тип int**и значение по умолчанию NULL. Необходимо указать либо *subsystem_id* , либо *subsystem_name* , но нельзя указать оба значения. В следующей таблице показаны значения для каждой подсистемы.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**2**|ActiveX-скрипт<br /><br /> ** \* \* Важно \* ! \* ** подсистема сценариев ActiveX будет удалена из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента в следующей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.|  
|**3**|Операционная система (CmdExec)|  
|**4**|Агент моментальных снимков репликации|  
|**5**|Агент чтения журнала репликации|  
|**6**|Агент распространения репликации|  
|**7**|Replication Merge Agent|  
|**8**|Агент чтения очереди репликации|  
|**9**|Команда служб Analysis Services|  
|**10**|Запрос служб Analysis Services|  
|**11**|[!INCLUDE[ssIS](../../includes/ssis-md.md)] выполнение пакетов служб|  
|**12**|Скрипт PowerShell|  
  
`[ @subsystem_name = ] 'subsystem_name'` Имя подсистемы, к которой нужно отозвать доступ. Аргумент *subsystem_name* имеет тип **sysname**и значение по умолчанию NULL. Необходимо указать либо *subsystem_id* , либо *subsystem_name* , но нельзя указать оба значения. В следующей таблице показаны значения для каждой подсистемы.  
  
|Значение|Описание|  
|-----------|-----------------|  
|ActiveScripting|ActiveX-скрипт|  
|CmdExec|Операционная система (CmdExec)|  
|Моментальный снимок|Агент моментальных снимков репликации|  
|LogReader|Агент чтения журнала репликации|  
|Distribution|Агент распространения репликации|  
|Объединить|Replication Merge Agent|  
|QueueReader|Агент чтения очереди репликации|  
|ANALYSISQUERY|Команда служб Analysis Services|  
|ANALYSISCOMMAND|Запрос служб Analysis Services|  
|Dts|[!INCLUDE[ssIS](../../includes/ssis-md.md)] выполнение пакетов служб|  
|PowerShell|Скрипт PowerShell|  
  
## <a name="remarks"></a>Комментарии  
 При отмене доступа к подсистеме разрешения для участника, указанного в учетной записи-посреднике, не изменяются.  
  
> [!NOTE]  
>  Чтобы определить, какие шаги задания ссылаются на прокси-сервер, щелкните правой кнопкой мыши узел " **прокси** " в разделе **Агент SQL Server** в Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и выберите пункт **Свойства**. В диалоговом окне **Свойства учетной записи-посредника** перейдите на страницу **ссылки** , чтобы просмотреть все шаги задания, ссылающиеся на этот прокси-сервер.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_revoke_proxy_from_subsystem**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере отменяется доступ к подсистеме служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] у учетной записи-посредника `Catalog application proxy`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_revoke_proxy_from_subsystem  
    @proxy_name = 'Catalog application proxy',  
    @subsystem_name = N'Dts';  
```  
  
## <a name="see-also"></a>См. также  
 [Агент SQL Server хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [Реализация агент SQL Server безопасности](../../ssms/agent/implement-sql-server-agent-security.md)   
 [sp_grant_proxy_to_subsystem &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql.md)  
  
  
