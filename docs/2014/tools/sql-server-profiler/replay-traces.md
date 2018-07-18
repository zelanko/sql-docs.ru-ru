---
title: Воспроизведение трассировок | Документация Майкрософт
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
- SQL Server Profiler, replaying traces
- Run to Cursor option
- Toggle Breakpoint option
- traces [SQL Server], replaying
- replaying traces
- playback engine [SQL Server Profiler]
- events [SQL Server], replaying traces
- Profiler [SQL Server Profiler], replaying traces
ms.assetid: da958d3c-7f3e-44c9-aecc-8a9493bea7c0
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 76ef0ddde1f23d68e198854466a8b0abbbecc427
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37325284"
---
# <a name="replay-traces"></a>Воспроизведение трассировок
  Воспроизведением называется возможность повторить действие, захваченное в трассировке. После создания или редактирования трассировки ее можно сохранить в файл и позже воспроизвести. Приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] позволяет воспроизводить трассировку с одного компьютера. При высокой рабочей нагрузке используйте программу распределенного воспроизведения, которая позволяет воспроизводить данные трассировки с нескольких компьютеров.  
  
 В этом разделе описывается использование возможностей воспроизведения приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Дополнительные сведения о программе распределенного воспроизведения см. в разделе [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md).  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] содержит в себе многопоточный модуль воспроизведения, который имитирует соединения пользователей и проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Воспроизведение хорошо помогает при диагностике ошибок приложений и процессов. После изучения проблемы и внесения необходимых изменений можно снова запустить трассировку, которая обнаружила эту проблему, на исправленном приложении или процессе, а затем, после воспроизведения исходной трассировки, сравнить результаты.  
  
 Воспроизведение трассировки поддерживает отладку с использованием параметров **Точка останова** и **Выполнить до курсора** в меню [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Replay** menu. Эти команды особенно помогают при анализе длинных скриптов, позволяя разбить воспроизведение на короткие сегменты, которые могут быть последовательно проанализированы.  
  
 Сведения о том, какие разрешения необходимы для воспроизведения трассировки, см. в статье [Разрешения, необходимые для запуска приложения SQL Server Profiler](permissions-required-to-run-sql-server-profiler.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Требования к воспроизведению](replay-requirements.md)|Описывает события, которые могут быть включены в определение трассировки для последующего воспроизведения в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Параметры воспроизведения &#40;SQL Server Profiler&#41;](replay-options-sql-server-profiler.md)|Описывает параметры, устанавливаемые в диалоговом окне **Конфигурация воспроизведения** приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Вопросы воспроизведения трассировки &#40;SQL Server Profiler&#41;](considerations-for-replaying-traces-sql-server-profiler.md)|Описывает события трассировки, которые не могут быть воспроизведены в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , и влияние воспроизведения на производительность работы сервера.|  
  
## <a name="see-also"></a>См. также  
 [Распределенное воспроизведение SQL Server](../distributed-replay/sql-server-distributed-replay.md)  
  
  
