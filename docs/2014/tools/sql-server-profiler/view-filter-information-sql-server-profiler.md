---
title: Просмотр сведений о фильтре (приложение SQL Server Profiler) | Документы Microsoft
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
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: 8d002dea-376a-452c-b3ca-3e93656ed75f
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7936ad4df64746697b5c9d0ff8f2be1c7a5cbef1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099705"
---
# <a name="view-filter-information-sql-server-profiler"></a>просмотреть сведения о фильтре (приложение SQL Server Profiler)
  В этом разделе описывается, как просмотреть фильтры столбцов данных для классов событий, используя приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-view-filter-information"></a>Просмотр сведений о фильтре  
  
1.  Откройте файл трассировки, таблицу трассировки или скрипт SQL и в меню **Файл** выберите пункт **Свойства**. Пропустите этот шаг, если шаблон трассировки редактируется или создается новая трассировка.  
  
2.  На вкладке **Выбор событий** правой кнопкой мыши щелкните имя столбца данных для фильтра, который необходимо просмотреть, и выберите команду **Изменить фильтр столбца**.  
  
3.  В диалоговом окне **Изменение фильтра** разверните операторы сравнения фильтра, чтобы просмотреть присвоенное значение для указанного критерия. Повторите шаги 2 и 3 относительно всех столбцов, для которых необходимо просмотреть сведения о фильтре.  
  
> [!NOTE]  
>  Операторы сравнения с присвоенными значениями выделены полужирным шрифтом.  
  
## <a name="see-also"></a>См. также  
 [Приложение SQL Server Profiler](sql-server-profiler.md)  
  
  