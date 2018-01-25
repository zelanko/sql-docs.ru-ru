---
title: "Установка репликации SQL Server | Документы Майкрософт"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: sql
ms.technology: setup-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- components [SQL Server replication]
- command line installations [SQL Server replication]
- installing replication
- replication [SQL Server], installing
- command prompt [SQL Server replication]
ms.assetid: c50ad078-060b-4a8d-ad45-9e31a8d85729
caps.latest.revision: "41"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 52760c112e4b188b16a54705b748f404fe7f8299
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="install-sql-server-replication"></a>Установка репликации SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Компоненты репликации можно установить с помощью мастера установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или через командную строку. Репликацию можно установить при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]или при изменении существующего экземпляра.  
  
После установки компонентов репликации необходимо настроить сервер перед началом использования репликации. Дополнительные сведения см. в разделе [Настройка распространения](../../relational-databases/replication/configure-distribution.md) электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
>[!IMPORTANT]  
>Если при изменении существующего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]устанавливаются компоненты репликации, то после завершения установки необходимо перезапустить агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Это действие гарантирует, что агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] распознает подсистемы агента репликации и сможет обращаться к агентам репликации из шагов задания.  
  
## <a name="installing-replication-by-using-setup"></a>Установка репликации с помощью программы установки  
**Установка репликации при установке нового экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**  
  
- Чтобы установить компоненты репликации, включая объекты RMO, на странице **Выбор компонентов** мастера установки выберите **Репликация SQL Server** .  
  
## <a name="installing-replication-from-the-command-prompt"></a>Установка репликации из командной строки  
 **Установка репликации при установке нового экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**  
  
- См. раздел [Установка SQL Server из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).  
  
## <a name="see-also"></a>См. также раздел  
 [Установка SQL Server](../../database-engine/install-windows/install-sql-server.md)   
 [Установка SQL Server из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)   
 [Возможности, поддерживаемые различными выпусками SQL Server](../../sql-server/editions-and-components-of-sql-server-2017.md)  
  
  
