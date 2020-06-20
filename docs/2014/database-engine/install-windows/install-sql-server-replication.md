---
title: Установка репликации SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- components [SQL Server replication]
- command line installations [SQL Server replication]
- installing replication
- replication [SQL Server], installing
- command prompt [SQL Server replication]
ms.assetid: c50ad078-060b-4a8d-ad45-9e31a8d85729
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ba941fda1d463e7bb4a26bd2fbb45d2a82ca27b3
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84932499"
---
# <a name="install-sql-server-replication"></a>Установка репликации SQL Server
  Компоненты репликации можно установить с помощью мастера установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или через командную строку. Репликацию можно установить при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]или при изменении существующего экземпляра.  
  
 После установки компонентов репликации необходимо настроить сервер перед началом использования репликации. Дополнительные сведения см. в разделе [Настройка распространения](../../relational-databases/replication/configure-distribution.md) электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!IMPORTANT]  
>  Если при изменении существующего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]устанавливаются компоненты репликации, то после завершения установки необходимо перезапустить агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Это действие гарантирует, что агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] распознает подсистемы агента репликации и сможет обращаться к агентам репликации из шагов задания.  
  
## <a name="installing-replication-by-using-setup"></a>Установка репликации с помощью программы установки  
 **Установка репликации при установке нового экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**  
  
-   Чтобы установить компоненты репликации, включая объекты RMO, на странице **Выбор компонентов** мастера установки выберите **Репликация SQL Server** .  
  
## <a name="installing-replication-from-the-command-prompt"></a>Установка репликации из командной строки  
 **Установка репликации при установке нового экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**  
  
-   См. раздел [Install SQL Server 2014 из командной строки](install-sql-server-from-the-command-prompt.md).  
  
## <a name="see-also"></a>См. также:  
 [Установка SQL Server 2014](install-sql-server.md)   
 [Установка SQL Server 2014 из командной строки](install-sql-server-from-the-command-prompt.md)   
 [Возможности, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
