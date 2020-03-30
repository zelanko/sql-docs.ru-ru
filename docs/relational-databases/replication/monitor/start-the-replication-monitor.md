---
title: Запуск монитора репликации | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, starting
ms.assetid: e037bd27-cc87-4ee9-9e5f-83f6d717cfa4
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 13f31de587e0cacaea6d0b137949084165914597
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "76287875"
---
# <a name="start-the-replication-monitor"></a>Запуск монитора репликации
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Монитор репликации может быть запущен из командной строки или в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] на любом экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Запустив монитор репликации, добавьте в монитор одного или несколько издателей. Дополнительные сведения см. в статье [Добавление и удаление издателей в мониторе репликации](../../../relational-databases/replication/monitor/add-and-remove-publishers-from-replication-monitor.md).  
  
### <a name="to-start-replication-monitor-from-sql-server-management-studio"></a>Запуск монитора репликации из среды SQL Server Management Studio  
  
1.  Подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Щелкните правой кнопкой мыши папку **Репликация** или любую из ее вложенных папок, а затем щелкните **Запустить монитор репликации**.  

### <a name="to-start-replication-monitor-from-the-command-prompt"></a>Запуск монитора репликации из командной строки  
  
1.  Находясь в командной строке, перейдите в каталог установки средств. Путь по умолчанию: [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]Tools\Binn\.  
  
2.  Запустите файл sqlmonitor.exe.  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за репликацией](../../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
