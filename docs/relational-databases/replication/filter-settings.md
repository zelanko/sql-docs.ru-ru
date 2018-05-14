---
title: Настройки фильтра | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.filtersettings.f1
ms.assetid: 1b401d7d-db8a-4ba1-acb1-b8dec14e3311
caps.latest.revision: 6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 39d6e1726fb30c6ca9032829bde63193fef10dd6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="filter-settings"></a>Настройки фильтра
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Диалоговое окно **Настройки фильтра** позволяет определить фильтры для сеток монитора репликации. Например, чтобы показать на вкладке **Все подписки** только активные подписки, выберите **Состояние** в столбце **Имя столбца** , **Равен** в столбце **Оператор** и **Активна** в столбце **Значение1** . После определения фильтра, основанного на одном или нескольких столбцах, этот фильтр применяется так, чтобы в сетке отображалось только подмножество строк, удовлетворяющих критериям фильтрации.  
  
## <a name="options"></a>Параметры  
 **Имя столбца**  
 Имя столбца, по которому нужно выполнить фильтрацию. Фильтрацию можно выполнять по одному или нескольким столбцам.  
  
 **Оператор**  
 Выберите оператор для фильтра, например **Меньше**или Равно.  
  
 **Значение1** и **Значение2**  
 Введите или выберите значение для фильтра. Для большинства операторов нужно только значение в первом столбце **Значение1** , но для операторов **В диапазоне** и **Вне диапазона** требуется значение столбца **Значение2** .  
  
 **Очистить фильтр**  
 Нажмите эту кнопку для очистки всех ранее определенных фильтров. Для удаления одного фильтра выделите строку фильтра и нажмите клавишу «DELETE».  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за репликацией](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
