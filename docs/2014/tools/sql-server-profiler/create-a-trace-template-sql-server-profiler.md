---
title: Создание шаблона трассировки (приложение SQL Server Profiler) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- templates [SQL Server], traces
- trace templates [SQL Server]
- saving trace template
ms.assetid: 025868b0-3790-4cda-8757-5a58327bfba0
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: eb91515468fc7c54c1223246f4870589f6a6bd51
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097389"
---
# <a name="create-a-trace-template-sql-server-profiler"></a>создать шаблон трассировки (приложение SQL Server Profiler)
  В этом подразделе описывается создание нового шаблона трассировки при помощи [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-create-a-trace-template"></a>Создание шаблона трассировки  
  
1.  В меню **Файл** укажите пункт **Шаблоны**, а затем выберите **Создать шаблон**.  
  
2.  В диалоговом окне **Свойства шаблона трассировки** выберите тип сервера из списка **Выберите тип сервера**.  
  
3.  В окне **Имя нового шаблона** введите имя шаблона.  
  
4.  При необходимости выберите **Использовать существующий шаблон в качестве основы**, а затем выберите шаблон из списка.  
  
     Все события, столбцы данных и фильтры изначально устанавливаются заданными в выбранном шаблоне.  
  
5.  При необходимости выберите **Применять как шаблон по умолчанию для выбранного типа сервера**.  
  
6.  На вкладке **Выбор событий** добавьте, удалите или измените события, столбцы данных или фильтры.  
  
7.  В меню **Выбор событий**используйте сетку для добавления или удаления событий и столбцов данных в файле трассировки следующим образом:  
  
    -   Чтобы добавить событие, разверните соответствующую категорию событий в столбце **События** и выберите имя события.  
  
    -   При добавлении события все относящиеся к нему столбцы данных включаются автоматически. Чтобы удалить столбец данных для события из трассировки, снимите флажок в столбце данных для этого события.  
  
    -   Чтобы добавить фильтры, щелкните имя столбца данных и определите критерии фильтра в диалоговом окне **Изменение фильтра** . Также можно щелкнуть имя столбца данных правой кнопкой мыши и выбрать пункт **Изменить фильтр столбца** , чтобы открыть диалоговое окно **Изменение фильтра** . Нажмите кнопку **ОК** , чтобы добавить фильтр.  
  
8.  Нажмите кнопку **Сохранить.**  
  
## <a name="see-also"></a>См. также  
 [Указать столбцы событий и данных для файла трассировки &#40;SQL Server Profiler&#41;](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)   
 [Извлечение шаблона из выполняемой трассировки (приложение SQL Server Profiler)](derive-a-template-from-a-running-trace-sql-server-profiler.md)   
 [Извлечение шаблона из файла трассировки или таблицы трассировки (приложение SQL Server Profiler)](derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)   
 [Шаблоны и разрешения приложения SQL Server Profiler](sql-server-profiler-templates-and-permissions.md)   
 [Приложение SQL Server Profiler](sql-server-profiler.md)  
  
  