---
title: "Установить максимальный размер для таблицы трассировки (приложение SQL Server Profiler) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- size [SQL Server], trace tables
- maximum table size for traces
ms.assetid: d0ae83e5-1c88-4a2e-be05-2c341280b978
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 733cbc9e74e9e9e56c7bcb918f8c695dd1304a7e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="set-a-maximum-table-size-for-a-trace-table-sql-server-profiler"></a>установить максимальный размер для таблицы трассировки (приложение SQL Server Profiler)
  В этом подразделе рассказывается о том, как задать максимальный размер таблицы трассировки при помощи приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-set-a-maximum-table-size-for-a-trace-table"></a>Установка максимального размера таблицы трассировки  
  
1.  В меню **Файл** выберите пункт **Создать трассировку**, а затем подключитесь к экземпляру SQL Server.  
  
     Отображается диалоговое окно **Свойства трассировки**.  
  
    > [!NOTE]  
    >  Если установлен параметр **Начать трассировку немедленно после установления соединения**, диалоговое окно **Свойства трассировки**не отображается, а вместо этого начинается трассировка. Чтобы отключить этот параметр, в меню **Сервис**выберите пункт **Параметры**и снимите флажок **Начать трассировку немедленно после установления соединения** .  
  
2.  В поле **Имя трассировки** введите имя трассировки.  
  
3.  В списке **Имя шаблона**выберите шаблон трассировки.  
  
4.  Установите флажок **Сохранить в таблицу**.  
  
5.  Подключитесь к серверу, на который будет записываться трассировка.  
  
     Откроется диалоговое окно **Целевая таблица** .  
  
6.  Выберите базу данных для трассировки из списка **База данных** .  
  
7.  В поле **Таблица** введите или выберите имя таблицы.  
  
8.  Установите флажок **Установить максимальное число строк** и укажите максимальное число строк для таблицы трассировки.  
  
    > [!NOTE]  
    >  Когда количество строк в таблице превысит указанный максимум, регистрация событий трассировки прекратится. Однако трассировка продолжится.  
  
## <a name="see-also"></a>См. также:  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  

