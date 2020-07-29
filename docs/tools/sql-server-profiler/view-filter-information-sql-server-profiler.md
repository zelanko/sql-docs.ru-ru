---
title: Просмотр сведений о фильтре
titleSuffix: SQL Server Profiler
description: Узнайте, как просматривать фильтры, которые SQL Server Profiler применяет к столбцам данных для ограничения отслеживаемых событий.
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 8d002dea-376a-452c-b3ca-3e93656ed75f
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 786b85d9c2f9707c26a18c3a7ddef27a127090c6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85759536"
---
# <a name="view-filter-information-sql-server-profiler"></a>просмотреть сведения о фильтре (приложение SQL Server Profiler)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

В этом разделе описывается, как просмотреть фильтры столбцов данных для классов событий, используя приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-view-filter-information"></a>Просмотр сведений о фильтре  
  
1.  Откройте файл трассировки, таблицу трассировки или скрипт SQL и в меню **Файл** выберите пункт **Свойства**. Пропустите этот шаг, если шаблон трассировки редактируется или создается новая трассировка.  
  
2.  На вкладке **Выбор событий** правой кнопкой мыши щелкните имя столбца данных для фильтра, который необходимо просмотреть, и выберите команду **Изменить фильтр столбца**.  
  
3.  В диалоговом окне **Изменение фильтра** разверните операторы сравнения фильтра, чтобы просмотреть присвоенное значение для указанного критерия. Повторите шаги 2 и 3 относительно всех столбцов, для которых необходимо просмотреть сведения о фильтре.  
  
> [!NOTE]  
>  Операторы сравнения с присвоенными значениями выделены полужирным шрифтом.  
  
## <a name="see-also"></a>См. также:  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
