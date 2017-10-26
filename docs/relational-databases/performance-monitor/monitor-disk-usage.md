---
title: "Мониторинг использования диска | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
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
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5ff4acc6d6465b09c721d376b14ba6574938ef38
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="monitor-disk-usage"></a>Наблюдение за использованием диска
  В Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] операции чтения и записи на диск выполняются с помощью вызовов ввода-вывода операционной системы Microsoft Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет, когда и каким образом выполняется дисковый ввод-вывод, однако базовые операции ввода-вывода выполняет сама операционная система Windows. Подсистема ввода-вывода включает системную шину, платы контроллера диска, диски, накопители на магнитной ленте, дисковод компакт-дисков и много других устройств ввода-вывода. Дисковые операции ввода-вывода часто являются узким местом в системе.  
  
 Контроль активности диска состоит из двух областей, на которые необходимо обратить внимание:  
  
-   Контроль дисковых операций ввода-вывода и обнаружение излишней подкачки.  
  
-   Выделение активности диска, создаваемой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Дополнительные сведения см. в разделе [Наблюдение за использованием диска](http://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx)  
  
  

