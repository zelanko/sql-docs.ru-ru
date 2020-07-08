---
title: Настройки фильтра | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.filtersettings.f1
ms.assetid: 1b401d7d-db8a-4ba1-acb1-b8dec14e3311
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 58750ffba9d8eb19c02ceb4870fda0ddffeb5a7d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85653134"
---
# <a name="filter-settings"></a>Настройки фильтра
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
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
 [Наблюдение за репликацией](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
