---
title: Воспроизведение скрипта на языке Transact-SQL
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: df6664f31f092c6c773614c2a363e66a0b925259
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75307475"
---
# <a name="replay-a-transact-sql-script-sql-server-profiler"></a>воспроизвести скрипт на языке Transact-SQL (приложение SQL Server Profiler)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

При тестировании возможных решений для устранения ошибки производительности используйте приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для воспроизведения скриптов на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] и сравните производительность до внесения изменений и после внесенных изменений.  
  
### <a name="to-replay-a-transact-sql-script"></a>Воспроизведение скрипта на языке Transact-SQL  
  
1.  В меню **Файл** выберите **Открыть**и щелкните **Файл скрипта**.  
  
2.  Выберите файл скрипта на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] , который нужно открыть. Убедитесь, что скрипт на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] содержит события, необходимые для воспроизведения. Дополнительные сведения см. в разделе [Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md).  
  
3.  В меню **Воспроизведение** выберите **Пуск**и подключитесь к серверу, на котором нужно воспроизвести скрипт.  
  
4.  В диалоговом окне **Конфигурация воспроизведения** проверьте настройки и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Воспроизведение трассировок](../../tools/sql-server-profiler/replay-traces.md)   
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
