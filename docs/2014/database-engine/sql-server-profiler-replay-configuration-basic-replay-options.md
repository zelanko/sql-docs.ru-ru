---
title: SQL Server Profiler — конфигурация воспроизведения (базовые параметры воспроизведения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.generaloptions.f1
helpviewer_keywords:
- Replay Configuration dialog box
ms.assetid: 85a1dec6-9bbc-477a-86c5-b463db9ebb31
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 379cb1ab2ed12ad8d5d835068bb68008fd6ca9af
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48088304"
---
# <a name="sql-server-profiler---replay-configuration-basic-replay-options"></a>Приложение SQL Server Profiler — конфигурация воспроизведения (базовые параметры воспроизведения)
  В диалоговом окне **Конфигурация воспроизведения** страница **Основные параметры воспроизведения** используется для указания способа воспроизведения файла или таблицы трассировки.  
  
 Для просмотра этого окна используйте приложение [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] для открытия файла трассировки или таблицы, содержащей события, предназначенные для воспроизведения. Дополнительные сведения см. в разделе [Replay Requirements](../tools/sql-server-profiler/replay-requirements.md). Когда файл или таблица трассировки открыты, в меню **Воспроизведение** щелкните **Начать**, a затем подключитесь к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , на котором необходимо воспроизвести трассировку.  
  
## <a name="options"></a>Параметры  
 **Сервер воспроизведения**  
 Отображает экземпляр сервера [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для подключения с целью воспроизведения.  
  
 **Изменить...**  
 Запускает диалоговое окно **Соединение с сервером** для подключения к другому серверу.  
  
 **Сохранить в файл**  
 Сохраняет результаты воспроизведения в файл. [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] отображает стандартное диалоговое окно, где можно указать расположение для сохранения файла.  
  
 **Сохранить в таблицу**  
 Сохраняет результаты воспроизведения в таблицу. Приложение [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] отображает диалоговое окно выбора таблицы, в котором можно указать место для сохранения таблицы.  
  
 **Число потоков воспроизведения**  
 Задайте число потоков воспроизведения, используемых одновременно. Чем больше это число, тем больше ресурсов потребляется при воспроизведении, но при этом воспроизведение ускоряется и возрастает его параллельность.  
  
 **Воспроизвести события в порядке трассировки**  
 Позволяет воспроизвести события последовательно. Используйте этот параметр, если трассировка воспроизводится с целью отладки.  
  
 **Воспроизвести события, используя несколько потоков**  
 Позволяет воспроизвести события параллельно. Этот параметр позволяет воспроизводить события быстрее, чем в последовательном режиме, но при этом отключается возможность отладки. События упорядочиваются по их системным идентификаторам процессов (SPID).  
  
 **Отобразить результаты воспроизведения**  
 Отображает результаты воспроизведения в приложении [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Воспроизведение таблицы трассировки &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)   
 [Воспроизведение файла трассировки (приложение SQL Server Profiler)](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)   
 [Воспроизведение трассировок](../tools/sql-server-profiler/replay-traces.md)  
  
  
