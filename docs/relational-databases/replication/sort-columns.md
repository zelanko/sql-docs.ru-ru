---
title: "Сортировка столбцов | Документация Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.monitor.sortcolumns.f1
ms.assetid: 66b44b6c-10a5-4e3f-a97b-7568609c88ac
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a409aaee6b079621d8eee5c48766756e07d40604
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="sort-columns"></a>Сортировка столбцов
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Диалоговое окно **Сортировка столбцов** позволяет сортировать сетки в мониторе репликации по значению одного или нескольких столбцов. (Отсортировать по одному столбцу можно, щелкнув его заголовок в сетке монитора репликации). Например, чтобы отсортировать подписки на вкладке **Все подписки** по состоянию, а затем по типу соединения, выполните следующие действия.  
  
1.  В первой строке сетки выберите **Состояние** в столбце **Имя столбца** и значение в столбце **Порядок сортировки** .  
  
2.  Во второй строке сетки выберите **Тип соединения** в столбце **Имя столбца** и значение в столбце **Порядок сортировки** .  
  
## <a name="options"></a>Параметры  
 **Имя столбца**  
 Имя столбца, по которому нужно выполнить сортировку. Можно выполнить сортировку по одному или нескольким столбцам. Нельзя выполнить сортировку по столбцам **Текущая средняя производительность** и **Худшая производительность в данный момент** на вкладке **Публикации** из-за способа вычисления значений в этих столбцах.  
  
 **Порядок сортировки**  
 Укажите значение **По возрастанию** или **По убыванию**.  
  
 **Очистить все**  
 Удалите все строки из сетки сортировки. Для удаления одной строки выделите строку и нажмите клавишу «DELETE».  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за репликацией](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
