---
title: Требования безопасности к службам управления | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: cf42651f256a2fb1e3c72e7bb7ff312486ea2472
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62810065"
---
# <a name="security-requirements-for-managing-services"></a>Требования безопасности к службам управления
  Чтобы управлять службами агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , используйте диспетчер конфигурации сервера SQL Server или среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Управление службами на кластеризованных серверах выполняется с помощью администратора кластера.  
  
 Чтобы управлять службой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и устанавливать параметры конфигурации сервера, необходимо быть членом предопределенной роли сервера **serveradmin** или **sysadmin** . Члены группы **Администраторы** Windows могут запускать и останавливать службы и настраивать параметры сервера, предоставляемые Windows.  
  
> [!NOTE]  
>  Чтобы правильно функционировать, учетные записи, используемые для служб, должны быть настроены на правильный домен, файловую систему и разрешения реестра. Сведения о необходимых разрешениях см. в разделе [Настройка учетных записей службы Windows и разрешений](configure-windows-service-accounts-and-permissions.md).  
  
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
  
  
