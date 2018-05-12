---
title: Введение в мониторинг служб Analysis Services в SQL Server Profiler | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7b3c2dcec84956cd83c09a6c9be1d70975df67cc
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="introduction-to-monitoring-analysis-services-with-sql-server-profiler"></a>Введение в мониторинг служб Analysis Services при помощи приложения SQL Server Profiler
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] можно использовать для мониторинга событий, формируемых экземпляром служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. С помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]можно выполнять следующее:  
  
-   Проводить мониторинг производительности экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
-   Выполнять отладку инструкций многомерных выражений.  
  
-   Выявлять инструкции многомерных выражений, выполняющиеся слишком медленно.  
  
-   Проверять инструкции многомерных выражений на стадии разработки проекта в пошаговом режиме, чтобы убедиться, что код выполняется так, как ожидается.  
  
-   Устранять проблемы в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] с помощью перехвата событий на рабочей системе и воспроизведения их на отладочной. Этот подход полезно использовать при тестировании или отладке. Он позволяет пользователям использовать рабочую систему без помех.  
  
-   Выполнять аудит и отслеживание действий, происходящих в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Администратор по безопасности может просмотреть любое из событий аудита. Это включает успешную или неуспешную попытку входа, разрешения на доступ к инструкциям и объектам.  
  
-   Отображение на экране данных о зарегистрированных событиях или сбор и сохранение данных о каждом событии в файл или таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для дальнейшего анализа или воспроизведения. При воспроизведении данных можно повторно запустить сохраненные события в порядке их возникновения в реальном времени или пошаговом режиме.  
  
## <a name="using-sql-server-profiler"></a>Использование приложения SQL Server Profiler  
 Чтобы использовать приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для создания или воспроизведения трассировок, необходимо быть членом роли сервера служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Член роли сервера служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может запускать приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] из группы программ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в меню **Пуск** .  
  
 При использовании приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]обратите внимание на следующее:  
  
-   Определения трассировок хранятся в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] с использованием инструкции CREATE.  
  
-   Несколько трассировок можно запустить одновременно.  
  
-   Несколько соединений могут получать события из одной трассировки.  
  
-   Трассировка может продолжаться при остановке и перезапуске служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
    > [!NOTE]  
    >  Пароли в событиях трассировки скрыты и представлены в виде ******.  
  
 Чтобы обеспечить оптимальную производительность, используйте приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для мониторинга только наиболее важных событий. Мониторинг слишком многих событий приводит к перегрузке и может привести к избыточному увеличению размера файла или таблицы трассировки, особенно при длительном мониторинге. Кроме того, для ограничения количества собираемых данных и предотвращения увеличения трассировок используйте фильтры.  
  
## <a name="see-also"></a>См. также  
 [События трассировки служб Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)   
 [Создание трассировки приложения Profiler для воспроизведения & #40; Службы Analysis Services & #41;](../../analysis-services/instances/create-profiler-traces-for-replay-analysis-services.md)  
  
  
