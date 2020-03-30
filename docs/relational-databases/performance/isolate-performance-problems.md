---
title: Локализация проблем производительности | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- isolating performance problems [SQL Server]
- monitoring performance [SQL Server], isolating problems
- database monitoring [SQL Server], isolating problems
- tuning databases [SQL Server], isolating problems
- monitoring server performance [SQL Server], isolating problems
- database performance [SQL Server], isolating problems
- server performance [SQL Server], isolating problems
ms.assetid: 2eb425cb-9166-4027-ae08-c8fc2d236f44
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 643551201567ae10980c1fe3d5efca95a1bc9ded
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68051971"
---
# <a name="isolate-performance-problems"></a>Локализация проблем производительности
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Зачастую для локализации проблем производительности базы данных более эффективным является совместное использование нескольких средств [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или Microsoft Windows вместо одного. Например, возможность графического плана выполнения, также называемая инструкцией Showplan, помогает быстро распознать взаимоблокировки в отдельном запросе. Однако при совместном использовании возможности контроля [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и Windows можно с еще большей легкостью распознать некоторые другие проблемы производительности.  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] может быть использовано для контроля и диагностики проблем, связанных с языком Transact-SQL и приложениями. Системный монитор может быть использован для контроля проблем аппаратного обеспечения и других системных проблем.  
  
 Для поиска и устранения проблем можно осуществлять контроль следующих областей:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или пакеты инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)] , переданные пользовательскими приложениями;  
  
-   деятельность пользователя, например блокировки и взаимоблокировки;  
  
-   работа аппаратного обеспечения, например использование диска.  
  
 Проблемы могут включать:  
  
-   ошибки разработки приложения, включающие неверно написанные инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] ;  
  
-   ошибки аппаратного обеспечения, например ошибки, связанные с диском или сетью;  
  
-   чрезмерное блокирование из-за неверно спроектированной базы данных.  
  
## <a name="tools-for-common-performance-problems"></a>Средства для устранения общих проблем производительности  
 Не менее важным является тщательный выбор проблем производительности, за которыми будет следить каждый инструмент. Инструменты и программы зависят от типа проблемы производительности, которую необходимо устранить.  
  
 В следующих подразделах описывается набор средств контроля и настройки, а также проблемы, для устранения которых они используются.  
  
 [Выявление узких мест](../../relational-databases/performance/identify-bottlenecks.md)  
  
 [Отслеживание использования памяти](../../relational-databases/performance-monitor/monitor-memory-usage.md)  
  
  
