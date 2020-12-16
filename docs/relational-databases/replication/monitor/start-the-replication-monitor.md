---
description: Запуск монитора репликации
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
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: d88c974bbf6d8f18271f4ea6f68b95e5c0506203
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97432592"
---
# <a name="start-the-replication-monitor"></a>Запуск монитора репликации
[!INCLUDE[sql-asdbmi](../../../includes/applies-to-version/sql-asdbmi.md)]
  Монитор репликации может быть запущен из командной строки или в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] на любом экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Запустив монитор репликации, добавьте в монитор одного или несколько издателей. Дополнительные сведения см. в статье [Добавление и удаление издателей в мониторе репликации](../../../relational-databases/replication/monitor/add-and-remove-publishers-from-replication-monitor.md).  
  
### <a name="to-start-replication-monitor-from-sql-server-management-studio"></a>Запуск монитора репликации из среды SQL Server Management Studio  
  
1.  Подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Щелкните правой кнопкой мыши папку **Репликация** или любую из ее вложенных папок, а затем щелкните **Запустить монитор репликации**.  

### <a name="to-start-replication-monitor-from-the-command-prompt"></a>Запуск монитора репликации из командной строки  
  
1.  Находясь в командной строке, перейдите в каталог установки средств. Путь по умолчанию: [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]Tools\Binn\.  
  
2.  Запустите файл sqlmonitor.exe.  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за репликацией](../../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
