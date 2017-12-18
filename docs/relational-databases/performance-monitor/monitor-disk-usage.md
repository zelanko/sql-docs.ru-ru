---
title: "Мониторинг использования диска | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database monitoring [SQL Server], disk usage
- disks [SQL Server]
- monitoring performance [SQL Server], disk usage
- server performance [SQL Server], disk usage
- monitoring [SQL Server], disk activity
- excess paging [SQL Server]
- tuning databases [SQL Server], disk usage
- I/O [SQL Server], monitoring
- disks [SQL Server], monitoring activity
- isolating disk activity [SQL Server]
- database performance [SQL Server], disk usage
- monitoring server performance [SQL Server], disk usage
ms.assetid: 1525449c-ea7d-4222-b294-1ba1fe99c9ac
caps.latest.revision: "23"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: cca3caac615c8378be5b87217325a5a067a026e4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="monitor-disk-usage"></a>Наблюдение за использованием диска
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] операции чтения и записи на диск выполняются с помощью вызовов ввода-вывода операционной системы Microsoft Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет, когда и каким образом выполняется дисковый ввод-вывод, однако базовые операции ввода-вывода выполняет сама операционная система Windows. Подсистема ввода-вывода включает системную шину, платы контроллера диска, диски, накопители на магнитной ленте, дисковод компакт-дисков и много других устройств ввода-вывода. Дисковые операции ввода-вывода часто являются узким местом в системе.  
  
 Контроль активности диска состоит из двух областей, на которые необходимо обратить внимание:  
  
-   Контроль дисковых операций ввода-вывода и обнаружение излишней подкачки.  
  
-   Выделение активности диска, создаваемой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Дополнительные сведения см. в разделе [Наблюдение за использованием диска](http://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx)  
  
  
