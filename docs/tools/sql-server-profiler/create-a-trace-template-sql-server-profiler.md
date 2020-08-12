---
title: Создание шаблона трассировки
titleSuffix: SQL Server Profiler
description: Сведения о том, как создать шаблон трассировки в SQL Server Profiler. Сведения о том, как добавлять фильтры в шаблон и добавлять или удалять события и столбцы данных.
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 025868b0-3790-4cda-8757-5a58327bfba0
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: af272f50f281a8c3a564913cfb91be8abcab2898
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774870"
---
# <a name="create-a-trace-template-sql-server-profiler"></a>создать шаблон трассировки (приложение SQL Server Profiler)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
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
  
8.  Нажмите кнопку **Сохранить**.  
  
## <a name="see-also"></a>См. также:  
 [Указание столбцов событий и данных для файла трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)   
 [Извлечение шаблона из выполняемой трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md)   
 [Извлечение шаблона из файла трассировки или таблицы трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)   
 [Шаблоны и разрешения приложения SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
