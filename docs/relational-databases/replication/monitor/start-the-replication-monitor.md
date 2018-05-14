---
title: Запуск монитора репликации | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, starting
ms.assetid: e037bd27-cc87-4ee9-9e5f-83f6d717cfa4
caps.latest.revision: 36
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7e542046c9fa5ce28b41cc6f9952e84f53c3f84e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="start-the-replication-monitor"></a>Запуск монитора репликации
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Монитор репликации может быть запущен из командной строки или в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] на любом экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Запустив монитор репликации, добавьте в монитор одного или несколько издателей. Дополнительные сведения см. в статье [Добавление и удаление издателей в мониторе репликации](../../../relational-databases/replication/monitor/add-and-remove-publishers-from-replication-monitor.md).  
  
### <a name="to-start-replication-monitor-from-sql-server-management-studio"></a>Запуск монитора репликации из среды SQL Server Management Studio  
  
1.  Подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Щелкните правой кнопкой мыши папку **Репликация** или любую из ее вложенных папок, а затем щелкните **Запустить монитор репликации**.  
  
### <a name="to-start-replication-monitor-from-the-command-prompt"></a>Запуск монитора репликации из командной строки  
  
1.  Находясь в командной строке, перейдите в каталог установки средств. Путь по умолчанию: [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]Tools\Binn\.  
  
2.  Запустите файл sqlmonitor.exe.  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за репликацией](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
