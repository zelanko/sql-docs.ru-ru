---
title: Рассылка сообщения о завершении работы (командная строка) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- SQL Server, stopping
- named instances [SQL Server], broadcasting shutdown messages
- shutdown message broadcast
- broadcasting shutdown message
- command prompt [SQL Server], broadcasting shutdown messages
- default instances [SQL Server], broadcasting shutdown messages
- stopping SQL Server
ms.assetid: 9f20ccd5-d952-431d-ba12-339911af9430
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f4ac2fc507e86a9f0b24b03f661326a64f20f354
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055877"
---
# <a name="broadcast-a-shutdown-message-command-prompt"></a>Рассылка сообщения о завершении работы (командная строка)
  В этой статье описывается широковещательная передача сообщения о завершении работы в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью команды **net send** . В этом сообщении должно быть указано время остановки экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы пользователи могли к этому времени завершить выполнение своих задач.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-broadcast-a-shutdown-message"></a>Рассылка сообщения о завершении работы  
  
1.  В командной строке введите:  
  
     **net send /users "message"**  
  
     Параметр **/users** указывает, что сообщение будет отправлено всем пользователям, поддерживающим соединение с сервером.  
  
> [!NOTE]  
>  Команда **net send** требует, чтобы служба была запущена как на компьютере отправителя, так и на компьютерах получателей. Служба сообщений по умолчанию отключена в Windows Server 2003. Дополнительные сведения о команде **net send**см. в документации по Windows.  
  
 В сети может оказаться более удобным использовать для связи с пользователями электронную почту или телефон. Чтобы определить, какие пользователи в настоящий момент подключены к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используйте монитор активности. Сведения о мониторе активности см. в статье [Монитор активности](../../relational-databases/performance-monitor/activity-monitor.md) и [Открытие монитора активности (среда SQL Server Management Studio)](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Запуск, остановка, приостановка, возобновление и перезапуск ядра СУБД, агента SQL Server и обозревателя SQL Server](start-stop-pause-resume-restart-sql-server-services.md)  
  
  
