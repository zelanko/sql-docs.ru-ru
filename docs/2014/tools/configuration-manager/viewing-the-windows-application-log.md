---
title: Просмотр журнала приложений Windows | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 654d4adbd2e4baa97b16e83261089d8d78289af6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63150757"
---
# <a name="viewing-the-windows-application-log"></a>Просмотр журнала приложений Windows
  Если настройками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предусмотрено использование журнала приложений Microsoft Windows, каждый сеанс [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записывает новые события в этот журнал. В отличие от журнала ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , новый журнал приложений не создается заново каждый раз при запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Просмотр и управление журналом приложений Windows осуществляется с помощью средства просмотра событий Windows или средства просмотра журналов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 С помощью средства просмотра событий можно просмотреть три журнала.  
  
|Тип журнала Windows|Описание|  
|----------------------|-----------------|  
|Системный журнал|Регистрирует события, записанные компонентами операционной системы Windows. Например, отказ загрузки драйвера или другого системного компонента при запуске записывается в системный журнал.|  
|Журнал безопасности|Регистрирует события безопасности, например неудавшиеся попытки входа в систему. Это помогает отследить изменения в системе безопасности и идентифицировать возможные «дыры». Например, попытка войти в систему регистрируется в журнале безопасности в зависимости от параметров аудита в диспетчере пользователей.<br /><br /> Только члены предопределенной роли сервера **sysadmin** могут просматривать журнал безопасности.|  
|Журнал приложений|Регистрирует события, записываемые приложениями. Например, приложение базы данных может записать в журнал приложений ошибку файла.|  
  
 Дополнительные сведения о средстве просмотра событий, управлении журналом приложений и данных, которые он представляет, см. в документации Windows.  
  
 **Просмотр журнала приложений Windows**  
  
 [Просмотр журнала приложений Windows (Windows)](../../relational-databases/performance/view-the-windows-application-log-windows-10.md)  
  
  
