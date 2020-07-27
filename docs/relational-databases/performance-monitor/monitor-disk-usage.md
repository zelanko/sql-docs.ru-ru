---
title: Мониторинг использования диска | Документация Майкрософт
description: Мониторинг активности дисков для SQL Server включает мониторинг дискового ввода-вывода и выявление избыточной подкачки, а также изоляцию активности дисков, создаваемой SQL Server.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
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
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 2bf6f22b6a3b76694c89bd480b289ecd0db1dce5
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458491"
---
# <a name="monitor-disk-usage"></a>Наблюдение за использованием диска
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  В Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] операции чтения и записи на диск выполняются с помощью вызовов ввода-вывода операционной системы Microsoft Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет, когда и каким образом выполняется дисковый ввод-вывод, однако базовые операции ввода-вывода выполняет сама операционная система Windows. Подсистема ввода-вывода включает системную шину, платы контроллера диска, диски, накопители на магнитной ленте, дисковод компакт-дисков и много других устройств ввода-вывода. Дисковые операции ввода-вывода часто являются узким местом в системе.  
  
 Контроль активности диска состоит из двух областей, на которые необходимо обратить внимание:  
  
-   Контроль дисковых операций ввода-вывода и обнаружение излишней подкачки.  
  
-   Выделение активности диска, создаваемой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Дополнительные сведения см. в разделе [Наблюдение за использованием диска](https://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx). 
 
 Дополнительные сведения о том, как устранять неполадки с операциями ввода-вывода в SQL Server, см. в статье [Slow I/O - SQL Server and disk I/O performance](https://techcommunity.microsoft.com/t5/SQL-Server-Support/Slow-I-O-SQL-Server-and-disk-I-O-performance/ba-p/333983) (Медленные операции ввода-вывода: производительность SQL Server и операций дискового ввода-вывода).
  
  
