---
title: Воспроизведение сценария Transact-SQL (приложение SQL Server Profiler) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- scripts [SQL Server], traces
- replaying traces
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 58fa1914ae43a53c4efd8c65891a77419b5b5492
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37212194"
---
# <a name="replay-a-transact-sql-script-sql-server-profiler"></a>воспроизвести скрипт на языке Transact-SQL (приложение SQL Server Profiler)
  При тестировании возможных решений для устранения ошибки производительности используйте приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для воспроизведения скриптов на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] и сравните производительность до внесения изменений и после внесенных изменений.  
  
### <a name="to-replay-a-transact-sql-script"></a>Воспроизведение скрипта на языке Transact-SQL  
  
1.  В меню **Файл** выберите **Открыть**и щелкните **Файл скрипта**.  
  
2.  Выберите файл скрипта на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] , который нужно открыть. Убедитесь, что скрипт на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] содержит события, необходимые для воспроизведения. Дополнительные сведения см. в разделе [Replay Requirements](replay-requirements.md).  
  
3.  В меню **Воспроизведение** выберите **Пуск**и подключитесь к серверу, на котором нужно воспроизвести скрипт.  
  
4.  В диалоговом окне **Конфигурация воспроизведения** проверьте настройки и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Воспроизведение трассировок](replay-traces.md)   
 [Приложение SQL Server Profiler](sql-server-profiler.md)  
  
  
