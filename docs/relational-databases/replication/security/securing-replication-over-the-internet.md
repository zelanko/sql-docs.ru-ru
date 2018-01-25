---
title: "Защита репликации через Интернет | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [SQL Server replication], Internet
- Internet [SQL Server replication], security
ms.assetid: 25b7af05-2721-4b24-9083-fb671e8bf4e0
caps.latest.revision: "28"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 908bc79a6b4d5db74ba0bd0e76c7457b934635f4
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="securing-replication-over-the-internet"></a>Securing Replication Over the Internet
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Репликация через Интернет может обеспечивать гибкость, особенно для мобильных подписчиков, но ее необходимо настроить так, чтобы гарантировался требуемый уровень безопасности. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] рекомендует использование одной из двух техник безопасной публикации сведений через Интернет.  
  
-   Виртуальная частная сеть (VPN)  
  
-   Параметр веб-синхронизации для репликации слиянием  
  
## <a name="virtual-private-network"></a>Виртуальная частная сеть  
 Виртуальные частные сети обеспечивают простой и безопасный многоуровневый подход к репликации данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] через Интернет. Соединение с виртуальной частной сетью через Интернет логически функционирует как соединение глобальной сети (WAN) между сайтами.  
  
 Это достигается за счет разрешения пользователям доступа к туннелю через Интернет или другую публичную сеть с помощью протокола PPTP корпорации [!INCLUDE[msCoName](../../../includes/msconame-md.md)] , доступного в операционных системах [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows NT версии 4.0 или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2000, либо протокола L2TP, доступного в операционной системе Windows 2000. Этот процесс обеспечивает безопасность и функции, подобные тем, которые доступны в частной сети.  
  
 Дополнительные сведения о настройке виртуальных частных сетей см. в документации по [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows.  
  
## <a name="web-synchronization-through-iis"></a>Веб-синхронизация через IIS  
 Параметр веб-синхронизации для репликации слиянием обеспечивает возможность репликации данных по протоколу HTTPS, что представляет собой удобный подход к репликации данных через брандмауэр. Дополнительные сведения см. в статьях [Настройка веб-синхронизации](../../../relational-databases/replication/configure-web-synchronization.md) и [Архитектура безопасности для веб-синхронизации](../../../relational-databases/replication/security/security-architecture-for-web-synchronization.md).  
  
## <a name="see-also"></a>См. также:  
 [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Безопасность и защита (репликация)](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  
