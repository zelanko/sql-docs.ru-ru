---
title: Мониторинг использования диска | Документация Майкрософт
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
ms.openlocfilehash: 60168c1622ebe7660bb10d421b9d35a6d41523f0
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68091018"
---
# <a name="monitor-disk-usage"></a>Наблюдение за использованием диска
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] операции чтения и записи на диск выполняются с помощью вызовов ввода-вывода операционной системы Microsoft Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет, когда и каким образом выполняется дисковый ввод-вывод, однако базовые операции ввода-вывода выполняет сама операционная система Windows. Подсистема ввода-вывода включает системную шину, платы контроллера диска, диски, накопители на магнитной ленте, дисковод компакт-дисков и много других устройств ввода-вывода. Дисковые операции ввода-вывода часто являются узким местом в системе.  
  
 Контроль активности диска состоит из двух областей, на которые необходимо обратить внимание:  
  
-   Контроль дисковых операций ввода-вывода и обнаружение излишней подкачки.  
  
-   Выделение активности диска, создаваемой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Дополнительные сведения см. в разделе [Наблюдение за использованием диска](https://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx). 
 
 Дополнительные сведения о том, как устранять неполадки с операциями ввода-вывода в SQL Server, см. в статье [Slow I/O - SQL Server and disk I/O performance](https://techcommunity.microsoft.com/t5/SQL-Server-Support/Slow-I-O-SQL-Server-and-disk-I-O-performance/ba-p/333983) (Медленные операции ввода-вывода: производительность SQL Server и операций дискового ввода-вывода).
  
  
