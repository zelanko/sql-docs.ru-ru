---
title: Требования безопасности к службам управления | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent service, security
- services [SQL Server], security
- SQL Server services, security
- WMI Providers [SQL Server]
- server configuration [SQL Server]
- security [SQL Server], services
- services [SQL Server], WMI
ms.assetid: 1874a317-ddb2-425d-98d9-b53e1be6fc6a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ede737abf7d158e4d8dee66885ced018f03a375e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68025635"
---
# <a name="security-requirements-for-managing-services"></a>Требования безопасности к службам управления
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Чтобы управлять службами агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , используйте диспетчер конфигурации сервера SQL Server или среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Управление службами на кластеризованных серверах выполняется с помощью администратора кластера.  
  
 Чтобы управлять службой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и устанавливать параметры конфигурации сервера, необходимо быть членом предопределенной роли сервера **serveradmin** или **sysadmin** . Члены группы **Администраторы** Windows могут запускать и останавливать службы и настраивать параметры сервера, предоставляемые Windows.  
  
> [!NOTE]  
>  Чтобы правильно функционировать, учетные записи, используемые для служб, должны быть настроены на правильный домен, файловую систему и разрешения реестра. Сведения о необходимых разрешениях см. в разделе [Настройка учетных записей службы Windows и разрешений](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
## <a name="windows-management-instrumentation"></a>Инструментарий управления Windows (WMI)  
 Диспетчер конфигурации SQL Server и среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] используют инструментарий управления Windows (WMI) для отображения и изменения некоторых свойств сервера. Чтобы управлять службами и получать состояния служб, пользователь должен иметь права доступа к объекту инструментария WMI. В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]следующие страницы свойств сервера используют инструментарий WMI:  
  
-   Службы, запускаемые автоматически  
  
-   Параметры запуска  
  
-   безопасность  
  
-   Прочие параметры сервера  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Настройка инструментария WMI для отображения состояния сервера в инструментальных средствах SQL Server](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
## <a name="related-content"></a>См. также  
 [Основные понятия о поставщике WMI для управления конфигурацией](../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
