---
title: Воспроизведение сценария Transact-SQL (приложение SQL Server Profiler) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: sql-server-profiler
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], replaying
- scripts [SQL Server], traces
- replaying traces
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b21ed5c4b270a64c6eee3cc2d41cb4f1ba0518df
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="replay-a-transact-sql-script-sql-server-profiler"></a>воспроизвести скрипт на языке Transact-SQL (приложение SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] При тестировании возможных решений для устранения ошибки производительности используйте приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для воспроизведения сценариев [!INCLUDE[tsql](../../includes/tsql-md.md)] и сравните производительность до и после внесения изменений.  
  
### <a name="to-replay-a-transact-sql-script"></a>Воспроизведение скрипта на языке Transact-SQL  
  
1.  В меню **Файл** выберите **Открыть**и щелкните **Файл скрипта**.  
  
2.  Выберите файл скрипта на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] , который нужно открыть. Убедитесь, что скрипт на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] содержит события, необходимые для воспроизведения. Дополнительные сведения см. в разделе [Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md).  
  
3.  В меню **Воспроизведение** выберите **Пуск**и подключитесь к серверу, на котором нужно воспроизвести скрипт.  
  
4.  В диалоговом окне **Конфигурация воспроизведения** проверьте настройки и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Воспроизведение трассировок](../../tools/sql-server-profiler/replay-traces.md)   
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
