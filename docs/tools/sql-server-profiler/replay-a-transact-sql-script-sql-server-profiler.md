---
title: "Воспроизвести скрипт на языке Transact-SQL (SQL Server Profiler) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], replaying
- scripts [SQL Server], traces
- replaying traces
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 337569e89216611f972b0ac2305b42cc5c519826
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="replay-a-transact-sql-script-sql-server-profiler"></a>воспроизвести скрипт на языке Transact-SQL (приложение SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]При тестировании возможных решений для устранения ошибки производительности используйте [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] воспроизведение [!INCLUDE[tsql](../../includes/tsql-md.md)] сценарии и сравните производительность до и после внесенных изменений.  
  
### <a name="to-replay-a-transact-sql-script"></a>Воспроизведение скрипта на языке Transact-SQL  
  
1.  В меню **Файл** выберите **Открыть**и щелкните **Файл скрипта**.  
  
2.  Выберите файл скрипта на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] , который нужно открыть. Убедитесь, что скрипт на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] содержит события, необходимые для воспроизведения. Дополнительные сведения см. в разделе [Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md).  
  
3.  В меню **Воспроизведение** выберите **Пуск**и подключитесь к серверу, на котором нужно воспроизвести скрипт.  
  
4.  В диалоговом окне **Конфигурация воспроизведения** проверьте настройки и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Воспроизведение трассировок](../../tools/sql-server-profiler/replay-traces.md)   
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
