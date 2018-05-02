---
title: Просмотр сведений о фильтре (приложение SQL Server Profiler) | Документы Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: sql-server-profiler
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: 8d002dea-376a-452c-b3ca-3e93656ed75f
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 04c9af7d7f050918c00af72165478a59aa76e0f9
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="view-filter-information-sql-server-profiler"></a>просмотреть сведения о фильтре (приложение SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В этом разделе описывается, как просмотреть фильтры столбцов данных для классов событий, используя приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-view-filter-information"></a>Просмотр сведений о фильтре  
  
1.  Откройте файл трассировки, таблицу трассировки или скрипт SQL и в меню **Файл** выберите пункт **Свойства**. Пропустите этот шаг, если шаблон трассировки редактируется или создается новая трассировка.  
  
2.  На вкладке **Выбор событий** правой кнопкой мыши щелкните имя столбца данных для фильтра, который необходимо просмотреть, и выберите команду **Изменить фильтр столбца**.  
  
3.  В диалоговом окне **Изменение фильтра** разверните операторы сравнения фильтра, чтобы просмотреть присвоенное значение для указанного критерия. Повторите шаги 2 и 3 относительно всех столбцов, для которых необходимо просмотреть сведения о фильтре.  
  
> [!NOTE]  
>  Операторы сравнения с присвоенными значениями выделены полужирным шрифтом.  
  
## <a name="see-also"></a>См. также:  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
