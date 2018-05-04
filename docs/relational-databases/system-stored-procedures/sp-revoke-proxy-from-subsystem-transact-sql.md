---
title: sp_revoke_proxy_from_subsystem (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- sp_revoke_login_from_subsystem
- sp_revoke_login_from_subsystem_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revoke_proxy_from_subsystem
ms.assetid: b87bc8ba-3ea8-4aed-b54b-32c3d82d9d2a
caps.latest.revision: 37
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f160d25be2c9ba3f863294655ff50d50d3aa7e77
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sprevokeproxyfromsubsystem-transact-sql"></a>sp_revoke_proxy_from_subsystem (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [ **@proxy_id** = ] *id*  
 Идентификатор учетной записи-посредника, для которой необходимо запретить доступ. *Proxy_id* — **int**, значение по умолчанию NULL. Либо *proxy_id* или *proxy_name* должен быть указан, но не оба аргумента одновременно.  
  
 [ **@proxy_name** =] **"***proxy_name***"**  
 Имя учетной записи-посредника, у которой отменяется право на доступ. *Proxy_name* — **sysname**, значение по умолчанию NULL. Либо *proxy_id* или *proxy_name* должен быть указан, но не оба аргумента одновременно.  
  
 [ **@subsystem_id** = ] *id*  
 Идентификатор подсистемы, у которой отменяется право на доступ. *Subsystem_id* — **int**, значение по умолчанию NULL. Либо *subsystem_id* или *subsystem_name* должен быть указан, но не оба аргумента одновременно. В следующей таблице показаны значения для каждой подсистемы.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**2**|ActiveX-скрипт<br /><br /> **\*\* Важные \* \***  подсистема сценариев ActiveX будет удалена из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агент в будущей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.|  
|**3**|Операционная система (CmdExec)|  
|**4**|Агент моментальных снимков репликации|  
|**5**|Агент чтения журнала репликации|  
|**6**|Агент распространения репликации|  
|**7**|Агент слияния репликации|  
|**8**|Агент чтения очереди репликации|  
|**9**|Команда служб Analysis Services|  
|**10**|Запрос служб Analysis Services|  
|**11**|[!INCLUDE[ssIS](../../includes/ssis-md.md)] выполнение пакетов служб|  
|**12**|Скрипт PowerShell|  
  
 [ **@subsystem_name**=] **"***subsystem_name***"**  
 Имя подсистемы, у которой отменяется право на доступ. *Subsystem_name* — **sysname**, значение по умолчанию NULL. Либо *subsystem_id* или *subsystem_name* должен быть указан, но не оба аргумента одновременно. В следующей таблице показаны значения для каждой подсистемы.  
  
|Значение|Описание|  
|-----------|-----------------|  
|ActiveScripting|ActiveX-скрипт|  
|CmdExec|Операционная система (CmdExec)|  
|Моментальный снимок|Агент моментальных снимков репликации|  
|LogReader|Агент чтения журнала репликации|  
|Distribution|Агент распространения репликации|  
|Объединить|Агент слияния репликации|  
|QueueReader|Агент чтения очереди репликации|  
|ANALYSISQUERY|Команда служб Analysis Services|  
|ANALYSISCOMMAND|Запрос служб Analysis Services|  
|Dts|[!INCLUDE[ssIS](../../includes/ssis-md.md)] выполнение пакетов служб|  
|PowerShell|Скрипт PowerShell|  
  
## <a name="remarks"></a>Замечания  
 При отмене доступа к подсистеме разрешения для участника, указанного в учетной записи-посреднике, не изменяются.  
  
> [!NOTE]  
>  Чтобы определить, какие шаги задания ссылаются на учетную запись-посредник, щелкните правой кнопкой мыши **учетные записи-посредники** узле **агента SQL Server** в Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]и нажмите кнопку **свойства**. В **свойства учетной записи-посредника** выберите **ссылки** страницу для просмотра всех шагов задания, которые ссылаются на этот прокси-сервер.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_revoke_proxy_from_subsystem**.  
  
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
 [Хранимые процедуры агента SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [Обеспечение безопасности агента SQL Server](http://msdn.microsoft.com/library/d770d35c-c8de-4e00-9a85-7d03f45a0f0d)   
 [sp_grant_proxy_to_subsystem &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql.md)  
  
  
