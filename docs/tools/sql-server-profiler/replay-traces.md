---
title: Воспроизведение трассировок | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
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
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: fe0132fa04e2201a66c64e672b074d380a831b94
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733372"
---
# <a name="replay-traces"></a>Воспроизведение трассировок
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Воспроизведением называется возможность повторить действие, захваченное в трассировке. После создания или редактирования трассировки ее можно сохранить в файл и позже воспроизвести. Приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] позволяет воспроизводить трассировку с одного компьютера. При высокой рабочей нагрузке используйте программу распределенного воспроизведения, которая позволяет воспроизводить данные трассировки с нескольких компьютеров.  
  
 В этом разделе описывается использование возможностей воспроизведения приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Дополнительные сведения о программе распределенного воспроизведения см. в разделе [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md).  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] содержит в себе многопоточный модуль воспроизведения, который имитирует соединения пользователей и проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Воспроизведение хорошо помогает при диагностике ошибок приложений и процессов. После изучения проблемы и внесения необходимых изменений можно снова запустить трассировку, которая обнаружила эту проблему, на исправленном приложении или процессе, а затем, после воспроизведения исходной трассировки, сравнить результаты.  
  
 Воспроизведение трассировки поддерживает отладку с использованием параметров **Точка останова** и **Выполнить до курсора** в меню [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Replay** menu. Эти команды особенно помогают при анализе длинных скриптов, позволяя разбить воспроизведение на короткие сегменты, которые могут быть последовательно проанализированы.  
  
 Сведения о том, какие разрешения необходимы для воспроизведения трассировки, см. в статье [Разрешения, необходимые для запуска приложения SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Требования к воспроизведению](../../tools/sql-server-profiler/replay-requirements.md)|Описывает события, которые могут быть включены в определение трассировки для последующего воспроизведения в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Параметры воспроизведения (приложение SQL Server Profiler)](../../tools/sql-server-profiler/replay-options-sql-server-profiler.md)|Описывает параметры, устанавливаемые в диалоговом окне **Конфигурация воспроизведения** приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Вопросы воспроизведения трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/considerations-for-replaying-traces-sql-server-profiler.md)|Описывает события трассировки, которые не могут быть воспроизведены в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , и влияние воспроизведения на производительность работы сервера.|  
  
## <a name="see-also"></a>См. также:  
 [Распределенное воспроизведение SQL Server](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  
