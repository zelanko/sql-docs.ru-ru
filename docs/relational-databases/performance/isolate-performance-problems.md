---
title: Локализация проблем производительности | Документация Майкрософт
description: Использование SQL Server Profiler и системного монитора для отслеживания и устранения проблем с Transact-SQL, приложениями, оборудованием и системой.
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
author: WilliamDAssafMSFT
ms.author: wiassaf
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ed6728b164ab0d8562965935ad869c767a8a9961
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97460327"
---
# <a name="isolate-performance-problems"></a>Локализация проблем производительности
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
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
  
  
