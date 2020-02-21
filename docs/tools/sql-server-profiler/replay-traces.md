---
title: Воспроизведение трассировок
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: da958d3c-7f3e-44c9-aecc-8a9493bea7c0
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: 50ef296f7ce7198dc0e233aca08e33c5f1cf7af0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307460"
---
# <a name="replay-traces"></a>Воспроизведение трассировок

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Воспроизведением называется возможность повторить действие, захваченное в трассировке. После создания или редактирования трассировки ее можно сохранить в файл и позже воспроизвести. Приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] позволяет воспроизводить трассировку с одного компьютера. При высокой рабочей нагрузке используйте программу распределенного воспроизведения, которая позволяет воспроизводить данные трассировки с нескольких компьютеров.  
  
 В этом разделе описывается использование возможностей воспроизведения приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Дополнительные сведения о программе распределенного воспроизведения см. в разделе [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md).  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] содержит в себе многопоточный модуль воспроизведения, который имитирует соединения пользователей и проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Воспроизведение хорошо помогает при диагностике ошибок приложений и процессов. После изучения проблемы и внесения необходимых изменений можно снова запустить трассировку, которая обнаружила эту проблему, на исправленном приложении или процессе, а затем, после воспроизведения исходной трассировки, сравнить результаты.  
  
 Воспроизведение трассировки поддерживает отладку с использованием параметров **Точка останова** и **Выполнить до курсора** в меню **Воспроизведение** в [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Эти команды особенно помогают при анализе длинных скриптов, позволяя разбить воспроизведение на короткие сегменты, которые могут быть последовательно проанализированы.  
  
 Сведения о том, какие разрешения необходимы для воспроизведения трассировки, см. в статье [Разрешения, необходимые для запуска приложения SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Требования к воспроизведению](../../tools/sql-server-profiler/replay-requirements.md)|Описывает события, которые могут быть включены в определение трассировки для последующего воспроизведения в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Параметры воспроизведения (приложение SQL Server Profiler)](../../tools/sql-server-profiler/replay-options-sql-server-profiler.md)|Описывает параметры, устанавливаемые в диалоговом окне **Конфигурация воспроизведения** приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Вопросы воспроизведения трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/considerations-for-replaying-traces-sql-server-profiler.md)|Описывает события трассировки, которые не могут быть воспроизведены в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , и влияние воспроизведения на производительность работы сервера.|  
  
## <a name="see-also"></a>См. также:  
 [Распределенное воспроизведение SQL Server](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  
