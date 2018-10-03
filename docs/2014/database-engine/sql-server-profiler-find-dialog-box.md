---
title: SQL Server Profiler — диалоговое окно «Найти» | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.find.f1
helpviewer_keywords:
- Find dialog box
ms.assetid: dfaeec04-93d3-4214-9fc1-38b80179b36b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 23bbfd748bcb649e5f7d103683d20413764a62a8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48078934"
---
# <a name="sql-server-profiler---find-dialog-box"></a>Приложение SQL Server Profiler — диалоговое окно «Поиск»
  Диалоговое окно **Поиск** предназначено для поиска в трассировках по заданным символам или словам. Чтобы отменить поиск во время выполнения, нажмите клавишу ESC.  
  
 Чтобы открыть это диалоговое окно в приложении [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], в меню **Правка** выберите команду **Найти**.  
  
## <a name="options"></a>Параметры  
 **Найти**  
 Введите текст, который требуется найти. Условию поиска соответствует любая строка, содержащая заданную строку. Например, условию поиска строки «Completed» соответствует строка «SQL:BatchCompleted». Знаки подстановки (*, ? и т. д.) не поддерживаются.  
  
 **Искать в столбце**  
 Щелкните столбец данных, в котором нужно искать, либо выберите **\<все столбцы>**, чтобы искать во всех столбцах данных трассировки.  
  
 **Учитывать регистр**  
 Поиск текста в том же регистре, что и в поле **Найти** . Чтобы искать в трассировке строки как в верхнем, так и в нижнем регистре, снимите этот флажок.  
  
 **Слово целиком**  
 Ограничение поиска целыми словами. Чтобы найти символы в слове, снимите флажок **Слово целиком** .  
  
 **Следующий**  
 Ищет следующее вхождение символов, указанных в поле **Найти** .  
  
 **Найти ранее**  
 Производит поиск в трассировке в обратном направлении, чтобы найти предыдущее вхождение символов, указанных в поле **Найти** .  
  
## <a name="see-also"></a>См. также  
 [Поиск значения или столбца данных во время трассировки &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md)   
 [Создать трассировку &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)   
 [Открытие таблицы трассировки (приложение SQL Server Profiler)](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)   
 [Открытие файла трассировки (приложение SQL Server Profiler)](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)   
 [Шаблоны и разрешения приложения SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [Приложение SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
