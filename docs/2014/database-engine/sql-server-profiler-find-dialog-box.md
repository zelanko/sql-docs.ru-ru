---
title: Диалоговое окно «SQL Server Profiler-Поиск» | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.find.f1
helpviewer_keywords:
- Find dialog box
ms.assetid: dfaeec04-93d3-4214-9fc1-38b80179b36b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 141cfe63151f65e171550beda1c20e232a6205e0
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84928685"
---
# <a name="sql-server-profiler---find-dialog-box"></a>Приложение SQL Server Profiler — диалоговое окно «Поиск»
  Диалоговое окно **Поиск** предназначено для поиска в трассировках по заданным символам или словам. Чтобы отменить поиск во время выполнения, нажмите клавишу ESC.  
  
 Чтобы открыть это диалоговое окно в приложении [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], в меню **Правка** выберите команду **Найти**.  
  
## <a name="options"></a>Варианты  
 **Найти**  
 Введите текст, который требуется найти. Условию поиска соответствует любая строка, содержащая заданную строку. Например, условию поиска строки «Completed» соответствует строка «SQL:BatchCompleted». Знаки подстановки (*, ? и т. д.) не поддерживаются.  
  
 **Искать в столбце**  
 Щелкните столбец данных для поиска или нажмите **\<All columns>** для поиска всех столбцов данных в трассировке.  
  
 **Учитывать регистр**  
 Поиск текста в том же регистре, что и в поле **Найти** . Чтобы искать в трассировке строки как в верхнем, так и в нижнем регистре, снимите этот флажок.  
  
 **Слово целиком**  
 Ограничение поиска целыми словами. Чтобы найти символы в слове, снимите флажок **Слово целиком** .  
  
 **Следующий**  
 Ищет следующее вхождение символов, указанных в поле **Найти** .  
  
 **Найти ранее**  
 Производит поиск в трассировке в обратном направлении, чтобы найти предыдущее вхождение символов, указанных в поле **Найти** .  
  
## <a name="see-also"></a>См. также:  
 [Поиск значения или столбца данных во время трассировки &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md)   
 [Создание SQL Server Profiler &#40;трассировки&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)   
 [Откройте таблицу трассировки &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)   
 [Откройте файл трассировки &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)   
 [Шаблоны и разрешения приложения SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [Приложение SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
