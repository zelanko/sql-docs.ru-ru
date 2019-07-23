---
title: Задание максимального размера для таблицы трассировки (приложение SQL Server Profiler) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- size [SQL Server], trace tables
- maximum table size for traces
ms.assetid: d0ae83e5-1c88-4a2e-be05-2c341280b978
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5c12f87a5c70050fa6de7cfec41ee81fe8496452
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68104194"
---
# <a name="set-a-maximum-table-size-for-a-trace-table-sql-server-profiler"></a>установить максимальный размер для таблицы трассировки (приложение SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
  
  
