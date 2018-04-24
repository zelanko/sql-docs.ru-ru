---
title: Рассылка сообщения о завершении работы (командная строка) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: configure-windows
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server, stopping
- named instances [SQL Server], broadcasting shutdown messages
- shutdown message broadcast
- broadcasting shutdown message
- command prompt [SQL Server], broadcasting shutdown messages
- default instances [SQL Server], broadcasting shutdown messages
- stopping SQL Server
ms.assetid: 9f20ccd5-d952-431d-ba12-339911af9430
caps.latest.revision: 28
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cfe736cfcbf52edaeaaeb7de418acbec76d4644b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="broadcast-a-shutdown-message-command-prompt"></a>Рассылка сообщения о завершении работы (командная строка)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этой статье описывается широковещательная передача сообщения о завершении работы в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью команды **net send** . В этом сообщении должно быть указано время остановки экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы пользователи могли к этому времени завершить выполнение своих задач.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-broadcast-a-shutdown-message"></a>Рассылка сообщения о завершении работы  
  
1.  В командной строке введите:  
  
     **net send /users "message"**  
  
     Параметр **/users** указывает, что сообщение будет отправлено всем пользователям, поддерживающим соединение с сервером.  
  
> [!NOTE]  
>  Команда **net send** требует, чтобы служба была запущена как на компьютере отправителя, так и на компьютерах получателей. Служба сообщений по умолчанию отключена в Windows Server 2003. Дополнительные сведения о команде **net send**см. в документации по Windows.  
  
 В сети может оказаться более удобным использовать для связи с пользователями электронную почту или телефон. Чтобы определить, какие пользователи в настоящий момент подключены к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используйте монитор активности. Сведения о мониторе активности см. в статье [Монитор активности](../../relational-databases/performance-monitor/activity-monitor.md) и [Открытие монитора активности (среда SQL Server Management Studio)](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md).  
  
## <a name="see-also"></a>См. также:  
 [Запуск, остановка, приостановка, возобновление и перезапуск ядра СУБД, агента SQL Server и обозревателя SQL Server](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
