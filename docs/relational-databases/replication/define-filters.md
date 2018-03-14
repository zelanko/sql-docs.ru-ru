---
title: "Определение фильтров | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
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
- sql13.rep.replconflictviewer.definefilters.f1
helpviewer_keywords:
- Define Filters dialog box
ms.assetid: 1fa71d22-ce5a-4aae-ba05-4d755842aeac
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4baa09c02936eb9e67bbcbcbf2b69d70253a4111
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="define-filters"></a>Определение фильтров
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Диалоговое окно **Определение фильтров** позволяет определять фильтры, применяемые к конфликтам данных для просмотра подмножества этих конфликтов в данной сетке. Чтобы определить фильтр, выберите оператор из раскрывающегося списка **Оператор** , а затем введите значение. Например, чтобы просмотреть только те конфликты, в которых проигравшей стороной является сервер **ReplTest1**, выберите **Равно** из раскрывающегося списка **Оператор** и введите **ReplTest1** в первом столбце **Значение** .  
  
## <a name="options"></a>Параметры  
 **Оператор**  
 Выберите оператор для фильтра, например **Меньше**или Равно.  
  
 **Value**  
 Введите значение для фильтра. Для большинства операторов нужно только значение в первом столбце **Значение** , но для операторов **Между** и **Вне** необходимы значения в обоих столбцах **Значение** .  
  
 **Clear**  
 Нажмите эту кнопку для сброса всех ранее определенных фильтров.  
  
## <a name="see-also"></a>См. также:  
 [Средство просмотра конфликтов репликации (Майкрософт) (репликация слиянием)](../../relational-databases/replication/microsoft-replication-conflict-viewer-merge-replication.md)   
 [Средство просмотра конфликтов репликации (Майкрософт) (репликация транзакций)](../../relational-databases/replication/microsoft-replication-conflict-viewer-transactional-replication.md)  
  
  
