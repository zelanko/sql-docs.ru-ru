---
title: "Требования безопасности к службам управления | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "служба агента SQL Server, безопасность"
  - "службы [SQL Server], безопасность"
  - "службы SQL Server, безопасность"
  - "поставщики WMI [SQL Server]"
  - "конфигурация сервера [SQL Server]"
  - "безопасность [SQL Server], службы"
  - "службы [SQL Server], WMI"
ms.assetid: 1874a317-ddb2-425d-98d9-b53e1be6fc6a
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# Требования безопасности к службам управления
  Чтобы управлять службами агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , используйте диспетчер конфигурации сервера SQL Server или среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Управление службами на кластеризованных серверах выполняется с помощью администратора кластера.  
  
 Чтобы управлять службой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и устанавливать параметры конфигурации сервера, необходимо быть членом предопределенной роли сервера **serveradmin** или **sysadmin** . Члены группы **Администраторы** Windows могут запускать и останавливать службы и настраивать параметры сервера, предоставляемые Windows.  
  
> [!NOTE]  
>  Чтобы правильно функционировать, учетные записи, используемые для служб, должны быть настроены на правильный домен, файловую систему и разрешения реестра. Сведения о необходимых разрешениях см. в разделе [Настройка учетных записей службы Windows и разрешений](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
## Инструментарий управления Windows (WMI)  
 Диспетчер конфигурации SQL Server и среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] используют инструментарий управления Windows (WMI) для отображения и изменения некоторых свойств сервера. Чтобы управлять службами и получать состояния служб, пользователь должен иметь права доступа к объекту инструментария WMI. В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]следующие страницы свойств сервера используют инструментарий WMI:  
  
-   Службы, запускаемые автоматически  
  
-   Параметры запуска  
  
-   Безопасность  
  
-   Прочие параметры сервера  
  
## Связанные задачи  
 [Настройка инструментария WMI для отображения состояния сервера в инструментальных средствах SQL Server](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
## См. также  
 [Основные понятия о поставщике WMI для управления конфигурацией](../Topic/WMI%20Provider%20for%20Configuration%20Management%20Concepts.md)  
  
  