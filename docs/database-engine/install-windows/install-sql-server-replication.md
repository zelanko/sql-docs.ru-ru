---
title: "Установка репликации SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "компоненты [репликация SQL Server]"
  - "установки из командной строки [репликация SQL Server]"
  - "установка репликации"
  - "репликация [SQL Server], установка"
  - "командная строка [репликация SQL Server]"
ms.assetid: c50ad078-060b-4a8d-ad45-9e31a8d85729
caps.latest.revision: 41
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 41
---
# Установка репликации SQL Server
  Компоненты репликации можно установить с помощью мастера установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или через командную строку. Репликацию можно установить при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]или при изменении существующего экземпляра.  
  
 После установки компонентов репликации необходимо настроить сервер перед началом использования репликации. Дополнительные сведения см. в разделе [Настройка распространения](../../relational-databases/replication/configure-distribution.md) электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Если при изменении существующего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливаются компоненты репликации, то после завершения установки необходимо перезапустить агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это действие гарантирует, что агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] распознает подсистемы агента репликации и сможет обращаться к агентам репликации из шагов задания.  
  
## Установка репликации с помощью программы установки  
 **Установка репликации при установке нового экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**  
  
-   Чтобы установить компоненты репликации, включая объекты RMO, на странице **Выбор компонентов** мастера установки выберите **Репликация SQL Server**.  
  
## Установка репликации из командной строки  
 **Установка репликации при установке нового экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**  
  
-   См. раздел [Установка SQL Server 2016 из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).  
  
## См. также:  
 [Установка SQL Server 2016](../../database-engine/install-windows/install-sql-server-2016.md)   
 [Установка SQL Server 2016 из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)   
 [Возможности, поддерживаемые различными выпусками SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  
  
  