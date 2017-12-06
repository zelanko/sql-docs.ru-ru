---
title: "Просмотр журнала приложений Windows | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application logs [SQL Server]
- Windows application logs [SQL Server]
- viewing Windows application logs
- errors [SQL Server], logs
- system logs [SQL Server]
- security logs [SQL Server]
- displaying Windows application logs
- logs [SQL Server], Windows application logs
ms.assetid: f9853b74-7db7-47cc-b957-e49ed5bc0a1a
caps.latest.revision: "20"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 657c2cc723f862f2a1325721649ab1759a5cb0e5
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="viewing-the-windows-application-log"></a>Просмотр журнала приложений Windows
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен на использование журнала приложений Microsoft Windows, каждый [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сеанса записывает новые события в журнал событий. В отличие от журнала ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , новый журнал приложений не создается заново каждый раз при запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Просмотр и управление журналом приложений Windows осуществляется с помощью средства просмотра событий Windows или средства просмотра журналов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 С помощью средства просмотра событий можно просмотреть три журнала.  
  
|Тип журнала Windows|Description|  
|----------------------|-----------------|  
|Системный журнал|Регистрирует события, записанные компонентами операционной системы Windows. Например, отказ загрузки драйвера или другого системного компонента при запуске записывается в системный журнал.|  
|Журнал безопасности|Регистрирует события безопасности, например неудавшиеся попытки входа в систему. Это помогает отследить изменения в системе безопасности и идентифицировать возможные «дыры». Например, попытка войти в систему регистрируется в журнале безопасности в зависимости от параметров аудита в диспетчере пользователей.<br /><br /> Только члены предопределенной роли сервера **sysadmin** могут просматривать журнал безопасности.|  
|Журнал приложений|Регистрирует события, записываемые приложениями. Например, приложение базы данных может записать в журнал приложений ошибку файла.|  
  
 Дополнительные сведения о средстве просмотра событий, управлении журналом приложений и данных, которые он представляет, см. в документации Windows.  
  
 **Просмотр журнала приложений Windows**  
  
 [Просмотр журнала приложений Windows (Windows)](../../relational-databases/performance/view-the-windows-application-log-windows-10.md)  
  
  
