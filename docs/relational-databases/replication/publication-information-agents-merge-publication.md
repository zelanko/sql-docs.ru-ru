---
title: "Сведения о публикации, вкладка \"Агенты\" (публикация слиянием) | Документация Майкрософт"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.monitor.publicationinfo.downlevelagents.merge.f1
ms.assetid: 73ff590a-20da-4f10-b592-c60b7226d22b
caps.latest.revision: "23"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 70827d7aff090787f25f0cc8966e2647a51f9a9a
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="publication-information-agents-merge-publication"></a>Сведения о публикации, агенты (публикация слиянием)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Вкладка **Агенты** содержит общие сведения об агенте моментальных снимков для выбранной публикации.  
  
## <a name="options"></a>Параметры  
 Для получения более подробных сведений и задач, относящихся к агенту моментальных снимков, щелкните правой кнопкой мыши строку этого агента и выберите параметр в контекстном меню. Чтобы изменить способ отображения данных в сетке, щелкните правой кнопкой мыши сетку, а затем один из следующих параметров.  
  
-   **Сортировать**: сортировка по одному или нескольким столбцам в диалоговом окне **Сортировка столбцов** .  
  
-   **Выберите столбцы для отображения**: выбор столбцов для отображения и порядка их отображения в диалоговом окне **Выбор столбцов** .  
  
-   **Фильтр**: фильтрация строк в сетке на основании значений столбцов в диалоговом окне **Параметры фильтра** .  
  
-   **Очистить фильтр**: удаление всех параметров фильтра для сетки.  
  
 Настройки фильтра уникальны для каждой сетки. Выбор и сортировка столбцов применяются ко всем сеткам одного типа, как, например, сетка публикаций для каждого издателя.  
  
 **Состояние**  
 Состояние агента моментальных снимков. Возможные значения состояния показаны в следующем списке:  
  
-   Ошибка  
  
-   Попытка повторно выполнить неудачно завершившиеся команды  
  
-   Не выполняется  
  
-   Завершен  
  
 **Агент**  
 Агент моментальных снимков. Это единственный агент, связанный с публикацией слиянием. Агент слияния связан с подписками на эту публикацию. Дополнительные сведения см. в статье [Просмотр сведений и выполнение задач для агентов, связанных с подпиской (монитор репликации)](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md).  
  
 **Время последнего запуска**  
 Время последнего запуска агента.  
  
 **Длительность**  
 Продолжительность выполнения агента. Этот параметр представляет собой время, прошедшее с момента начала сеанса, если агент запущен в данный момент, или общее время, если агент был запущен ранее.  
  
 **Последнее действие**  
 Последнее действие выполнено во время самого последнего выполнения агента.  
  
## <a name="see-also"></a>См. также:  
 [Запуск монитора репликации](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Просмотр сведений и выполнение задач для публикации (монитор репликации)](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [Просмотр сведений и выполнение задач для агентов, связанных с публикацией (монитор репликации)](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md)   
 [Наблюдение за репликацией](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
